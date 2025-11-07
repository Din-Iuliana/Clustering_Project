# Clustering_Project
Bullying Analysis and Student Segmentation.
This project analyzes a large dataset of students to understand patterns of bullying, absenteeism, social behavior, and health indicators. Using unsupervised machine learning techniques, the dataset is segmented into distinct student profiles to help identify risk levels and behavioral patterns.

Project Overview
The dataset contains survey responses from students (age, sex, experiences with bullying, physical fighting, feelings of loneliness, absenteeism, peer relationships, and health indicators). The goal of this project is to:
Identify patterns in student behavior.
Segment students into clusters using KMeans clustering.
Understand relationships between bullying, absenteeism, and social/health factors.

Key Steps
1. Data Preprocessing
Renaming columns for clarity.
Handling missing values by removing incomplete entries.
Encoding categorical variables to numerical format (Yes/No → 1/0, mapping age from text to numeric).
Feature scaling using MinMaxScaler.

2. Exploratory Data Analysis (EDA)
Distribution and correlation analysis of key features.
Visualization using Seaborn, Matplotlib, and Plotly.
Boxplots, heatmaps, and barplots to examine behavior across clusters.

3. Dimensionality Reduction
Applying PCA (Principal Component Analysis) to reduce dimensionality.
Visualizing explained variance and cumulative variance to determine the number of principal components to retain.

4. Clustering
Using KMeans clustering with the Elbow Method and silhouette score to determine the optimal number of clusters.
Segmenting students into 4 clusters, labeled for interpretability:
0	Moderate-Risk / Occasionally Involved	Students occasionally exposed to bullying or minor conflicts.
1	Low-Risk / Well-Adjusted	Emotionally stable and socially connected students.
2	High-Risk / Violent & Absent	High absenteeism, violent behavior, or frequent bullying exposure.
3	Well-Integrated / Low-Conflict	Emotionally balanced, socially integrated students.

5. Cluster Analysis

Comparing clusters on key variables like bullying, fighting, absenteeism, loneliness, peer relationships, and health indicators.
Visualizations for understanding behavioral patterns and identifying high-risk groups.

6. Cluster Quality
Evaluated cluster separation using Silhouette Score.
Ensured clusters are meaningful and interpretable.

Technologies Used
Python
Pandas & NumPy (data manipulation)
Matplotlib, Seaborn, Plotly (visualization)
Scikit-learn (preprocessing, PCA, KMeans)
Yellowbrick (Elbow method visualization)

Usage
Clone the repository.
Install required packages (pandas, numpy, matplotlib, seaborn, scikit-learn, yellowbrick, plotly)
Run the notebook/script with the dataset Bullying_2018.csv.
Analyze results and visualizations of student clusters.
