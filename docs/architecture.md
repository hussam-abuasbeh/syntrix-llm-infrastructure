# Syntrix Architecture

## Overview

Syntrix follows a hybrid architecture that combines LLM-based semantic reasoning with deterministic validation and rule-based control.

## Pipeline

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
