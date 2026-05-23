# 🧠 Mental Health Sentiment Classification Using Transformers



This project presents a comparative analysis of five pre-trained transformer models for classifying mental health conditions from patient statements using Natural Language Processing (NLP). The study fine-tunes and evaluates BERT, RoBERTa, DistilBERT, ClinicalBERT, and BioBERT on a large mental health sentiment dataset containing 53,043 labeled statements and validates the best model on real clinical patient conversations from MentalChat16K.

> 🏆 **Best Model: RoBERTa-base (Optimized) — 83.95% Accuracy | 0.8241 Macro F1**

---

## 📊 Dataset

| Property | Details |
|---|---|
| **Source** | [Kaggle Mental Health Sentiment](https://www.kaggle.com/datasets/suchintikasarkar/sentiment-analysis-for-mental-health) |
| **Size** | 53,043 labeled statements |
| **Labels** | Anxiety, Bipolar, Depression, Normal, Personality Disorder, Stress, Suicidal |
| **Split** | 80% Train / 10% Val / 10% Test |
| **Clinical Testing** | [MentalChat16K](https://huggingface.co/datasets/ShenLab/MentalChat16K) — inference only |

---

## 📈 Results

### Model Comparison (3 Epochs | lr=2e-5 | max_len=128)

| Rank | Model | Accuracy | Macro F1 | Micro F1 | Precision | Recall |
|---|---|---|---|---|---|---|
| 🥇 1st | RoBERTa-base (Optimized) | **83.95%** | **0.8241** | **0.8395** | **0.8280** | **0.8212** |
| 🥈 2nd | RoBERTa-base (Original) | 82.87% | 0.8059 | 0.8287 | 0.8142 | 0.8033 |
| 🥉 3rd | BERT-base-uncased | 82.48% | 0.7928 | 0.8248 | 0.8005 | 0.7876 |
| 4th | BioBERT-base-cased | 82.20% | 0.7891 | 0.8220 | 0.7927 | 0.7874 |
| 5th | DistilBERT-base-uncased | 82.03% | 0.7752 | 0.8203 | 0.7834 | 0.7715 |
| 6th | Bio_ClinicalBERT | 81.11% | 0.7839 | 0.8111 | 0.7862 | 0.7828 |

### RoBERTa — Original vs Optimized

| Version | Accuracy | Macro F1 | Improvement |
|---|---|---|---|
| RoBERTa Original | 82.87% | 0.8059 | — |
| **RoBERTa Optimized** | **83.95%** | **0.8241** | **+1.08% / +0.0182** |


---


## 🔍 Key Findings

**Finding 1 — General Models Beat Domain-Specific Models**
RoBERTa and BERT outperformed ClinicalBERT and BioBERT. When training data is informal social media text, general purpose models perform better than domain-specific ones. This challenges the common assumption that clinical models always work best for healthcare NLP tasks.

**Finding 2 — Optimization Significantly Improves Performance**
Increasing epochs from 3 to 5, reducing learning rate from 2e-5 to 1e-5, increasing sequence length from 128 to 256, and using cosine learning rate scheduling improved RoBERTa accuracy by +1.08% and Macro F1 by +0.0182.

**Finding 3 — Caregiver Stress Dominates Real Clinical Conversations**
When validated on MentalChat16K real patient interviews, 82.2% of statements were classified as Stress — confirming the model captures genuine clinical patterns and not just training data artifacts.

**Finding 4 — Suicidal and Depression Classes Are Hardest to Separate**
Suicidal (F1=0.73) and Depression (F1=0.78) had the lowest per-label scores. This is because these two conditions share very similar language patterns. Even human experts find it difficult to distinguish them from text alone without clinical context.

---

## 🏥 Clinical Validation (MentalChat16K)

Tested best model on 500 real patient interview statements. **82.2% classified as Stress** — consistent with clinical research showing caregiver stress as the dominant concern in behavioral health sessions.

---

## ▶️ How to Run

```bash
# 1. Clone repo
git clone https://github.com/GungunSadhwani/mental-health-sentiment-classification-using-transformers.git

# 2. Install dependencies
pip install -r requirements.txt

# 3. Download dataset from Kaggle and upload to Google Drive

# 4. Open in Google Colab with T4 GPU
#    Runtime → Change runtime type → T4 GPU
#    Run notebooks/patient_sentiment_analysis.ipynb
```

---

## 🛠️ Tech Stack

`Python 3.12` `PyTorch` `HuggingFace Transformers` `Scikit-learn` `Google Colab T4 GPU`


---

## 👤 Author

| | |
|---|---|
| **Name** | Gungun Sadhwani |
| **Year** | 2025 |
| **GitHub** | [@GungunSadhwani](https://github.com/GungunSadhwani) |

---

## 📄 License

This project is licensed under the MIT License.

---

⭐ **If you found this helpful, please star the repository!**
