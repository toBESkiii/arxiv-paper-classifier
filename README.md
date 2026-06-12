ArXiv Research Paper Classifier

An end-to-end big data NLP pipeline that classifies and simplifies academic research papers from arXiv using PySpark, ensemble machine learning models, and LLaMA 3.3 via the Groq API.


The Problem

Thousands of computer science papers are published on arXiv every week. Most are written in dense academic language that makes them inaccessible to students, beginners, and non-experts — even when the research is directly relevant to them.

This project tackles two problems:


Automatically classify papers into their correct research domain
Generate plain-English summaries so anyone can understand what a paper is about



How It Works

Pipeline Overview

Raw arXiv Papers → Text Cleaning → Feature Extraction → Classification → LLM Summary Generation

Stage 1 — Data


1,000 arXiv research papers across 5 computer science domains:

Artificial Intelligence
Computational Linguistics
Computer Vision
Machine Learning
Computer Security





Stage 2 — Text Preprocessing (PySpark)


Removed stopwords, punctuation and noise
Tokenised and normalised raw paper text
Applied CountVectorizer and TF-IDF for numerical feature extraction


Stage 3 — Topic Modelling


Applied LDA (Latent Dirichlet Allocation) to identify underlying topics across the corpus


Stage 4 — Classification Models

Three models were trained and evaluated on the processed dataset:

ModelAccuracyWeighted F1-ScoreNotesLogistic Regression70.33%0.6568Overfitted on training dataNaive Bayes——Baseline comparisonEnsemble Model74.23%0.7007Best overall performance


The ensemble model outperformed individual classifiers on an imbalanced dataset. Weighted F1-score was used as the primary evaluation metric rather than accuracy alone, to account for class imbalance.



Stage 5 — LLM Integration


Integrated LLaMA 3.3 via the Groq API to take classification results and generate plain-English summaries
Makes research accessible to non-expert audiences without sacrificing technical accuracy



Tech Stack

CategoryToolsLanguagePythonBig Data FrameworkPySparkFeature ExtractionCountVectorizer, TF-IDFTopic ModellingLDAML ModelsLogistic Regression, Naive Bayes, EnsembleLLM IntegrationLLaMA 3.3, Groq APIEnvironmentGoogle Colab


Key Results


Best model: Ensemble — 74.23% accuracy, 0.7007 weighted F1-score
Key insight: Accuracy alone is insufficient for imbalanced datasets — weighted F1-score provides a more reliable performance measure
LLM integration successfully converted complex classification outputs into accessible plain-English summaries


What I Learned


How to build scalable ML pipelines on large text datasets using PySpark
Why evaluation metric selection matters more than raw accuracy on imbalanced data
How to integrate production LLM APIs to add real value on top of ML outputs
