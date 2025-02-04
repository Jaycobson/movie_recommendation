# Movie Recommendation System

![Movie Recommendation](https://github.com/Jaycobson/movie_recommendation/tree/main/image.jpg)

## Overview
This project implements a **Content-Based Movie Recommendation System** using **TF-IDF Vectorization** and **Cosine Similarity** to find similar movies based on features like title, keywords, cast, and genres. The system suggests movies that are most similar to a given movie by analyzing textual data and computing similarity scores.


[Link to PowerBI Visualization](https://github.com/Jaycobson/movie_recommendation/tree/main/deliverables)

## How It Works

### 1. Data Cleaning : 
The data consisted of missing values in more than 6 columns. For the numerical column, the mean was used to fill the missing values because it wouldn't skew the data further. The categorical columns were filled by discretion with mode and a constant 'unknown'. Unknown symbolises that the data was missing instead of having NaN, also some columns were filled with the mode because it can be assumed that if a record occurs more than 90% of the time than others, it would still be a good guess to fill the missing values with that value. The data was retained instead of dropping inorder to preserve the quality or correctness of the recommendation model.

### 2. Exploratory data analysis and Visualization:
During this phase, I check for the shape, numerical columns, categorical columnns and also checked the summary statistics to have a glimpse of how the distribution looks like. I visualized the bar plot and the scatterplot between budget and revenue. There was a positive correlation, this means the higher the  budget the higher the revenue. Although, it wasn't a perfect positive correlation, it was still a very strong correlation.

### 3. Feature Engineering: Combining Key Attributes
A new column, `combined_features`, is created by concatenating the **title, keywords, cast, and genres** of each movie. This ensures the recommendation system has enough context to compare movies effectively.

### 4. TF-IDF Vectorization: Converting Text into Numeric Data
To process textual data efficiently, **TF-IDF (Term Frequency-Inverse Document Frequency)** is used to transform text into numerical vectors. This helps measure how important a word is relative to all movies in the dataset. Additionally, stopword removal is applied to eliminate common words like "the," "is," and "and" to improve relevance.

### 5. Cosine Similarity: Measuring Similarity Between Movies
Once the data is vectorized, **cosine similarity** is computed between movies. Cosine similarity calculates the angle between two vectors, allowing the model to identify how closely related two movies are in terms of their textual content.

### 6. Generating Movie Recommendations
A function, `recommend_movies(movie_title, top_n=10)`, is implemented to:
- Find the index of the given movie title in the dataset.
- Compute similarity scores with all other movies.
- Sort the movies by similarity in descending order.
- Return the **top N most similar movies** based on content.

Additionally, a **popularity-based recommendation method** is included that suggests the highest-rated movies in the same genre.

## Installation
To use this project, ensure you have the required dependencies installed. You can install them using:
```bash
pip install -r requirements.txt
```

## How to Use
1. Ensure all files were gotten properly
2. Run the notebook to clean the movies data 
3. Run the recommendation.ipynb notebook and run the `recommend_movies` function with a movie title to get recommendations.
4. (Optional) Use the popularity-based recommendation method to suggest trending movies in the same genre.

### Example Usage
```python
recommend_movies("Avatar", top_n=5)
```
#### Output:
```
Recommended Movies:
1. Avengers: Endgame  
2. Interstellar  
3. Guardians of the Galaxy  
4. Star Wars: The Force Awakens  
5. The Martian  
```
For popularity-based recommendations:
```python
recommend_movies_by_popularity("Avatar", top_n=5)
```

### Challenges
One major challenge during the project was the missing values, i believe that there are better ways to fill the missing values but i wanted to ensure I submitted on time because i started quite late. The NLTK package and spacy can be used to extract patterns in the Overview column so it will be used to fill missing values in the keyword column. Also LLM's can be used to detect sentiments and easily help to fill the keyword column that had missing values. 

The homepage column had a lot of missing values and there weren't recognisable patterns that could be used to sort the missing values. We had a little bit above 60% null values for the homepage column, dropping it would have meant loosing other information so i decided to leave it since i did not use it for the recommmendation model.
