# 🚀 AI-Powered Narrative & Anomaly Insights for Reporting

*Demonstrating how AI can streamline financial/ESG reporting by automatically generating executive-ready narratives and flagging anomalies from structured data.*

## 📖 Project Overview

**Goal:** Demonstrate how AI can streamline financial/ESG reporting by automatically generating executive-ready narratives and flagging anomalies from structured data.

 connected, compliant reporting by showing how LLMs + lightweight stats can save hours of analyst effort, reduce errors, and increase transparency.

---

## 📈 Go-To-Market (GTM) Narrative

### Target Users
- Compliance officers
- Financial controllers  
- ESG managers

### Value Proposition
- **Automate** first-draft narratives and anomaly explanations
- **Save** 5–10 hours per filing cycle
- **Reduce risk** of oversight with structured anomaly flagging

### Differentiation
- **Embedded** directly in Workiva workflows (no copy-paste to/from external tools)
- **Built-in** audit trail + governance controls (critical for enterprise)

### Launch Motion
1. Start with a "Smart Summary" beta in SEC reporting workflows
2. Collect adoption metrics (time saved, % of reports using AI draft)
3. Expand to ESG, Risk, and Audit modules

---

## 📝 Product Requirements Document (PRD) Snapshot

### Problem Statement
Analysts spend too much time drafting repetitive narratives and scanning for anomalies.

### Proposed Solution
AI-generated summaries and anomaly callouts from connected data sources, with human review.

### Success Metrics
- **30%** reduction in report prep time
- **90%** accuracy of metrics cited in AI output
- **≥70%** adoption in pilot teams

---

## 🔧 Key Technical Features

### Contracted Output, Not Prose
We return a **strict JSON contract** so downstream steps (review, export, filing) are reliable and automatable—no surprise formats or missing fields.

### Data-Grounded Narratives
The AI can't invent figures; every number is **pulled from the source dataset**, which cuts rework and prevents compliance risk.

### Provenance by Design
Each claim carries a **reference back to the exact metric/cell**, giving auditors and reviewers click-through traceability.

### Risk Coverage Guarantee
If the system flags an anomaly, the narrative **must address it**—no blind spots in the final draft.

### Fail-Closed Safety Net
If any check fails (schema, numbers, references, coverage), we **block export** and show a clear fix path—protecting trust and avoiding bad filings.

### Key Performance Indicators
- **0%** unreferenced numbers
- **≥90%** schema-valid generations  
- **100%** of flagged anomalies covered
- **↓** drafting time per report

---

## 👩‍💻 User Stories & Acceptance Criteria

### User Story 1: AI-Generated Narratives
**As a compliance manager, I want AI-generated narrative summaries of quarterly metrics so I can focus on review instead of drafting.**

**Acceptance Criteria:**
- ✅ Upload/ingest data file
- ✅ Receive draft narrative (3–5 sentences)
- ✅ Numbers must match source metrics

### User Story 2: Anomaly Detection & Explanation
**As a financial analyst, I want anomalies flagged and explained so I don't miss critical risks.**

**Acceptance Criteria:**
- ✅ Outlier detection (z-score ≥2 or IQR bounds)
- ✅ LLM explains business context in <80 words
- ✅ Each anomaly includes suggested follow-up

### User Story 3: Audit Trail & Compliance
**As an auditor, I want an audit trail of AI vs human edits so compliance is maintained.**

**Acceptance Criteria:**
- ✅ All AI outputs logged
- ✅ Provenance shows source rows/columns

---

## 🏗️ Architecture Diagram

```
            +-------------+
Upload CSV → |   pandas    | → stats (QoQ, z-score, IQR)
            +-------------+
                    |
            +-------------------+
            |   PII Scrubber    |
            +-------------------+
                    |
            +----------------------------+
            |   LLM (OpenAI GPT-4o-mini) |
            +----------------------------+
                    |
            +-------------------+
            |   Validator (pydantic)  |
            +-------------------+
                    |
            +-------------------+
            | Streamlit UI (view, edit, export DOCX) |
            +-------------------+
```

---

## 🛣️ Roadmap: From Orchestration to Agentic AI

### Phase 1: MVP (Today)
- Upload → AI narrative + anomaly callouts → export
- Human review loop in Streamlit

### Phase 2: Enterprise Orchestration
- Integrate with Snowflake/Sheets APIs
- n8n automations: nightly jobs → Slack notifications → auto-doc export
- API hooks for multi-team workflows

### Phase 3: Agentic AI Workflows
**AI agent autonomously:**
- Monitors incoming data streams
- Detects anomalies
- Drafts narratives
- Routes draft via approval chain (Slack/Jira)
- Submits final doc into Workiva filing pipeline

**Guardrails:** Human-in-the-loop approvals, full audit logs, provenance tags

### Phase 4: Full Platform Integration
- Extend to ESG, Risk, Audit modules
- Multi-agent collaboration (e.g., "Narrative Agent" + "Risk Agent" + "Compliance Agent")
- MCP-enabled tool layer for secure, permissioned access to data + exports

---

## ✅ Output Evaluation Criteria

To ensure AI-generated narratives and anomaly explanations are reliable, outputs are evaluated against the following dimensions:

### 1. Accuracy
- **Numerical integrity:** All numbers in the AI output must exactly match source data
- **Consistency:** No contradictory statements across different sections of the report

### 2. Relevance
- **On-topic:** Summaries must reference only provided metrics (no hallucinated KPIs)
- **Anomaly coverage:** All flagged anomalies (z-score ≥2, IQR outliers) must be addressed in the narrative

### 3. Clarity
- **Readability:** Plain business English, ≤12th grade reading level
- **Conciseness:** Summaries ≤5 sentences, anomaly explanations ≤80 words
- **Executive tone:** Neutral, fact-based, avoids speculation unless marked as "possible causes"

### 4. Auditability
- **Provenance:** Each figure or anomaly explanation cites the exact source column/row
- **Versioning:** All AI outputs logged with timestamp + prompt + response
- **Traceability:** Audit trail shows human edits vs AI draft

### 5. Robustness
- **Boundary handling:** Borderline z-scores (2.0–2.2) labeled "borderline" rather than "critical"
- **Missing data:** Graceful degradation (skip or annotate missing values rather than invent)
- **Bias check:** Ensure language is neutral (no loaded terms like "failure," "catastrophic")

### 6. Adoption Metrics
- **Human acceptance rate:** % of AI sentences kept vs edited
- **Analyst time saved:** Minutes saved per filing cycle
- **Coverage:** % of filings/reports using AI draft

---

## 📊 Metrics & Next Steps

### Pilot KPIs
- Time saved
- Adoption rate
- Accuracy of metrics

### Expansion KPIs
- Filing error reduction
- % anomalies explained
- Cross-module adoption

### Future Work
- MCP integration for secure tool access
- Local-model option (for data residency)
- Continuous evaluation dashboard

---


