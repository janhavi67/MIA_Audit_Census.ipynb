# Membership Inference Attack (MIA) & Privacy Audit

## 🛡️ Project Overview
This project performs a security audit on a Machine Learning model trained on the **UCI Adult Census Income** dataset. I implemented a **Membership Inference Attack (MIA)** to determine if a specific individual's data was used to train a target "Victim" model.

The goal of this research is to quantify data leakage in overfitted models and evaluate the effectiveness of regularization as a privacy-preserving defense.

---

## 🚀 Key Features
- **Victim Model:** Decision Tree Classifier (92% Train Acc / 82% Test Acc).
- **Adversarial Model:** Random Forest "Hacker" model trained on prediction signatures.
- **Leakage Signals:** Engineered features including `Log-Loss`, `Entropy`, and `Is_Correct`.
- **Privacy Query Tool:** Custom function to audit the "Leak Risk" of individual profiles.

---

## 📊 Experimental Results
Through this audit, I identified that model correctness is the primary side-channel for data exposure.

| Metric | Result |
| :--- | :--- |
| **Privacy Gap (Train vs Test)** | 10.2% |
| **Attack Success Rate** | 55.14% |
| **Primary Leakage Vector** | Prediction Correctness (Importance > 0.5) |

### Hacker Analysis
- **Recall (91.5%):** The attacker is highly effective at identifying true members.
- **Defense:** Demonstrated that `min_samples_leaf=10` provides a 5% protection boost compared to unregularized trees.

---

## 🛠️ How to Use
1. Clone the repository:
   `git clone https://github.com/YOUR_USERNAME/AI-Privacy-Audit-MIA.git`
2. Install dependencies:
   `pip install -r requirements.txt`
3. Run the notebook:
   `jupyter notebook notebooks/MIA_Audit.ipynb`

---

## 📝 Conclusion & Future Work
This audit proves that even high-performing models can leak sensitive membership information. 
**Future Scope:** Implementing **Differential Privacy (DP)** using the Opacus library to mathematically guarantee a "Privacy Budget" ($\epsilon$).
