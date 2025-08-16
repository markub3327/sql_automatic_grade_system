# AI-Driven Evaluation of SQL Tests: A Generative Large Language Model Approach
Evaluate student SQL submissions with the assistance of a Generative Large Language Model (LLM). This project augments traditional auto-grading by using schema-aware prompting and natural-language reasoning to assess correctness, categorize mistakes, and surface rich feedback and analytics.

## Highlights
- Schema-aware grading: the LLM reads a database schema description to contextualize evaluations.
- Automated scoring: classify submissions as correct/incorrect and optionally assign partial credit.
- Error categorization: map common failure modes (e.g., wrong join, aggregation mistakes) to interpretable labels.
- Analytics: generate reports and plots (e.g., confusion matrices, classification metrics) to monitor performance.
- Reproducible pipeline: version inputs, cache model outputs, and export results for downstream analysis.

## How it works
1. Ingest assessment context
    - Database schema description (e.g., a PDF or text file).
    - A dataset of SQL submissions stored in an SQLite database.

2. Construct prompts
    - Combine the schema summary, the task, and each submitted query into a grading prompt.

3. LLM-assisted evaluation
    - Query a configurable OpenAI-compatible API to obtain judgments (labels, rationales, and optional feedback).

4. Aggregation and metrics
    - Compare LLM predictions with ground truth (if available), compute classification metrics, and visualize results.

5. Reporting
    - Export predictions, rationales, and evaluation artifacts for audit and iterative improvement.

## Requirements
- Python 3.9
- A virtual environment managed with virtualenv
- Dependencies:
  - `sqlite3` for database interactions
  - `tqdm` for progress bars
  - `pandas` for data manipulation
  - `pdfplumber` for PDF parsing (if you are using the PDF database schema descriptions)
  - `openai` Python package for interacting with OpenAI's API
  - 'scikit-learn' for classification metrics and confusion matrices 