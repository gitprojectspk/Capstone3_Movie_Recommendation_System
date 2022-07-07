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



***Collaborative Filtering :***
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
![image](https://user-images.githubusercontent.com/96436449/177887935-770840ec-06e0-4114-8bbb-5262cf3cea32.png)
