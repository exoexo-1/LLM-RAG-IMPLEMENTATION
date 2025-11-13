# 📘 **AmbedkarGPT — Intern Task (RAG + Ollama + LangChain)**

A simple **command-line Q&A system** built as part of the **Kalpit Pvt Ltd – AI Intern Hiring Assignment**.
The system uses a **Retrieval-Augmented Generation (RAG)** pipeline to answer questions **strictly based on Dr. B.R. Ambedkar’s speech**.

This project:

* Loads *speech.txt*
* Splits it into chunks
* Embeds using **HuggingFace (all-MiniLM-L6-v2)**
* Stores vectors in **ChromaDB**
* Retrieves relevant chunks
* Sends context + question to **Ollama (Mistral 7B)**
* Answers only from the provided context
* Falls back to *“I don’t know”* if answer is not in the text

---

# 📂 **Project Structure**

```
AmbedkarGPT-Intern-Task/
│── db/                    # Auto-generated Chroma vector store
│── venv/                  # Your virtual environment (ignored in GitHub)
│── DrAmbedkar's Speach.ipynb   # Development notebook
│── requirements.txt
│── speech.txt             # Provided Ambedkar speech
│── README.md              # You're reading it :)
```

---

# ⚙️ **Installation & Setup**

## 1️⃣ **Clone the Repository**

```bash
git clone https://github.com/exoexo-1/LLM-RAG-IMPLEMENTATION
cd AmbedkarGPT-Intern-Task
```

---

## 2️⃣ **Create Virtual Environment**

```bash
python -m venv venv
source venv/bin/activate        # Mac/Linux
venv\Scripts\activate           # Windows
```

---

## 3️⃣ **Install Dependencies**

```bash
pip install -r requirements.txt
```

This installs:

* langchain
* langchain-community
* sentence-transformers
* chromadb
* torch
* ollama
* requests

---

## 4️⃣ **Install & Setup Ollama (Important)**

### **Download Ollama**

Mac/Linux:

```bash
curl -fsSL https://ollama.ai/install.sh | sh
```

Windows:
Download from → [https://ollama.com/download](https://ollama.com/download)

---

### **Pull the Mistral 7B Model**

```bash
ollama pull mistral
```

---

### **Start Ollama**

```bash
ollama serve
```

You must keep this running while using the script.

---

# 🧠 **How the System Works (RAG Pipeline)**

1. **speech.txt** is loaded
2. Text is split into chunks (300 chars, 100 overlap)
3. Embeddings created using `all-MiniLM-L6-v2`
4. Stored in **Chroma vector database**
5. User asks a question
6. System retrieves top 2 relevant chunks
7. Builds a prompt:

```
Use ONLY this context:
<retrieved chunks>

Question: <user question>
```

8. Sends prompt to **Ollama Mistral**
9. Prints the answer

---

# ▶️ **Running the Chat Application**

Simply run all cells of file  `DrAmbedkar's Speach.ipynb`.



---

# 💬 **Example Usage**

```
Enter your question about Dr. B.R. Ambedkar's speeches:
> What is the real enemy according to the speech?

Assistant:
The speech states that "The real enemy is the belief in the shastras."
```

Out-of-context example:

```
> When was Ambedkar born?

Assistant:
I don't know.
```

---

# 🧪 **Test Questions**

To verify your system:

* *What is the real enemy?*
* *Why can’t someone believe in shastras and oppose caste?*
* *What does the speech say about social reform?*
* *What is compared to a gardener’s work?*
* *Who were Ambedkar’s contemporaries?* → Should answer: **I don't know**

---

# 🏁 **Submission Requirements (all satisfied)**

✔ `speech.txt`
✔ `requirements.txt`
✔ Functional RAG pipeline
✔ Uses LangChain + Chroma + HuggingFace embeddings
✔ Uses Ollama Mistral 7B
✔ Notebook/code well-commented
✔ Command-line chat loop implemented
✔ README explaining setup and usage


---

# 🙌 **Author**

Lakshya Agrawal
AI Intern Candidate — Kalpit Pvt Ltd

---

