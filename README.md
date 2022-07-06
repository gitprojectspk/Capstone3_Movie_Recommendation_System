# Capstone3_Movie_Recommendation_System

Whether you realize it or not, recommendations drive so many of our decisions on daily basis. Be it obvious recommendations such as suggestions of new restaurants from friends, or a certain model of camera discussed in a blog, to less direct recommendations such as Netflix promoting shows you are likely to enjoy, or Amazon proposing other purchases that go well with what you are buying.

Let’s take Netflix as an example. Instead of having to browse through thousands of box sets and movie titles, Netflix presents you with a much narrower selection of items that you are likely to enjoy. This capability saves you time and delivers a better user experience. With this function, Netflix achieved lower cancellation rates, saving the company around a billion dollars a year.

**What is a Recommendation Engine?**
Simply put a Recommendation System is a filtration program whose prime goal is to predict the “rating” or “preference” of a user towards a domain-specific item. 
A recommendation engine can be of three types- collaborative recommendation engine, content-based recommendation engine, and hybrid recommendation engine.

**Collaborative Recommendation Engine:** In collaborative filtering, a recommendation system recommends a user the products based on the preferences of the other users with similar tastes
**Content Based Recommendation Engine:** As the name suggests, a content-based recommendation engine recommends the relevant content to the users based on their preferred features of other content.
**Hybrid recommendation engine:** Collaborative filtering and content-based filtering both are used widely in the recommendation systems. A recommendation engine with both the collaborative filtering and content-based filtering is called a hybrid recommendation engine.

For this Project, I will build Content based and Collaborative recommendation engine for a movie database. 
I will be using below datasets from Kaggle. 
Dataset Link:
https://www.kaggle.com/datasets/rounakbanik/the-movies-dataset

##Exploratory Data Analysis 
The Dataset has around 670 users and 7000 movies and 10 unique values of ratings. 
![image](https://user-images.githubusercontent.com/96436449/177659696-3d289158-8997-4e4a-a676-e67bf01f7aaa.png)

The data show that Forrest Gump is the most popular film.
![image](https://user-images.githubusercontent.com/96436449/177659836-06b02672-d68d-40ad-9d92-19431e1914a0.png)

Here we can see that ratings are not evenly distributed among movies. The movie with id 356 [Forrest Gump] is the most rated movie, however it does not have more that 341 ratings.
![image](https://user-images.githubusercontent.com/96436449/177659908-79de7807-a16b-4b52-bbfa-17853ff9ebad.png)

The histogram shows that most users (roughly 560 out of 671 –80%) have less than 250 ratings.
![image](https://user-images.githubusercontent.com/96436449/177659977-91021921-94fa-45e4-aeba-3b77bd0179e7.png)

The histogram shows that most movies (roughly 6500 out of 7063 –90%) have less than 30 ratings.
![image](https://user-images.githubusercontent.com/96436449/177659987-18d4b5b8-571b-4100-9861-6f276c5d2ea2.png)

The plot shows many movies having 0 ratings. Less number of users have rated movies. Most of the users have given rating between 3 to 4.
![image](https://user-images.githubusercontent.com/96436449/177660021-4aa3bc50-fd78-48a3-928c-3cfe897a73bf.png)
 Average rating given to frequently watched films.
![image](https://user-images.githubusercontent.com/96436449/177660036-9ff6f6f9-44d8-4602-aed9-9341e9c10f73.png)
