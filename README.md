# project101
Email ticket organizer
from pathlib import Path

Customer Service Email Organizer
Automatically categorize and prioritize customer service emails using machine learning.
This project was developed as part of the MLT Program at Morehouse College with support
from the Texas Advanced Computing Center (TACC).

Problem Statement
*Amazon receives thousands of customer service emails daily. Manual triage is slow, and
spam or malware further delays responses, reducing customer satisfaction.
* Goal: Assign each email a category, detect spam/malware, predict urgency/severity for
triage.

Dataset
* Source: Kaggle -> support ticket dataset
* Total emails: 1,694
* Categories: Complaint (1565), Account/Billing (65), Returns/Refunds (30), Shipping
(34)
* Preprocessing: Lowercasing, NA removal, TF–IDF vectorization (1–2 grams), Train/test
split: 80/20 stratified

Methods
* Models Tested: Decision Tree, Random Forest, Logistic Regression
* Vectorizer: TF–IDF (max 5,000 features)
* Training: Stratified 80/20 split
* Routing Logic: Predict category → assign to queue; Score severity → assign priority
* Why Decision Tree?: Highest accuracy (94.1%), Easy to interpret

Results
* Model Accuracy: Decision Tree: 94%, Random Forest: 93%, Logistic Regression: 93%
* Severity Classifier: 99.5% accuracy (strong for LOW, weaker for MEDIUM)
* Example Predictions:
* “URGENT! Package is damaged” → Shipping, HIGH
* “Refund item doesn’t fit” → Returns, LOW
* “Credit card charged twice” → Billing, MEDIUM

Impact

* Faster triage of customer emails
* Urgent cases surface first
* Spam/malware blocked before reaching agents

Limitations
* Low data for Shipping/Returns categories
* MEDIUM severity under-predicted

Future Plans
* Add end-user applications (web dashboard, mobile app)
* Enhance spam &amp; virus detection (attachments, domains, headers)
* Improve accuracy with advanced NLP (DistilBERT, Longformer)
* Human-in-the-loop active learning
* Multilingual support
* Security and compliance (PII redaction, encryption, audit logs)

Installation &amp; Usage
* Requirements: Python 3.8+, Packages: scikit-learn, pandas, numpy, matplotlib, seaborn
* Setup:
* Clone repository: git clone https://github.com/your-username/customer-email-
organizer.git
* cd customer-email-organizer
* Install dependencies: pip install -r requirements.txt
* Run training: python train_model.py
* Run predictions: python predict.py --input sample_emails.csv

References
* Scikit-learn Documentation: https://scikit-learn.org/stable/user_guide.html
* Kaggle Customer Complaints Dataset: https://www.kaggle.com
* Pedregosa, F. et al. (2011). Scikit-learn: Machine Learning in Python. JMLR.
* Villena-Román, J. et al. (2011). Combining ML with Rule-Based Systems. CLEF.
