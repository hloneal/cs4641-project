# cs4641-project
Georgia Tech CS 4641 Spotify Project

# Spotify Recommender System Report
Anthony Yu, Ashwin Kumar, Harrison O'Neal, Joseph Lee 

## Presentation Video Link:
https://www.youtube.com/watch?v=s6KjwkIbjnI

## Link to Code Repository
https://github.com/hloneal/cs4641-project

## Introduction: What are you trying to do? Articulate your objectives using absolutely no jargon.
- As more and more artists are releasing music using streaming platforms such as Spotify, Apple Music, Soundcloud, etc., it is difficult for these artists to get the exposure they need in order to become more popular. We want to create a recommender that takes in data of a user and the kind of music they listen to and generates recommendations for new songs and artists based on that data. Spotify has an enormous amount of content that is similar to the more popular content but simply goes unnoticed. This system is not just to promote the smaller artists that do not get their deserved exposure, but also diversify the kind of content that the user listens to as there may be different genres similar to the common ones.

## How is it done today, and what are the limits of current practice?
- Currently on Spotify, when on the page of a specific artist, there is a “Fans also like” section that provides other similar artists. The issue with this is that it only gives other top artists that people most likely have heard of already. For example, if you were to go to Justin Bieber’s page, it shows that fans also like Zayn and Shawn Mendes. Another issue with this is that the reasoning behind these recommendations is just shared fans as well as shared descriptions (in other media such as blogs and magazines). 

## What is new in your approach and why do you think it will be successful?
- In our Spotify Dataset from Kaggle, we have access to data about the artists and their popularity as well the specific musical aspects of their songs such as “acousticness”, “danceability”, “instrumentalness”, “speechiness”, etc. We have this data not only arranged by artists but also by genre and year. We want to create recommendations not just on artist popularity but as well as the musicality of their songs. For example if someone wants a similar song that is lively and more instrumental than speech based, we want to be able to give them an artist or genre that can fit that description. So far we only know a handful of clustering algorithms so we will try to implement the K-Means, GMM, and DBSCAN algorithms to cluster similar groups. We think it will be successful because it is backed by a Spotify dataset with actual user information so there will be objective similarities between what our project will recommend and what music the user listens to.

## Who cares? If you are successful, what difference will it make?
- As stated before if our project is successful, the smaller and less known artists will potentially increase their following. Because more and more people are able to upload their music to these streaming services, especially Spotify, many people can hopefully increase their popularity through our project. It would also help people who want to diversify their playlists from the mainstream and popular options.

## What are the risks?
- The risks involve using such a large dataset with many undesirable options. For example we don’t want to take a user who enjoys music with a lot of base and recommend another artist who only has one follower and one song that they released 10 years ago because their likely inactive, we would want to recommend an active artist that has some existing following already.

## Cost and Time
- There should not be any costs other than the time our team puts into the project. The project will take the rest of the semester (~1.5 months).
What are the midterm and final exams to check for success?


## References
- https://hpac.cs.umu.se/teaching/sem-mus-17/Reports/Madathil.pdf
- http://ceur-ws.org/Vol-2225/paper2.pdf
- http://make.cs.nthu.edu.tw/makeWeb/alp/alp_paper/A%20Music%20Recommendation%20System%20based%20on%20Music%20and%20User%20Grouping.pdf











# Spotify Recommender Final Report

## Summary Figures
<img width="400" alt="Screen Shot 2021-07-09 at 3 21 14 PM" src="https://user-images.githubusercontent.com/82124162/125127985-5ab92c80-e0cb-11eb-9464-05b07512b0ee.png"> <img width="400" alt="Screen Shot 2021-07-09 at 3 21 03 PM" src="https://user-images.githubusercontent.com/82124162/125127988-5b51c300-e0cb-11eb-8784-eca8e02b297d.png">
<img width="400" alt="Screen Shot 2021-07-09 at 3 20 59 PM" src="https://user-images.githubusercontent.com/82124162/125127994-5b51c300-e0cb-11eb-9d65-39d0987ab7e3.png">
<img width="400" alt="Screen Shot 2021-07-09 at 3 20 53 PM" src="https://user-images.githubusercontent.com/82124162/125127995-5bea5980-e0cb-11eb-90f7-c979fa1b68f8.png">
<img width="400" alt="Screen Shot 2021-07-09 at 3 20 43 PM" src="https://user-images.githubusercontent.com/82124162/125127997-5bea5980-e0cb-11eb-977c-00b6ef6402c0.png">
<img width="400" alt="Screen Shot 2021-07-09 at 3 20 38 PM" src="https://user-images.githubusercontent.com/82124162/125127998-5c82f000-e0cb-11eb-8153-3eefabed9a1c.png">
<img width="400" alt="Screen Shot 2021-07-09 at 3 20 33 PM" src="https://user-images.githubusercontent.com/82124162/125127999-5c82f000-e0cb-11eb-8d73-ac94636ea91d.png">
<img width="400" alt="Screen Shot 2021-07-09 at 3 20 27 PM" src="https://user-images.githubusercontent.com/82124162/125128000-5d1b8680-e0cb-11eb-8a03-0ac5f1ca64d3.png">
<img width="400" alt="Screen Shot 2021-07-09 at 3 20 22 PM" src="https://user-images.githubusercontent.com/82124162/125128001-5d1b8680-e0cb-11eb-8cfe-ee438de574dc.png">
<img width = "400" src="https://user-images.githubusercontent.com/85848075/128109771-28a1c958-1ec6-45a2-adac-19bc877c08da.png">



## Introduction/Background
Our dataset was a dataset containing 586,672 songs, each with 20 variables. These songs are songs on Spotify, and the dataset itself was found on Kaggle. We initially used 12 variables then brought it down to 10 variables. As shown above we have histograms outlining the distribution of the tracks by attribute. Using this above information, we determined which variables are the best to use. Based on those results we then used PCA to perform dimensionality reduction to make the data a little cleaner. As mentioned in the beginning of the report, we used this cleaned data to then apply unsupervised and supervised learning alorithms. 

## Methods
We have created a system to download our data locally and import the important metrics of over 500,000 songs into array structures. Additionally, we used K-Means to cluster the datapoints and determine the optimal number of clusters to use moving forward. This algorithm is used in multiple ways. Firstly, it can be used to find the optimal number of clusters based on our data using the losses curve. Through our experimentation, we have determined that 25 clusters are the optimal number computation-wise, as shown in the optimal clustering losses graph we have created. Additionally, the clusters themselves are the building blocks of our recommendation engine. If a user enjoys one song, then we can recommend another song found in the same cluster as they will be similar. Also when looking at the graphs above, we used components that have a lot of variability so that not all the tracks are potentially recommended even though they are not that similar. For example, we will not be using components such as speechiness or instrumentalness because most of the tracks are in the same range, so it would be difficult to differentiate them. However, components such as valence, energy, and danceability have a more spread out distribution so there is a little more variability and hopefully a more accurate recommendation. 

After performing K-Means to cluster the datapoints along with dimensionality reduction, we implemented multiple supervised learning techniques and studied their accuracies to choose the best method. The four methods we employed was linear regression, linear regression with PCA, linear regression with SVD, and random forest. We found the linear regression methods to only return an accuracy of 10 - 11%, while running random forest outputted a close to 95% accuracy. 

![Correct_importance](https://user-images.githubusercontent.com/87092746/128132460-af51a34f-b453-4e4c-9944-5a5ff6ce7e89.png)


## Results/Discussion
Through our implementations of unsupervised and supervised learning methods, we have created a system that can recommend a song with an accuracy that we honestly did not expect.  We determined our accuracy by using the clusters we found from the unsupervised learning as the training targets, and then we compared the testing results to the target clusters to determine if the supervised learning properly classified the datapoint or not.


<img width = "400" src="https://user-images.githubusercontent.com/82124162/128111174-b766ed5d-d6c5-4bc9-98a6-adf36e409697.png">
<img width = "400" src="https://user-images.githubusercontent.com/82124162/128109096-329b3c3e-caa9-465d-862e-eb02a935bc86.png">

## Challenges 
While creating our Spotify Recommender System, we faced a good number of challenges. The first challenge that we faced was with the dataset itself. The dataset was extremely large, containing 586672 songs with each song having 20 distinct variables. Since there were so many variables, we had difficulty deciding which variables to use and which ones to cut. The main challenge with the unsupervised learning portion of the project was that since our dataset was so large, our Kmeans algorithm took a really long time to run. This limited our progress because it would take hours to check if our code was running properly. The biggest challenge with the supervised learning was choosing which algorithm to use. After trying a number of different algorithms, we saw that the random forest algorithm had the best results. This made sense because our goal was to group and match appropriate songs rather than determine appropriate trends. The hardest challenge came up during the last stages of the project. After performing our dimensionality reduction, we found that 9 variables were the most efficient and effective variables to use. However in running a feature importance test, we found that the importance was very skewed towards one variable because it wasn’t normalized. Normalizing this one variable turned out to be extremely time consuming due to the sheer size of the dataset. After completing this normalization of the necessary variables, the variable importance became much more balanced with no one variable holding the majority of the decision power.
