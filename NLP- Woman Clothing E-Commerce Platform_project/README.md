# Women's Clothing Reviews: Natural Language Processing & Text Mining Pipeline

This repository hosts an end-to-end **Natural Language Processing (NLP)** and text mining case study conducted on e-commerce customer review data. By leveraging core computational linguistics frameworks, the pipeline processes unstructured customer feedback to perform **Exploratory Text Analysis**, **Sentiment Analysis (TextBlob)**, and unsupervised **Topic Modeling (Latent Dirichlet Allocation - LDA)** to extract semantic customer satisfaction vectors and retail product insights.

---

## 📂 Dataset Repository & Architecture

The project ingests an e-commerce review matrix composed of unstructured customer feedback logs alongside a metadata data dictionary:

1. **`Womens Clothing Reviews Data.xlsx - Woman Clothing Reviews.csv`:** The core transactional data engine containing actual customer interactions. Key features include:
   - `Product ID`, `Category`, `Subcategory1`, `SubCategory2`: E-commerce product hierarchy tokens.
   - `Review Title` & `Review Text`: Unstructured textual strings written by customers.
   - `Rating` (1 to 5 stars) & `Recommend Flag` (Binary: `1` if recommended, `0` if not).
   - `Customer Age`, `Location`, and shopping `Channel` (Web vs. Mobile).
2. **`Womens Clothing Reviews Data.xlsx - Dictionary.csv`:** Mapping file providing structural definitions for each feature in the review ledger.

---

## 🛠️ The NLP Text Preprocessing Pipeline

Text mining requires transitioning messy, human-written text into highly standardized normalized tokens. The workspace in `WomenClothREviews_Cleaning.ipynb` implements a rigid preprocessing pipeline using `nltk` and `re`:

1. **Text Sanitization:** Standardizing all text inputs to lowercase, stripping punctuation strings, removing special escape patterns (e.g., `_x000d_`), and dropping numbers using Regular Expressions.
2. **Tokenization & Stopword Elimination:** Breaking blocks of review paragraphs into distinct word tokens and removing standard English stopwords (e.g., "is", "the", "at") using customized NLTK lists to retain pure contextual keywords.
3. **Morphological Standardization:** Applying **Lemmatization** via `WordNetLemmatizer` or **Stemming** (`SnowballStemmer`/`PorterStemmer`) to strip grammatical suffixes and reduce words down to their root dictionary form (e.g., "dresses", "dressed", and "dressing" are all mapped down to "dress").

---

## 🔬 Advanced Text Analytics Frameworks

Once cleaned, the unstructured strings are processed through multiple computational analysis tracks:

### 1. Exploratory Lexicon Visualizations
* **Word Clouds (`WordCloud`):** Generating visual frequency layouts masked across product segments to instantly pinpoint popular keywords (e.g., "love", "fit", "fabric", "comfortable").
* **POS (Part-of-Speech) Tagging:** Grouping tokens strictly by their structural grammatical types (`pos_tag`) to analyze what specific adjectives and nouns customers associate with clothing items.

### 2. Sentiment Analysis via TextBlob
* Leverages `TextBlob` to score customer sentiments across two primary dimensions:
  - **Polarity:** Measures structural tone on a scale from `