# Unsupervised-Machine-Learning
This project applies unsupervised learning techniques to the NHANES (National Health and Nutrition Examination Survey) dataset to uncover patterns in health, lifestyle, and demographic data.

The goal is to:
- Reduce dimensionality of high-dimensional health data
- Identify underlying latent factors
- Separate individuals based on cardiovascular risk profiles

# Dataset
NHANES (2009–2012)
~10,000 observations, 76 variables
Includes health, lifestyle, and demographic information

# Methods
Data Preprocessing:
- Removed variables with excessive missing values
- Replace the remaining missing values using the mean
- Feature engineering:
  - Blood pressure ratio
  - Cholesterol–BMI ratio
  - Pulse–age ratio
  - Sleep adjustment metric
- Normalization of all numerical variables
- Outlier detection and removal

# Principal Component Analysis (PCA)
- Reduced dataset to 7 principal components
- Captured ~84.1% of total variance

Key interpretations:
- PC1: General cardiovascular health & age-related factors
- PC2: Body composition (weight, BMI, height)
- PC3+: Socioeconomic and lifestyle-related health patterns

# Factor Analysis

Two models were explored:
1. Best fit model
  - Explained 85.1% of the variance
  - Strong representation of age, BMI, and weight relationships
  - Risk of overfitting
2. Balanced model (preferred for generalization)
  - Explained 73.8% of variance
  - Better trade-off between complexity and interpretability

Key factors identified:
  - Age-related health factor
  - Body composition factor
  - Height-related factor

# Clustering (Cardiovascular Risk Segmentation)
Applied k-means clustering
Compared with:
  - PAM
  - Kernel k-means
  - EM clustering

Final model: k-means (k = 2)
Cluster interpretation:
- Cluster 1: Healthier individuals (lower BMI, blood pressure, cholesterol)
- Cluster 2: Higher-risk group (elevated BMI, BP, cholesterol)
- Alternative 3-cluster solution explored but showed weaker separation
- Silhouette scores indicate moderate overlap between clusters

# Key Results
- Successfully reduced dimensionality while preserving most variance
- Identified interpretable latent health factors
- Segmented population into meaningful cardiovascular risk groups
- Found that simpler clustering (k=2) outperformed more complex methods

# Insights
- Health outcomes are strongly linked to age and body composition
- Socioeconomic and lifestyle variables influence physiological indicators
- Clear separation exists between lower-risk and higher-risk individuals, even in unsupervised settings

# Limitations
- Cluster separation is not very strong (overlap present)
- Some variables are not well-explained in factor models
- Results depend on preprocessing choices and feature selection

# How to Run
Open the R Markdown file (.Rmd) and run all chunks.

The project uses the following libraries:

library(dplyr)

library(GGally)

library(ggplot2)

library(factoextra)

library(cluster)

library(mclust)

library(kernlab)

library(MASS)

To load the dataset:
- Option A (recommended):

install.packages("NHANES")

library(NHANES)
- Option B (if package installation fails):

NHANES <- read.csv("NHANES_data.csv")

Alternatively:
Open the .html file to view results directly (no setup required)

# Project Structure
├──README.md

├──Data/

      └── NHANES_data_csv

├──Report/

      └── Report.pdf

├──Notebooks/

      ├── unsupervised_learning_nhanes.Rmd

      └── unsupervised_learning_nhanes.html

# Author
Silvia Andreeva

Rocio Lopez Blazquez
