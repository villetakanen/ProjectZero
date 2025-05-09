# Project Plan: Protocol Zero

## 1. Project Title

**Protocol Zero**

## 2. Vision & Goal

**Vision:** To create an accessible, locally-run Large Language Model (LLM) assistant that helps tabletop RPG players and Game Masters quickly find, understand, and summarize rules from various RPG systems.

**Goal:** To develop an open-source "recipe" (code, setup instructions, best practices) and a curated library of default prompts for interacting with RPG rulebooks (PDFs) using a local LLM like Gemma. This project aims to be community-driven, allowing contributions for new systems, improved prompts, and enhanced functionality.

## 3. Scope

### 3.1. In-Scope (Initial Focus - MVP)

* **Local LLM Setup:** Clear instructions for setting up a local LLM environment (e.g., using Ollama with Gemma).
* **Core RAG Pipeline:**
    * PDF ingestion (focus on text extraction).
    * Text chunking strategies suitable for RPG rulebooks.
    * Local embedding generation.
    * Vector store creation and management (e.g., FAISS).
    * Integration with the local LLM (Gemma) for question-answering and summarization.
* **Basic CLI:** A command-line interface to load PDFs, ask questions, and receive answers.
* **"Recipe" Documentation:** Detailed `README.md` and setup guides.
* **Initial Prompt Library:** A small set of well-tested, generic prompts for common rule queries (e.g., "How does X work?", "Summarize Y mechanic").
* **Git Repository:** Hosting the code, documentation, and prompt library.
* **Support for 1-2 popular RPG systems** as initial examples/test cases (e.g., D&D 5e SRD, a popular OSR system).

### 3.2. Out-of-Scope (Potential Future Enhancements)

* Advanced PDF parsing (complex tables, image-based rules, non-English PDFs initially).
* Sophisticated GUI (beyond a very simple one if time permits in later phases).
* Cloud deployment or SaaS offerings.
* Fine-tuning LLMs (focus on RAG with pre-trained models initially).
* Real-time collaboration features.
* Automated testing beyond basic unit tests for core components.

## 4. Target Audience

* Tabletop RPG Players
* Game Masters (GMs/DMs)
* Developers interested in local LLMs and RAG applications.
* RPG content creators.

## 5. Core Components & Technologies

* **LLM:** Gemma (via Ollama as the primary recommended method for ease of local setup).
* **Programming Language:** Python.
* **Key Python Libraries (Initial Suggestions):**
    * `langchain` / `langchain-community` (or LlamaIndex as an alternative if preferred by contributors)
    * `pymupdf` (for PDF text extraction)
    * `sentence-transformers` (for local embeddings)
    * `faiss-cpu` (for local vector store)
    * `ollama` (Python client for Ollama)
    * `typer` or `click` (for CLI)
* **Version Control:** Git (e.g., GitHub, GitLab).
* **Documentation:** Markdown.

## 6. Phased Development Plan

### Phase 1: Core Engine & Basic CLI (Lead: Initial Contributors)

* **Duration:** 4-6 Weeks
* **Goals:**
    * Establish the Git repository with basic structure.
    * Develop the core RAG pipeline (PDF loading, chunking, embedding, vector store, LLM query).
    * Implement a functional command-line interface (CLI) for:
        * Pointing to a PDF rulebook.
        * Building/loading the vector store for that rulebook.
        * Asking questions and getting answers.
    * Detailed `README.md` with setup instructions for Ollama, Gemma, and the Python environment.
    * Basic error handling.
    * Test with 1-2 SRD (System Reference Document) PDFs.
* **Deliverables:**
    * Functional Python scripts for the RAG pipeline and CLI.
    * Initial `README.md`.
    * Example usage in documentation.

### Phase 2: Community Onboarding & Prompts Library (Lead: Community Effort)

* **Duration:** Ongoing
* **Goals:**
    * Refine contribution guidelines (`CONTRIBUTING.md`).
    * Encourage community testing and feedback on the core engine.
    * Start building a library of "default prompts" for various RPG systems and common query types.
        * Create a structured way to store and categorize prompts (e.g., by game system, by rule type).
    * Expand support for more RPG systems based on community interest and PDF availability (focus on SRDs or freely available rulebooks first).
    * Bug fixing and performance improvements based on feedback.
* **Deliverables:**
    * `CONTRIBUTING.md`.
    * A growing `prompts/` directory in the Git repo.
    * Scripts or guides for testing new PDFs and prompts.
    * Issues list populated with bugs and feature requests.

### Phase 3: Enhanced UI & Advanced Features (Lead: Community Effort, potential sub-teams)

* **Duration:** Ongoing, post-Phase 2 stabilization
* **Goals:**
    * (Optional) Develop a simple web UI (e.g., using Streamlit or Gradio) for easier interaction.
    * Explore more advanced PDF parsing techniques if needed for problematic PDFs.
    * Investigate different chunking strategies for better context.
    * Allow users to easily switch between different rulebooks/vector stores.
    * Implement features like conversation history (for the current session).
* **Deliverables:**
    * (If pursued) Basic web UI.
    * Improved parsing/chunking modules.
    * Enhanced user experience features.

### Phase 4: Documentation, Polish & "Release" (Lead: Core Maintainers & Community)

* **Duration:** Milestone-based
* **Goals:**
    * Comprehensive documentation: user guides, developer guides, prompt engineering tips.
    * Code cleanup and refactoring.
    * "Version 1.0" tagging or similar, signifying a stable and useful tool.
    * Showcase examples and use cases.
* **Deliverables:**
    * Polished documentation website or wiki.
    * Stable codebase.
    * Announcements and outreach to RPG communities.

## 7. Repository Structure (Git - Example)

```
├── .github/              # GitHub specific files (e.g., issue templates, workflows)
├── docs/                 # Detailed documentation, guides
├── prompts/              # Library of default prompts
│   ├── generic/
│   │   └── general_queries.md
│   └── systems/
│       ├── dnd5e_srd/
│       │   └── combat_rules.md
│       └── [other_system]/
├── scripts/              # Helper scripts (e.g., for batch processing, testing)
├── src/                  # Core Python source code
│   ├── main.py           # CLI entry point
│   ├── core/             # Core RAG pipeline logic
│   │   ├── ingestion.py
│   │   ├── chunking.py
│   │   ├── embedding.py
│   │   └── qa.py
│   └── utils/            # Utility functions
├── tests/                # Unit tests, integration tests
├── .gitignore
├── CONTRIBUTING.md
├── LICENSE               # Choose an open-source license (e.g., MIT, Apache 2.0)
├── README.md
└── requirements.txt      # Python dependencies
```

## 8. Contribution Guidelines

* A `CONTRIBUTING.md` file will detail:
* How to set up the development environment.
* Coding standards (e.g., linting, formatting).
* How to submit issues and pull requests.
* Process for proposing new features or changes.
* Guidelines for adding new RPG system support and prompts.
* Code of Conduct.

## 9. Community & Communication

* **Primary Platform:** GitHub (Issues, Discussions, Pull Requests).
* **Secondary (Optional):** Discord server, Subreddit, or dedicated forum for discussions, Q&A, and community building.
* Regular updates (e.g., weekly or bi-weekly summaries) on project progress.

## 10. Roadmap & Future Ideas (Post-MVP)

* **Advanced Prompt Engineering:** Techniques for multi-turn conversations, context chaining.
* **Evaluation Framework:** Metrics to assess the quality of answers and summaries.
* **Support for other local LLMs:** Expanding beyond Gemma if there's community demand.
* **Integration with VTTs (Virtual Tabletops):** (Ambitious)
* **Character Sheet Interaction:** (Ambitious)
* **Multi-language support** for rulebooks and UI.
* **Plugin system** for community extensions.

---

This project plan provides a solid foundation. Remember to adapt it as the project evolves and the community grows!
