# Customer Support Intent Detection

Jinja templates for dynamic intent detection prompts in customer support.

## Dataset Summary

Total support requests: 5

Requests with possible sarcasm: 2

Requests with attachments: 1

Intent distribution:
- req001: bug_report
- req002: bug_report
- req003: technical_support
- req004: technical_question
- req005: feature_request

## Prompt Variants

### 1. intent_classification

- Mode: `document`
- Labels: bug_report, technical_question, feature_request, billing, feedback
- Few-shot examples: yes, up to 3- JSON-only response: yes
This variant forces a single intent classification.

### 2. intent_with_urgency

- Mode: `document`
- Labels: bug_report, technical_question, feature_request, billing, feedback
- Few-shot examples: yes, up to 5- JSON-only response: yes
This variant forces a single intent classification.

### 3. category_based

- Mode: `category`
- Labels: bug_report, technical_question, feature_request, billing, feedback, not_applicable
- Few-shot examples: no- JSON-only response: yes
This variant changes the output schema from one document-level label to a list of category-level intents.


## Why Jinja Is Useful Here

The templates handle:

- conditional task modes (document vs category),
- optional few-shot examples,
- different label spaces,
- sarcasm warnings,
- attachment notes,
- urgency levels,
- document-level versus category-level JSON schemas,
- batch versus single-request prompts.