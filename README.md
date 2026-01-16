# 🏥 Agentic RAG System with Safety Measures

A Retrieval-Augmented Generation (RAG) system with comprehensive safety mechanisms, featuring a Maker-Checker loop for medical research queries.
link to colab : (https://colab.research.google.com/drive/15046CHmXFWNwgNzeipwTWTpg9Hmh-PA2?authuser=1#scrollTo=GX4tFqC48ltg)
![Python](https://img.shields.io/badge/python-3.8+-blue.svg)
![Groq](https://img.shields.io/badge/Groq-API-green.svg)
![ChromaDB](https://img.shields.io/badge/ChromaDB-Vector%20DB-orange.svg)
![License](https://img.shields.io/badge/license-MIT-blue.svg)

## 🎯 Overview

This system demonstrates a complete agentic RAG pipeline that answers complex medical queries while ensuring safety, accuracy, and reliability. It uses multiple AI agents working in concert to validate inputs, retrieve relevant information, generate responses, and ensure quality through automated checking and refinement.

## 🏗️ System Architecture
User Query
↓
┌─────────────────────────┐
│ Input Validation │ ← Sanitize & Safety Check
└─────────────────────────┘
↓
┌─────────────────────────┐
│ Document Retrieval │ ← Vector Search (ChromaDB)
└─────────────────────────┘
↓
┌─────────────────────────┐
│ MAKER Agent │ ← Generate Response (Groq API)
└─────────────────────────┘
↓
┌─────────────────────────┐
│ CHECKER Agent │ ← Validate Safety & Quality
└─────────────────────────┘
↓
┌─────────────────────────┐
│ REFINER Agent │ ← Improve if Needed
└─────────────────────────┘
↓
Final Response


## ✨ Key Features

### 🛡️ **Safety Mechanisms**
- **Input Validation**: Detects and blocks malicious patterns (XSS, SQL injection, path traversal)
- **Harmful Content Filtering**: Prevents responses to dangerous queries
- **Crisis Detection**: Routes users to mental health resources when needed
- **Medical Disclaimers**: Automatically enforces professional medical advice disclaimers
- **Maker-Checker Loop**: Dual-agent validation with automatic refinement

### 🤖 **Agentic Components**
1. **Maker Agent**: Generates initial responses using Groq's LLM
2. **Checker Agent**: Performs 6-point safety validation
3. **Refiner Agent**: Improves responses based on checker feedback

### 📚 **RAG Implementation**
- Vector database with semantic search (ChromaDB)
- Sentence transformer embeddings (all-MiniLM-L6-v2)
- Relevance scoring and source attribution
- Multi-document synthesis

### ✅ **Quality Checks**
- ✓ Medical disclaimer presence
- ✓ No diagnosis language
- ✓ Source citations
- ✓ Appropriate response length
- ✓ No harmful content
- ✓ Reasonable confidence scoring

## 🚀 Quick Start

### Prerequisites

```bash
pip install groq chromadb sentence-transformers numpy
```
# Initialize the system
rag_system = AgenticRAGSystem()

# Process a query
result = rag_system.process_query("What are treatment options for diabetes?")

# Access the response
print(result['answer'])
print(f"Confidence: {result['confidence']}")
print(f"Sources: {result['sources']}")


What are treatment options for type 2 diabetes?
Based on current medical research: Type 2 diabetes management includes 
lifestyle modifications (diet and exercise), oral medications (metformin 
as first-line), GLP-1 receptor agonists, SGLT2 inhibitors, and insulin 
therapy when needed...

⚠️ IMPORTANT: This information is for educational purposes only. Please 
consult with a qualified healthcare provider for personalized medical advice.

Sources:
1. ADA Clinical Practice Guidelines 2024 (Reliability: 95%)


Knowledge Base
The system includes 8 medical documents covering:

Diabetes management
Hypertension treatment
COVID-19 information
Antibiotic usage
Cancer screening
Mental health
Nutrition guidelines
Vaccination recommendations
To add your own documents:
MEDICAL_KNOWLEDGE.append({
    "id": "custom_001",
    "content": "Your medical content here...",
    "topic": "topic_name",
    "source": "Source Name 2024",
    "reliability": 0.95
})
🎓 Use Cases
Medical Education: Help students learn about medical conditions
Patient Information: Provide general health information
Research Assistant: Quick access to medical guidelines
Health Literacy: Improve understanding of medical topics
Triage Support: Initial information gathering (not diagnosis)
⚠️ Limitations & Disclaimers
❌ Not a substitute for professional medical advice
❌ Cannot diagnose medical conditions
❌ Cannot prescribe medications
❌ Knowledge cutoff: Information current as of training data
✅ Always consult healthcare professionals for medical decisions 
ضضض
