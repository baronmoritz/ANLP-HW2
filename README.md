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

## What the Jinja Templates Do

The project uses four Jinja templates to generate different prompt variants:

| Template | Purpose |
| --- | --- |
| `macros.j2` | Reusable macros for formatting (e.g., `comma_list`, `json_string_array`) |
| `intent_prompt.txt.j2` | Single request prompts with conditional logic for different classification tasks |
| `batch_prompt.txt.j2` | Batch processing prompts using loops over multiple requests |
| `report.md.j2` | Project summary report with statistics and configuration details |

The templates dynamically generate:
- Different classification tasks (intent vs. urgency) from the same template structure
- Few-shot examples with variable counts
- Category-based loops for classification per category
- Different JSON output schemas based on task configuration
- Conditional warnings for sarcasm and attachments

## Why Jinja Is Benefitial for this use case

Jinja provides critical advantages over plain Python string formatting:

### 1. **Multiple Variants from One Template**
A single `intent_prompt.txt.j2` generates three completely different prompt types:
- Intent classification with 5 labels
- Urgency classification with 4 labels  
- Category-based classification with per-category intent assignment

Without Jinja, each variant would require separate hard-coded strings with duplicated logic.

### 2. **Conditional Logic**
Templates use `{% if task.name == "urgency_classification" %}` to:
- Hide urgency metadata during urgency classification (preventing data leakage)
- Switch between intent and urgency labels dynamically
- Adapt instructions based on task mode (document vs. category)

### 3. **Loops for Dynamic Content**
`{% for category in request.categories %}` and `{% for example in examples[:task.max_examples] %}` enable:
- Variable numbers of categories per request
- Configurable few-shot example counts
- Batch processing of multiple requests

### 4. **Separation of Concerns**
- **Data**: Support requests, labels, and configurations live in JSON files
- **Presentation**: Prompt wording and structure live in template files
- **Logic**: Conditional branches and loops stay in templates
- **Execution**: Minimal Python code handles rendering

This makes the project easier to maintain as tasks evolve from simple classification to few-shot, multi-label, or aspect-based workflows.

### 5. **Maintainability**
Adding a new task variant only requires updating `task_configs.json` — no template or Python code changes needed. Editing prompts means modifying template files, not embedded strings.