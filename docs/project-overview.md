# Syntrix Project Overview

## Case Study

### Problem

Teams often need realistic structured data to test AI workflows, dashboards, backend systems, and evaluation pipelines.

However, real customer, patient, or business data can be difficult to use because of privacy, compliance, access restrictions, and data quality issues.

### Solution

Syntrix is a privacy-aware AI infrastructure layer for structured data workflows.

It combines LLM-based reasoning with deterministic validation layers to generate schema-aware, constraint-compliant structured synthetic data.

### System Approach

Syntrix uses LLMs for semantic reasoning and schema understanding, while deterministic backend logic handles validation, normalization, constraint enforcement, and output consistency.

### Key Design Principle

LLMs are useful for reasoning, but they should not be trusted blindly for structured outputs.

Syntrix separates reasoning from validation to improve reliability.

### Core Components

- LLM reasoning layer
- Schema inference layer
- Deterministic validation layer
- Rule-based constraint engine
- Structured JSON output layer
- Backend API layer

### Engineering Challenges

- Preventing invalid LLM-generated schemas
- Enforcing field-level constraints
- Maintaining consistency across related fields
- Supporting domain-aware generation
- Producing reliable structured outputs
- Designing privacy-aware synthetic data workflows

### Current Status

Syntrix is a working MVP under active development.

The core pipeline is implemented, with ongoing improvements in UI/UX, evaluation, observability, and domain coverage.

---

## Architecture

### Overview

Syntrix follows a hybrid architecture that combines LLM-based semantic reasoning with deterministic validation and rule-based control.

### Pipeline

```text
User Input
   |
   v
Input Parser
   |
   v
LLM Reasoning Layer
   |
   v
Schema Normalization
   |
   v
Validation Layer
   |
   v
Rule Engine
   |
   v
Structured Data Plan
   |
   v
Synthetic Data Generation
   |
   v
Validated Output
```

### LLM Reasoning Layer

Responsible for:

- Understanding feature semantics
- Inferring domain context
- Suggesting schema structure
- Identifying possible relationships between fields

### Deterministic Validation Layer

Responsible for:

- Type validation
- Constraint enforcement
- Output normalization
- Rule-based corrections
- Consistency checks

### Why Hybrid?

The LLM provides flexibility and semantic understanding.

The deterministic layer provides reliability, control, and predictable behavior.

This design reduces hallucinations and improves the quality of structured outputs.

---

## Example Workflows

### Example 1 — Feature-to-Schema

```json
{
  "input": "first_name, last_name, country, city, age, marital_status, salary",
  "workflow": "Feature-to-Schema",
  "expected_output_summary": {
    "fields": [
      "first_name",
      "last_name",
      "country",
      "city",
      "age",
      "marital_status",
      "salary"
    ],
    "expected_capabilities": [
      "infer data types",
      "suggest realistic distributions",
      "generate categorical values",
      "apply validation rules",
      "detect relationships between fields"
    ]
  }
}
```

### Example 2 — Description-to-Schema

```json
{
  "input": "Create a customer churn dataset for a telecom company with customer demographics, subscription plans, support tickets, monthly billing, and churn status.",
  "workflow": "Description-to-Schema",
  "expected_output_summary": {
    "domain": "telecom",
    "expected_fields": [
      "customer_id",
      "age",
      "city",
      "subscription_plan",
      "network_type",
      "monthly_bill",
      "support_tickets_count",
      "churn_status"
    ],
    "expected_capabilities": [
      "domain-aware schema generation",
      "realistic field selection",
      "constraint generation",
      "relationship detection",
      "generation-ready configuration"
    ]
  }
}
```

---

## Roadmap

### Phase 1 — Core MVP Stabilization

- Stabilize schema generation workflows
- Improve deterministic validation rules
- Strengthen structured JSON outputs
- Improve backend API reliability
- Add more example workflows

### Phase 2 — Evaluation Layer

- Add schema quality checks
- Add rule violation reporting
- Add output consistency metrics
- Add domain realism checks

### Phase 3 — Domain Registries

- Expand healthcare registry
- Expand telecom registry
- Add banking and finance registry
- Add education and HR workflow templates

### Phase 4 — UI/UX Improvements

- Improve workflow layout
- Add clearer result explanation
- Add validation visibility
- Add export options

### Phase 5 — Demo and Documentation

- Add demo video
- Add screenshots
- Add case study
- Add API usage examples

---

## Repository Notes

This repository currently focuses on project documentation, architecture, examples, and positioning.

The purpose is to present Syntrix as a production-oriented AI engineering project and proof-of-work.

Source code and demo materials may be added selectively as the project is stabilized.

### Do Not Include

- Model weights
- API keys
- `.env` files
- Local machine paths
- Private company code
- Large experimental files
- Confidential client or employer-related materials
