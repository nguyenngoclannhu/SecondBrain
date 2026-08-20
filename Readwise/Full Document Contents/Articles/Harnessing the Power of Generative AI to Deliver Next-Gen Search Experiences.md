# Harnessing the Power of Generative AI to Deliver Next-Gen Search Experiences

![rw-book-cover](https://i.ytimg.com/vi/HD_xreaLKb4/maxresdefault.jpg)

## Metadata
- Author: [[Google Cloud Tech]]
- Full Title: Harnessing the Power of Generative AI to Deliver Next-Gen Search Experiences
- Category: #articles
- Summary: Generative AI is transforming search experiences by organizing information into a unified system that makes it easy to find data across various formats. It utilizes semantic search technology, which understands content meaning rather than just keywords, improving retrieval accuracy. Enterprise search also offers features like summarization and multimodal search capabilities, enhancing productivity for users.
- URL: https://www.youtube.com/watch?v=HD_xreaLKb4&t=504s

## Full Document
[MUSIC PLAYING]KAZ SATO: Hi.Konnichiwa.I'm Kaz Sato, developer advocate for Google Cloud basedin Tokyo, Japan.HOLT SKINNER: Hi there.I'm Holt, also a developer advocate from the Google Cloudteam based in Austin, Texas.

One of the most challenging problemsto solve for an organization is the discoverability of information.Many times, data will be scattered across a bunchof different sources.Some might be in docs, some in databases, others in web pages.This makes it difficult for employees and customersto find just what they're looking for,whether it be internal data or on a public site.

There are three main challenges when building a search servicefor an enterprise.One is the service level requirements for any enterprisesearch service is high.Most companies don't have time or budgetto build a service that is capable of handlinglarge amounts of data in a wide variety of formatsall while being scalable and available 24/7.

The second challenge is that traditional keyword searchis too restricted, especially for userswho are familiar with AI-powered search and recommendationsevery day on YouTube, Instagram, and other apps.

These experiences are standard today,but it's much more difficult to implement.The third challenge is how to take advantage of generative AIand LLMs that are the pinnacle of information retrieval technology.Generative AI App Builder with enterprise searchfrom Google Cloud provides a simple setupservice that unifies all this information together and makes it straightforward to find.

Gen App Builder supports creating search enginesand chat interfaces.In this session, we'll be focusingon how to bring the power of search to your applications.It's an out-of-the-box solution, whichmeans you can deploy the fully managed search engine quickly.You don't have to build and lead an entire DevOps team to manage it.

It also utilizes semantic search,which provides the next-gen search experience,as we'll discuss later.Enterprise search provides LLM-based summarization,multimodal search, and chatbot integration,utilizing the latest in generative AI technology.

One of the greatest features of Gen App Builderis its ease of use for developers.Let's get started by looking at the onboarding experience.Keep in mind that this product is in early accessand the process might look slightly differentonce it's publicly available.Let's go through the process of setting up a basic search.

Engine for a public website, structured data, and unstructured data.First, you go to the Generative AI App Builder section in the Google Cloud Console.Then, you enable the API.Then, you select Create a Search Engine.Then, you give it a name and choose the data type.

Let's go through the website process first.After our search engine has been created, we just need to add the sites we want to include.If we open the advanced view, then we can exclude certain sites as well.For this example, let's search over the Google Cloud website, cloud.google.com.After setting the website, we now have a view of the URLs included in our search engine.You can also add more websites if you want.And just that fast, the search engine has already indexed our website.We can now click on Preview Search to try it out.The Preview page lets you try out your search engine in a browser.You can select a desktop or mobile view.A search for another Google Cloud product, Document AI, shows lots of relevant results for the product.We can also look for more detailed information like how to handle nested entities with Document AI.Now let's go back and create a new search engine, this time for structured data.

You can import the data from cloud storagein a structured format like JSON or from a BigQuery table.Let's import data from BigQuery.We'll use a public data set of moviesthat can be found on Kaggle.Importing this data requires very little setup,because the tool will figure out the schema for you.All you have to do is provide a link to the data,and it'll get ingested.

Once it finishes importing, we can test the search engine outjust like the previous one.The process for unstructured dataworks pretty similarly to structured data.Unstructured data doesn't follow a schema.Usually, this will be in the form of documents like PDFs.You create a search engine for unstructured data,then you can import files from cloud storage.

In this case, I'm importing Alphabet earnings reports.Once they're imported, you can search the filesto find specific information.Now we've explored the main types of search engines.Let's see how we can use them in our applications.

If we go to the Integration page,the console provides simple ways to integrate this new searchengine into an application.You can go to the API tab to get prewritten API calls and codesamples to integrate this into server applicationsor to build your own UI.Or you can copy and paste the HTML code in the widget tabto embed this directly into your website.

Going to the Configure menu from this pagetakes you to the widget settings whereyou can configure autocomplete, among other featuresfor the search engine widget.For structured data, we can also control more specific settings,such as the fields that are shown in the widget,like the movie title, description, ratings,and add thumbnail images.The Analytics page provides aggregate metricsfor the search engine, including session information,click-through rate, top queries, and devices.Now I'm going to toss it over to Kazto talk about semantic search.

KAZ SATO: So we have learned how enterprise search makesdevelopers' work much easier to build an AI-powered searchengine in a short time.In my part, I'd like to dive deeperinto this semantic search technology providedby enterprise search and how it would change the searchexperience in a wide variety of businesses.Many of you might ask, what is semantic search, by the way?

To understand what it is, we needto know the major shift undergoing in the IT industry.The traditional IT systems organize most dataas structured or tabular datausing simple keywords, labels, and categories in databasesand search engines.This has been the foundation of the user experienceyou'd have with the usual IT system for information.

Retrieval and recommendation.In contrast, AI-powered search services arrange datainto a simple data structure known as embedding.What is embedding?Let’s see how AI organizes data using embeddings.Once lined with specific content like text, images, tweets,or anything, AI creates a space calledembedding space, which is essentiallya map of the content's meaning.

AI can identify the location of each content on the map.That is what embedding is.Let’s take an example where our text discusses movies, music,and actors with a distribution of 10%, 2%, and 30%respectively.In this case, the AI can create an embedding with the threevalues 0.1, 0.02, and 0.3 in three-dimensional space.

Please note that this is a simplifiedexample for explanation.In reality, embedding space may have hundreds, or 1,000 or 2,000dimensions that can represent millionsof different categories of content.

And the AI can put content with similar meaningsclosely together in the same space.According to the Google machine learning crash course,embedding refers to the process of mappinghigh-dimensional raw data, such as images or text,which have tens or thousands of meters of dimensionsto a lower-dimensional space with hundredsor thousands of dimensions using deep learning models.

This is done to extract the meaningor semantics of the data and createa map of the content's meaning.And this is how Google organizes dataacross various services like Google Search, YouTube,Play, and many others to provide search resultsand recommendations with relevant content.

Embeddings can also be used to representdifferent types of things in businesses such as products,uses, user activities, conversations, music,and videos, signals from IoT sensors, and so on.

Let's see what real embedding space looks like.This is an embedding space for handwritten digital images.The embeddings are grouped based on how similartheir shapes are.

This is another embedding space for text sentences.Even though they are written in different languages,the sentences with similar meanings are grouped together.

Embeddings is an essential technologyutilized by Google Search to enhance its semantic searchabilities along with keyword search.

When a search query is entered, a language model based on BERTconverts it into an embedding.Web pages are also transformed into embeddings beforehand,enabling this service to conduct a vector search to locateyour web pages that match the query's intentionin the embedding space.

In the past, Google Search used only a keyword search model.This model sometimes gave you too many math textbooksfor students when someone searched for math practice.

Books for adults.But now, with semantic search, it can understand the intentionbehind the query and show the most helpful result at the top.This is a major shift in the IT industry,especially for information retrieval and recommendations.AI is now playing a crucial role in human-computerinteraction in those applications.It organizes data into embeddingswhich represent the user's intention,the meaning of a product, or many other thingsyou have in your business.This creates a new level of search experiencethat is becoming the new standard.Now, let's examine the semantic search experience providedto this enterprise search.

In this demo, we use 20 PDF files of Google research papersthat have a total of 400 pages.What if you are asked by your manager,"Can you investigate what video localizednarratives and annotated diversity are by scrutinizing 400 pages?"The solution is to import all files into enterprise searchand run a query.

Let's see how it works.After importing your files, just enter a text query.What are video localized narratives?Then, enterprise search quickly finds the relevant pagesfrom all the files by understandingthe text query and its intent, and alsothe meaning of all 400 pages.

It's not just a keyword search, but a searchby meaning with the AI-powered semantic searchtechnology we built with Google Search and language models.Also, you noticed that enterprise search generatesa summary of the query result. This summarizationis automatically done by a large languagemodel in the search engine. Instead of looking ateach page one by one, you can instantly get thegist of the search result. And you can trust it becausethe summary is generated from the real businessreports, not a generated text from nowhere by a chatbot.

This is the way you can use the power of the generative AIwith the responsibility for business use cases.Here's another demo. This is a sneak previewthat shows the possible usecases of enterprise search. Later this year,enterprise search will enable developers toimport their own embeddings as a search attribute.That means not only the document or web text;it can also execute semantic searchon any arbitrary medium or entity representedwith the embeddings. For example, if you importmultimodal embeddings that capture the meaningof the product images, then you can run a text queryfor finding the products by what the images mean,not only from the product description.This demo data set is provided by Mercari.

A marketplace app with over 50 million downloadsin the United States.It would be possible to enable such a rich userexperience with the multimodal semantic searchnot only for our retail businesses like Mercari,but also for financial, health care,or other various industries.

Let's recap what we covered this session.As Holt introduced, enterprise searchgives you an out of the box developer experience.Whether it's web pages or tabular dataor documents or PDF files, you can just bring them in.Enterprise search automatically builds the schema and searchindex for your data with a simple UI flow.

Second point is the semantic search.It searches by content's meaning, not just by keywords.Behind the scenes, the documents are converted into embeddings,enabling the next-gen search experience.The last point is the LLM capability.

With the summarization, enterprise searchsaves you time by eliminating the need to openand look at every page for understanding what you get with the search results.Instead, you can get the gist of themin seconds, dramatically improving the informationretrieval productivity in a wide variety of businesses.

Also, the multimodal feature will allowyou to search from images, text, and many different mediumsand entities in your businesses.These LLM features are based not on the virtual output.

Out of nowhere, outputs from AI chatbotsare grounded with business facts and responsibility.To get started with Gen App Builder and enterprise search,please check out the Gen AI page on cloud.google.com.

That was our system.Thank you so much.HOLT SKINNER: Thank you so much for watching,and enjoy the rest of I/O.[MUSIC PLAYING]
