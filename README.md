🎬 Movie Recommendation System

A Content-Based Movie Recommendation Engine using Python, TF-IDF, and Cosine Similarity

📖 Table of Contents

📘 Project Overview

🧠 How It Works

🧱 System Architecture

📊 Dataset Information

🏗 Technologies Used

📦 Installation

📂 Project Structure

▶️ How to Run

🎯 Example Output

📈 Visualizations

⚠️ Limitations

🚀 Future Enhancements

📚 References

📜 License

📘 Project Overview

This project is a Content-Based Movie Recommendation System that suggests movies similar to a given movie based on metadata such as:

Genres

Keywords

Tagline

Cast

Director

It uses TF-IDF Vectorization to convert movie metadata into feature vectors, and Cosine Similarity to compute similarity between movies.

🧠 How It Works
🔹 Step 1: Load Dataset

The system loads a movies.csv file containing metadata for thousands of movies.

🔹 Step 2: Feature Selection

The algorithm uses the following features:

selected_feature = ['genres','keywords','tagline','cast','director']

🔹 Step 3: Data Cleaning

Missing values are replaced with empty strings to avoid errors.

🔹 Step 4: Combine Features

A new combined text field is created:

combined_feature = "genres keywords tagline cast director"

🔹 Step 5: Vectorization

The combined text is transformed using TfidfVectorizer which converts text into weighted numerical vectors.

🔹 Step 6: Similarity Matrix

Cosine similarity is computed between all pairs of movies, producing a similarity matrix:

similarity[movie1][movie2]

🔹 Step 7: User Input

The user enters a movie name.
If an exact match isn’t found, difflib.get_close_matches helps find the closest title.

🔹 Step 8: Movie Recommendation

Top 30 most similar movies are displayed.

🧱 System Architecture
                ┌──────────────────────────┐
                │     movies.csv dataset   │
                └──────────────┬───────────┘
                               │
                     Load & Clean Data
                               │
                ┌──────────────▼───────────────┐
                │  Combine metadata features    │
                └──────────────┬───────────────┘
                               │
                   TF-IDF Vectorization
                               │
                ┌──────────────▼───────────────┐
                │   Cosine Similarity Matrix    │
                └──────────────┬───────────────┘
                               │
             User enters movie name (input)
                               │
                ┌──────────────▼───────────────┐
                │ Find closest title + ranking  │
                └──────────────┬───────────────┘
                               │
                   TOP 30 Recommended Movies

📊 Dataset Information

Your movies.csv file should contain the following columns:

Column	Description
index	Unique movie ID
title	Movie title
genres	List of genres
keywords	Plot keywords
tagline	Short description or tagline
cast	Main cast members
director	Director name

Example:

index,title,genres,keywords,tagline,cast,director
0,Avatar,Action Adventure Fantasy,"future, alien",Enter the world of Pandora,"Sam Worthington, Zoe Saldana",James Cameron

🏗 Technologies Used

Python

NumPy

Pandas

Scikit-Learn

Matplotlib (visualization)

Seaborn (heatmap visualization)

📦 Installation
1. Install dependencies
pip install numpy pandas scikit-learn matplotlib seaborn

2. If running in Google Colab

Connect your Google Drive and place movies.csv in your Drive.

📂 Project Structure
📁 movie-recommendation-system
│
├── movie_recommendation_system.py
├── movies.csv
└── README.md

▶️ How to Run
Option 1 — Run Locally
python movie_recommendation_system.py

Option 2 — Run in Google Colab

Upload the script and dataset, then run each cell.

🎯 Example Output
please enter the movie name: Avatar

Movies suggested for you:
0 => ['Alien']
1 => ['Terminator 2']
2 => ['Prometheus']
3 => ['Guardians of the Galaxy']
4 => ['Star Trek']
...

📈 Visualizations
🔥 Cosine Similarity Heatmap

Use this code to visualize similarity:

plt.figure(figsize=(14,10))
sns.heatmap(similarity[:20, :20],
            xticklabels=movie_data['title'][:20],
            yticklabels=movie_data['title'][:20],
            cmap='coolwarm')
plt.title("Cosine Similarity Heatmap (Top 20 Movies)")
plt.xticks(rotation=90)
plt.show()

🔍 What the colors mean:

Brighter colors → stronger similarity

Darker colors → weaker similarity

⚠️ Limitations

Only supports content-based recommendations

Cannot capture user preferences, ratings, or watch history

Accuracy depends on data quality in movies.csv

TF-IDF does not understand deep semantic movie meaning

🚀 Future Enhancements

Add Streamlit web interface

Include movie posters & IMDB links

Use Word2Vec / BERT embeddings for deeper understanding

Build a hybrid recommender (content + collaborative filtering)

Add genre-based filtering

Improve search with fuzzy matching

📚 References

Scikit-Learn Documentation

TF-IDF Vectorization Theory

Cosine Similarity in Recommendation Engines

📜 License

This project is open-source and available under the MIT License.
