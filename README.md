# 🎬 Movie Recommender

### Intelligent Content-Based Movie Recommendation System

In a world overflowing with content, choosing the next movie to watch has become surprisingly difficult. Streaming platforms offer thousands of titles, yet users often feel overwhelmed or stuck in the same narrow preferences.

This project was built to solve that problem through a practical, transparent, and educational approach to **content-based recommendation**.

---

## 🎯 Motivation & Vision

Most commercial recommendation systems rely heavily on collaborative filtering (what similar users watched). While powerful, these systems often suffer from:

- Cold-start problems for new movies or new users  
- Black-box behavior that is hard to explain  
- Heavy dependence on large volumes of user interaction data  

We chose a different path.

**Movie Recommender** demonstrates how high-quality recommendations can be generated purely from the *content* of a movie — its plot, genres, and tagline — without requiring any user history. By combining classical Natural Language Processing (TF-IDF + Cosine Similarity) with modern live data from The Movie Database (TMDB), we created a system that is:

- Interpretable
- Fast
- Easy to understand and extend
- Useful even when no user data exists

This project serves both as a working application and as a clear learning resource for anyone interested in recommendation systems, NLP, and full-stack machine learning products.

---

## ✨ Key Features

- **Smart Search** — Type a keyword and get instant suggestions + poster results  
- **Curated Home Feed** — Browse Trending, Popular, Top Rated, Now Playing, and Upcoming movies  
- **Rich Movie Details** — Poster, backdrop, overview, genres, and release information  
- **Dual Recommendation Engine**
  - **TF-IDF Content Similarity** — Finds movies with similar plots, themes, and styles  
  - **Genre Discovery** — Surfaces popular titles from the same primary genre  
- Clean, modern Streamlit interface with responsive poster grids  
- FastAPI backend designed for reliability and easy deployment  

---

## 🧠 How the Recommendation Engine Works

### 1. Content-Based Filtering (TF-IDF)

We transform each movie into a rich textual representation:

```text
tags = overview + " " + genres + " " + tagline


movie-rec/
├── app.py                  # Streamlit frontend application
├── main.py                 # FastAPI backend & recommendation logic
├── movies.ipynb            # Data cleaning, feature engineering & model building
├── movies_metadata.csv     # Source dataset (\~45k movies)
├── df.pkl                  # Processed movie DataFrame
├── indices.pkl             # Title → index mapping
├── tfidf.pkl               # Fitted TfidfVectorizer
├── tfidf_matrix.pkl        # Pre-computed TF-IDF matrix
├── requirements.txt
├── runtime.txt
├── .python-version
├── .gitignore
└── README.md


python -m venv .venv
source .venv/bin/activate          # Windows: .venv\Scripts\activate

pip install -r requirements.txt

TMDB_API_KEY=your_tmdb_api_key_here

uvicorn main:app --reload --host 0.0.0.0 --port 8000

streamlit run app.py

API_BASE = "http://127.0.0.1:8000"

📊 Dataset
Source: movies_metadata.csv (MovieLens / Kaggle Movies Dataset)
Size: Approximately 45,000 movies
Key fields used: title, overview, genres, tagline, vote_average, popularity
All heavy computation (text cleaning, TF-IDF vectorization, matrix creation) is performed offline in the notebook and saved as pickle files. This design keeps the API lightweight and responsive.

☁️ Deployment
The project is production-ready and includes:
runtime.txt specifying Python 3.11.9
A previously deployed backend example on Render
Recommended deployment approach:
Backend → Render, Railway, Fly.io, or similar
Frontend → Streamlit Community Cloud or the same platform
Remember to set the TMDB_API_KEY environment variable in your hosting environment.

🤝 Contributing
Contributions are welcome. If you plan significant changes, please open an issue first so we can discuss the direction together.
