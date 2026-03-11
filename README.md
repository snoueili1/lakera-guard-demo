# Lakera Guard + OpenAI Security Demo (Colab)

## Overview

This demo showcases how an AI security layer can protect a Large Language Model (LLM) from adversarial prompts and malicious user inputs.

The notebook integrates:

- OpenAI for LLM inference
- Lakera Guard v2 for prompt security analysis
- An interactive attack simulator
- A security pipeline visualization
- Real-time threat analytics and metrics

The goal is to demonstrate why **pre-LLM security filtering** is critical when deploying AI systems in production environments.

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/snoueili1/lakera-guard-demo/blob/main/notebooks/lakera_guard_demo.ipynb)

---

# How to Run the Demo

1. Open the notebook in Google Colab.

2. Run the setup cell to install dependencies.

3. Add your API keys inside the notebook:

OPENAI_API_KEY = "your_openai_key"  
LAKERA_API_KEY = "your_lakera_key"

4. Run all cells in order.

5. Use the interface to:

- Toggle Lakera Guard ON/OFF
- Simulate attacks
- Send custom prompts
- View threat detection results
- Inspect security metrics and charts

---

# High-Level Flow

The demo simulates a secure AI pipeline where user prompts pass through a security layer before reaching the LLM.

User Prompt  
↓  
Lakera Guard (Prompt Security Analysis)  
↓  
Threat Decision  
↓  
Blocked OR Sent to LLM  
↓  
OpenAI Model Response  

If Lakera detects a threat such as prompt injection, data exfiltration, or harmful content, the request is **blocked before the model processes it**.

If no threat is detected, the prompt is passed to the LLM for inference.

---

# Security Layers Demonstrated

The demo highlights two layers of AI safety:

### 1. Pre-LLM Security (Lakera Guard)

Lakera analyzes every prompt and detects:

- Prompt injection attacks
- Data exfiltration attempts
- PII exposure
- Harmful or criminal content

This layer prevents malicious prompts from ever reaching the model.

### 2. Model Safety (LLM)

If Lakera is disabled, the prompt goes directly to the LLM, which relies on built-in safety policies to refuse unsafe requests.

This demonstrates why relying solely on the model can be insufficient.

---

# Attack Simulation

The notebook includes an attack simulator with several categories:

- Prompt Injection
- Data Exfiltration
- Harmful Content
- Crime
- PII Requests

Each category contains multiple example attacks to test the system.

Users can also manually write their own prompts to evaluate whether Lakera blocks them.

---

# Security Dashboard

The notebook tracks several metrics during the session:

- Total requests processed
- Allowed prompts
- Blocked threats
- Distribution of detected attack types

A simple visualization displays how many attacks were blocked and which categories were triggered.

---

# Ideas for a Production Demo

If this were extended into a full product demonstration, additional capabilities could include:

### Expanded Attack Library

Include more advanced attack scenarios such as:

- Jailbreak chains
- Indirect prompt injection via documents
- Multi-step data exfiltration attacks
- Prompt obfuscation techniques

### Multi-Agent or Tool Attacks

Demonstrate attacks targeting:

- Retrieval-Augmented Generation (RAG)
- external tool usage
- API integrations

### Real-Time Security Monitoring

Add a full monitoring dashboard including:

- attack timeline
- threat heatmaps
- latency analysis
- per-detector analytics

### Enterprise Use Cases

Demonstrate protection for:

- Healthcare assistants
- Financial advisory chatbots
- Customer support AI
- Internal enterprise copilots

### Model Comparison

Compare how different models respond when Lakera is disabled vs enabled.

---

# Goal of the Demo

The objective of this notebook is to illustrate a key principle in AI security:

**LLMs should not be the only line of defense.**

A dedicated security layer like Lakera Guard provides deterministic protection and visibility before prompts ever reach the model.
