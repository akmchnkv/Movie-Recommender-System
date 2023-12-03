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
 
 ![top10](https://github.com/akmchnkv/Movie-Recommender-System/blob/main/reports/figures%20/top10.png)
 
Exploratory data analysis (EDA) revealed insights into the distribution of ratings, user preferences, and movie popularity. Additionally, we explored the diversity of movie genres and the frequency of user interactions with the system.
**Insights:**
- The rating value of 4 is the most frequently occurring among user ratings
- Drama emerges as the most favored movie genre among our users based on analysis
- The data shows that the majority of users are male
- The most part of the sample are young people in age between 35 and 55
- "Legends of the Fall" (1994) stands out as the most frequently rated film in our dataset, based on the user ratings provided.
- Students in average watch movies more often than other categories **(😂😂😂 I guess we've discovered the first law of movie data science: the probability of movie marathons is directly proportional to the number of assignments))**

## Model Implementation
The core of the recommendation system is based on Matrix Factorization ([reference](https://towardsdatascience.com/recommendation-system-matrix-factorization-d61978660b4b)), a collaborative filtering technique. Collaborative filtering is a method of making predictions about the interests of a user by collecting preferences or taste information from many users. The implemented model utilizes user and item embeddings to predict movie ratings. The idea behind matrix factorization is to represent users and items in a lower dimensional latent space. Since the initial [work](https://sifter.org/%7Esimon/journal/20061211.html) by Simon Funk in 2006 a multitude of matrix factorization approaches have been proposed for recommender systems. 

The MatrixFactorization class, implemented in PyTorch, facilitates the training process, enabling the model to learn latent representations that capture the nuances of user-item relationships.

## Model Advantages and Disadvantages
### Advantages:
- Matrix Factorization captures latent relationships between users and items (MF excels in capturing latent relationships between users and items. By representing users and items in a lower-dimensional latent space, the model unveils nuanced connections that contribute to more accurate recommendations)
- The model can handle missing data and make predictions for unrated items
- Matrix Factorization facilitates personalized recommendations by focusing on individual user preferences.

### Disadvantages:
- Cold start problem for new users or items (When a user or item has limited interaction history, it becomes challenging for the model to provide accurate recommendations)
- Sensitivity to sparsity in the user-item interaction matrix (In scenarios where the data is sparse, meaning there are fewer ratings for a significant number of items, the model may face challenges in capturing diverse user preferences)
- The model primarily relies on historical user-item interactions and may not consider contextual information or changes in user preferences over time. This limitation can impact the adaptability of the system to evolving user tastes

## Training Process
The training process involves minimizing the Mean Squared Error (MSE) leveraging stochastic gradient descent (SGD)l oss between predicted and true ratings over multiple epochs. The model is trained using a DataLoader to handle batches of training and validation data. The training progress is visualized through a plot of training and validation losses across epochs.

![loss](https://github.com/akmchnkv/Movie-Recommender-System/blob/main/reports/figures%20/loss.png)

### Key components of the training process include:

#### Loss Function:
MSE measures the average squared difference between predicted and true ratings, providing a quantitative measure of the model's performance.

#### Model Optimization:
Optimization is achieved through gradient descent, specifically Stochastic Gradient Descent. SGD updates the model parameters in the direction that minimizes the loss for each batch of training data. 

#### Batch Training:
To efficiently handle large datasets, the training data is processed in batches using PyTorch's DataLoader. Batch training enhances computational efficiency and facilitates parallel processing, leading to faster convergence during optimization.

#### Epochs:
The training process iterates over a predefined number of epochs. An epoch constitutes a complete pass through the entire training dataset. During each epoch, the model learns and refines its parameters based on the training data.

#### Validation:
Model performance is monitored not only on the training data but also on a separate validation set. Validation data helps prevent overfitting, as the model's ability to generalize to unseen data is crucial.

## Evaluation
The evaluation of the Matrix Factorization-based recommendation system involves assessing its predictive performance and generalization to unseen data. A crucial aspect of evaluation is predicting ratings for each user, excluding one movie at a time. 

### Key elements of the evaluation process include:

#### Exclusion Methodology:
For each user, one movie is excluded from the user's rated movies. The model is then tasked with predicting the rating for the excluded movie based on the user's remaining interactions. This process is repeated for all users and their respective movies.

#### Mean Squared Error (MSE):
The primary metric for evaluating the model's predictive accuracy is the Mean Squared Error. It quantifies the average squared difference between predicted and true ratings across all predictions. A lower MSE indicates better alignment between predicted and actual ratings.


## Results
The primary metric for assessing the model's predictive accuracy is the Mean Squared Error. The obtained MSE of 1.1689 signifies the squared difference between predicted and true ratings across all predictions. Visualizing the distribution of true and predicted ratings through histograms offers insights into the alignment between the model's predictions and the actual user preferences. Surprisingly, a detailed comparison of these distributions reveals a remarkable similarity, suggesting that the recommendation system accurately captures the nuances of user preferences in its predictions.

![result](https://github.com/akmchnkv/Movie-Recommender-System/blob/main/reports/figures%20/result.png)

In conclusion, the Matrix Factorization-based movie recommendation system demonstrates effectiveness in providing accurate and personalized movie suggestions to users. The achieved results highlight the system's ability to learn latent relationships between users and movies
