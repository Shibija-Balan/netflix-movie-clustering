# Netflix Movies Clustering

## Project Description
This project explores clustering of Netflix movies based on their **duration, rating, and primary genre**. Using **KMeans clustering**, movies were grouped into 5 clusters to uncover patterns in content characteristics. The goal is to understand how movies differ by length, rating, and genre on Netflix.

## Dataset
- Source: [Netflix Titles Dataset](https://www.kaggle.com/datasets/shivamb/netflix-shows)
- Columns used:
  - `title` — Movie title
  - `type` — Movie or TV Show
  - `duration` — Duration of the movie (in minutes)
  - `rating` — Content rating (e.g., PG, R)
  - `listed_in` — Genres/categories
- Missing values were dropped for selected columns, and only movies were considered (no TV shows).

## Steps / Methodology

### 1. Preprocessing
- Filtered dataset to only include movies (`duration` containing 'min').
- Converted `duration` to integer (minutes).
- Extracted primary genre from `listed_in`.
- Encoded categorical variables:
  - `rating` to `rating_encoded` (LabelEncoder)
  - `genre` to `genre_encoded` (LabelEncoder)

### 2. Clustering
- Features used: `rating_encoded`, `duration`, `genre_encoded`.
- Standardised features using `StandardScaler`.
- Applied K-Means clustering with 5 clusters:
  ```python
  kmeans = KMeans(n_clusters=5, random_state=77)
  movies['cluster'] = kmeans.fit_predict(X_scaled)
