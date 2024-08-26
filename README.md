# Documentation
## Objective:
We have to create a recommendation system that, given a movie, outputs some movies(say, 10) that are similar to the input movie. Recommendation Systems are a type of information filtering systems as they improve the quality of search results and provides items that are more relevant to the search item or are realted to the search history of the user.
There are two main types of recommendation systems:
1. Content-based filtering: They suggest similar items based on a particular item. This system uses item metadata, such as genre, director, description, actors, etc. for movies, to make these recommendations. The general idea behind these recommender systems is that if a person liked a particular item, he or she will also like an item that is similar to it.
2. Collaborative filtering: This system matches persons with similar interests and provides recommendations based on this matching. Collaborative filters do not require item metadata like its content-based counterparts.
We will use the former in this project.
## Methodology: 
First we import the necessary libraries and install the dependencies. Then we read the movies.csv and ratings.csv files using the pd.read_csv() function.
Ratings dataset has-
userId: Unique for each user. movieId: We take the movie title from the movie dataset using this feature. Rating: Each user gives ratings for all the films. Using this, we are going to predict the top 10 similar films. Here, we can see that userId one has watched movieId 1 and 3 and rated them 4.0 but has not rated movieId two. This interpretation is more challenging to extract from this dataframe. Therefore, to make things easier to understand and work with, we will make a new dataframe where each column represents each unique user, and each row represents each unique movie.
To remove noise from the dataset, we set the criteria: 
To qualify for a movie: More than 10 ratings
To qualify for a user: More than 50 movies rated
Then, after making the necessary modifications with our thresolds of 10 and 50, the final dataset has dimensionality of 2121*378 and is sparse.
To remove the sparsity we use the csr_matrix function from the scipy library.
Thus, obtaining the final dataset, we then apply the KNN algorithm.
Finally, the recommendation function: It first checks the existence of a movie in the database, then applies the KNN algorithm to find the nearest neighbours and outputs the 10 nearest neighbours.
## Conclusion:
We have used the content based filtering approach to the find and output the top 10 nearest movies to a given input movie using the KNN algorithm utilizing the cosine distance metric.
