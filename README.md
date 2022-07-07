# Movie_Recommendation_System
![image](https://user-images.githubusercontent.com/96436449/177886092-e8925aa8-2456-4c7f-8647-539d04d303d5.png)

Whether you realize it or not, recommendations drive so many of our decisions on daily basis. Be it obvious recommendations such as suggestions of new restaurants from friends, or a certain model of camera discussed in a blog, to less direct recommendations such as Netflix promoting shows you are likely to enjoy, or Amazon proposing other purchases that go well with what you are buying.

Let’s take Netflix as an example. Instead of having to browse through thousands of box sets and movie titles, Netflix presents you with a much narrower selection of items that you are likely to enjoy. This capability saves you time and delivers a better user experience. With this function, Netflix achieved lower cancellation rates, saving the company around a billion dollars a year.


**What is a Recommendation Engine?**

Simply put a Recommendation System is a filtration program whose prime goal is to predict the “rating” or “preference” of a user towards a domain-specific item. 
A recommendation engine can be of three types- collaborative recommendation engine, content-based recommendation engine, and hybrid recommendation engine.

**Collaborative Recommendation Engine:** In collaborative filtering, a recommendation system recommends a user the products based on the preferences of the other users with similar tastes

**Content Based Recommendation Engine:** As the name suggests, a content-based recommendation engine recommends the relevant content to the users based on their preferred features of other content.

**Hybrid recommendation engine:** Collaborative filtering and content-based filtering both are used widely in the recommendation systems. A recommendation engine with both the collaborative filtering and content-based filtering is called a hybrid recommendation engine.

![image](https://user-images.githubusercontent.com/96436449/177885547-a7bb4044-1855-49d5-8269-29923571257f.png)


For this Project, I have built Content based and Collaborative recommendation engine for a movie database. 
I have used datasets from Kaggle. 
Dataset Link:

https://www.kaggle.com/datasets/rounakbanik/the-movies-dataset

https://www.kaggle.com/datasets/tmdb/tmdb-movie-metadata


***Exploratory Data Analysis ***

Let’s explore the dataset to find some insights about the data. There are close to 670 users and 7000 movies and 10 unique values of ratings. 
![image](https://user-images.githubusercontent.com/96436449/177886177-c3616aa8-0c66-408b-8eba-ec845452b32f.png)

The data show that Forrest Gump is the most popular film.
![image](https://user-images.githubusercontent.com/96436449/177886228-d5d2db50-711a-4c17-8f17-e106fe95d2d7.png)

Here we can see that ratings are not evenly distributed among movies. The movie with id 356 [Forrest Gump] is the most rated movie, however it does not have more that 341 ratings.
![image](https://user-images.githubusercontent.com/96436449/177886333-77af1507-78dc-46f5-94f3-13484ddaa02e.png)


The histogram shows that most users (roughly 560 out of 671 –80%) have less than 250 ratings.
![image](https://user-images.githubusercontent.com/96436449/177886352-82dd7cb9-649d-459a-9701-60589a0df6dd.png)

The histogram shows that most movies (roughly 6500 out of 7063 –90%) have less than 30 ratings.
![image](https://user-images.githubusercontent.com/96436449/177886365-7b2e4bc9-2c99-4224-b2ce-43665e7aa52c.png)

The plot shows many movies having 0 ratings. Less number of users have rated movies. Most of the users have given rating between 3 to 4.
![image](https://user-images.githubusercontent.com/96436449/177886388-77c6ab9f-291b-4849-ad72-d685d9ff64af.png)

Average rating given to frequently watched films.
![image](https://user-images.githubusercontent.com/96436449/177886393-19f0a010-5ca1-429f-be01-0276285c8b73.png)



*Collaborative Filtering :*
Collaborative filtering is used by most recommendation systems to find similar patterns or information of the users, this technique can filter out items that users like based on the ratings or reactions by similar users.

![image](https://user-images.githubusercontent.com/96436449/177886461-566788df-456d-4afc-883b-a4dcbc6d6505.png)


There are two types of collaborative filtering.
1. Memory Based Approach 

Memory-based collaborative filtering uses all the data in the database to generate a prediction

**User-User-Based Collaborative Filtering**

In this type of filtering, we find the users that have the most similar preferences to the user we are making recommendations for and based on that group's preferences, make suggestions. It works around the premise that person A has similar tastes to person B and C. and both person B and C also like a certain item, then it is likely that person A would also like that new item.

![image](https://user-images.githubusercontent.com/96436449/177886583-6489c90d-8a4b-4c55-9f28-206819aa4bda.png)

**Item-Item-based Collaborative Filtering**

It assumes, if Item A and B receive similar reviews, either positive or negative, then however other people feel about A, they should feel the same way about B.
![image](https://user-images.githubusercontent.com/96436449/177886667-2f3ee364-4efb-47ab-9a7e-8f920820cfcb.png)


we need to convert this data into matrix of item for machine to understand. I filled Nan values with 0. 

 ![image](https://user-images.githubusercontent.com/96436449/177888053-2b2b70c8-928a-408e-9f50-9fe741c0060d.png)

Using corrwith function in Pandas, I calculated pair-wise correlations between rows and columns of a dataframe and used it for our prediction. 
Making recommendation for movie 'Shawshank Redemption, The (1994)’ : 
we will see which movies are similar to Shawshank Redemption, The (1994) movie based on rating. 

![image](https://user-images.githubusercontent.com/96436449/177888167-fbf90808-dd70-49f8-b675-ef9156820fd6.png)

**Model Based Filtering:**
Model-based collaborative filtering uses the data in the database to create a model that can then be used to generate predictions.
I used 2 collaborative-based filtering algorithms — K nearest neighbor and Singular value decomposition.

K Nearest Neighbor (KNN) : 
k nearest neighbour algorithm is used to represent movies. The distance among points are calculated based on cosine similarity — which is determined by the angle between two vectors (as shown in the diagram). Cosine similarity is preferred instead of Euclidean distance, because it suffers less when the dataset is high in dimensionality.
![image](https://user-images.githubusercontent.com/96436449/177888350-bc5cd05e-b583-4533-883e-4618684b0e3f.png)

![image](https://user-images.githubusercontent.com/96436449/177888342-fd3a494c-f049-410d-890f-89021b909a2b.png)

*Matrix sparsity*

A common challenge with real-world ratings data is that most users will not have rated most items, and most items will only have been rated by a small number of users. This results in a very empty or sparse DataFrame.
I found that our DataFrame is over 97% empty. This means that less than 3% of the DataFrame includes any data.
This can create problems if we were to use KNN with sparse data because KNN requires you to find the K nearest users that have rated the item and if there are not many neighbors therefore, we would have to return an average of all reviews because there is no other data. This will not actually take the similarities into account.

We will leverage the power of matrix factorization to deal with this sparsity. Matrix factorization is when we decompose the user-rating matrix into the product of two lower dimensionality matrices.

*Matrix Factorization — Singular Value Decomposition*

Singular Value Decomposition is a matrix factorization technique that decomposes the matrix into the product of lower dimensionality matrices, and then extracts the latent features from highest importance to lowest. Instead of iterating through individual ratings like KNN, it views the rating matrix as a whole. Therefore, it has less computation cost compared to KNN but also makes it less interpretable.

![image](https://user-images.githubusercontent.com/96436449/177888547-8e9fb266-4236-402f-bd4d-106bde928d6c.png)

Data preprocessing and Modelling :

Train-Test Split Evaluation
Here we will split the dataset into 80% for training and 20% for testing. Instead of iterating the model build 5 times as in cross validation, it will only train the model once and test it once. The result shows that SVD has less error.
![image](https://user-images.githubusercontent.com/96436449/177888669-c4aebc9e-9d9c-4572-8abe-eee25c9b6d0b.png)
![image](https://user-images.githubusercontent.com/96436449/177888675-cb5c5f33-261f-49ae-bebc-d74f14100f30.png)

Using this model, we can now predict rating for a user for a movie. 
For movie with ID 100, we get an estimated prediction of 2.43. 
This recommender system doesn't care what the movie is (or what it contains). It works purely on the basis of an assigned movie ID and tries to predict ratings based on how the other users have predicted the movie.



CONTENT BASED RECOMMENDATION SYSTEM: 

Content based filtering makes predictions of what the audience is likely to prefer based on the content properties, e.g., genres, language, video length.

![image](https://user-images.githubusercontent.com/96436449/177888748-17522d92-3257-48b9-83de-54b85108f61c.png)


Let’s build Collaborative recommendation engine using movie database. 
For this Project, I will build Content based recommendation engine using movie database. I will be using TMDB 5000 Movie Database from kaggle (https://www.kaggle.com/datasets/tmdb/tmdb-movie-metadata) 

It contains 2 CSV files.
tmdb_5000_credits.csv
tmdb_5000_movies.csv

In this recommender system, I will first find similarities based on only ‘Overview’ feature of the movie. As it consists of most of the description about the movie.

Next, I will use below features to find its similarity with other movies and predict similar movies.
cast - The name of lead and supporting actors.
crew - The name of Director, Editor, Composer, Writer etc
genre - The genre of the movie, Action, Comedy ,Thriller etc. 
keywords - The keywords or tags related to the movie. 


Let's use the ‘overview’ column first to recommend movies to the user. This column contains the plot of movies.
![image](https://user-images.githubusercontent.com/96436449/177888838-07a9b9a9-b824-4085-a339-776ef40b6ce5.png)

As you can see, we need to remove stopwords [a, the etc) before feeding them into the vectorizer.
We will use TfidfVectorizer here. 

TfidfVectorizer:

Simply using the word count as a feature value of a word really doesn’t reflect the importance of that word in a document. For example, if a word is present frequently in all documents in a corpus, then its count value in different documents is not helpful in discriminating between different documents. On other hand, if a word is present only in a few of documents, then its count value in those documents can help discriminating them from the rest of the documents. Thus, the importance of a word, i.e. its feature value, for a document not only depends upon how often it is present in that document but also how is its overall presence in the corpus. This notion of importance of a word in a document is captured by a scheme, known as the term frequency-inverse document frequency (tf-idf ) weighting scheme. 

The term frequency is a ratio of the count of a word’s occurrence in a document and the number of words in the document. Thus, it is a normalized measure that takes into consideration the document length. Let us show the count of word i in document j by tf_{ij}. The document frequency of word i represents the number of documents in the corpus with word i in them. Let us represent document frequency for word i by df_i. With N as the number of documents in the corpus, the tf-idf weight w_{ij} for word i in document j is computed by the following formula:
![image](https://user-images.githubusercontent.com/96436449/177888906-d33a1708-7b1e-4278-92ed-08a74e27b8f2.png)


We fed the Overview feature to the TfidfVectorizer . We used linear_kernel to calculate the matrix values. We can now get the top recommendations for a few movies. 
![image](https://user-images.githubusercontent.com/96436449/177888918-37fd146a-776b-4e9e-af7a-4859c68a545c.png)


![image](https://user-images.githubusercontent.com/96436449/177888924-748b9e56-a966-4c0d-8859-1d21596ce193.png)


We will now use "cast", "crew", "keywords", "genres" features to find similarities 


Data Wrangling :
In this data set, the movie data is present in the form of lists containing strings. 
Using few python function, I converted the stringfield data into a safe and usable structure.
I am going to build a recommender based on top 3 actors, the director, genres and keywords.
Let’s see how the data looks like after the above transformations. The next step would be to convert the above feature instances into lowercase and remove all the spaces between them.

![image](https://user-images.githubusercontent.com/96436449/177888971-8a7df59f-2ea1-4215-ba50-874c5e991c86.png)


In order to use textual data for predictive modeling, the text must be parsed to remove certain words – this process is called tokenization. These words need to then be encoded as integers, or floating-point values, for use as inputs in machine learning algorithms. This process is called feature extraction (or vectorization).
Scikit-learn’s CountVectorizer is used to convert a collection of text documents to a vector of term/token counts. It also enables the ​pre-processing of text data prior to generating the vector representation.

![image](https://user-images.githubusercontent.com/96436449/177889021-1c0d5df2-7649-4651-83b9-d30b84a19c6c.png)

Our movie recommendation engine works by suggesting movies to the user based on the metadata information. The similarity between the movies is calculated and then used to make recommendations. For that, our text data should be preprocessed and converted into a vectorizer using the CountVectorizer. 

As the name suggests, CountVectorizer counts the frequency of each word and outputs a 2D vector containing frequencies.

There exist several similarity score functions such as cosine similarity, Pearson correlation coefficient, etc. 
Here, I used the cosine similarity score as this is just the dot product of the vector output by the CountVectorizer.

Corpus creation: 
Let’s create a corpus containing all of the metadata information extracted to input into the vectorizer.


![image](https://user-images.githubusercontent.com/96436449/177889046-d309210b-33b6-4670-abe9-4e2be81e6784.png)

Our recommender system is now ready to recommend the similar movies based on the similar features.

![image](https://user-images.githubusercontent.com/96436449/177889071-025ace87-1808-4ecd-9f46-42e339b6fe6a.png)

