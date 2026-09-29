# Codebase Cartography

<div align="center">

![Python](https://img.shields.io/badge/Python-3.10%2B-blue?style=for-the-badge&logo=python&logoColor=white)
![Neo4j](https://img.shields.io/badge/Neo4j-Graph%20DB-008CC1?style=for-the-badge&logo=neo4j&logoColor=white)
![Ollama](https://img.shields.io/badge/Ollama-Local%20LLM-000000?style=for-the-badge&logo=ollama&logoColor=white)
![LangChain](https://img.shields.io/badge/LangChain-Orchestration-1C3C3C?style=for-the-badge&logo=langchain&logoColor=white)

</div>

---

## Overview

Codebase Cartography is an open-source, fully self-hosted pipeline that uses a locally-run LLM to automatically map a codebase's structure into a queryable knowledge graph.

---

## Problem

When codebases get big, nobody actually understands how everything connects anymore. New devs or even senior ones end up just going through files to figure out what calls what, and they miss hidden dependencies. This leads to stuff breaking in production when someone changes one function without realizing 5 other services depend on it.

---

## Idea

We're building a tool that uses a locally run LLM to read through a codebase and automatically map out how everything is connected: functions, classes, API endpoints, database tables as a graph instead of just plain text. So instead of searching for a function name and hoping you find every place it's used, you can literally ask "what happens if I delete this?" and get a real answer traced through the actual code structure.

---

## How AI Powers It

The AI serves two core functions in the pipeline. First, it performs structured extraction: reading raw code files and outputting structured JSON that identifies entities (functions, classes, services) and their relationships (calls, imports, dependencies), which is then stored in a Neo4j graph database. Second, it handles query translation: converting natural-language developer questions into executable graph database queries (text-to-Cypher), running them, and returning traced results. Both functions are integral to the system — without the AI extraction step, no graph is built, and without the query translation step, the tool cannot be queried in natural language.

---

## Built With

- **Python** — Core pipeline and data processing.
- **Llama 3 / DeepSeek-Coder V2** — Local LLM for node/edge extraction and query translation.
- **Ollama / vLLM** — Local inference engine serving the LLM.
- **Neo4j (Community Edition)** — Graph database storing extracted entities and relationships.
- **LangChain / LlamaIndex** — Orchestration of prompts, context handling, and GraphCypherQA chains.

---
