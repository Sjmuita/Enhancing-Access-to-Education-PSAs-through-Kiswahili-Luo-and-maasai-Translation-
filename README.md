# Enhancing Access to Education PSAs through Kiswahili, Luo, and Maasai Translation

**United States International University – Africa**  
**Contributors:** Shalyn Muita, Arnold Bophine, Jemimah Bochaberi, Chanteel Kimathi, Melvin Lebo  
**Date:** August 6, 2025

---

##  Project Overview

Public Service Announcements (PSAs) are a vital communication tool for education, civic awareness, and health. However, language barriers often prevent these messages from reaching all communities, especially in multilingual regions like Kenya.

This project aims to improve access to educational PSAs by translating them into Kiswahili, Luo, and Maasai — ensuring that **every voice is heard, and every message is understood**.

---

##  Objectives

- Bridge the language gap in civic communication.
- Fine-tune machine translation models on domain-specific, low-resource data.
- Enable reliable, confidence-aware translation workflows.
- Support cultural preservation through localized language use.

---

##  Methodology

### 1. **Data Collection & Preprocessing**
- Scraped and curated **1,100+ education-related PSAs**.
- Cleaned and validated the dataset:
  - Removed duplicates and short/incomplete entries.
  - Standardized date, format, language, and URL fields.
  - Flagged anomalies for manual review.

### 2. **Initial Translation (Swahili)**
- Used **Google Translate API** to generate initial Swahili translations.
- Manually aligned and cleaned outputs for fine-tuning quality.

### 3. **Model Fine-Tuning**
- Fine-tuned **MarianMT (opus-mt-en-sw)** on English–Swahili PSA pairs.
- Training/Testing split: 90% / 10%
- Result: **BLEU score: 59.71** (after 1 epoch)

### 4. **Advanced Pipeline: NLLB-200**
- Developed a two-stage pipeline:
  - English → Kiswahili → Luo using `facebook/nllb-200-distilled-600M`
- Integrated:
  - Language tags (`eng_Latn`, `swh_Latn`, `luo_Latn`)
  - Token-level **confidence scoring** using softmax probabilities
- Maasai (MAA) handled via custom civic domain dictionary.

### 5. **Translation Quality Analysis**
- Visualized confidence distributions with **KDE plots**.
- Identified examples with **high and low confidence**.
- Output included:
  - Final translated text
  - Token confidence
  - Language metadata

---

##  Key Results

###  **ENG → Kiswahili**
- **Mean confidence:** ~0.70
- **Confidence range:** 0.6 – 0.75
- Translations are reliable and consistent.

###  **Kiswahili → Luo**
- **Mean confidence:** ~0.50 (more variable)
- Some strong outputs (e.g., *"Kony jopuonjre!"* → ~0.796)
- Needs more data and refinement.

###  Maasai (MAA)
- Custom dictionary-based translation on small civic subset.
- Evaluated with **BLEU, perplexity, and coherence**.

---

##  Challenges

- **Low-resource data**: Limited manually translated Swahili and almost no Luo PSA data.
- **Ambiguity**: Luo model showed lower confidence due to sparse training.
- **Terminology mismatch**: Domain-specific terms like *“CBC”*, *“KUCCPS”* were hard to translate without glossaries.

---

##  Recommendations & Future Work

- Enhance low-confidence translations via **expert human review**.
- Expand domain-specific datasets in **education, civic, legal** topics.
- Integrate **topic modeling (LDA)** and **quality estimation models**.
- Develop **interactive dashboards** for stakeholders to explore translation insights.

---

## 📜 License

- **Code**: [MIT License](https://opensource.org/licenses/MIT)
- **Dataset**: [CC BY 4.0 License](https://creativecommons.org/licenses/by/4.0/)

---

## 🙏 Acknowledgments

We acknowledge the support of our professor Dr.Edward Ombui, linguists, civic educators, and the open-source community for contributing resources, guidance, and datasets to this project.

