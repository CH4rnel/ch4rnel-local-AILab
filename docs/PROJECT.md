# CH4rnel Local AI Lab — Project Specification

## 1. Purpose

CH4rnel Local AI Lab is a local AI experimentation and development
platform running primarily on Arch Linux.

The project provides a common infrastructure for:

- local LLM inference;
- model experimentation;
- RAG;
- knowledge management;
- LoRA/QLoRA training;
- AI-assisted development;
- local and external tool integration;
- reproducible experiments.

## 2. Design Principles

### Model independence

Models are independent components.

DeepSeek, Qwen and other model families must not contain runtime,
knowledge or training infrastructure inside their directories.

### Runtime independence

Ollama and Open WebUI are runtime components.

They provide services to models but are not part of a specific model.

### Knowledge independence

Knowledge sources are independent from models.

Multiple models may consume the same knowledge base.

### Training isolation

Training experiments must not modify original model files.

Training produces adapters or derived model artifacts.

### Reproducibility

Every training experiment should record:

- base model;
- model revision;
- dataset;
- dataset version;
- training parameters;
- software versions;
- hardware;
- resulting adapter;
- evaluation results.

## 3. Runtime Architecture

```text
                    User
                     |
             +-------+-------+
             |               |
         Open WebUI        VS Code
             |               |
             +-------+-------+
                     |
                   Ollama
                     |
        +------------+------------+
        |            |            |
     DeepSeek       Qwen        Other
        |            |            |
        +------------+------------+
                     |
               Knowledge / RAG
                     |
          +----------+----------+
          |          |          |
       Documents   APIs       Tools

       4. Training Architecture
Base Model
    |
    +---- Dataset
    |
    +---- Training Configuration
    |
    v
QLoRA / LoRA
    |
    v
Adapter
    |
    +---- Evaluation
    |
    v
Optional Merge
    |
    v
Quantization
    |
    v
Ollama

5. Hardware Target

Primary development machine:

OS: Arch Linux x86_64
CPU: Intel Xeon E5-2699 v4
CPU threads: 44
RAM: 32 GB
GPU: NVIDIA GeForce RTX 2060
VRAM: 6 GB

Training configurations must take the 6 GB VRAM limit into account.

6. Storage Policy

Git stores:

source code;
configuration;
documentation;
prompts;
scripts;
small curated datasets.

Git does not store:

model weights;
checkpoints;
generated embeddings;
vector databases;
runtime caches;
secrets;
large raw datasets.

7. Development Phases

Phase 1 — Infrastructure:

Git repository
directory structure
documentation
Ollama
Open WebUI
VS Code integration

Phase 2 — Models:

DeepSeek
Qwen3
additional local models

Phase 3 — Knowledge:

Arch Linux documentation
Linux man pages
programming documentation
curated personal notes

Phase 4 — RAG:

document ingestion
embeddings
vector storage
retrieval
evaluation

Phase 5 — Training:

dataset preparation
QLoRA
LoRA
evaluation
adapter management

Phase 6 — Agents and Tools:

API integrations
MCP
local tools
controlled automation

8. Non-Goals

The project does not attempt to:

store all model weights in Git;
modify upstream models directly;
couple a knowledge base to one model;
expose local services publicly by default.