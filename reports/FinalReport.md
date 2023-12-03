# Movie Recommendation System Report
A recommender system is a type of information filtering system that suggests items or content to users based on their interests, preferences, or past behavior. These systems are commonly used in various domains, such as e-commerce, entertainment, social media, and online content platforms. I create a recommender system of movies for users such that:
 - System suggest some movies to the user based on user's favorite movies (list of movie ids)
 - This task is solved using a machine learning model of collaborative filltering - **Matrix Factorization**
 - Notebooks have benchmark that evaluate the quality of recommendations of model
 
 ## Data Analysis
 For this task I use [MovieLens 100K dataset](https://grouplens.org/datasets/movielens/100k/) consisting user ratings to movies
 * It consists of 100,000 ratings from 943 users on 1682 movies
 * Ratings are ranged from 1 to 5
 * Each user has rated at least 20 movies
 
Exploratory data analysis (EDA) revealed insights into the distribution of ratings, user preferences, and movie popularity. Additionally, we explored the diversity of movie genres and the frequency of user interactions with the system.
**Insights:**
- The rating value of 4 is the most frequently occurring among user ratings
- Drama emerges as the most favored movie genre among our users based on analysis
- The data shows that the majority of users are male
- The most part of the sample are young people in age between 35 and 55
- "Legends of the Fall" (1994) stands out as the most frequently rated film in our dataset, based on the user ratings provided.
- Students in average watch movies more often than other categories **(😂😂😂 I guess we've discovered the first law of movie data science: the probability of movie marathons is directly proportional to the number of assignments))**

## Model Implementation
The core of the recommendation system is based on Matrix Factorization, a collaborative filtering technique. The implemented model utilizes user and item embeddings to predict movie ratings. The MatrixFactorization class, implemented in PyTorch, facilitates the training of the model.

## Model Advantages and Disadvantages
### Advantages:
- Matrix Factorization captures latent relationships between users and items
- The model can handle missing data and make predictions for unrated items

### Disadvantages:
- Cold start problem for new users or items
- Sensitivity to sparsity in the user-item interaction matrix

## Training Process
The training process involves minimizing the Mean Squared Error (MSE) loss between predicted and true ratings. The model is trained using a DataLoader to handle batches of training and validation data. The training progress is visualized through a plot of training and validation losses across epochs.

## Evaluation
The evaluation of the recommendation system involves assessing its predictive performance. We use Matrix Factorization to predict ratings for each user, excluding one movie at a time.

## Results
The model's performance is summarized by the Mean Squared Error (=  1.1689), providing an indication of how well the predicted ratings align with the ground truth.

In conclusion, the Matrix Factorization-based movie recommendation system demonstrates promising results in capturing user preferences and providing personalized suggestions. Further refinements and enhancements could address challenges such as the cold start problem and sparsity in user-item interactions.
