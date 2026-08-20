# Embeddings: Embedding Space and Static Embeddings

![rw-book-cover](https://developers.google.com/static/machine-learning/crash-course/images/mlcc-hero.png)

## Metadata
- Author: [[Google for Developers]]
- Full Title: Embeddings: Embedding Space and Static Embeddings
- Category: #articles
- Summary: Embeddings represent data as vectors in a lower-dimensional space, making it easier to analyze complex information. The position of items in this space indicates their similarity, though the meanings of the dimensions can be hard to interpret. Static embeddings, like those from the word2vec model, capture semantic relationships between words based on their context in language.
- URL: https://developers.google.com/machine-learning/crash-course/embeddings/embedding-space

## Full Document
An [**embedding**](https://developers.google.com/machine-learning/glossary#embedding-vector) is a vector representation of data in [**embedding space**](https://developers.google.com/machine-learning/glossary#embedding-space). Generally speaking, a model finds potential embeddings by projecting the high-dimensional space of initial data vectors into a lower-dimensional space. For a discussion of high-dimensional versus low-dimensional data, see the [Categorical Data](https://developers.google.com/machine-learning/crash-course/categorical-data/one-hot-encoding) module.

Embeddings make it easier to do machine learning on large [**feature vectors**](https://developers.google.com/machine-learning/glossary#feature-vector), such as the sparse vectors representing meal items discussed in the [previous section](https://developers.google.com/machine-learning/crash-course/embeddings). Sometimes the relative positions of items in embedding space have a potential semantic relationship, but often the process of finding a lower-dimensional space, and relative positions in that space, is not interpretable by humans, and the resulting embeddings are difficult to understand.

Still, for the sake of human understanding, to give an idea of how embedding vectors represent information, consider the following one-dimensional representation of the dishes hot dog, pizza, salad, shawarma, and borscht, on a scale of "least like a sandwich" to "most like a sandwich." The single dimension is an imaginary measure of "sandwichness."

![Figure 3. Along an axis of sandwichness, from least to most:
    borscht, salad, pizza, hot dog, shawarma.](https://developers.google.com/static/machine-learning/crash-course/images/embeddings_1D.png)Figure 3. Along an axis of sandwichness, from least to most: borscht, salad, pizza, hot dog, shawarma.
Where on this line would an apple strudel fall? Arguably, it could be placed between `hot dog` and `shawarma`. But apple strudel also seems to have an additional dimension of *sweetness* or *dessertness* that makes it very different from the other options. The following figure visualizes this by adding a "dessertness" dimension:

![Figure 4. Same image as before, but with a vertical axis of
    dessertness. Apple strudel is between hot dog and shawarma but high up on
    the horizontal axis, but higher up the desserteness axis.](https://developers.google.com/static/machine-learning/crash-course/images/embeddings_2D.png)Figure 4. Same image as before, but with a vertical axis of dessertness. Apple strudel is between hot dog and shawarma but high up on the horizontal axis, but higher up the desserteness axis.
An embedding represents each item in *n*-dimensional space with *n* floating-point numbers (typically in the range –1 to 1 or 0 to 1). The embedding in Figure 3 represents each food in one-dimensional space with a single coordinate, while Figure 4 represents each food in two-dimensional space with two coordinates. In Figure 4, "apple strudel" is in the upper-right quadrant of the graph and could be assigned the point (0.5, 0.3), whereas "hot dog" is in the bottom-right quadrant of the graph and could be assigned the point (0.2, –0.5).

In an embedding, the distance between any two items can be calculated mathematically, and can be interpreted as a measure of relative similarity between those two items. Two things that are close to each other, like `shawarma` and `hot dog` in Figure 4, are more closely related in the model's representation of the data than two things more distant from each other, like `apple strudel` and `borscht`.

To learn about different methods of calculating distance between embedding vectors, see  [Measuring Similarity from Embeddings](https://developers.google.com/machine-learning/clustering/dnn-clustering/supervised-similarity).
Notice also that in the 2D space in Figure 4, `apple strudel` is much farther from `shawarma` and `hot dog` than it would be in the 1D space, which matches intuition: `apple strudel` is not as similar to a hot dog or a shawarma as hot dogs and shawarmas are to each other.

Now consider borscht, which is much more liquid than the other items. This suggests a third dimension, *liquidness*, or how liquid a food might be. Adding that dimension, the items could be visualized in 3D in this way:

![Figure 5. Same image as before, but with a third axis of liquidness
    orthogonal to the other two, and borscht moved far along that axis.](https://developers.google.com/static/machine-learning/crash-course/images/embeddings_3D.png)Figure 5. Foods plotted by "sandwichness," "dessertness," and "liquidness."
Where in this 3D space would tangyuan go? It's soupy, like borscht, and a sweet dessert, like apple strudel, and most definitely not a sandwich. Here is one possible placement:

![Figure 6. Same image as before, but with tangyuan placed high on
    dessertness and liquidness and low on sandwichness.](https://developers.google.com/static/machine-learning/crash-course/images/embeddings_3D_tangyuan.png)Figure 6. Same image as before, but with tangyuan placed high on dessertness and liquidness and low on sandwichness.
Notice how much information is expressed in these three dimensions. You could imagine adding additional dimensions, like how meaty or baked a food might be, though 4D, 5D, and higher-dimensional spaces are difficult to visualize.

#### Real-world embedding spaces

In the real world, embedding spaces are *d*-dimensional, where *d* is much higher than 3, though lower than the dimensionality of the data, and relationships between data points are not necessarily as intuitive as in the contrived illustration above. (For word embeddings, *d* is often 256, 512, or 1024.[1](https://developers.google.com/machine-learning/crash-course/embeddings/embedding-space#fn1))

In practice, the ML practitioner usually sets the specific task and the number of embedding dimensions. The model then tries to arrange the training examples to be close in an embedding space with the specified number of dimensions, or tunes for the number of dimensions, if *d* is not fixed. The individual dimensions are rarely as understandable as "dessertness" or "liquidness." Sometimes what they "mean" can be inferred but this is not always the case.

Embeddings will usually be specific to the task, and differ from each other when the task differs. For example, the embeddings generated by a vegetarian versus non-vegetarian classification model will be different from the embeddings generated by a model that suggests dishes based on time of day or season. "Cereal" and "breakfast sausage" would probably be close together in the embedding space of a time-of-day model but far apart in the embedding space of a vegetarian versus non-vegetarian model, for example.

#### Static embeddings

While embeddings differ from task to task, one task has some general applicability: predicting the context of a word. Models trained to predict the context of a word assume that words appearing in similar contexts are semantically related. For example, training data that includes the sentences "They rode a burro down into the Grand Canyon" and "They rode a horse down into the canyon" suggests that "horse" appears in similar contexts to "burro." It turns out that embeddings based on semantic similarity work well for many general language tasks.

While it's an older example, and largely superseded by other models, the **word2vec** model remains useful for illustration. `word2vec` trains on a corpus of documents to obtain a single global embedding per word. When each word or data point has a single embedding vector, this is called a **static embedding**. The following video walks through a simplified illustration of `word2vec` training.

**Note**: **word2vec** can refer to both an algorithm for obtaining static word embeddings and a set of word vectors that were pretrained with that algorithm. It's used in both senses in this module. 
Research suggests that these static embeddings, once trained, encode some degree of semantic information, particularly in relationships between words. That is, words that are used in similar contexts will be closer to each other in embedding space. The specific embeddings vectors generated will depend on the corpus used for training. See T. Mikolov et al (2013), ["Efficient estimation of word representations in vector space"](https://arxiv.org/abs/1301.3781), for details.

The following exercises use TensorFlow's [Embedding Projector](https://projector.tensorflow.org/), set to **Word2Vec 10k** in the **Data** section of the left sidebar, which should be the default selection. This visualization flattens 10,000 `word2vec` static vectors into a 3D space. Collapsing dimensions in this way can be misleading, because the points closest to each other in the original high-dimensional space may appear farther apart in the 3D projection.

Click the rotating visualization to pause it.

In the right sidebar, you can search for a specific word in **Search**, set to **by: word**. For any search with multiple results, click the text of the word to show the word's *n* nearest neighbors and their distances to your target word. (Use either distance calculation). You can set *n* either by dragging the slider or typing in the box to the right of **neighbors**.

If you search for the first word in the first exercise below, then click the text of `iii`, the right sidebar should look like this:

![Figure 7. Right sidebar of Embedding Projector showing
    the nearest neighbors of iii: iv, ii, vi, vii, and viii, among others](https://developers.google.com/static/machine-learning/crash-course/embeddings/images/embedding_exercise_1.png)Figure 7. Right sidebar of Embedding Projector showing the nearest neighbors of iii: iv, ii, vi, vii, and viii, among others
**Note:** To show nearest neighbors on any search with multiple results, you must click the letters of the target word, and not the whitespace to either side. 
##### Exercise

In these experiments, you'll play with the `word2vec` embeddings in Tensorflow's [Embedding Projector](https://projector.tensorflow.org/).

###### Task 1

Try to find the 20 nearest neighbors for the following, and see where the groups fall in the cloud.

* `iii`, `third`, and `three`
* `tao` and `way`
* `orange`, `yellow`, and `juice`

What do you notice about these results?

**Click here for our answer**

###### Task 2

Try to figure out some characteristics of the training data. For example, try to find the 100 nearest neighbors for the following, and see where the groups are in the cloud:

* `boston`, `paris`, `tokyo`, `delhi`, `moscow`, and `seoul` (this is a trick question)
* `jane`, `sarah`, `john`, `peter`, `rosa`, and `juan`

**Click here for our answer**

###### Task 3

Embeddings aren't limited to words. Images, audio, and other data can also be embedded. For this task:

1. Open TensorFlow's [Embedding Projector](https://projector.tensorflow.org/).
2. In the left sidebar titled **Data**, choose **Mnist with images**. This brings up a projection of the embeddings of the [MNIST](https://developers.google.com/machine-learning/glossary#mnist) database of handwritten digits.
3. Click to stop the rotation and choose a single image. Zoom in and out as needed.
4. Look in the right sidebar for nearest neighbors. Are there any surprises?

* Why do some `7`s have `1`s as their nearest neighbor? Why do some `8`s have `9` as their nearest neighbor?
* Is there anything about the images on the edges of the projection space that seem different from the images in the center of the projection space?

Keep in mind that the model that created these embeddings is receiving image data, which is to say, pixels, and choosing a numerical vector representation for each image. The model doesn't make an automatic mental association between the image of the handwritten digit and the numerical digit itself.

**Click here for our answer**

**Key terms:** * [Embedding vector](https://developers.google.com/machine-learning/glossary#embedding-vector)
* [Embedding space](https://developers.google.com/machine-learning/glossary#embedding-space)

 
[Help Center](https://support.google.com/machinelearningeducation)

1. François Chollet, [Deep Learning with Python](https://www.manning.com/books/deep-learning-with-python) (Shelter Island, NY: Manning, 2017), 6.1.2. [↩](https://developers.google.com/machine-learning/crash-course/embeddings/embedding-space#fnref1)
