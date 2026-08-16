# CH4rnel Local AI Lab

A local AI platform for Linux, development, research,
and experiments with LLMs, RAG, and fine-tuning.

## Goals

* local inference;
* private work with LLMs;
* multiple independent models;
* a custom knowledge base;
* RAG;
* experiments with LoRA/QLoRA;
* integration with VS Code;
* connection to local and external tools;
* reproducible configuration.

## Main Components

* Ollama
* Open WebUI
* DeepSeek
* Qwen
* VS Code
* RAG
* LoRA / QLoRA

## Architecture

```text
User
 |
 +-- Open WebUI
 |
 +-- VS Code
 |
 v
Ollama
 |
 +-- DeepSeek
 +-- Qwen
 +-- Other models
 |
 v
Knowledge / RAG
 |
 +-- Linux
 +-- Programming
 +-- AI
 +-- Personal knowledge
```
