# Spam Snippet Classifier — Project Spec

**Project goal:** Build a web app that classifies short email snippets (user-entered) as `spam` or `not_spam`.

**Input / Output:** Input: text (0–500 chars). Output: JSON { label: "spam"/"not_spam", score: 0.0–1.0 }.

**Success metrics & acceptance:** Focus on Precision, Recall, F1 for the spam class. Target: F1 >= 0.88 on held-out test set. Latency <= 150ms on CPU.

**Baseline:** TF-IDF + Logistic Regression (fast, interpretable).

**Candidate models:** CountVectorizer + MultinomialNB; TF-IDF + LogisticRegression; distilBERT (later).

**Datasets:** Enron + SpamAssassin public corpora (~100k examples expected). No user emails for training.

**Compute:** Development on laptop (4 cores, 16GB). Production on CPU instances; optional GPU for heavy experiments.

**Evaluation strategy:** Stratified train/val/test split (70/15/15). Use cross-validation if dataset is small.

**Repro & registry:** Use MLflow for experiments and Model Registry. Dockerize serving image; pin deps with `requirements.txt`.

**Deliverables (MVP):**
- Training script + MLflow logs.
- Best model promoted to MLflow registry.
- FastAPI endpoint for inference.
- Simple frontend (textbox) that calls the endpoint.

**Timeline:** Week 1 - data + baseline; Week 2 - experiments + MLflow; Week 3 - API + container; Week 4 - frontend + CI.

**Risks:** Dataset skew, label distribution mismatch with production, privacy/legal considerations.

**Open questions:** Tolerance for false positives? Will production accept synchronous CPU scoring?
