# Layoff Risk AI Assistant

This repository presents a multi-component AI system that detects layoff risk and provides empathetic support using Reddit layoff discussions. It combines **sentiment analysis**, **layoff risk scoring**, **topic modeling**, and a **fine-tuned language model assistant** to inform and comfort individuals navigating job uncertainty.

### Authors:
**Lufan Wang**: lufanw@uw.edu  

## Project Overview

This project was developed as part of an **AI for Social Impact** initiative at the University of Washington (Spring 2025). The goal is to empower employees with early warning signs of layoffs using natural language patterns and assistive AI responses.

## Dataset Information

**About the Dataset**  
We scraped and curated comments from subreddits like `r/layoff`, `r/cscareerquestions`, and `r/techlayoffs`, focusing on posts with clear narrative context or emotional tone. Each comment was manually or semi-automatically labeled with:
- **Sentiment**: `Negative`, `Neutral`, `Positive`
- **Layoff Risk Score**: Heuristic score based on keywords like `"reorg"`, `"budget cuts"`, `"fired"`
- **Risk Category**: `High`, `Medium`, `Low`

**Objective**  
To train a model that can:
- Detect emotional and structural indicators of impending layoffs
- Provide empathetic feedback to users
- Offer structured, explainable predictions using real employee language

## 1. `sentiment_model.ipynb` — Sentiment Classification

Trains a baseline **logistic regression** model on Reddit comments:
- Vectorized via **TF-IDF**
- Evaluated with **accuracy**, **precision**, **recall**, and **confusion matrix**
- Limitations: bias toward `neutral` class on small datasets

## 2. `risk_scorer.py` — Layoff Risk Heuristics

Implements a keyword-weighted scoring function:
- Keywords like `"laid off"`, `"severance"`, `"terminated"` weighted `0.7–1.0`
- Scores capped at `1.0` and converted into categories: `Low`, `Medium`, `High`
- Integrated into the assistant’s real-time classification pipeline

## 3. `topic_modeling.ipynb` — LDA Topic Discovery

Discovers thematic structure within layoff discussions:
- Uses `CountVectorizer` + `LatentDirichletAllocation`
- Topics include **job search struggles**, **team-wide reorgs**, **fake postings**, and **severance experiences**

## 4. `layoff_assistant.ipynb` — GPT-Style Empathetic Assistant

Formats `.jsonl` data for fine-tuning a language model:
- Each entry includes a `system` prompt, `user` input, and `assistant` reply

Example format:
```json
{
  "messages": [
    {"role": "system", "content": "You are an empathetic assistant helping users navigate layoff situations."},
    {"role": "user", "content": "I was just laid off after 5 years at my job."},
    {"role": "assistant", "content": "I'm so sorry to hear that. It's okay to feel overwhelmed. Have you been able to talk to anyone about next steps yet?"}
  ]
}
```

## 5. `demo_app.py` — Streamlit Interface

- Accepts user-entered text
- Displays predicted **sentiment** and **risk score**
- Shows AI assistant's supportive reply
- Fully local model architecture to ensure privacy

## Visuals

- Confusion matrix showing class bias and model performance
- Bar plots of top bigrams (e.g., `"budget cuts"`, `"fired me"`)
- Risk-level distribution chart
- Topic keyword lists and sample comments

## Citation

- Reddit comments accessed under **fair use** guidelines for educational research
- LLM fine-tuning conducted in accordance with OpenAI and Hugging Face usage policies

## Next Steps

- Improve labeling with **transformer-based sentiment classifiers**
- Train on **1,000+ examples** for robust empathy generation
- Integrate **retrieval-based memory** (e.g., company layoff histories)
- Deploy as an **open-source HR advisory tool**
