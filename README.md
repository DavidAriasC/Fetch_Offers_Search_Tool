# Fetch Offers Search Tool

## Introduction
This repository contains a Jupyter Notebook that aims to build a text-based search tool for offers. The tool enables users to search for offers by entering text queries that can relate to categories, brands, or retailers. Additionally, the tool provides a similarity score to help rank the search results.

## Requirements
- Python 3.x
- Pandas
- NumPy
- scikit-learn

To run the notebook, make sure to load the required `.csv` files:

- `categories.csv`
- `offer_retailer.csv`
- `brand_category.csv`

## Installation
To install the required libraries, run the following command:

```bash
pip install pandas numpy scikit-learn
```

## Usage

### Data Loading and Exploration

Firstly, the data is loaded into Pandas DataFrames:


```python
categories_df = pd.read_csv("categories.csv")
offer_retailer_df = pd.read_csv("offer_retailer.csv")
brand_category_df = pd.read_csv("brand_category.csv")
```

### Data Preprocessing and Feature Engineering

Text fields are converted to lower case for uniformity:

```python
offer_retailer_df['OFFER'] = offer_retailer_df['OFFER'].str.lower()
categories_df['PRODUCT_CATEGORY'] = categories_df['PRODUCT_CATEGORY'].str.lower()
brand_category_df['BRAND'] = brand_category_df['BRAND'].str.lower()
```

### NLP Model Development
The TF-IDF (Term Frequency-Inverse Document Frequency) technique is used to convert text data into vector form:

```python
vectorizer = TfidfVectorizer()
tfidf_matrix = vectorizer.fit_transform(offer_retailer_df['OFFER'])
```

### Search Functionality
The search function allows users to search by category, brand, or retailer and returns offers sorted by a similarity score:

```python
def search_offers(query, search_type='CATEGORY'):
    # ... (Refer to the notebook for the complete function)
```
    
### Scoring Mechanism
The cosine similarity metric is used to calculate similarity scores, which range from 0 to 1.

## Conclusion and Future Work
This notebook provides a foundational text-based search tool for offers. Future improvements could include the use of more advanced NLP techniques and deploying the tool as a web application.
