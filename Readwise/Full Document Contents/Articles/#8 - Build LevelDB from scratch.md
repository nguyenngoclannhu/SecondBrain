# #8 - Build LevelDB from scratch

![rw-book-cover](https://substackcdn.com/image/fetch/$s_!KsiL!,w_1200,h_600,c_fill,f_jpg,q_auto:good,fl_progressive:steep,g_auto/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2F11eed45c-f946-4b80-a8bc-e744a318680b_1928x1468.jpeg)

## Metadata
- Author: [[Quang Hoang]]
- Full Title: #8 - Build LevelDB from scratch
- Category: #articles
- Summary: Tác giả tự xây dựng lại LevelDB bằng Go để hiểu và tái tạo một storage engine từ đầu. LevelDB lưu dữ liệu bằng Memtable + WAL trên RAM và SSTable trên đĩa, dùng Bloom filter, index và cache để tối ưu đọc. Compaction gộp SSTable để giảm file và xóa dữ liệu cũ, nhưng gây chi phí và read amplification.
- URL: https://quanghoang.substack.com/p/leveldb

## Full Document
[![Quang | Googler | Kỹ sư phần mềm](https://substackcdn.com/image/fetch/$s_!JRm5!,w_80,h_80,c_fill,f_auto,q_auto:good,fl_progressive:steep,g_auto/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2Fc0858f4e-1c8d-44ca-9c00-66449b4c8f53_1146x1146.png)](https://quanghoang.substack.com/)

##### Finally, I remembered my Substack password …

Bài viết thuộc series [50 Days of System Design](https://quanghoang.substack.com/t/50-days-of-system-design).

> 
> ```
> We are destroying software telling new programmers: “Don’t reinvent the wheel!”. But, reinventing the wheel is how you learn how things work, and is the first step to make new, different wheels.
>                                       - antirez -
> ```
> 

Cách tốt nhất để học về System Design có lẽ là tự build một hệ thống từ đầu. Gần đây mình đang làm một side project với mục tiêu là build 1 hệ thống backend hoàn chỉnh từ “[hư không](https://youtu.be/BkHCO8f2TWs?t=6)”, nghĩa là chỉ dùng gạch và vữa thôi, hạn chế sử dụng các framework, lib sẵn có. Hiện tại đã có:

* [Go-LevelDB](https://github.com/quangh33/Go-LevelDB): An On-disk Key-value Storage Engine like LevelDB
* [memkv](https://github.com/quangh33/memkv): An In-memory Key-Value database like Redis
* [Go-Kafka](https://github.com/quangh33/Go-Kafka): A Distributed, Fault-Tolerant Message Queue like Kafka

Bài hôm nay là để giới thiệu về LevelDB (và quảng cáo cho [Go-LevelDB](https://github.com/quangh33/Go-LevelDB), **please give it a Star** 🫣)

#### Lịch sử

LevelDB thực ra không hề xa lạ với người dùng Internet, mỗi lần bật Chrome/Cốccốc lên là bạn đang đọc dữ liệu từ LevelDB được “nhúng” trong trình duyệt. Các thông tin như cookie, local/session storage storage, lịch sử duyệt web, bookmark, … đều được Chrome lưu trữ trong LevelDB.

LevelDB được tạo ra bởi **Jeff Dean** và **Sanjay Ghemawat** vào năm 2011, những kỹ sư đã thiết kế Bigtable và MapReduce. LevelDB lấy cảm hứng mạnh mẽ từ [Bigtable](https://cloud.google.com/bigtable), đặc biệt là việc sử dụng LSM-Tree. Bigtable là một hệ thống khổng lồ và phụ thuộc vào cơ sở hạ tầng độc quyền của Google. LevelDB được thiết kế lại từ đầu với các khái niệm tương tự nhưng không có bất kỳ phụ thuộc nội bộ độc quyền nào của Google. Dự án đã được [open source trên Github](https://github.com/google/leveldb).

#### Kiến trúc của LevelDB

Dữ liệu được lưu trữ trong LevelDB dưới dạng (key, value). Tương tự như [Bitcask](https://quanghoang.substack.com/p/50-days-of-sd-bitcask), LevelDB hỗ trợ 3 thao tác:

* get(key)
* put(key, value)
* delete(key)

Kiến trúc của LevelDB là một ví dụ kinh điển về việc triển khai Log-Structured Merge Tree - LSM-Tree. Kiến trúc này gồm 4 phần chính:

Table with 3 columns and 4 rows. (column headers with buttons are sortable)| Write-Ahead Log (WAL) | Hard Disk Drive | Đảm bảo tính "Durability" của dữ liệu. Mọi thao tác Put, Delete đều được ghi lại vào WAL trước khi chúng được đưa vào Memtable. LevelDB có thể dùng WAL để hồi phục dữ liệu sau khi hệ thống gặp sự cố |
| Memtable | RAM | Là 1 cấu trúc dữ liệu trong RAM (Skip List) dùng để lưu trữ các thao tác Put, Delete mới nhất. Dữ liệu trong Memtable được sắp xếp tăng dần theo key |
| Immutable Memtable | RAM | Khi Memtable đạt đến kích thước tối đa, nó trở thành Immutable Memtable. Nó không thể ghi thêm và chờ được ghi xuống Hard Disk |
| SSTable (Sorted String Table) | Hard Disk Drive | Là các file read-only trên Hard disk, chứa các cặp (key, value) được sắp xếp theo key. Chúng được tạo ra bằng cách đẩy ("flush") Immutable Table xuống Hard Disk |

[Get the data](javascript:void(0))Created with [Datawrapper](https://www.datawrapper.de/_/SDMki)

[![](https://substackcdn.com/image/fetch/$s_!YrY6!,w_1456,c_limit,f_auto,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2Fee56309f-74d5-4438-8f6e-c17d10fdedcc_1488x874.png)](https://substackcdn.com/image/fetch/$s_!YrY6!,f_auto,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2Fee56309f-74d5-4438-8f6e-c17d10fdedcc_1488x874.png)
##### Write operations: Put(), Delete()

LevelDB tối ưu hóa việc ghi bằng cách chuyển các thao tác ngẫu nhiên thành tuần tự, tận dụng hiệu suất của HDD:

1. **Ghi vào WAL:** Dữ liệu mới được ghi tuần tự vào **Write-Ahead Log (WAL)** nhằm đảm bảo tính bền vững. Mỗi entry trong WAL có cấu trúc như sau:

[![](https://substackcdn.com/image/fetch/$s_!XIIs!,w_1456,c_limit,f_auto,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2F78efc974-8de3-410b-a322-6ed78e8101b9_1066x222.png)](https://substackcdn.com/image/fetch/$s_!XIIs!,f_auto,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2F78efc974-8de3-410b-a322-6ed78e8101b9_1066x222.png)
	* **Check Sum** là giá trị hash của mỗi entry để kiểm tra tính toàn vẹn của data.
	* **Seq Num** là 1 số id của mỗi thao tác ghi, Seq Num tăng dần theo thời gian, nghĩa là dữ liệu càng mới thì có Seq Num càng lớn.
	* **Op** là Put (0) hoặc Delete (1).
2. **Ghi vào Memtable:** Sau khi ghi vào WAL, dữ liệu được đưa vào **Memtable** (1 Skip List trong RAM).
3. **Flush**: Khi Memtable đạt kích thước nhất định (4MB) [[1]](#footnote-1-176825557) , nó được chuyển thành Immutable Memtable, đồng thời một Memtable mới được tạo để tiếp tục nhận thao tác ghi. Một thread mới được tạo ra để đọc dữ liệu từ Immutable Memtable và ghi tuần từ xuống 1 file SSTable mới [[2]](#footnote-2-176825557) .

##### Read operation: Get()

Vì data nằm rải rác ở cả RAM lẫn Hard Disk, LevelDB phải tìm kiếm ở nhiều thành phần, từ mới nhất đến cũ nhất:

1. **Memtable (Mới nhất)**: LevelDB kiểm tra **Memtable** và **Immutable Memtable** trước, vì chúng chứa dữ liệu mới nhất.
2. **SSTable**: Nếu không tìm thấy ở Memtable, nó tiếp tục tìm kiếm ở các SSTable, từ mới đến cũ. SSTable bao gồm nhiều Data Block, mỗi Data Block là 4KB các cặp (key, value). Lưu ý các cặp (key, value) trong SSTable được sắp xếp tăng dần theo key và giảm dần theo Seq Num (nghĩa là với cùng 1 key thì dữ liệu càng mới càng nằm ở đầu file):

[![](https://substackcdn.com/image/fetch/$s_!1xlB!,w_1456,c_limit,f_auto,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2F2054a5a6-7714-420e-92b9-da6274794ad1_1674x216.png)](https://substackcdn.com/image/fetch/$s_!1xlB!,f_auto,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2F2054a5a6-7714-420e-92b9-da6274794ad1_1674x216.png)

Để tối ưu việc tìm kiếm trong SSTable, LevelDB sử dụng nhiều cơ chế khác nhau:

* **Bloom Filter**: trước khi bắt đầu tìm kiếm trong SSTable, LevelDB kiểm tra xem key có tồn tại trong Bloom Filter [[3]](#footnote-3-176825557) , nếu không nó sẽ bỏ qua file SSTable hiện tại.
* **Index Block:** Index Block lưu lại key cuối cùng ở mỗi Data Block và vị trí tương ứng của nó trong SSTable. Để tìm kiếm 1 key, LevelDB chỉ cần đọc Index Block và tìm Data Block đầu tiên chứa key đó [[4]](#footnote-4-176825557)  (bằng Binary Search do key được sort tăng dần), sau đó duyệt tuần tự từng record trong Data Block đó.

```
type IndexEntry struct {
	LastKey InternalKey
	Offset  int64
	Size    int
}
```
* **Table Cache**: một LRU cache lưu lại Bloom Filter, I/O Handle của các SSTable trong RAM nhằm hạn chế việc phải đọc đi đọc lại các SSTable từ hard disk.

```
**tableCache \*lru.Cache[int, \*SSTableReader]**

type SSTableReader struct {
	file       *os.File
	index      []IndexEntry
	filter     *bloom.BloomFilter
	cmp        internalKeyComparable
	**blockCache \*lru.Cache[string, []byte]**
	fileNum    int
}
```
* **Block Cache:** một LRU cache lưu lại data của các Data Block trong RAM. Cả Table Cache và Block Cache đều hết sức đơn giản vì data trong SSTable là read-only nên không cần phải lo chuyện Cache Invalidation.

##### Compaction

Từ Read operation trên ta có thể thấy thời gian để đọc 1 key tỷ lệ thuận với số lượng SSTable. LevelDB tối ưu hóa quá trình này bằng 1 thread chạy nền, liên tục hợp nhất các SSTable để:

* loại bỏ các record đã bị xóa
* hợp nhất các dữ liệu đã cũ.
* giảm số lượng SSTable.

Ví dụ:

* SSTable\_1 (cũ) chứa: `{ k1:put: 1 }, { k2:put: 2 }`
* SSTable\_2 (mới) chứa: `{ k1:put: 100}, { k2:del: nil}, {k3:put: 3}`

Sau khi compact, SSTable\_3 mới sẽ chứa: `{k1:put: 100}, {k3:put: 3}`. SSTable\_1 và SSTable\_2 bị xóa.

Thuật toán Compaction của LevelDB khá phức tạp, tuy nhiên các bạn có thể hình dung phiên bản đơn giản [[5]](#footnote-5-176825557)  của nó giống bài [Merge K Sorted List](https://leetcode.com/problems/merge-k-sorted-lists/) trên Leetcode (hint: dùng 1 Min Heap kích thước K).

#### Benchmark

Side project của mình không đạt được tốc độ khủng của LevelDB nhưng QPS cũng khá cao:

```
Write Sequential: **321854** QPS        3.1 µs/op
Write Random:     **242365** QPS        4.1 µs/op
Read Sequential:  **112360** QPS        8.9 µs/op
Read Random:      **10861**  QPS        92  µs/op
```

#### Hạn chế

* LevelDB được thiết kế để chỉ có **một tiến trình (process)** có thể mở và truy cập cơ sở dữ liệu tại một thời điểm.
* Chi phí Compaction cao: Quá trình Compaction là một thao tác nền tiêu tốn tài nguyên lớn
* Read amplification: một thao tác Get() có thể cần phải kiểm tra dữ liệu ở nhiều nơi (memtable và nhiều file SSTable). Điều này làm cho hiệu suất đọc bị chậm hơn so với kiến trúc B-Tree truyền thống.

[1 [find in text]](#footnote-anchor-1-176825557)

<https://github.com/quangh33/Go-LevelDB/blob/main/db.go#L375>

[2 [find in text]](#footnote-anchor-2-176825557)

<https://github.com/quangh33/Go-LevelDB/blob/main/db.go#L234>

[3 [find in text]](#footnote-anchor-3-176825557)

<https://github.com/quangh33/Go-LevelDB/blob/main/sstable.go#L232>

[4 [find in text]](#footnote-anchor-4-176825557)

<https://github.com/quangh33/Go-LevelDB/blob/main/sstable.go#L243>

[5 [find in text]](#footnote-anchor-5-176825557)

<https://github.com/quangh33/Go-LevelDB/blob/main/compaction.go#L91>

###### Subscribe to Quang | Googler | Kỹ sư phần mềm

By Quang Hoang · Launched 2 years ago

How tech works under the hood

By subscribing, I agree to Substack's [Terms of Use](https://substack.com/tos), and acknowledge its [Information Collection Notice](https://substack.com/ccpa#personal-data-collected) and [Privacy Policy](https://substack.com/privacy).
