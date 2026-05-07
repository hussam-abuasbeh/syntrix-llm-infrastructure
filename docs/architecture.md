# Syntrix Architecture

## Overview

Syntrix follows a hybrid architecture that combines LLM-based semantic reasoning with deterministic validation, domain registries, rule-based generation, quality reporting, and export workflows.

The LLM is used for understanding user intent, domain context, and schema meaning. The deterministic backend is responsible for correctness, constraints, relations, validation, quality scoring, and reproducible dataset generation.

## Pipeline

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
