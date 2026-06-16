# Advanced Natural Language Processing Course<br>Homework 2 Part 5

## Task

Create a small GitHub repository that demonstrates how Jinja templates can be used to generate prompts for an NLP or LLM-based task.
Possible domains include: Movie review analysis, Scientific abstract summarization, Product review classification, Medical text simplification, Educational question generation, Legal document explanation, Recipe instruction rewriting, Customer support intent detection, etc.

## Domain

This project focuses on **Customer Support Intent Detection** which is a common NLP task in technical support systems. The domain involves classifying incoming customer support requests into:
- **Intent categories**: `bug_report`, `technical_question`, `feature_request`, `billing`, `feedback`
- **Urgency levels**: `critical`, `high`, `medium`, `low`
- **Category-based analysis**: Intent classification for each technical category (e.g., `export`, `crash`, `api`, `authentication`)

The dataset contains 5 technical support requests with rich metadata including text, customer info, product type, categories, urgency level, sarcasm detection, and attachment flags.

