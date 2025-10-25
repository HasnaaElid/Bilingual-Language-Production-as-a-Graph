# Graph-Based Insights into the Bilingual Brain

<div class="badges">
  <span class="badge">Python</span>
  <span class="badge">fMRI</span>
  <span class="badge">Network Science</span>
  <span class="badge alt">Machine Learning</span>
</div>

**Summary.**  
This project applies graph analytics and machine learning to bilingual fMRI data to explore how the brain’s communication network reorganizes during speech in a non-native language.  
The analysis uses open data from *OpenNeuro ds004456* (Polish–English bilingual adults) and focuses on two tasks:
1. **Alice (Speech)** — reading a passage aloud in English  
2. **Articulation (Control)** — silently mouthing the same passage  

By modeling the brain as a network of interacting regions, the project examines whether bilingual speech introduces measurable changes in connectivity, coordination, and control.

---

## 📊 Contents

| File | Description |
|------|--------------|
| **`bilingual_graph.ipynb`** | Single-subject feasibility analysis. Loads one fMRI subject, extracts time series, builds a correlation graph, and computes key network metrics (degree, betweenness, PageRank). |
| **`bilingual_graph-apply.ipynb`** | Multi-subject extension (n≈19). Generates group-level summaries, trains predictive models (L1-Logistic Regression, Random Forest) to distinguish speech vs. articulation, and visualizes feature importance. |

---

## 🧠 Approach

1. **Data preparation** — Extract regional time series using the Schaefer-2018 brain atlas (100 parcels).  
2. **Graph construction** — Build a functional connectivity graph per run, keeping the five strongest connections per node.  
3. **Network metrics** — Compute degree, betweenness centrality, and PageRank using NetworkX.  
4. **Modeling** —  
   - Global features → Logistic Regression / Random Forest  
   - Regional features → L1-regularized Logistic Regression (subject-wise CV)  
5. **Evaluation** — Accuracy, ROC-AUC, confusion matrix, and interpretability of top predictive regions.

---

## 🧩 Key Results

- **Small-world organization** observed in both tasks, consistent with efficient neural communication.  
- **Right somatomotor and salience networks** showed increased centrality during speech — reflecting higher articulatory and attentional control.  
- **Predictive modeling:**  
  - Logistic Regression ROC-AUC ≈ **0.38** (global summary features)  
  - Random Forest ROC-AUC ≈ **0.26**  
  - L1-regularized Logistic Regression ROC-AUC ≈ **0.75**, highlighting consistent task-related patterns.  
- Results suggest measurable, reproducible reorganization in bilingual speech control networks.

---

## 🧠 Interpretation

Hesitation in bilingual speech may reflect not weakness but the **neural coordination cost** of managing two active language systems.  
Graph-based modeling helps visualize this cost and offers interpretable, data-driven evidence of bilingual brain flexibility.

---

## ⚙️ Environment

```bash
pip install -r requirements.txt
# or minimal
pip install numpy pandas scikit-learn networkx nilearn matplotlib seaborn
