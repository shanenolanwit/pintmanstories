+++
title = "AWS ML Specialty Study Points"
date = 2020-12-15T12:22:50Z
author = "Shane Nolan"
keywords = ["", ""]
cover = "/images/avatar.png"
summary = "AWS ML Specialty Study Points - A brain dump of topics to direct study and identify knowledge gaps"
+++

Following on from my [Guide to the AWS Machine Learning Specialty](/posts/aws-ml-exam-guide) I want to share this list which is based on what I feel are the most important terms and concepts to understand before tackling the ML specialty exam. You should be able to scan this list and comfortably explain and/or discuss each point.

## General ML Foundations
 - Supervised / semi supervised / unsupervised / transfer /  reinforcement learning
 - Rate of Growth - Derivative v Gradient
 - Parameters v Hyperparameters
 - Classification v Regression
 - Linear regression v Logistic regression
 - Overfitting v Underfitting

## Know your data
 - What is an attribute?
    - Discrete / Continuous
    - Nominal / Binary / Ordinal / Numeric
 - Using basic math to understand your data
    - Mean / Mode / Median
    - Range / Quartile / Inter Quartile Range
    - Variance / Standard Deviation
 - Visualizing your data
    - What do you want to show?
        - Comparison of values
        - Composition of something
        - Distribution of data
        - Detecting or analyzing trends
        - Relationship between data sets
    - Using the right chart at the right time
        - Area / Bar / Box / Bubble / Column / Histogram / Line / Pie / Scatter
    - Amazon CloudWatch
    - Amazon QuickSight
    - Matplotlib
 - Where is your data stored and how did it get there
    - S3 / Dynamo / Aurora / EFS
    - Kinesis 
        - Streams
        - Analytics
        - Firehose
        - Video Streams
    - Redshift
 - How is your data secured
    - IAM
    - VPC
    - KMS
 - What format is the data in

## Data Engineering 
 - For each attribute type, how do you handle missing values
 - Smote v GAN
 - How do you handle noisy data
 - Identifying redundant data / Correlation analysis
 - Data reduction
    - Curse of dimensionality
    - Principal Component Analysis
        - forward v backwards selection
    - Parametric reduction and the method of least squares
    - k-means
        - how to select k
    - Sampling
 - Data transformation
    - Binning
    - Feature Construction
    - Aggregation
    - Encoding
    - Normalization v Standardization
 - Kinesis Data Analytics
 - AWS Glue
 - AWS Lambda
 - Spark ML and Elastic Pipeline
 - IOT Analytics

## Classification
 - Compare and contrast with clustering
 - Decision trees
 - Attribute selection
 - Bayes v Naive Bayes
 - Neural networks
 - Evaluating classifier performance
    - Holdout and random sub-sampling
    - Cross validation
    - ROC v AUC / ROC v PR
    - Confusion Matrix
        - Precision v Recall
        - Sensitivity v Specificity
        - Accuracy
        - F1 Score
 - Ensemble Learning
    - Bagging / Boosting
    - AdaBoost
    - Gradient Boosting
    - Random Forests
 - Support Vector Machines
    - Linearly separable v linearly inseparable
 - Multiclass classification & minimax
 - k Nearest Neighbors
 - Deep Learning
    - CNN v RNN
 - Active Learning
 - Transfer Learning
 - SageMaker Random Cut Forest
 - XGBoost
 - Kinesis Random Cut Forest
 - Ground Truth

## AWS Black Box ML Services
Some AWS services provide powerful ML capabilities without its users requiring in depth knowledge of the technologies and techniques powering them. In my opinion, it is not necessary to know these services in detail, but you should be able to give some basic sample use cases, answer some basic questions about them and know how you would integrate them with each other and other AWS services. I primarily used the FAQ section of the AWS documentation to compliment my understanding of each service.

    - Comprehend 
    - DeepLens 
    - DeepRacer
    - Forecast 
    - Lex 
    - Personalize 
    - Rekognition 
    - Neo 
    - Textract 
    - Transcribe 
    - Translate 