# Customer Support Intent Detection

Jinja templates for dynamic intent detection prompts in customer support.

## Dataset Summary

Total support requests: 5

Requests with possible sarcasm: 2

Requests with attachments: 1

Urgency distribution:
- high: 2
- critical: 1
- medium: 1
- low: 1

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
This variant performs standard intent classification.

### 2. urgency_classification

- Mode: `document`
- Labels: critical, high, medium, low
- Few-shot examples: yes, up to 3- JSON-only response: yes
This variant classifies the urgency level of support requests instead of their intent, demonstrating how the same template structure can handle completely different classification tasks.

### 3. category_based

- Mode: `category`
- Labels: bug_report, technical_question, feature_request, billing, feedback, not_applicable
- Few-shot examples: no- JSON-only response: yes
This variant changes the output schema from one document-level label to a list of category-level intents.


## Why Jinja Is Useful Here

The templates handle:

- conditional task modes (document vs category vs urgency classification),
- optional few-shot examples,
- different label spaces (intents vs urgency levels),
- sarcasm warnings,
- attachment notes,
- document-level versus category-level JSON schemas,
- batch versus single-request prompts,
- completely different classification tasks (intent vs urgency) from the same template structure.