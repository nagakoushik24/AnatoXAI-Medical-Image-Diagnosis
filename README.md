## 🧾 Abstract

**AnatoXAI** introduces an *Anatomically-Informed Counterfactual Explainable AI* framework for **robust medical image diagnosis**.  
While deep learning models achieve high accuracy, they often lack interpretability — a crucial barrier in clinical adoption.  
AnatoXAI bridges this gap through:

- **Hybrid Vision-Graph Transformer (HybridVGT)** – combines global ViT features with anatomical graph reasoning.  
- **Anatomically-Constrained Counterfactuals** – generate clinically valid explanations by modifying only medically relevant regions.

The model improves diagnostic accuracy (AUC ↑ 0.8603) on the **NIH Chest X-ray14 dataset** and produces counterfactual explanations that are far more interpretable than Grad-CAM.

---


## 🎯 Objective

To develop an **AI-powered, explainable medical diagnosis system** that enhances clinician trust through anatomically grounded explanations.

---

## 🩺 Key Features

- ✅ **Virtual Health Assistant** for symptom checks and appointments  
- 🧠 **AI-based Medical Imaging** analysis using HybridVGT  
- 📊 **Health Analytics Dashboard** with SHAP and Grad-CAM comparisons  
- 🔍 **Counterfactual Explanations** for interpretable AI decisions  
- ⏰ **Health Management System** with reminders and follow-ups  

---

## 🧬 Methodology

### 1. Dataset and Preprocessing
- **Dataset:** NIH Chest X-ray14 (112,120 images, 14 disease classes)
- **Focus Diseases:** Atelectasis, Cardiomegaly, Consolidation, Edema, Pleural Effusion  
- **Segmentation:** U-Net for anatomical mask extraction  
- **Preprocessing:** 224×224 resizing, normalization, mask-based graph mapping  

### 2. Hybrid Vision-Graph Transformer (HybridVGT)
- Combines **ViT Backbone** (global visual context)  
- **Anatomical Graph Network** (lung, heart nodes)  
- **Fusion Layer:** Concatenates [CLS] token + graph embeddings  
- Trained using Adam optimizer with differential learning rates  

### 3. Anatomically-Constrained Counterfactuals
Optimizes:

```
L = L_pred + λ₁·L_prox + λ₂·L_anat
```

- Ensures **minimal yet meaningful** modifications  
- Restricts changes within anatomical masks for clinical plausibility  

---

## 📊 Experimental Results

| Model | Mean AUC |
|--------|-----------|
| ResNet-50 | 0.8414 |
| ViT | 0.8067 |
| **HybridVGT (Proposed)** | **0.8603** |

### 🩻 Qualitative Insights
- Grad-CAM: Highlights rough attention regions  
- **AnatoXAI Counterfactuals:** Show *what* changes led to diagnosis  
- Example: For Cardiomegaly, model reduces cardiac boundary to simulate a “normal” X-ray → clinically interpretable.

---

## 🏗️ System Architecture

### ⚙️ Components
- **Frontend:** React.js (doctor, patient, admin dashboards)  
- **Backend:** Flask REST API with AI microservice  
- **Database:** Firebase (auth & storage)  
- **AI Engine:** HybridVGT model hosted as Flask microservice  

### 👤 User Roles
- **Doctor Portal:** Upload, analyze, and visualize AI results  
- **Patient Portal:** View reports, follow-up reminders, chatbot  
- **Admin Panel:** Manage users, monitor system performance  
