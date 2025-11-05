# 🛡️ Data Privacy Case Study — Healthcare Data Anonymization
**Course Code:** BCSE318L · **Semester:** Fall 2025–26  
**Author:** Vinayak Raina (22BCE2052)  
**Faculty:** Mohammed Yacoob B. A.  
**Date of Submission:** 05 November 2025  

---

## 📘 Project Overview  
This repository contains the **Jupyter Notebook and source code** used for the **Data Privacy Case Study**, focusing on **applying and comparing anonymization techniques** — namely **k-Anonymity**, **l-Diversity**, and **Tokenization** — on a **synthetic healthcare dataset**.

The goal is to protect patient privacy while ensuring that the anonymized dataset remains useful for data analysis, predictive modeling, and research.  

The project uses Python-based privacy-preserving transformations combined with quantitative metrics to evaluate privacy–utility trade-offs.

---

## 🧩 Dataset  
**Source:** [Synthetic Healthcare Dataset (Kaggle)](https://www.kaggle.com/datasets/divyabhavana/synthetic-healthcare-dataset)  
**Size:** 1,000 records · 13 attributes  

**Key Attributes:**  
- **Explicit Identifiers (EI):** `Patient_ID`, `Hospital_ID`  
- **Quasi-Identifiers (QI):** `Age`, `Gender`, `Insurance_Type`, `Admission_Type`  
- **Sensitive Attributes (SA):** `Medical_Condition`, `Outcome`  
- Additional features include `Income`, `Region`, and `Smoking_Status`.

---

## ⚙️ Methodology  

### 1. **Data Preprocessing**
- Loaded the dataset using `pandas`.
- Classified attributes into **EI**, **QI**, and **SA**.
- Removed explicit identifiers and standardized quasi-identifiers.

### 2. **Anonymization Techniques**
Implemented and compared multiple privacy-preserving transformations:
- 🔹 **Tokenization:** Random UUID-based substitution for EI fields.
- 🔹 **Hashing (SHA-256):** Cryptographic irreversible encoding.
- 🔹 **Masking:** Partial visibility using asterisk-based concealment.
- 🔹 **Generalization:** Conversion of QI (e.g., age ranges, category simplification).

### 3. **Privacy Models**
- **k-Anonymity:** Ensures each record is indistinguishable from at least *k–1* others.  
- **l-Diversity:** Enforces diversity in sensitive attributes to prevent attribute disclosure.

### 4. **Evaluation Metrics**
- **Distinct QI combinations:** Measures dataset utility.  
- **Re-identification Risk:** Average risk across QI groups.  
- **Information Loss:** 1 – (post-anonymization distinct QI / baseline distinct QI).

### 5. **Visualization and Reporting**
Generated comparative visualizations:
- Risk vs. k and Information Loss vs. k plots  
- k–l risk heatmap  
- Entropy comparison for anonymization methods  
- Bar graphs for privacy risk and information loss  

All visualizations are automatically saved as:
- `anonymized_analysis.png`  
- `anonymized_privacy_visuals.png`

---

## 🧮 Key Results  

| **k** | **Distinct QI** | **Re-ID Risk** | **Info Loss (%)** |
|:--:|:--:|:--:|:--:|
| 2 | 220 | 0.348 | 15.7 |
| 3 | 206 | 0.311 | 21.1 |
| 4 | 192 | 0.296 | 26.4 |
| 5 | 169 | 0.289 | 35.2 |

**Findings:**
- Increasing *k* decreases **re-identification risk** (↑ privacy).  
- Higher *k* increases **information loss** (↓ utility).  
- Optimal configuration: **k = 3, l = 2** → best privacy–utility balance.  
- Tokenization and Hashing offered strong protection; Masking led to high utility loss.

---

## 🔍 Privacy–Utility Trade-off  
- Higher k-values result in stronger privacy guarantees but reduced analytical precision.  
- Excessive generalization (k > 5) yields diminishing returns for real-world utility.  
- At k=3, l=2, privacy risk dropped by ~11% while maintaining 100% record retention.  
- The trade-off plots confirm that the dataset remains useful for **machine learning and statistical analysis** even after anonymization.

---

## 🧠 Discussion and Recommendations  

**Privacy Summary:**
- Effective anonymization can protect sensitive healthcare data without sacrificing data utility.  
- Combining k-anonymity with controlled generalization and tokenization ensures balance between usability and compliance.  

**Recommendations:**
1. Implement **adaptive optimization** to automate k–l parameter selection.  
2. Extend the model with **Differential Privacy** for formal mathematical guarantees.  
3. Build a **web-based API or dashboard** for hospitals to upload and anonymize data securely.  
4. Use **larger, multi-hospital datasets** for future scalability tests.  
5. Add **interactive visual dashboards** (Plotly, Dash, Tableau) for comparative insights.

---

## 🌍 Real-World Applications  
1. **Hospitals & Healthcare Systems:** Safely share anonymized patient data for clinical research.  
2. **Pharmaceutical Companies:** Analyze treatment outcomes without exposing personal details.  
3. **Public Health Agencies:** Track disease spread with privacy-preserved patient data.  
4. **Academic Research:** Use anonymized datasets for model development and ethical AI training.

---

## 💾 Repository Structure  
```
DataPrivacy_CaseStudy/
│
├── DataPrivacy_CaseStudy.ipynb        # Jupyter Notebook (Main code)
├── medical_data.csv                   # Input dataset (synthetic healthcare data)
├── anonymized_data_k3.csv             # Final anonymized dataset (k=3, l=2)
├── anonymized_metrics.csv             # Metrics for k–l analysis
├── anonymized_methods.csv             # Method comparison data
├── anonymized_analysis.png            # Risk & utility visualization
├── anonymized_privacy_visuals.png     # Entropy & privacy comparison
└── README.md                          # Project documentation
```

---

## 🧰 Technologies Used  
- **Python 3.10+**  
- **Libraries:** `pandas`, `numpy`, `matplotlib`, `seaborn`, `hashlib`, `uuid`  
- **Visualization:** Matplotlib + Seaborn  
- **Environment:** Jupyter Notebook / Google Colab  

---

## 🚀 How to Run  
1. Clone the repository:
   ```bash
   git clone https://github.com/RAINAVINAYAK16/DataPrivacy_CaseStudy.git
   cd DataPrivacy_CaseStudy
   ```
2. Install dependencies:
   ```bash
   pip install pandas numpy matplotlib seaborn
   ```
3. Run the notebook:
   ```bash
   jupyter notebook DataPrivacy_CaseStudy.ipynb
   ```
4. Check outputs in the `/content/` directory:
   - `*_analysis.png`
   - `*_privacy_visuals.png`
   - `*_data_k3.csv`
   - `*_metrics.csv`

---

## 📈 Author’s Insight  
This project reflects how **ethical data engineering** can preserve individual privacy while still enabling innovation in healthcare analytics. It demonstrates the practical balance between **data protection and utility**, emphasizing that privacy-aware computation is not a constraint but a **catalyst for responsible AI and research**.

---

## 🧾 References  
- [Synthetic Healthcare Dataset – Kaggle](https://www.kaggle.com/datasets/divyabhavana/synthetic-healthcare-dataset)  
- [Wikipedia – K-Anonymity](https://en.wikipedia.org/wiki/K-anonymity)  
- [Wikipedia – L-Diversity](https://en.wikipedia.org/wiki/L-diversity)  
- [IBM Developer – Tokenization and Masking](https://developer.ibm.com/articles/secure-data-using-tokenization-and-masking/)  
- [GeeksforGeeks – Data Anonymization Techniques](https://www.geeksforgeeks.org/data-anonymization-in-data-mining/)  
- [Towards Data Science – Data Privacy Explained](https://towardsdatascience.com/data-privacy-k-anonymity-l-diversity-and-t-closeness-explained-4e0f4f17f22b)  
