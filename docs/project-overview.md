# Syntrix Project Overview

## Case Study

### Problem

Teams often need realistic structured data to test AI workflows, dashboards, backend systems, QA environments, demos, and evaluation pipelines.

However, real customer, patient, or business data is often difficult to use because of privacy restrictions, compliance requirements, access limitations, data sensitivity, and inconsistent data quality.

### Solution

Syntrix is a privacy-aware AI infrastructure layer for validated synthetic data generation.

It converts feature names or natural-language dataset descriptions into realistic, downloadable tabular datasets using LLM-based reasoning for semantic understanding and a deterministic backend engine for correctness, validation, and control.

### System Approach

Syntrix follows a hybrid architecture:

- The LLM reasoning layer understands user intent, feature meaning, domain context, and schema structure.
- The shared compiler normalizes schema definitions and applies semantic defaults.
- Domain registries provide realistic categories, numeric ranges, identifier patterns, aliases, and business rules.
- The deterministic generation engine creates rows, enforces constraints, applies relations, and performs postprocessing.
- The quality report evaluates generated datasets before they are presented to the user.

This separation allows Syntrix to use LLM flexibility without relying on the LLM as the final source of correctness.

### Key Design Principle

LLMs are useful for semantic reasoning, but they should not be trusted blindly for structured data generation.

Syntrix separates reasoning from correctness:

> LLMs understand intent.  
> Deterministic systems enforce structure, logic, and reliability.

---

## Architecture

### Overview

Syntrix follows a hybrid architecture that combines LLM-based semantic reasoning with deterministic validation, domain registries, rule-based generation, quality reporting, and export workflows.

The LLM is used for understanding user intent, domain context, and schema meaning. The deterministic backend is responsible for correctness, constraints, relations, validation, quality scoring, and reproducible dataset generation.

### Pipeline

```text
User Input
   |
   |-- Mode A: Feature Names
   |-- Mode B: Natural-Language Description
   |-- Manual Mode: User-Defined Schema
   |
   v
Input Parser
   |
   v
LLM Reasoning Layer
   |
   |-- Semantic understanding
   |-- Domain inference
   |-- Feature interpretation
   |-- Schema suggestion
   |
   v
Shared Compiler Pipeline
   |
   |-- Field compilation
   |-- Semantic tagging
   |-- Schema normalization
   |-- Default application
   |
   v
Domain Registry Layer
   |
   |-- Categories
   |-- Numeric defaults
   |-- Aliases
   |-- Identifier patterns
   |-- Business rules
   |
   v
Deterministic Generation Engine
   |
   |-- Row generation
   |-- Distribution handling
   |-- Constraint enforcement
   |-- Relation enforcement
   |-- Postprocessing
   |
   v
Quality Evaluation Layer
   |
   |-- Schema score
   |-- Row validity score
   |-- Relation score
   |-- Domain score
   |-- Distribution score
   |-- Warnings and violations
   |
   v
Public API Response
   |
   |-- Dataset
   |-- Features
   |-- Relations
   |-- Correlations
   |-- Sample rows
   |-- Quality report
   |-- Validation messages
   |-- Export links
   |
   v
UI Preview / Download
```

---

## Core Components

- LLM reasoning layer
- Shared compiler pipeline
- Schema inference and normalization
- Domain registry system
- Deterministic generation engine
- Relation enforcement and postprocessing
- Quality report and validation scoring
- Backend API layer
- Async job system
- Export and download workflows
- UI preview flow

---

## Supported Workflows

### Mode A — Feature Names to Validated Dataset

Mode A is used when the user already knows the columns they want.

The system preserves the user-provided feature list, infers schema meaning, applies semantic defaults, generates rows, enforces relations, validates quality, and prepares exports.

### Mode B — Description to Validated Dataset

Mode B is used when the user describes the dataset in natural language.

The system detects the domain, builds a domain-aware schema, applies registry defaults, generates rows, validates the dataset, and prepares downloadable outputs.

### Manual Mode — Advanced Schema Builder

Manual Mode is used when the user wants full control.

The user manually defines fields, data types, distributions, ranges, categories, constraints, correlations, relations, row count, seed, and export format.

---

## Supported Domains

Syntrix currently supports production-demo quality workflows across:

- Telecom churn
- Banking fraud
- Healthcare readmission
- Education performance
- Technology / SaaS analytics

Each domain includes structured defaults for realistic fields, categories, numeric ranges, identifier patterns, relations, and validation rules.

---

## Quality Report

Syntrix includes a quality reporting layer that evaluates generated datasets before they are presented to the user.

The report can include:

- Passed / failed status
- Quality score
- Schema score
- Row validity score
- Relation score
- Domain score
- Distribution score
- Violations
- Warnings

This makes the system more trustworthy because it does not only generate data; it also validates whether the generated data is logically consistent.

---

## Example Workflows

### Example 1 — Mode A: Feature Names to Validated Dataset

```json
{
  "input": {
    "features": [
      "account_id",
      "company_size",
      "subscription_plan",
      "monthly_recurring_revenue",
      "active_users",
      "customer_health_score",
      "health_segment",
      "churn_risk_score",
      "churn_status"
    ]
  },
  "workflow": "Mode A",
  "expected_output_summary": {
    "goal": "Generate a validated SaaS analytics dataset while preserving the exact user-provided columns.",
    "expected_capabilities": [
      "infer semantic meaning from feature names",
      "detect the SaaS analytics domain",
      "apply domain-aware defaults",
      "generate realistic rows",
      "enforce relations between fields",
      "produce quality report",
      "prepare downloadable export"
    ]
  }
}
```

### Example 2 — Mode B: Description to Validated Dataset

```json
{
  "input": {
    "description": "Generate a banking fraud detection dataset with account type, customer age, transaction type, transaction amount, merchant category, channel, risk score, fraud flag, and transaction status."
  },
  "workflow": "Mode B",
  "expected_output_summary": {
    "goal": "Convert a natural-language business request into a validated banking fraud dataset.",
    "expected_capabilities": [
      "detect the banking fraud domain",
      "build a domain-aware schema",
      "apply registry defaults",
      "generate realistic transaction rows",
      "enforce fraud-risk relationships",
      "validate dataset quality",
      "prepare downloadable export"
    ]
  }
}
```

### Example 3 — Manual Mode: Advanced Schema Builder

```json
{
  "input": {
    "rows": 50000,
    "seed": 42,
    "export_format": "csv",
    "features": [
      {
        "name": "employee_id",
        "data_type": "string",
        "distribution": "functional",
        "constraints": {
          "unique": true,
          "nullable": false
        }
      },
      {
        "name": "age",
        "data_type": "integer",
        "distribution": "uniform",
        "min": 18,
        "max": 65
      },
      {
        "name": "department",
        "data_type": "category",
        "categories": [
          "Engineering",
          "Sales",
          "Finance",
          "Human Resources"
        ]
      },
      {
        "name": "salary",
        "data_type": "float",
        "distribution": "uniform",
        "min": 800,
        "max": 7000
      }
    ],
    "correlations": [
      {
        "fields": [
          "age",
          "salary"
        ],
        "correlation": 0.45
      }
    ],
    "relations": [
      {
        "type": "lookup_dependency",
        "source_field": "department",
        "target_field": "job_title"
      }
    ]
  },
  "workflow": "Manual Mode",
  "expected_output_summary": {
    "goal": "Generate a controlled dataset from a manually configured schema.",
    "expected_capabilities": [
      "allow exact field-level control",
      "apply user-defined distributions",
      "enforce constraints",
      "apply correlations and relations",
      "use seed for reproducibility",
      "export the dataset"
    ]
  }
}
```

---

## Production-Oriented Backend Features

Syntrix includes several backend features designed to make the system more production-like:

- Shared compiler pipeline for Mode A and Mode B
- Domain registry system
- Deterministic relation enforcement
- Quality report and validation scoring
- Regression tests across supported domains
- Async job system for long-running generation requests
- Request limits and input validation
- Job cleanup and TTL handling
- Structured observability logs
- Cleaner public response shape
- Model lifecycle and GPU management endpoints

---

## Engineering Challenges

- Preventing invalid LLM-generated schemas
- Preserving user-provided columns in Mode A
- Converting natural-language requests into domain-aware schemas in Mode B
- Enforcing field-level constraints
- Maintaining consistency across related fields
- Applying deterministic business rules after generation
- Supporting domain-aware realistic data generation
- Generating quality reports with violations and warnings
- Avoiding frontend timeouts for long-running generations
- Designing privacy-aware synthetic data workflows
- Producing clean public API responses for the UI

---

## Current Status

Syntrix has completed its core implementation for the first product version.

The core system is implemented and functional, including:

- Mode A: feature names to validated dataset
- Mode B: natural-language description to validated dataset
- Manual Mode: advanced schema builder
- Shared compiler pipeline
- Domain registries
- Deterministic relation enforcement
- Quality report
- Async jobs
- Export workflows
- UI preview and download flow

The current focus is on external readiness and product presentation, including:

- UI/UX refinement
- Documentation polish
- Demo video
- Case study materials
- Example workflows
- Public portfolio positioning

---

## Roadmap

### Phase 1 — Public Presentation

- Polish README and project documentation
- Add clear example workflows
- Add screenshots
- Prepare demo video
- Prepare case study materials

### Phase 2 — UI/UX Refinement

- Improve workflow layout
- Improve quality report visibility
- Improve failed-job messages
- Improve preview and export experience

### Phase 3 — Deployment Readiness

- Finalize deployment configuration
- Clean environment variables
- Improve artifact storage cleanup
- Harden async job execution
- Improve monitoring and observability

### Phase 4 — Domain Expansion

- Expand domain registry coverage
- Add more domain-specific templates
- Add more relation and validation rules
- Improve domain realism checks

---

## Repository Notes

This repository currently focuses on project documentation, architecture, examples, and positioning.

The purpose is to present Syntrix as a production-oriented AI engineering project and proof-of-work.

Source code and demo materials may be added selectively as the project is prepared for public presentation.

### Do Not Include

- Model weights
- API keys
- `.env` files
- Local machine paths
- Private company code
- Large experimental files
- Confidential client or employer-related materials

---

## Outcome

Syntrix demonstrates an engineering-first approach to building reliable LLM systems.

The strongest part of the project is the combination of:

- LLM reasoning
- Deterministic compiler
- Domain registries
- Relation enforcement
- Quality reporting
- Export-ready dataset generation

This makes Syntrix more than a random synthetic data generator. It is a privacy-aware, domain-aware AI system for generating validated structured datasets.
