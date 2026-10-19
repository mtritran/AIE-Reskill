# AI Engineer - Agentic Systems (SE Reskilling)
## Course Syllabus & Training Overview

---

### 1. General Course Information

| Field | Details |
| :--- | :--- |
| **Topic Name** | AI Engineer - Agentic Systems (SE Reskilling) |
| **Topic Code** | *TBD* |
| **Version** | 1.0 |
| **Target Job Profile** | Developer |
| **Target Job Rank** | DEV03, DEV04 |
| **Total Duration** | 8 Weeks / 40 Days (320 Hours total: 160h instructor-led/mentored + 160h self-learning/labs) |

#### Target Training Audience Description
- **Target Profile:** Backend, Full-stack, Platform, or Integration Engineers with **3–8+ years** of professional software development experience.
- **Prerequisites & Mindset:**
  - Basic Python knowledge or experience.
  - Solid API, database, and software engineering skills.
  - High willingness and readiness to learn LLM-centric and agentic system architecture.

---

### 2. Course Objectives

Equip learners with the competencies and practical experience to:
1. **Build typed FastAPI services** with validated I/O, asynchronous integrations, database CRUD operations, and comprehensive automated test suites.
2. **Analyze and justify architectural trade-offs** (synchronous vs. event-driven, DI/IoC patterns, streaming vs. batch processing) with explicit evaluation of risks and maintainability.
3. **Implement prompt engineering and structured outputs** utilizing standard roles and JSON schema validation to produce reliable, machine-consumable responses under context, cost, and latency constraints.
4. **Analyze agentic tasks and select reasoning paradigms** (CoT, ReAct, Plan–Execute–Replan, ToT, Reflection) and orchestration patterns (deterministic workflow vs. dynamic agent), backed by reliability controls and quantitative metrics.
5. **Design and optimize enterprise RAG pipelines** (chunking, embeddings, vector indexing, hybrid search, metadata filtering, and ACL) to guarantee grounded, citation-backed answers with strict refusal behaviors.
6. **Implement multi-tiered memory layers** incorporating short-term task/intent state and long-term semantic memory, governed by automated update, caching, and staleness policies.
7. **Evaluate LLM and Agent systems** using golden evaluation datasets, scoring rubrics, adversarial tool-use testing, and end-to-end trace/replay observability (e.g., Langfuse, Phoenix).
8. **Apply robust AI guardrails and governance controls**: prompt-injection defenses, scoped tool permissions, sensitive-data handling, audit logging, sandboxed execution, and human-in-the-loop approval gates.
9. **Containerize and operationalize LLM services** using Docker, secure secrets/configuration management, and optimize performance (TPS, TTFT, prompt caching, model routing).
10. **Integrate all architectural layers into an enterprise-ready assistant** featuring verifiable outputs, auditable logs, and measurable quality, safety, and performance.

---

### 3. Skill Competency Matrix

| Skill Area | Level of Outcome | Priority | Key Job Outputs & Competency Expectations |
| :--- | :---: | :---: | :--- |
| **Python Asynchronous Programming** | Level 3: Advanced | Secondary | • Advanced concurrency patterns and best practices in asynchronous programming.<br>• Independently coordinates multiple asynchronous operations.<br>• Proficient in debugging, profiling, and testing async Python applications. |
| **Python Application Debugging Techniques** | Level 3: Advanced | Secondary | • Advanced knowledge of Python debugging techniques, profiling, unit/integration testing, and code analysis tools.<br>• Resolves complex debugging and performance bottleneck tasks independently. |
| **Software Architecture** | Level 2: Intermediate | Secondary | • Solid working knowledge of software architecture fundamentals (components, interfaces, data flows, and design patterns).<br>• Independently designs modular small-scale services; seeks guidance on distributed concerns (scalability, fault tolerance, security).<br>• Applies architectural principles in Python-centric environments. |
| **FastAPI** | Level 3: Advanced | Secondary | • Delivers production-grade FastAPI backends with clean routing, dependency injection, and centralized error handling.<br>• Designs typed Pydantic schemas and SQLAlchemy ORM models with sound session and transaction management.<br>• Secures APIs via AuthN/AuthZ (JWT/OAuth2 with role- and permission-based access control).<br>• Ensures high test coverage with `pytest` and essential middleware (CORS, structured logging, Request-ID, error handlers). |
| **LLM Alignment** | Level 2: Intermediate | Primary | • Designs reliable prompts with explicit system/user/developer roles and JSON schema structured outputs.<br>• Manages context-window constraints, token budgeting, latency, and cost via prompt tuning and sampling parameters.<br>• Leverages transformer foundations and embedding models for semantic retrieval.<br>• Mitigates hallucinations through grounded retrieval and context engineering.<br>• Evaluates reasoning paradigms (CoT, ReAct, Plan–Execute, ToT, Reflection) and selects models according to performance benchmarks.<br>• Identifies trade-offs between Prompting, RAG, and Fine-tuning. |
| **Retrieval-Augmented Generation (RAG)** | Level 3: Advanced | Primary | • Constructs end-to-end RAG pipelines: document ingestion, intelligent chunking, embedding generation, and vector search.<br>• Integrates hybrid search (lexical + dense) and optimizes baseline naive RAG systems.<br>• Implements metadata filtering, access control lists (ACL), and citation-backed answer generation with refusal mechanisms.<br>• Architects advanced RAG strategies (multi-index RAG, Graph RAG) with graph databases (Neo4j, Apache AGE, Memgraph).<br>• Diagnoses retrieval and grounding failures based on empirical query metrics. |
| **Agentic Systems** | Level 3: Advanced | Primary | • Implements tool calling with schema validation, separation of read and write actions, safe execution (timeouts, retries, rate limits), and result summarization.<br>• Develops agentic workflows (router, planner–executor, ReAct loops, reflection) using modern orchestration frameworks (e.g., LangGraph, Agno, OpenAI Agents).<br>• Builds memory systems combining short-term intent tracking, conversation summarization, and vector-backed long-term memory with TTL/staleness policies.<br>• Establishes evaluation frameworks: golden datasets, tool-selection accuracy, task success rate, and trace/replay dashboards. |
| **Docker Containerization** | Level 2: Intermediate | Secondary | • Packages and orchestrates containerized LLM services (images, containers, ports, persistent volumes, internal networks).<br>• Manages environment variables and secret stores; troubleshoots build and networking issues.<br>• Containerizes local LLM inference engines (Ollama, vLLM) with reproducible models, caching, model routing, and TPS/TTFT monitoring. |
| **ML Model Governance** | Level 2: Intermediate | Primary | • Enforces LLM/Agent governance: prompt injection mitigations, fine-grained tool permissions, and human approval gates for high-impact actions.<br>• Implements data sanitation (PII masking) and tamper-proof audit trails for compliance.<br>• Secures execution with sandboxed runtime environments, policy engines, and formal threat modeling (including memory poisoning defenses). |

---

### 4. Learning Outcomes (LO)

> **Current vs. Future Needs Balance:** 70% of learning time focuses on current operational needs, and 30% focuses on emerging future needs.

| LO Code | Learning Outcome Description | Bloom's Taxonomy Level | Focus Balance |
| :---: | :--- | :---: | :---: |
| **LO1** | **Apply** advanced Python and FastAPI skills to build a typed FastAPI service with Pydantic validation, SQLAlchemy CRUD, at least one async external call (`asyncio`/`httpx`) with resilience patterns, and `pytest` unit/integration test coverage. | **B3 - Apply** | Current Needs |
| **LO2** | **Analyze** Python system designs and justify architectural trade-offs (event-driven vs. sync, DI/IoC impacts, stream vs. batch processing) with explicit risk and maintainability assessments. | **B4 - Analyze** | Current Needs |
| **LO3** | **Implement** reliable LLM interactions using roles and structured outputs (JSON schema), while managing context limits and optimizing latency/cost via parameter and prompt tuning. | **B3 - Apply** | Current Needs |
| **LO4** | **Analyze** an agent-style task and justify the choice of reasoning paradigm and model strategy, assessing how context engineering approaches affect failure modes such as hallucination, tool misuse, and context degradation. | **B4 - Analyze** | Current Needs |
| **LO5** | **Analyze and improve** a RAG system by diagnosing retrieval and grounding failures, and justify design choices across chunking strategies, embedding/index options, hybrid search, metadata filtering/ACL, and advanced architectures based on measured retrieval quality. | **B4 - Analyze** | Current Needs |
| **LO6** | **Analyze and improve** a grounded LLM system by diagnosing retrieval/grounding and tool-use failures, justifying design choices across RAG and agentic workflow designs using measured quality metrics, execution traces, and task patterns. | **B4 - Analyze** | Current Needs |
| **LO7** | **Implement** a conversational AI memory layer with short-term state (intent tracking, summarization), long-term semantic memory (vector store), and policies for memory updates and stale-memory detection (e.g., FAISS / pgvector + Redis + SQLite). | **B3 - Apply** | Current Needs |
| **LO8** | **Analyze and evaluate** LLM/agent systems using golden datasets and rubrics, adversarial tool-use tests, and trace–replay observability platforms (e.g., Langfuse / Phoenix) to diagnose and improve quality. | **B4 - Analyze** | Future Needs |
| **LO9** | **Execute and operate** an LLM service by containerizing with Docker, configuring secrets/config management, selecting deployment topologies, and implementing cost/latency optimizations with TPS and TTFT monitoring. | **B3 - Apply** | Future Needs |
| **LO10** | **Implement** security guardrails for an LLM/agent system: prompt-injection defenses, scoped tool permissions, sensitive-data handling, audit logging, human approval gates, memory-poisoning protection, and sandboxed tool/code execution. | **B3 - Apply** | Future Needs |
| **LO11** | **Analyze** requirements and risks to design, deliver, and evaluate a production-like enterprise assistant featuring grounded RAG (citations/refusals), permissioned tools with approval gates, multi-tier memory, AuthN/AuthZ, and end-to-end observability. | **B4 - Analyze** | Current Needs |

---

### 5. Curriculum Topic Outline

| Skill Area | Mapped Training Units | Primary Units Covered |
| :--- | :--- | :--- |
| **Python Application Development** | Unit 1, Unit 3 | • Unit 1: Python Programming Advance<br>• Unit 3: Back-end Development with FastAPI |
| **Software Architecture** | Unit 2 | • Unit 2: Software Architecture in Python |
| **FastAPI Backend** | Unit 3 | • Unit 3: Back-end Development with FastAPI |
| **LLM Alignment & Foundations** | Unit 4, Unit 5 | • Unit 4: LLM Fundamentals<br>• Unit 5: LLM Advanced |
| **Retrieval-Augmented Generation** | Unit 6 | • Unit 6: RAG Engineering |
| **Agentic Systems** | Unit 7, Unit 8, Unit 9, Unit 10, Unit 13 | • Unit 7: Tool Calling & API Integration<br>• Unit 8: Agentic Workflow Design<br>• Unit 9: Memory & Context Engineering<br>• Unit 10: Evaluation for LLM & Agent Systems<br>• Unit 13: Mock Project (Capstone) |
| **Docker Containerization** | Unit 11, Unit 13 | • Unit 11: LLMOps & Production Deployment<br>• Unit 13: Mock Project (Capstone) |
| **ML Model Governance & Security** | Unit 12, Unit 13 | • Unit 12: Security, Governance & Safety<br>• Unit 13: Mock Project (Capstone) |

---

### 6. Time Allocation Breakdown

| Category | Proportion (%) | Duration (Mins) | Approx. Hours | Description & Format |
| :--- | :---: | :---: | :---: | :--- |
| **Concept / Lecture** | 18% | 1,728 mins | ~29 hrs | Core theoretical foundations, architectural principles, live demos |
| **Self-Learning** | 23% | 2,208 mins | ~37 hrs | Guided self-study, reference tutorials, documentation deep dives |
| **Seminar / Workshop** | 4% | 384 mins | ~6 hrs | Interactive workshops, deep-dive discussions |
| **Class Meeting** | 0% | 0 mins | 0 hrs | Ad-hoc cohort syncs |
| **Assignment / Lab** | 37% | 3,552 mins | ~59 hrs | Hands-on code implementations, lab exercises, capstone development |
| **Guides / Review** | 13% | 1,248 mins | ~21 hrs | Code reviews, design defense, knowledge presentations, quiz reviews |
| **Test / Quiz** | 0% | 0 mins | 0 hrs | Continuous ungraded check-ins |
| **Exam & Evaluation** | 6% | 576 mins | ~10 hrs | Pre-test, final theory test, practice test, mock interview |
| **Total Course Time** | **100%** | **9,600 mins** | **160 hrs** *(Instructor-led core)* | *(Full course spans 320 hrs including independent lab increments)* |

---

### 7. Training Materials & Environments

| Resource Type | Specification / Status | Notes |
| :--- | :--- | :--- |
| **Textbooks** | *N/A* | Curated modular courseware provided via daily reading links |
| **Reference Materials** | Industry-standard documentation & tutorials | DataCamp, Real Python, LangChain Academy, Microsoft Agent Governance Toolkit |
| **Technical Stack** | Python 3.11+, uv, FastAPI, Pydantic, SQLAlchemy, pytest, Docker, Ollama / vLLM, LangGraph / Agno, FAISS / pgvector, Redis, SQLite, Langfuse / Phoenix | Local development workstation & virtual lab environments |

---

### 8. Assessment & Passing Criteria

| Assessment Component | Requirement & Criteria | Weight / Policy |
| :--- | :--- | :--- |
| **Lab Assignments** | 100% completion of all assigned daily and unit lab exercises | Mandatory prerequisite for graduation |
| **Final Test – Theory** | Comprehensive theoretical assessment covering LO1–LO10 | Score threshold: **> 80%** |
| **Final Test – Practice** | Hands-on technical practical exam (4-hour duration) | Score threshold: **> 80%** |
| **Overall Passing Criteria** | • Total Topic GPA **≥ 6.0 / 10.0**<br>• Attendance **≥ 80%** of total training time | Required for official certification |

---

### 9. Training Delivery Principles & Operational Guidelines

#### A. Trainee Cohort Requirements
- **Entry Qualifications:** Passed entrance technical test and interview of the Fresher / Reskilling program.
- **Class Size:** Maximum **25 trainees** per cohort to ensure high-touch mentoring.

#### B. Trainer & Mentor Requirements
- Trainers and mentors possess verified senior expertise in Python, Software Architecture, and LLM/Agentic Systems, evaluated and certified by FA.

#### C. Training & Mentorship Operations
- **Daily Mentorship:** Dedicated mentor support for Q&A, debugging, and exercise guidance: **1.5 – 2.0 hours/day**.
- **Accountability:** Trainees must complete daily assignments and present deliverables or answer short defense questions on the following day.
- **Final Examination:** 1 comprehensive final exam lasting **4 hours** (1 hour theory + 3 hours practice).

#### D. Re-Test & Scoring Policy
- **Attempts:** Trainees are permitted a maximum of **1 re-test attempt** with identical examination structure.
- **Grading Scheme for Re-Test:**
  - If re-test score $ge 6.0$: final recorded score is capped at **6.0**.
  - If re-test score $< 6.0$: final recorded score is the **actual score achieved**.

#### E. Course Waiver & Exemption Criteria
- Trainees may waive the topic if they pass the comprehensive quick evaluation test and achieve an audit rating of **Rank B** or higher from the Trainer Audit.

#### F. Homework & Submission Policy
- Trainers retain discretion to permit trainees to complete unfinished homework and submit by the beginning of the next training day.
