# 📚 Book Recommender System

A full-stack book recommendation web application that combines **Popularity-Based** and **Collaborative Filtering** techniques to help users discover books they'll love.

🔗 **Live Demo:** [book-recommender-system-qie9.onrender.com](https://book-recommender-system-qie9.onrender.com)

---

## 🖼️ Live Demo

🔗 **Try it here:** [book-recommender-system-qie9.onrender.com](https://book-recommender-system-qie9.onrender.com)

> The app shows a **Top 50 Books** homepage and a **Recommend** page where you can type any book title to get 4 similar book suggestions.

---

## 🧠 How It Works

This system implements two recommendation strategies:

### 1. Popularity-Based Filtering
- Aggregates all user ratings to compute average rating and total vote count per book
- Filters books with a **minimum of 250 ratings** to ensure statistical reliability
- Ranks and displays the **Top 50 books** on the home page

### 2. Collaborative Filtering (User-Item Matrix)
- Filters to **power users** (≥200 ratings) and **well-rated books** (≥50 ratings) to reduce noise
- Constructs a **User-Item pivot matrix** where rows are books and columns are users
- Applies **Cosine Similarity** from Scikit-learn to find books with similar rating patterns
- Returns the **top 4 most similar books** for any given title

---

## 📂 Project Structure

```
Book_Recommender_System/
│
├── app.py                   # Flask web application (routes & logic)
├── templates/
│   ├── index.html           # Home page — Top 50 popular books
│   └── recommend.html       # Recommendation page
│
├── books.pkl                # Serialized books dataframe
├── popular.pkl              # Serialized top-50 popular books
├── pt.pkl                   # Serialized user-item pivot table
├── similarity_scores.pkl    # Serialized cosine similarity matrix
│
├── requirements.txt         # Python dependencies
├── Procfile                 # Render/Heroku deployment config
└── Book_Recommender_System.ipynb  # EDA + Model building notebook
```

---

## 📊 Dataset

**Source:** [Book-Recommendation Dataset — Kaggle](https://www.kaggle.com/datasets/arashnic/book-recommendation-dataset)

| File | Records | Key Columns |
|------|---------|-------------|
| `Books.csv` | 271,360 | ISBN, Book-Title, Book-Author, Year, Publisher |
| `Users.csv` | 278,858 | User-ID, Location, Age |
| `Ratings.csv` | 1,149,780 | User-ID, ISBN, Book-Rating (0–10) |

---

## ⚙️ Tech Stack

| Layer | Technology |
|-------|-----------|
| Language | Python 3.8+ |
| ML / Data | Pandas, NumPy, Scikit-learn |
| Visualization | Matplotlib, Seaborn |
| Backend | Flask |
| Serialization | Pickle |
| Frontend | HTML, CSS, Bootstrap |
| Deployment | Render |

---

## 🚀 Running Locally

### 1. Clone the repository
```bash
git clone https://github.com/Shubham-kumar1-hub/Book_Recommender_System.git
cd Book_Recommender_System
```

### 2. Install dependencies
```bash
pip install -r requirements.txt
```

### 3. Run the Flask app
```bash
python app.py
```

### 4. Open in browser
```
http://127.0.0.1:5000
```

> **Note:** The `.pkl` files are pre-generated and included in the repo. To regenerate them from scratch, download the dataset from Kaggle and run `Book_Recommender_System.ipynb`.

---

## 📈 Model Evaluation

| Metric | Collaborative Filter | Popularity Model |
|--------|---------------------|-----------------|
| Coverage | ~700 books | Top 50 books |
| Personalization | High (user-specific) | Low (same for all) |
| Cold Start | Not handled | Works for all |
| Similarity Measure | Cosine Similarity | Avg Rating + Vote Count |

For detailed EDA and evaluation, see [`Book_Recommender_System.ipynb`](Book_Recommender_System.ipynb).

---

## 🔮 Future Improvements

- [ ] Add content-based filtering using book genres/descriptions
- [ ] Hybrid model combining collaborative + content-based
- [ ] Handle cold-start problem for new users
- [ ] User login to save preferences and rating history
- [ ] Improve UI with better search and autocomplete

---

## 👤 Author

**Shubham Kumar**
- GitHub: [@Shubham-kumar1-hub](https://github.com/Shubham-kumar1-hub)

---

## 📄 License

This project is open source and available under the [MIT License](LICENSE).
