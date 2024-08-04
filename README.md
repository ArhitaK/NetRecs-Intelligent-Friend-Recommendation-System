# NetRecs-Intelligent-Friend-Recommendation-System
NetRecs is a sophisticated friend recommendation system designed to analyze social network data using advanced graph mining techniques. Implemented with Python, NetworkX, and Pandas, this system effectively processes and visualizes social connections to deliver precise and insightful friend recommendations. By leveraging these technologies, NetRecs aims to enhance and streamline the process of discovering meaningful connections within your network.

# Problem Statement:
Given a directed social graph, the task is to predict missing links to recommend users. This involves solving the problem of link prediction in graphs.

# Data Overview:
The dataset is sourced from Facebook's recruiting challenge on Kaggle: Facebook Recruiting. It contains two columns, representing edges in the graph:

-source_node (int64)
-destination_node (int64)

## Performance metric for supervised learning:
-Both precision and recall is important so F1 score is good choice
-Confusion matrix

# Mapping the Problem to Supervised Learning:

Training samples of both positive (good) and negative (bad) links were generated from the directed graph. For each link, various features were extracted, including the number of followers, whether the user follows back, page rank, Katz score, Adamic-Adar index, SVD features of the adjacency matrix, and several weight features. These features were used to train a machine learning model to predict the likelihood of a link.
Some reference papers and videos :
-https://www3.nd.edu/~dial/publications/lichtenwalter2010new.pdf
-https://kaggle2.blob.core.windows.net/forum-message-attachments/2594/supervised_link_prediction.pdf
-https://www.youtube.com/watch?v=2M77Hgy17cg


## Case Study Flow:
============================

-Directed graph data provided
-Approx. 1.86M nodes and 9.43M edges.
-Data was obtained from kaggle. Link: https://www.kaggle.com/c/FacebookRecruiting
-We have provided only connected nodes. i.e. 9.43M edges. But for each user among n user's, there is n-1 edges. So, for n nodes total possible edges are of 10^12 order.
-On EDA, it is established that number of followers are less than 12 for 90% of users.
-The dataset was highly imbalanced , as only one classification label is present.
-We decided y = 0 , is link is not present and took random sample from it.
-In training and test dataset were exactly balanced.
-Featurization is the most important part of this case study. We extracted various features types of features...
  -Similarity measures
  -Ranking Measure
  -Various Graph Features
  -Various Weight Features
-SVD features using Adjancy matrix. (n_components = 6)
-We Trained two models Random Forest and XGBOOST
-XGBOST took most time for run.

## Observations:

-Understanding of graph and feature engineering was the most important part of this case study.
-For Random Forest, Follow_back was the most important feature found, followed by weight_f2 and shortest_path.
-Best result was obtained in case of XGBOOST.
-XGBOOST took most of time.
-For XGBOOST, follows_back was the most important feature. Followed by cosine_follower and weight_f1.
-XGBOOST gave the best result.







