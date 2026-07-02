# 🔍 NLP-based Semantic Research Paper Search Engine

A semantic search engine built on 50,000+ ArXiv Machine Learning papers that goes beyond keyword matching — it understands the **meaning** of your query and returns the most relevant papers along with summaries, keywords, and tech entity detection.

---

## ✨ Features

- **Semantic Search** — FAISS + Sentence Transformers se meaning-based search (not just keyword matching)
- **Auto Summarization** — DistilBART se har result ka abstract automatically summarize hota hai
- **Keyword Extraction** — KeyBERT se paper ke important keyphrases nikalta hai
- **Tech Entity Detection (NER)** — GLiNER (zero-shot NER) se paper me use hone wali Programming Languages, Frameworks, Libraries, Databases automatically detect hoti hain

---

## 🛠️ Tech Stack

| Component | Tool Used |
|---|---|
| Dataset | `CShorten/ML-ArXiv-Papers` (Hugging Face) |
| Embeddings | `sentence-transformers/all-MiniLM-L6-v2` |
| Vector Search | `FAISS` (IndexFlatIP) |
| Summarization | `sshleifer/distilbart-cnn-12-6` |
| Keyword Extraction | `KeyBERT` |
| NER | `GLiNER` (urchade/gliner_medium-v2.1) |
| Environment | Google Colab |

---

## 📁 Project Structure

```
research_paper_search/
├── notebooks/
│   ├── 01_eda_and_embeddings.ipynb   # Data prep + embedding generation
│   └── 02_search_engine.ipynb        # Search + NER + Summarization pipeline
├── data/                             # Auto-generated (not uploaded to GitHub)
│   ├── cleaned_arxiv_papers.csv
│   ├── arxiv_embeddings.npy
│   └── paper_faiss.index
├── requirements.txt
└── README.md
```

---

## 🚀 How to Run

### Step 1: Clone the repo
```bash
git clone https://github.com/YOUR_USERNAME/research-paper-search-engine.git
```

### Step 2: Open in Google Colab
- Upload both notebooks to Google Drive
- Open `01_eda_and_embeddings.ipynb` in Colab
- Enable **T4 GPU** (Runtime → Change runtime type → T4 GPU)

### Step 3: Mount Drive + Install dependencies
```python
from google.colab import drive
drive.mount('/content/drive')
```
```bash
pip install -r requirements.txt
```

### Step 4: Run Notebook 1 first
Ye notebook Hugging Face se data download karega, clean karega aur embeddings generate karega (~20-30 min first time)

### Step 5: Run Notebook 2
Search engine + NER + Summarization pipeline chalao

### Step 6: Search karo!
```python
results = search_engine("deep learning for medical image analysis", k=5)
print_results(results)
```

---

## 📊 Sample Output

```
================================================================================
Result #1
Similarity Score : 0.8921
Title            : Deep Learning Approaches for Medical Image Segmentation
Summary          : This paper proposes a novel deep learning framework for
                   automated segmentation of medical images using CNN...
Keywords         : deep learning, medical imaging, image segmentation, CNN
Tech Entities:
   [programming language] Python
   [framework] PyTorch, TensorFlow
   [library] OpenCV, scikit-learn
```

---

## ⚠️ Note
The `data/` folder is not included in this repo (files are too large for GitHub).
Run `01_eda_and_embeddings.ipynb` first to auto-generate all required data files.
