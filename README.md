# Practical Machine Learning and Deep Learning - Assignment 2 - Movie Recommender System

## Student Info

**Name**: Elina Akimchenkova  
**Email Address**: e.akimchenkova@innopolis.university  
**Group Number**: B21-DS02

A recommender system is a type of information filtering system that suggests items or content to users based on their interests, preferences, or past behavior. These systems are commonly used in various domains, such as e-commerce, entertainment, social media, and online content platforms. I create a recommender system of movies for users such that:
 - System suggest some movies to the user based on user's favorite movies (list of movie ids)
 - This task is solved using a machine learning model of collaborative filltering - **Matrix Factorization**
 - Notebooks have benchmark that evaluate the quality of recommendations of model
 
 ![recommendations](https://github.com/akmchnkv/Movie-Recommender-System/blob/main/reports/figures%20/recommendations.png)

## Prerequisites

### Dependencies
Install all required packages with
```bash
pip install -r requirements.txt
```

### Repo structure
```
movie-recommender-system
├── README.md               # The top-level README
│
├── data
│   ├── interim             # Intermediate data that has been transformed.
│   └── raw                 # The original, immutable data
│
├── models                  # Trained and serialized models, final checkpoints
│
├── notebooks               #  Jupyter notebooks. Naming convention is a number (for ordering),
│                               and a short delimited description, e.g.
│                                         
│ 
│
├── reports
|    └── final_report.md     # Report containing data exploration, solution exploration, training process, and evaluation
|    ├── figures             # figures
     


```
