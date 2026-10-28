# ResearchFinderAI 🔎

### An AI-Powered Research Discovery, Paper Analysis & Academic Exploration Desktop Application

**Discover Research Papers. Understand Ideas. Analyze Evidence. Find Your Next Research Direction.**

ResearchFinderAI is an AI-assisted research workspace designed to help students, researchers, and academics discover relevant research papers, explore emerging research directions, read academic PDFs, ask questions about research, and conduct structured paper reviews—all through a unified desktop interface.

Instead of manually searching through numerous papers, switching between research websites, and repeatedly reading lengthy documents, ResearchFinderAI combines AI-assisted research planning, academic paper discovery, semantic ranking, PDF analysis, web-assisted question answering, and multilingual translation in one application.

The project is being packaged as a **Windows desktop application**, with support for local AI models and optional cloud-based AI services.

---

## ✨ Key Features

### 1. 🔍 AI-Assisted Research Discovery

Turn a research idea into a structured paper-discovery workflow.

- Enter a research topic, research question, or initial idea.
- Use an AI model to understand the idea and generate a concise research summary.
- Automatically develop up to 10 related academic search topics.
- Search for relevant academic literature across multiple topic areas.
- Collect and merge unique research papers.
- Rank papers using semantic similarity to the overall research summary.
- View the final list of the top 10 ranked papers.

**Example research topic:**

`AI-based fault detection in electrical power systems`

The application develops related search topics, searches for papers, combines the results, and ranks the papers according to their relevance to the research idea.

### 2. 📚 Academic Paper Search

ResearchFinderAI integrates academic discovery sources to help locate relevant research literature.

**OpenAlex integration**
- Search academic works using generated research topics.
- Retrieve available titles, abstracts, publication years, DOI links, citation counts, and paper links.
- Prefer open-access papers with PDF links.
- Search literature published from 2020 onward in the current configuration.

**arXiv fallback**
- Automatically fall back to arXiv when OpenAlex refuses a request because of access, API-budget, or rate-limit issues.
- Retrieve available paper titles, abstracts, publication years, and PDF links.

The final results are semantically ranked rather than displayed solely in the order returned by the search API.

*Coverage depends on the sources, available metadata, API limits, and whether accessible paper PDFs are available.*

### 3. 🧠 Semantic Paper Ranking

ResearchFinderAI uses local machine-learning models to evaluate how closely papers match the research idea.

The current implementation uses:

- Sentence Transformers with `all-MiniLM-L6-v2` for semantic title ranking.
- `BAAI/bge-base-en-v1.5` embeddings for document retrieval.
- Cosine similarity to compare research descriptions, titles, and abstracts.
- A multi-stage ranking workflow to narrow down candidate papers.

The result is a ranked shortlist designed to make it easier to identify papers relevant to the research direction.

### 4. 📊 Live Research Progress Tracking

ResearchFinderAI provides a visible progress workflow instead of leaving the user waiting without feedback.

Track the main stages:

1. **Understanding your idea** — generate a research summary and related topics.
2. **Searching papers** — see the status of individual topic searches.
3. **Merging results** — combine unique papers from different searches.
4. **Final ranking** — identify the highest-ranked papers.

The interface can display completed, running, and failed topic searches, the number of papers found, the number of unique papers collected, the final ranking count, elapsed time, and research logs.

This makes the research process more transparent and helps users understand where a search is spending time or encountering a problem.

### 5. 📄 Integrated PDF Reader

Open a discovered research paper in the application's Reader workspace.

- Retrieve the available PDF for a selected paper.
- Display the paper inside the application.
- Process the document for AI-assisted question answering.
- Extract text from the PDF.
- Split the extracted text into chunks.
- Generate embeddings for semantic retrieval.
- Track PDF download, extraction, embedding, and processing progress.
- View processing errors when a document cannot be prepared.

The application also supports uploading your own PDF document, with a current upload limit of **50 MB**.

This allows you to analyze papers you already have, even when you did not discover them through the built-in search.

### 6. 💬 AI Research Assistant

Ask questions about a processed research paper through an integrated conversational interface.

The AI research assistant can:

- Answer questions using relevant passages retrieved from the selected paper.
- Search the web for additional context when needed.
- Combine retrieved paper information with web-search results.
- Display tool activity, search queries, retrieved results, and source information.
- Stream agent activity and responses into the interface.
- Use previous conversation messages as context for follow-up questions.
- Stop an ongoing response when necessary.

The assistant uses retrieval-augmented generation (RAG) to search the processed paper and has access to web-search tools.

**Example questions**
- What is the main contribution of this paper?
- Explain the proposed methodology step by step.
- What dataset and evaluation metrics were used?
- What are the major limitations?
- How does the proposed approach compare with previous work?
- Explain this technical term in the context of the paper.

Answers depend on the available paper text, retrieved evidence, AI model, and external search results. They should be checked against the original publication.

### 7. 📝 Structured Research Paper Review

ResearchFinderAI includes a dedicated Review workspace for producing a detailed, evidence-grounded review of a selected paper.

The review prompt is designed to cover:

1. Executive summary
2. Research problem and motivation
3. Goals, objectives, and research questions
4. Novelty and contributions
5. Complete workflow or pipeline
6. Methods, algorithms, models, and system architecture
7. Datasets, materials, tools, and experimental setup
8. Key results, reported metrics, and baselines
9. Practical benefits and potential applications
10. Limitations, assumptions, and threats to validity
11. Comparison with existing work
12. Reproducibility details
13. Future research directions
14. Important facts and technical terms
15. A balanced critical verdict

The review instructions emphasize distinguishing reported findings from interpretation, avoiding invented metrics, and identifying information that the paper does not specify.

The goal is to make technical papers easier to understand while preserving the distinction between what the authors report and what an AI system infers.

*The review is AI-generated and should be verified against the original paper, particularly for numerical results, citations, and scientific claims.*

### 8. 🌐 Web-Assisted Research

ResearchFinderAI can search the web through its research assistant when additional context is useful.

Available search configurations:

- **DuckDuckGo** — default web-search option without a user-provided API key.
- **Tavily** — optional search provider configured with an API key.

The research assistant can invoke paper retrieval and web search as separate tools, allowing it to look for information in the selected document or seek additional online context.

Web-assisted answers depend on connectivity, search-provider availability, and the relevance of returned sources.

### 9. 🌍 Multilingual Translation

ResearchFinderAI includes a translation panel to help users work with technical and academic text in different languages.

The current language options include:

- Bangla
- Hindi
- Urdu
- Arabic
- Spanish
- French
- German
- Chinese
- Japanese
- Korean
- Russian
- Turkish

Select text marked as translatable in the interface to open the translation workflow. On the Reader page, the selected text can be sent to the translation panel; on other pages, the translation can appear in a popup.

The target language can be configured in Settings.

This feature is intended to help students understand unfamiliar academic terminology and read research material in a preferred language.

### 10. 🤖 Flexible AI Engine: Local or Cloud

ResearchFinderAI supports two AI execution options.

**Local AI with Ollama**
- Run a supported language model locally.
- Choose from supported model options such as `qwen3:1.7b`, `qwen3:4b`, `qwen3:8b`, `qwen3:14b`, `llama3.2:3b`, and `gpt-oss:20b`.
- Check whether Ollama is installed and running.
- Check whether the selected model has been downloaded.
- Download a missing model through the application.
- View model-download progress and errors.
- Inspect detected hardware information and the recommended model.

**Cloud AI with Groq**
- Optionally configure a Groq API key.
- Use the configured Groq model instead of the local Ollama model.
- Switch back to local AI by removing the Groq key from Settings.

The configured model and available computer resources influence response speed and the complexity of tasks the system can handle.

*Local inference still requires suitable hardware, memory, disk space, and a compatible Ollama installation. The application also needs internet access for online search, initial model downloads, and cloud services.*

### 11. ⚙️ Centralized Settings

Manage the application's AI and research configuration from one Settings panel.

Available settings include:

- Groq API key
- Ollama model selection
- Tavily API key
- OpenAlex API key
- Target translation language

The application also displays relevant model and provider status information.

An optional OpenAlex API key can increase the available API budget. If OpenAlex refuses a request, the current search implementation can fall back to arXiv.

Settings are saved in browser storage associated with the application's local origin. The updated desktop configuration reuses a saved localhost port so that supported settings remain available between launches.

### 12. 💾 Persistent Desktop Configuration

The Windows desktop packaging is designed to keep application data separate from the installation directory.

The current implementation uses Electron's persistent user-data location for application data and logs, and stores the Hugging Face model cache under that data location.

The persistence update also keeps a saved localhost port so that the same local application origin can be reused between launches.

This design is intended to preserve saved settings and supported cached data when the application is closed and reopened or reinstalled without deleting its user data.

**Important:** The Saved Papers list currently uses application-session state. Do not assume that saved-paper entries persist across restarts unless persistent library storage is implemented separately. A first launch after upgrading from an older build may also require saving settings again.

### 13. 📋 Activity Logs and Diagnostics

The application includes a Logs panel and visible status indicators to help diagnose problems.

- Check whether the backend is connected.
- See when AI models are loading or ready.
- Review model-loading messages and errors.
- Inspect research workflow events.
- Track PDF processing stages.
- Monitor local model download progress.
- View backend log messages when a request fails.

If the application cannot start its backend, the desktop shell is designed to show an error message pointing to the backend log location.

### 14. 🖥️ Windows Desktop Experience

ResearchFinderAI is packaged using Electron with a Python backend and React frontend.

The desktop shell is designed to:

- Open the application in a dedicated desktop window.
- Start the packaged backend automatically.
- Wait for the local backend to become available before opening the interface.
- Keep the frontend and backend communicating through a local API.
- Open external HTTP/HTTPS links in the system browser.
- Store supported application data outside the installation directory.

The project includes a Windows build workflow intended to produce a downloadable installer artifact through GitHub Actions.

The installer should be considered available only after the workflow completes successfully and publishes its artifact.

---

## 🧰 Technology Stack

| Component | Technology |
|---|---|
| Desktop application | Electron |
| Frontend | React, Vite, CSS |
| UI icons | Lucide |
| Backend API | Python, FastAPI |
| Data validation | Pydantic |
| AI workflow | LangGraph |
| Language models | Ollama / Groq |
| Academic discovery | OpenAlex, arXiv |
| Web search | DuckDuckGo / Tavily |
| Semantic ranking | Sentence Transformers |
| Text embeddings | Hugging Face embeddings |
| Vector retrieval | FAISS |
| PDF processing | PyMuPDF |
| Machine learning | PyTorch |
| Desktop packaging | Electron Builder and PyInstaller-based backend packaging |
| Build automation | GitHub Actions |

---

## 🔄 How ResearchFinderAI Works

```text
Research Idea
     │
     ▼
AI Research Planning
     │
     ├── Research Summary
     └── Related Search Topics
                  │
                  ▼
       Academic Paper Search
          OpenAlex / arXiv
                  │
                  ▼
          Merge Unique Papers
                  │
                  ▼
       Semantic Relevance Ranking
                  │
                  ▼
          Top Ranked Papers
                  │
                  ▼
             PDF Reader
                  │
          Text Extraction
                  │
             Chunking
                  │
             Embeddings
                  │
                  ▼
         AI Research Assistant
           ├── Paper Retrieval
           ├── Web Search
           ├── Question Answering
           ├── Structured Review
           └── Translation
```

---

## 🚀 Getting Started

### Option 1: Windows Desktop Application

1. Visit the [ResearchFinderAI-Persistence repository](https://github.com/mdmotalebmiraz7/ResearchFinderAI-Persistence).
2. Open the **Actions** tab.
3. Select the **Build Windows installer** workflow.
4. Open a successful workflow run.
5. Download the published installer artifact, if available.
6. Follow the installation instructions included with the build.

The build workflow must complete successfully before a working installer artifact can be downloaded.

### Option 2: Run from Source

For development, the project separates the frontend, backend, and desktop shell.

The repository contains:

- `frontend/` — React user interface
- `backend/` — Python API, research workflow, AI providers, and document processing
- `desktop/` — Electron desktop application
- `.github/workflows/` — automated build workflow

Consult the repository's build scripts and dependency files for the appropriate development setup.

### Configure AI Services

Open the application's Settings panel to configure the desired AI engine and search services.

- For local inference, install and run Ollama, then select and download a supported model.
- For cloud inference, configure a Groq API key.
- For enhanced web search, optionally configure a Tavily API key.
- For an increased OpenAlex API budget, optionally configure an OpenAlex API key.
- Choose the desired translation language.

Keep all API keys private. Never commit secrets to the public repository.

---

## 🛡️ Privacy and Responsible Use

ResearchFinderAI supports local AI inference, but not every operation is necessarily offline.

- Local Ollama inference can run on the user's computer.
- Groq requests use a cloud service.
- Academic discovery and web search require internet access.
- API keys are stored in browser storage associated with the application's local origin.
- Information sent to cloud AI or online search providers may be processed by those providers.
- Research papers may be subject to copyright and access restrictions.
- AI-generated summaries, translations, and reviews can contain mistakes.

Do not submit confidential research, unpublished intellectual property, private data, or sensitive documents to external services unless you have confirmed that the provider's policies are appropriate for your use case.

Always verify important claims, metrics, citations, and conclusions against the original publication.

---

## ⚠️ Current Limitations

ResearchFinderAI is an evolving project. The following limitations are important to understand:

- Research coverage depends on OpenAlex, arXiv, API budgets, and available paper metadata.
- The current discovery configuration prioritizes recent open-access papers and papers with PDF links.
- Local model performance depends on available hardware and memory.
- Initial startup can take time while machine-learning models are loaded or downloaded.
- PDF processing can fail for inaccessible, malformed, encrypted, or unsupported documents.
- AI-generated reviews and answers are not substitutes for reading and evaluating the original paper.
- The current backend stores active research and processed-paper state in memory, so some session data may be lost when the backend restarts.
- The Saved Papers list is not currently guaranteed to persist across application restarts.
- Windows installer availability depends on a successful build and artifact publication.

---

## 🚧 Project Status

ResearchFinderAI is under active development, with ongoing work on desktop packaging, persistence, research workflows, and AI-assisted paper analysis.

The long-term goal is to make academic exploration more accessible through a unified application that helps users move from a research idea to relevant literature, document understanding, and critical analysis.

### Project Links

- **Current desktop-app repository:** [ResearchFinderAI-Persistence](https://github.com/mdmotalebmiraz7/ResearchFinderAI-Persistence)
- **Previous project repository:** [ResearchFinderAI](https://github.com/mdmotalebmiraz7/ResearchFinderAI)
- **Project demo on LinkedIn:** [Watch the ResearchFinderAI demo](https://www.linkedin.com/feed/update/urn:li:ugcPost:7514804105626750976/)

---

## 🎯 Vision

ResearchFinderAI aims to bring academic discovery, semantic paper ranking, AI-assisted reading, research review, web-assisted exploration, and multilingual support into one accessible desktop workspace.

**ResearchFinderAI — From Research Ideas to Research Insights.**
