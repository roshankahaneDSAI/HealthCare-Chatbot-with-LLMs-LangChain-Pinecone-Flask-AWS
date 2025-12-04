# 🏥 **HealthCare Chatbot – LLMs × LangChain × Pinecone × Flask × AWS**

![Python](https://img.shields.io/badge/Python-3.10-blue?logo=python)
![Flask](https://img.shields.io/badge/Flask-2.3-black?logo=flask)
![LangChain](https://img.shields.io/badge/LangChain-RAG-blue)
![Pinecone](https://img.shields.io/badge/Pinecone-VectorDB-purple)
![OpenAI](https://img.shields.io/badge/OpenAI-LLMs-412991?logo=openai)
![AWS](https://img.shields.io/badge/AWS-Deployment-orange?logo=amazonaws)
![License: MIT](https://img.shields.io/badge/License-MIT-green)

---

## 🧠 **Overview**

**HealthCare-Chatbot-with-LLMs-LangChain-Pinecone-Flask-AWS** is a retrieval-augmented, domain-aware healthcare assistant that combines:

🔹 **LLMs** for natural conversation
🔹 **LangChain** for prompt orchestration & RAG pipelines
🔹 **Pinecone** for high-performance vector search
🔹 **Flask** for a lightweight UI backend
🔹 **AWS-ready** code structure for deployment

This chatbot can answer medical/healthcare queries using your custom document corpus stored in a Pinecone vector index.

---

## 📁 **Project Structure**

```
HealthCare-Chatbot/
│── app.py                     # Flask UI server & API
│── vector_index.py            # Embedding + Pinecone index builder
│── requirements.txt           # Python dependencies
│── setup.py                   # Packaging metadata
│── template.sh                # Helper script for deployment
│── .env                       # API keys (excluded in repo)
│
├── data/                      # Source docs for vector indexing
│
├── research/
│     └── Experiment.ipynb     # Example experiments, prototyping
│
├── src/
│     ├── prompt.py            # Prompt templates, system prompts
│     ├── rag_components.py    # LangChain RAG pipeline components
│
├── templates/
│     └── ChatUI.html          # Frontend UI (Flask)
│
└── static/
      └── style.css            # UI styling
```

---

## ⭐ **Features**

### 🔍 **RAG (Retrieval-Augmented Generation)**

* Hybrid LLM + vector search design
* LangChain retrievers and chains
* Supports medical domain documents

### 📚 **Pinecone Vector Database**

* Fast similarity search
* Auto-index update utilities (`vector_index.py`)
* Plug-and-play embedding builders

### 🖥 **Flask Chat UI**

* Clean HTML template
* Simple REST endpoints for user queries
* Supports streaming (optional upgrade)

### 🔬 **Notebooks for Experimentation**

* Example pipelines
* Embedding evaluation
* Prompt tuning

### ☁️ **AWS Deployment Ready**

* Works with EC2, ECS, EB, or Lambda
* Environment-driven configuration
* Deployment helper script (`template.sh`)

---

## 🚀 **Quickstart (Local Setup)**

### **1️⃣ Create a virtual environment**

```bash
python -m venv .venv
source .venv/bin/activate        # Mac/Linux
# or
.venv\Scripts\activate           # Windows
```

---

### **2️⃣ Install dependencies**

```bash
pip install -r requirements.txt
```

---

### **3️⃣ Configure environment variables**

Create `.env`:

```
PINECONE_API_KEY=your_key
PINECONE_ENV=your_env
OPENAI_API_KEY=your_key
MODEL_NAME=gpt-4o-mini   # or any LLM you prefer
INDEX_NAME=medical-index
```

---

### **4️⃣ Build / update the vector index**

```bash
python vector_index.py
```

This script:

* Loads documents from `data/`
* Generates embeddings using your LLM provider
* Stores them in Pinecone

---

### **5️⃣ Run the Flask App**

```bash
python app.py
```

Visit:

👉 **[http://localhost:8080](http://localhost:8080)**

The UI is served using **templates/ChatUI.html** + **static/style.css**.

---

# 📷 **Screenshots**

### 🌐 **Website (Flask Chat UI)**

![chatscreen Screenshot](.static/chatscreen.png)

---

## 🧱 **Architecture Diagram (Conceptual)**

```
           ┌────────────────────────┐
           │      User / Browser    │
           └─────────────┬──────────┘
                         │
                  (Flask REST API)
                         │
           ┌─────────────▼────────────┐
           │        app.py (UI)        │
           └─────────────┬────────────┘
                         │
                 (RAG Pipeline)
                         │
    ┌────────────────────┴─────────────────────┐
    │   rag_components.py  |  prompt.py         │
    └─────────────┬────────────────────────────┘
                  │
           (Vector Retrieval)
                  │
        ┌─────────▼──────────┐
        │   Pinecone VectorDB │
        └─────────┬──────────┘
                  │
         (LLM Completion w/ Context)
                  │
        ┌─────────▼───────────┐
        │    OpenAI / LLMs     │
        └──────────────────────┘
```

---

## ☁️ **AWS Deployment Guide**

You can deploy using any of the following:

### **▶ Deploy on EC2**

* SSH into EC2
* Install Python + dependencies
* Use `gunicorn` / `nginx`
* Run `template.sh` for automated setup

### **▶ Deploy via Elastic Beanstalk**

* Works with Flask out-of-the-box
* Use `setup.py` + requirements.txt

### **▶ Deploy as Lambda (Serverless)**

* Use `serverless-wsgi` wrapper
* Add API Gateway route

### **▶ Deploy with Docker + ECS**

* Add a Dockerfile
* Push to ECR
* Run via ECS Fargate

Want a Dockerfile? I can generate one.

---

## 🔧 **Development Workflow**

| Area                    | Files                                         |
| ----------------------- | --------------------------------------------- |
| **Prompts**             | `/src/prompt.py`                              |
| **RAG pipeline**        | `/src/rag_components.py`                      |
| **Frontend (HTML/CSS)** | `/templates/ChatUI.html`, `/static/style.css` |
| **Vector indexing**     | `vector_index.py`                             |
| **Experiments**         | `/research/Experiment.ipynb`                  |

---

## 🧪 **Extend the Chatbot**

You can add:

* ✔ New medical datasets (drop into `/data`)
* ✔ Custom embedding models (edit `vector_index.py`)
* ✔ Personalized prompt structures
* ✔ Additional retrieval chains
* ✔ AWS S3 document ingestion

Just ask if you want examples!

---

## 🤝 **Contributing**

1. Fork the repository
2. Create a feature branch
3. Commit clean, linted code
4. Submit a PR with details

---

## 📜 **License**

This project is licensed under the **MIT License**.
See **LICENSE** for details.

---

## ❤️ **Author**

**Roshan Kahane**
ML Engineer | AI Chatbots | RAG Architect
🔗 **LinkedIn:** [https://www.linkedin.com/in/roshan-kahane-347550398/]

