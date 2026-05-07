# Syntrix Case Study

## Problem

Teams often need realistic structured data to test AI workflows, dashboards, backend systems, QA environments, and evaluation pipelines.

However, real customer, patient, or business data is often difficult to use because of privacy restrictions, compliance requirements, access limitations, data sensitivity, and inconsistent data quality.

## Solution

Syntrix is a privacy-aware AI infrastructure layer for validated synthetic data generation.

It converts feature names or natural-language dataset descriptions into realistic, downloadable tabular datasets using LLM-based reasoning for semantic understanding and a deterministic backend engine for correctness, validation, and control.

## System Approach

Syntrix follows a hybrid architecture:

- The LLM reasoning layer understands user intent, feature meaning, domain context, and schema structure.
- The shared compiler normalizes schema definitions and applies semantic defaults.
- Domain registries provide realistic categories, numeric ranges, identifier patterns, aliases, and business rules.
- The deterministic generation engine creates rows, enforces constraints, applies relations, and performs postprocessing.
- The quality report evaluates generated datasets before they are presented to the user.

This separation allows Syntrix to use LLM flexibility without relying on the LLM as the final source of correctness.

## Key Design Principle

LLMs are useful for semantic reasoning, but they should not be trusted blindly for structured data generation.

Syntrix separates reasoning from correctness:

> LLMs understand intent.  
> Deterministic systems enforce structure, logic, and reliability.

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

## Supported Domains

Syntrix currently supports production-demo quality workflows across:

- Telecom churn
- Banking fraud
- Healthcare readmission
- Education performance
- Technology / SaaS analytics

Each domain includes structured defaults for realistic fields, categories, numeric ranges, identifier patterns, relations, and validation rules.

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

## Production-Oriented Features

Syntrix includes several production-oriented backend features:

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
