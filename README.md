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

## Ideas for a Production Demo

If this demo were extended into a more complete production or evaluation environment, several additional capabilities could be added.

### Expanded Attack Library
The current demo uses a small set of predefined prompts to simulate attacks. A production-ready version could include a larger library of adversarial inputs covering different attack patterns such as:

- multi-step prompt injection chains  
- indirect prompt injection through retrieved documents (RAG)  
- prompt obfuscation techniques designed to bypass filters  
- multi-step data exfiltration attempts  

This would better reflect the types of attacks commonly observed in real-world LLM deployments.

### Benchmark-Based Evaluation
A more rigorous evaluation could rely on standardized benchmarks such as the **PINT (Prompt Injection Test) benchmark**, which is designed to measure the robustness of systems against prompt injection attacks. Running Lakera Guard against such benchmarks would allow the demo to generate structured evaluation metrics across many attack scenarios.

### Dataset-Driven Testing
Instead of relying only on handcrafted prompts, the demo could integrate **larger public datasets available on platforms such as Hugging Face** that are commonly used for LLM safety evaluations. These datasets contain thousands of adversarial prompts, including jailbreak attempts, harmful instructions, and moderation-related inputs. Running batch evaluations against these datasets would enable repeatable and scalable security testing.

### Security Metrics and Evaluation
A production demo could also report additional evaluation metrics commonly used in LLM security testing, such as:

- **Detection Rate**: the percentage of malicious prompts correctly identified and blocked by Lakera Guard  
- **False Positive Rate**: the percentage of benign prompts incorrectly flagged as malicious  
- **Latency Impact**: the additional response time introduced by the security layer  

Tracking these metrics would help quantify the effectiveness and operational impact of the security system.

### Observability and Monitoring
For real-world deployments, observability is critical. The demo could integrate monitoring tools such as Splunk or Grafana to provide operational visibility into the AI system. Example dashboards could include:

- attack timelines  
- threat distribution heatmaps  
- detection rates over time  
- security alerts triggered by malicious prompts  

This would allow security teams to monitor LLM activity and detect adversarial behavior in real time.

### Enterprise Use Cases
Finally, the demo could be extended to showcase protection across several real-world AI applications such as:

- healthcare assistants  
- financial advisory chatbots  
- customer support AI agents  
- internal enterprise copilots  

These scenarios would illustrate how a dedicated security layer like Lakera Guard can help protect LLM-powered systems deployed in production environments.

### Model Comparison

Compare how different models respond when Lakera is disabled vs enabled.

---

# Goal of the Demo

The objective of this notebook is to illustrate a key principle in AI security:

**LLMs should not be the only line of defense.**

A dedicated security layer like Lakera Guard provides deterministic protection and visibility before prompts ever reach the model.
