# Layoff Risk AI Assistant

This project presents a multi-component AI system designed to **detect layoff risk** and **offer empathetic support** using Reddit discussions and structured layoff datasets. It integrates **sentiment analysis**, **risk scoring**, and **retrieval-augmented generation (RAG)** to empower individuals facing career uncertainty.

**Live Demo**: [http://10.19.66.229:5173/](http://10.19.66.229:5173/)

## Author

**Lufan Wang**  
Email: [lufanw@uw.edu](mailto:lufanw@uw.edu)  
University of Washington

## Included Files

| File Name                                | Description                                                                 |
|------------------------------------------|-----------------------------------------------------------------------------|
| `Layoffs.csv`                            | Historical layoff dataset scraped from [layoffs.fyi](https://layoffs.fyi) for trend analysis and model training. |
| `layoff_comments_with_sentiment.csv`     | Curated Reddit comments annotated with sentiment labels and risk scores.   |
| `Layoffs Prediction.ipynb`               | Jupyter notebook that explores predictive modeling using the `Layoffs.csv` dataset. |
| `Reddit comments.ipynb`                  | Notebook analyzing Reddit posts using TF-IDF, logistic regression, and sentiment classification. |
| `Claude with Layoff Embedding RAG Cookbook.ipynb` | A Retrieval-Augmented Generation (RAG) demo using Claude to answer layoff-related queries. |


## Key Features

- **Layoff Risk Prediction** from structured company layoff datasets
- **Sentiment Classification** on Reddit comments using TF-IDF + logistic regression
- **Visualization** of risk distributions and bigram trends
- **RAG Assistant** to respond empathetically using vector search and LLMs


## Data Sources

- **Layoff Records**: Collected from [Layoffs.fyi](https://layoffs.fyi/)
- **Reddit Data**: Scraped from subreddit discussions including:
  - `r/layoff`
  - `r/techlayoffs`
  - `r/cscareerquestions`
- **Annotation Labels**:
  - `Sentiment`: `Negative`, `Neutral`, `Positive`
  - `Layoff Risk`: Heuristic score from `0.0` to `1.0` based on trigger keywords
  - `Risk Category`: Classified as `Low`, `Medium`, or `High`


## Example Use Case

A user enters:

> "We had a surprise all-hands. Everyone's nervous."

The system responds with:
- **Predicted Sentiment**: `Negative`
- **Layoff Risk Level**: `High`
- **Assistant Reply**: _"It’s understandable to feel anxious. Has leadership shared any specific updates? Let’s look at recent trends together."_


## Visualizations

- Confusion matrix for model performance
- Layoff risk distribution histogram
- LDA topic modeling results with top keywords per topic
- Bigrams frequency analysis (e.g., `"budget cuts"`, `"fired me"`)


## Citation & Usage

- All Reddit-based content was accessed under **fair-use** for educational research purposes.
- RAG-based assistant was developed using Claude/OpenAI APIs, adhering to their [usage policies](https://openai.com/policies/usage-policies).
