# 🏥 Emergency Medical Triage – Custom RAG Model
This project implements a Retrieval-Augmented Generation (RAG) system for emergency medical triage using Haystack and OpenAI’s GPT models. The model retrieves relevant clinical content from a curated document store and generates structured triage decisions based on user queries.

### ⚕️ Use Case
Emergency triage is a high-stakes process where rapid, accurate decisions are critical. This project explores how RAG-enabled large language models (LLMs) can support clinical decision-making by:

- Assigning triage levels based on symptoms
- Providing rationale for decisions
- Referencing reliable medical sources (e.g., WHO triage manuals, medical textbooks)

### 🧠 Tech Stack
- Framework: Haystack (Python)
- LLM: OpenAI GPT (via API)
- Retriever: BM25 (InMemory), with support for FAISS
- Evaluation: Ragas framework for LLM performance assessment
- Pipeline components: Retriever, DocumentJoiner, PromptBuilder, OpenAI Generator, AnswerBuilder
- Optional: RAGAS Evaluator

### ⚙️ How It Works
1. **Query Input**: User enters a triage-related question (e.g. “A 70-year-old male with chest pain and shortness of breath. What should be done?”)
2. **Document Retrieval**: Top-k relevant chunks are retrieved from the document store (BM25 or FAISS).
3. **Prompt Construction**: Retrieved content is injected into a prompt template.
4. **Generation**: OpenAI GPT generates a triage recommendation and rationale.
5. **Evaluation**: RAGAS evaluates outputs on metrics such as: Answer Relevancy, Faithfulness, Context Precision, Custom metric: Patient Triaged (binary)

### 📊 Sample Output
{
  "triage_decision": "Red (Critical)",
  "rationale": "Patient is elderly, experiencing chest pain and shortness of breath — possible cardiac event. Requires immediate intervention."
}

### ✅ Key Learnings
- Prompt engineering and document chunking are critical to RAG performance.
- Evaluation without ground-truth labels is possible using LLM-based metrics.
- Model interpretability is vital in clinical settings — black-box models are not ideal.
