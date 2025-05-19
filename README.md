# 🧠 Deep Learning for Encrypted Network Traffic Classification

This project replicates the deep learning-based classification approach from the paper:

**“Deep Learning for Network Traffic Classification”**  
*Niloofar Bayat, Weston Jackson, Derrick Liu*

It focuses on identifying the **application or service behind encrypted TLS traffic** using only **packet size sequences** — without decrypting the data.

---

## 📂 Dataset: `GCseq25.csv`

- Each row represents one **encrypted network flow**
- **Column 0**: Label (domain name from TLS SNI field, e.g., `google.fr`, `quora.com`)
- **Columns 1–100**: Packet size sequence  
  - Positive values = outgoing packets  
  - Negative values = incoming packets  
  - 0 = padding if flow < 100 packets

✅ Labels are derived from the SNI field in the TLS handshake  
✅ No payloads or IPs are exposed — privacy-respecting classification

---

## 🎯 Problem Statement

Modern TLS-encrypted traffic hides application content, making Deep Packet Inspection (DPI) ineffective. This project demonstrates how **deep learning can classify encrypted flows** using only the **shape of the traffic** — enabling smart, privacy-preserving network monitoring.

---

## 🛠️ Approach

We implemented and evaluated:
- A baseline **Deep Neural Network (DNN)**
- A **CNN + LSTM hybrid** model for sequential packet learning
- A **Random Forest** for classical ML comparison
- An **ensemble** (RF + CNN-LSTM) using soft voting

All models are trained on the top-N most frequent domains in the dataset for balanced performance.

---

## 🚀 How to Run the Code

### 1. Open the Notebook in Google Colab

You can launch the notebook directly in Colab:

[![Open In Colab](https://colab.research.google.com/drive/1iNrFKy2rbVKm4V8kV9BMncWCMvHbhiNr#scrollTo=VN0TzeoXHkFC)

Or download and run locally.

### 2. Upload the Dataset

- Download `GCseq25.csv` from this repository
- Upload it manually in the Colab notebook when prompted, or place it in the same directory if running locally

### 3. Install Dependencies (if running locally)

```bash
pip install pandas numpy scikit-learn matplotlib tensorflow
