# Neo Kim (@systemdesignone): "If you want to become good at system design (in 3 weeks), learn these case studies… 🧵 1. How Amazon S3 Achieves 99.999999999% Durability: ↳ https://newsletter.systemdesign.one/p/amazon-s3-durability 2. How Google Docs Works: ↳ https://newsletter.systemdesign.one/p/how-does…"

![rw-book-cover](https://substackcdn.com/image/fetch/$s_!k2ht!,f_auto,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2F8ecdda16-0adb-490a-bec6-d95e27f83d00_1080x1350.png)

## Metadata
- Author: [[Substack]]
- Full Title: Neo Kim (@systemdesignone): "If you want to become good at system design (in 3 weeks), learn these case studies… 🧵 1. How Amazon S3 Achieves 99.999999999% Durability: ↳ https://newsletter.systemdesign.one/p/amazon-s3-durability 2. How Google Docs Works: ↳ https://newsletter.systemdesign.one/p/how-does…"
- Category: #articles
- Document Tags: [[ai]] [[inbox]] 
- Summary: This newsletter curates and explains key system design case studies to help you learn quickly. It lists real-world systems like Amazon S3, Google Docs, Kafka, Stripe, Uber, and more. The author celebrates 79,500+ subscribers and invites readers to join.
- URL: https://substack.com/@systemdesignone/note/c-171002018?r=5vkti0&utm_medium=ios&utm_source=notes-share-action

## Full Document
🎉 My newsletter has just reached 79,500+ subscribers!

It takes me many hours every week to track, curate, and dissect the latest AI developments. My secret trick is that I love doing it.

Join us!

[![](https://substackcdn.com/image/fetch/$s_!IB4l!,w_520,h_272,c_fill,f_auto,q_auto:good,fl_progressive:steep,g_auto/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2F7a99ebdc-88de-4602-9969-3dded45f1b10_1536x1024.png)](https://aimaker.substack.com/p/learn-ai-agents-notebooklm-customization-guide-video-podcast-flashcards-quiz)
[![](https://substackcdn.com/image/fetch/$s_!Y2bf!,w_520,h_272,c_fill,f_auto,q_auto:good,fl_progressive:steep,g_auto/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2F4cdcb025-bd92-46ad-92ec-db0370eca431_735x490.jpeg)](https://thestillwandering.substack.com/p/the-death-of-the-corporate-job)[![Still Wandering](https://substackcdn.com/image/fetch/$s_!RrBX!,w_36,h_36,c_fill,f_auto,q_auto:good,fl_progressive:steep,g_auto/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2F2aca1720-7e52-458e-a915-e67466f7b1ae_1024x1024.png)](https://thestillwandering.substack.com/p/the-death-of-the-corporate-job)[Still Wandering](https://thestillwandering.substack.com/)The death of the corporate job.
![](https://substackcdn.com/image/fetch/$s_!DzDi!,w_176,c_limit,f_auto,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack.com%2Fimg%2Fhome_page%2Fbenefit-1-transparent-bg.png)
[![](https://substackcdn.com/image/fetch/$s_!yBjH!,w_520,h_272,c_fill,f_auto,q_auto:good,fl_progressive:steep,g_auto/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2F6e75f1f5-de44-4f3f-b608-6ed90142bdd9_1199x903.jpeg)](https://thestillwandering.substack.com/p/the-epidemic-of-wasted-talent)
![](https://substackcdn.com/image/fetch/$s_!u9e1!,w_100,c_limit,f_auto,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack.com%2Fimg%2Fapp_page%2Fhighlight-2-v5.png)
[![](https://substackcdn.com/image/fetch/$s_!rfU8!,w_520,h_272,c_fill,f_auto,q_auto:good,fl_progressive:steep,g_auto/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2F2a23b686-4dee-4b4d-900e-6da8476a940e_1280x881.jpeg)](https://hardlyworking1.substack.com/p/max-weber-destroyed-ezra-klein-and)
[![](https://substackcdn.com/image/fetch/$s_!zP6F!,w_520,h_272,c_fill,f_auto,q_auto:good,fl_progressive:steep,g_auto/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2F4ab0cbe3-b476-4057-884a-9bf329d162b6_736x418.jpeg)](https://kyla.substack.com/p/ai-is-the-market-and-the-market-is)[![Kyla’s Newsletter](https://substackcdn.com/image/fetch/$s_!Z1gl!,w_36,h_36,c_fill,f_auto,q_auto:good,fl_progressive:steep,g_auto/https%3A%2F%2Fbucketeer-e05bbc84-baa3-437e-9518-adb32be77984.s3.amazonaws.com%2Fpublic%2Fimages%2F538171b2-1dfc-4483-9389-42422876dbf9_1280x1280.png)](https://kyla.substack.com/p/ai-is-the-market-and-the-market-is)[Kyla’s Newsletter](https://kyla.substack.com/)AI Is the Market, and the Market Is the Government
[![](https://substackcdn.com/image/fetch/$s_!fOmN!,w_1704,h_892,c_fill,f_auto,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2F618d59fa-9b8f-4814-8d16-f29c2f23ae53_371x371.png)](https://www.byhand.ai/)
[![](https://substackcdn.com/image/fetch/$s_!5VoP!,w_520,h_272,c_fill,f_auto,q_auto:good,fl_progressive:steep,g_auto/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2Fd3c8d7ce-f13c-4258-9e15-08a21ab925cf_1024x1555.heic)](https://museguided.substack.com/p/the-intimacy-illusion)
[![](https://images.unsplash.com/photo-1615332116901-cdde5c8abf60?crop=entropy&cs=tinysrgb&fit=max&fm=jpg&ixid=M3wzMDAzMzh8MHwxfHNlYXJjaHw1NHx8YnViYmxlJTIwdGVjaHxlbnwwfHx8fDE3NTkyNTExNTR8MA&ixlib=rb-4.1.0&q=80&w=1080)](https://www.derekthompson.org/p/this-is-how-the-ai-bubble-will-pop)
[![](https://substackcdn.com/image/fetch/$s_!rnMR!,w_520,h_272,c_fill,f_auto,q_auto:good,fl_progressive:steep,g_auto/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2Ff2969b93-bebb-443d-97c2-84ab78e65943_640x426.jpeg)](https://www.thealgorithmicbridge.com/p/its-obviously-the-chatbots)
[The U.S. is currently very poorly positioned to manage these complex problems. The Trump administration is more concerned with attacking perceived internal enemies than the outside world, and has stripped the bureaucracies that would allow it to begin to think straight about the problem. China has better capacities to think in the long term, at least in principle - but it is also coming into the game very late, with little experience, and subject to its own misunderstandings. The risks of unanticipated and mutually compounding fuck-ups are very, very high.](https://www.programmablemutter.com/p/china-has-copied-americas-grab-for?selection=41fb5041-a3f6-433d-8f40-06224603b525)

[![](https://substackcdn.com/image/fetch/$s_!RRxt!,w_520,h_272,c_fill,f_auto,q_auto:good,fl_progressive:steep,g_auto/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2F504475dd-623d-4859-8300-c8d092a575f9_6000x4000.jpeg)](https://www.theargumentmag.com/p/what-happens-to-college-towns-after)[![The Argument](https://substackcdn.com/image/fetch/$s_!Nq8A!,w_36,h_36,c_fill,f_auto,q_auto:good,fl_progressive:steep,g_auto/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2Fd6b65fcd-fe11-48ac-bfe4-6c0f746e1608_300x300.png)](https://www.theargumentmag.com/p/what-happens-to-college-towns-after)[The Argument](https://www.theargumentmag.com/)What happens to college towns after peak 18-year-old? 
[![](https://substackcdn.com/image/fetch/$s_!sVY0!,w_520,h_272,c_fill,f_auto,q_auto:good,fl_progressive:steep,g_auto/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2F38cde0b2-204c-45f7-a3a6-168663cf398b_1024x681.jpeg)](https://www.persuasion.community/p/its-the-internet-stupid)
**If you want to become good at system design**

**(in 3 weeks), learn these case studies… 🧵**

1. How Amazon S3 Achieves 99.999999999% Durability:

2. How Google Docs Works:

3. How Kafka Works:

4. How Real-Time Gaming Leaderboards Work:

5. How Meta Serverless Handles 11.5 Million Function Calls per Second:

6. How Cloudflare Supports 55 Million Requests per Second With 15 Postgres Clusters:

7. How Slack Works:

8. How Reddit Works:

9. How YouTube Was Able to Support 2.49 Billion Users With MySQL:

10. How Pastebin Works:

11. How Stripe Prevents Double Payment Using Idempotent API:

12. How Uber Computes ETA at Half a Million Requests per Second:

What else should make this list?
