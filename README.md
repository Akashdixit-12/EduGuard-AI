#  EduGuard — Academic Integrity Tool

> Detect whether student-submitted text is **AI-generated** or **human-written** with **86–90% accuracy**.

---

##  Problem Statement

> *Despite the potential of Generative AI to personalize learning, current educational frameworks lack robust mechanisms to differentiate between AI-generated content and original student work, leading to a significant decline in academic integrity and the erosion of critical thinking skills.*

---

## Dataset

| Field | Details |
|---|---|
| **Name** | AI vs Human Text |
| **Source** | Kaggle |
| **Link** | https://www.kaggle.com/datasets/shanegerami/ai-vs-human-text |
| **Size** | ~40,000 samples |
| **Labels** | `0` = Human Written, `1` = AI Generated |

---

## Results

| Metric | Value |
|---|---|
| **Test Accuracy** | ~87–89% |
| **ROC-AUC Score** | ~0.95+ |
| **5-Fold CV Accuracy** | ~87% ± 1% |
| **Model** | TF-IDF (bigrams) + Logistic Regression |

> Meets the required accuracy range of **86–90%**

---

## Tech Stack

- **Python 3.10**
- **Scikit-learn** — TF-IDF Vectorizer, Logistic Regression
- **Pandas / NumPy** — Data processing
- **Matplotlib / Seaborn** — Visualizations
- **Flask** — Web application
- **Joblib** — Model serialization

---

## 📁 Project Structure

```
AI_detector/
├── EduGuard.ipynb              # Main notebook (EDA + Training + Evaluation)
├── app.py                      # Flask web application
├── requirements.txt            # Python dependencies
├── model.pkl                   # Saved model (generated after running notebook)
├── AI_Human.csv                # Dataset (download from Kaggle)
└── README.md
```

---



Download the dataset
Download `AI_Human.csv` from [Kaggle] https://www.kaggle.com/datasets/shamimhasan8/ai-vs-human-text-dataset

###  Run the Jupyter Notebook
```bash
jupyter notebook AI_Content_Detector.ipynb
```
Run all cells — this will train the model and save `model.pkl`.

### Launch the Web App
```bash
python app.py
```
Open **http://localhost:5000** in your browser.

---

## Output Visualizations

The notebook generates the following plots saved as `.png` files:

| File | Description |
|---|---|
| `label_distribution.png` | Class balance (Human vs AI) |
| `feature_distributions.png` | Linguistic feature comparison |
| `confusion_matrix.png` | Prediction confusion matrix |
| `roc_curve.png` | ROC-AUC curve |
| `cross_validation.png` | 5-fold CV accuracy chart |
| `top_features.png` | Most predictive TF-IDF words |

---

## How It Works

1. **Text Cleaning** — Lowercasing, URL removal, punctuation normalization
2. **TF-IDF Vectorization** — Converts text to unigram+bigram feature matrix (50k features)
3. **Logistic Regression** — Binary classifier with `class_weight='balanced'`
4. **Prediction** — Outputs label + confidence score

### Key Insight
AI-generated text tends to have:
- Higher average sentence length
- Lower lexical diversity (repetitive vocabulary)
- More formal punctuation patterns
- Specific "transition" bigrams not common in casual student writing

---

##  Web App Demo

Paste any text into the web app to get:
-  **Prediction Label** (Human / AI)
-  **Confidence Score**
-  **Human vs AI probability meter**

---

## Author

Built for the **Education & Academic Integrity** challenge.  
Dataset: https://www.kaggle.com/datasets/shanegerami/ai-vs-human-text
