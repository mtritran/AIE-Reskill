# AI Engineer - Agentic Systems (SE Reskilling)
## Detailed Course Training Schedule

> **Course Scope:** 8 Weeks • 40 Days • 13 Units • Total: 320 Hours (40 days × 8 hours/day)
> **Delivery Method:** Blended Learning (Self-Learning, Concept Lectures, Hands-on Labs, Architecture Reviews, Mock Project)

---

### Curriculum Roadmap Overview

| Week | Dates | Training Units | Covered Days | Primary Focus |
| :---: | :---: | :--- | :---: | :--- |
| **Week 1** | 16 Jul - 22 Jul | **Unit 1:** Python Programming Advance<br>**Unit 2:** Software Architecture in Python<br>**Unit 3:** Back-end Development with FastAPI | Days 1–5 | Advanced Python concurrency, async patterns, event-driven design, dependency injection, and typed FastAPI backends. |
| **Week 2** | 23 Jul - 29 Jul | **Unit 4:** LLM Fundamentals<br>**Unit 5:** LLM Advanced | Days 6–10 | Prompt engineering, structured outputs, context optimization, reasoning paradigms (CoT, ReAct, ToT), and model selection. |
| **Week 3** | 30 Jul - 05 Aug | **Unit 6:** RAG Engineering | Days 11–15 | Chunking, embeddings, hybrid search, metadata ACL, citation generation, Multi-Index RAG, and Graph RAG (Neo4j). |
| **Week 4** | 06 Aug - 12 Aug | **Unit 7:** Tool Calling & API Integration<br>**Unit 8:** Agentic Workflow Design | Days 16–20 | Schema design, tool sandboxing, human approval gates, router/planner-executor patterns, and LangGraph orchestration. |
| **Week 5** | 13 Aug - 19 Aug | **Unit 9:** Memory & Context Engineering | Days 21–25 | Working/episodic memory, intent tracking, long-term semantic memory (FAISS/pgvector + Redis + SQLite), and staleness policies. |
| **Week 6** | 20 Aug - 26 Aug | **Unit 10:** Evaluation for LLM & Agent Systems | Days 26–30 | Golden datasets, answer rubrics, adversarial tests, trace/replay systems (LangSmith, Langfuse, Phoenix), and observability. |
| **Week 7** | 27 Aug - 02 Sep | **Unit 11:** LLMOps & Production Deployment<br>**Unit 12:** Security, Governance & Safety | Days 31–35 | Dockerization, self-hosted LLMs (Ollama/vLLM), prompt caching, TPS/TTFT monitoring, prompt-injection defense, and threat modeling. |
| **Week 8** | 03 Sep - 09 Sep | **Unit 13:** Mock Project (Capstone) | Days 36–40 | Full-stack Enterprise Assistant integration (React UI + FastAPI + RAG + Permissioned Tools + Memory + Evals + Security) & Final Mock Interview. |

---

## Week 1: Python Advanced, Software Architecture & FastAPI (16 Jul - 22 Jul)

### Unit 1: Python Programming Advance

#### Day 1
- **Total Duration:** 8 Hours (480 mins)
- **Target Learning Outcomes:** `LO1`

| Session | Activity & Topic Content | LO | Delivery Type | Duration | Hours | Format |
| :---: | :--- | :---: | :---: | :---: | :---: | :---: |
| **S1** | • Python Package management: uv, venv<br>• Python Meta Programming: Closure, Higher-order Function, Decorator<br>• Pydantic models and schema validation<br>• Python Event Loop and Async patterns, async programing with asyncio/httpx | `LO1` | Self-learning | 120 mins | 2h | Online |
| **S2** | Python Async & Validation Review | `LO1` | Assignment/Lab | 180 mins | 3h | Offline |
| **S3** | Hands-on Labs | `LO1` | Assignment/Lab | 180 mins | 3h | Offline |

**Learning Materials & Resources:**
- [01 - Python Venv](https://www.geeksforgeeks.org/python/create-virtual-environment-using-venv-python/)
- [02 - Python uv](https://www.datacamp.com/tutorial/python-uv)
- [03 - Python & Decorator](https://app.datacamp.com/learn/courses/writing-functions-in-python)
- [04 - Python higher-order function](https://www.geeksforgeeks.org/python/higher-order-functions-in-python/)
- [05 - Python Event Loop & Async](https://www.datacamp.com/tutorial/python-async-programming)

**Expected Outputs & Deliverables:**
- **Output:**
  - Async execution flow diagram
  - Pydantic validation example
  - Decorator/Higher-order Function example
  - Key learning summary (1 page)

---

#### Day 2
- **Total Duration:** 8 Hours (480 mins)
- **Target Learning Outcomes:** `LO1`

| Session | Activity & Topic Content | LO | Delivery Type | Duration | Hours | Format |
| :---: | :--- | :---: | :---: | :---: | :---: | :---: |
| **S1** | • Document parsing in Python (Markdown, txt, PDF, HTML,...)<br>• Testing with Pytest<br>• Pandas, numpy | `LO1` | Self-learning | 120 mins | 2h | Online |
| **S2** | Data Processing & Test Design Review | `LO1` | Assignment/Lab | 180 mins | 3h | Offline |
| **S3** | Hands-on Labs | `LO1` | Assignment/Lab | 180 mins | 3h | Offline |

**Learning Materials & Resources:**
- [06 - Document parsing (PyPDF, PyPDF2)](https://realpython.com/pdf-python/)
- [07 - Testing with Pytest](https://campus.datacamp.com/courses/introduction-to-testing-in-python)
- [08 - Pandas, numpy](https://app.datacamp.com/learn/courses/writing-efficient-python-code)

**Expected Outputs & Deliverables:**
- **Output: Data Processing Note + Test Case Checklist**
  - Data parsing workflow
  - Sample pytest test suite
  - Pandas/Numpy usage mapping
  - Key learning summary (1 page)

---

### Unit 2: Software Architecture in Python

#### Day 3
- **Total Duration:** 8 Hours (480 mins)
- **Target Learning Outcomes:** `LO2`

| Session | Activity & Topic Content | LO | Delivery Type | Duration | Hours | Format |
| :---: | :--- | :---: | :---: | :---: | :---: | :---: |
| **S1** | • Event-driven architecture<br>• Dependency Injection (DI) & Inversion of Control (IoC)<br>• Stream & batch data processing | `LO2` | Self-learning | 180 mins | 3h | Online |
| **S2** | Architecture Trade-off Analysis | `LO2` | Assignment/Lab | 120 mins | 2h | Offline |
| **S3** | Hands-on Labs | `LO2` | Assignment/Lab | 180 mins | 3h | Offline |

**Learning Materials & Resources:**
- [01. Event-Driven Architecture Overview](https://www.geeksforgeeks.org/system-design/event-driven-architecture-system-design/)
- [02. Introduction to Apache Kafka](https://app.datacamp.com/learn/courses/introduction-to-apache-kafka)
- [03. Apache Kafka in Python](https://kafka-python.readthedocs.io/en/master/)
- [04. Dependency Injection (DI) and Inversion of Control (IoC) in Python](https://www.datacamp.com/tutorial/python-dependency-injection)

**Expected Outputs & Deliverables:**
- **Output: Architecture Decision Matrix + Design Note:**
  - Event-driven vs Sync comparison
  - DI/IoC analysis
  - Stream vs Batch comparison
  - Architecture recommendation

---

### Unit 3: Back-end Development with FastAPI

#### Day 4
- **Total Duration:** 8 Hours (480 mins)
- **Target Learning Outcomes:** `LO2`

| Session | Activity & Topic Content | LO | Delivery Type | Duration | Hours | Format |
| :---: | :--- | :---: | :---: | :---: | :---: | :---: |
| **S1** | • Foundation & Inputs<br>• Data Modeling (Pydantic)<br>• Database Setup with ORM (SQLAlchemy)<br>• CRUD & Dependency Injection (DI) | `LO2` | Self-learning | 180 mins | 3h | Online |
| **S2** | FastAPI Service Design Review | `LO2` | Assignment/Lab | 120 mins | 2h | Offline |
| **S3** | Hands-on Labs | `LO2` | Assignment/Lab | 180 mins | 3h | Offline |

**Learning Materials & Resources:**
- [01. Introduction to FastAPI](https://app.datacamp.com/learn/courses/introduction-to-fastapi)
- [02. Deploying AI into Production with FastAPI](https://app.datacamp.com/learn/courses/deploying-ai-into-production-with-fastapi)
- [03. Introduction to Databases in Python](https://app.datacamp.com/learn/courses/introduction-to-relational-databases-in-python)

**Expected Outputs & Deliverables:**
- **Service Architecture Diagram + API Design Package:**
  - Router-Service-Repository diagram
  - API contract draft
  - Pydantic model design
  - Dependency Injection explanation

**Logistics & Preparation Notes:**
- *Chuẩn bị tài liệu thực hành (Soạn tài liệu Hands-on)*

---

#### Day 5
- **Total Duration:** 8 Hours (480 mins)
- **Target Learning Outcomes:** `LO1, LO2`

| Session | Activity & Topic Content | LO | Delivery Type | Duration | Hours | Format |
| :---: | :--- | :---: | :---: | :---: | :---: | :---: |
| **S1** | • Authentication (AuthN) & Authorization (AuthZ)<br>• Testing & Middleware | `LO1` | Self-learning | 120 mins | 2h | Online |
| **S2** | Hands-on Labs | `LO1, LO2` | Assignment/Lab | 180 mins | 3h | Offline |
| **S3** | Workshop: Back-end Development with FastAPI | `LO1, LO2` | Seminar/Workshop | 180 mins | 3h | Virtual |

**Learning Materials & Resources:**
- [01. Introduction to FastAPI](https://app.datacamp.com/learn/courses/introduction-to-fastapi)
- [02. Deploying AI into Production with FastAPI](https://app.datacamp.com/learn/courses/deploying-ai-into-production-with-fastapi)
- [03. Introduction to Databases in Python](https://app.datacamp.com/learn/courses/introduction-to-relational-databases-in-python)

**Logistics & Preparation Notes:**
- *Chuẩn bị tài liệu thực hành (Soạn tài liệu Hands-on)*

---

## Week 2: LLM Fundamentals & Advanced Reasoning (23 Jul - 29 Jul)

### Unit 4: LLM Fundamentals

#### Day 6
- **Total Duration:** 8 Hours (480 mins)
- **Target Learning Outcomes:** `LO3`

| Session | Activity & Topic Content | LO | Delivery Type | Duration | Hours | Format |
| :---: | :--- | :---: | :---: | :---: | :---: | :---: |
| **S1** | • Prompt roles: system, developer, user, assistant<br>• Structured output and JSON schema<br>• Tokenization, context window, latency, and cost<br>• Temperature and sampling controls | `LO3` | Self-learning | 180 mins | 3h | Online |
| **S2** | Prompt & Structured Output Design | `LO3` | Assignment/Lab | 120 mins | 2h | Offline |
| **S3** | Hands-on Labs | `LO3` | Assignment/Lab | 180 mins | 3h | Offline |

**Learning Materials & Resources:**
- [01. Cost management, RAG vs Fine-tuning, LLMOps](https://app.datacamp.com/learn/courses/llmops-concepts)
- [02. Working with the OpenAI API](https://app.datacamp.com/learn/courses/working-with-the-openai-api)
- [03. Tokenization & Transformer](https://app.datacamp.com/learn/courses/intermediate-chatgpt)
- [04. Introduction to Embeddings with the OpenAI API](https://app.datacamp.com/learn/courses/introduction-to-embeddings-with-the-openai-api)
- [05. Fine-Tuning with Llama 3](https://app.datacamp.com/learn/courses/fine-tuning-with-llama-3)

**Expected Outputs & Deliverables:**
- **Output: Prompt Package + JSON Schema Definition**
  - System/User prompt design
  - Structured JSON output schema
  - Token and cost analysis
  - Prompt optimization note

**Logistics & Preparation Notes:**
- *Chuẩn bị tài liệu thực hành (Soạn tài liệu Hands-on)*

---

#### Day 7
- **Total Duration:** 8 Hours (480 mins)
- **Target Learning Outcomes:** `LO3`

| Session | Activity & Topic Content | LO | Delivery Type | Duration | Hours | Format |
| :---: | :--- | :---: | :---: | :---: | :---: | :---: |
| **S1** | • Transformer & Embeddings<br>• Hallucination and grounding<br>• Fine-tuning basics | `LO3` | Self-learning | 180 mins | 3h | Online |
| **S2** | Hands-on Labs | `LO3` | Assignment/Lab | 120 mins | 2h | Offline |
| **S3** | Presentation: knowledge | `LO3` | Guides/Review | 180 mins | 3h | Virtual |

**Logistics & Preparation Notes:**
- *Chuẩn bị tài liệu thực hành (Soạn tài liệu Hands-on)*

---

### Unit 5: LLM Advanced

#### Day 8
- **Total Duration:** 8 Hours (480 mins)
- **Target Learning Outcomes:** `LO3, LO4`

| Session | Activity & Topic Content | LO | Delivery Type | Duration | Hours | Format |
| :---: | :--- | :---: | :---: | :---: | :---: | :---: |
| **S1** | LLM Fundamentals revision | `LO3` | Concept/Lecture | 60 mins | 1h | Virtual |
| **S2** | • Reasoning paradigms (CoT / ReAct / Plan-Execute-Replan / ToT / Reflection)<br>• Model selection for agents (benchmark / wrapper / strategy) | `LO4` | Concept/Lecture | 120 mins | 2h | Virtual |
| **S3** | Reasoning Pattern Selection | `LO4` | Assignment/Lab | 120 mins | 2h | Offline |
| **S4** | Hands-on Labs | `LO4` | Assignment/Lab | 180 mins | 3h | Offline |

**Expected Outputs & Deliverables:**
- **Output: Reasoning Decision Matrix**
  - CoT/ReAct/Plan-Execute/RePlan/ToT/Reflection usage scenarios
  - Selected reasoning strategy
  - Model selection justification
  - Key risks and mitigation notes

---

#### Day 9
- **Total Duration:** 8 Hours (480 mins)
- **Target Learning Outcomes:** `LO4`

| Session | Activity & Topic Content | LO | Delivery Type | Duration | Hours | Format |
| :---: | :--- | :---: | :---: | :---: | :---: | :---: |
| **S1** | Deep context engineering (compression / retrieval / context-engine / failure cases) | `LO4` | Concept/Lecture | 120 mins | 2h | Virtual |
| **S2** | Context Engineering Failure Analysis | `LO4` | Assignment/Lab | 180 mins | 3h | Offline |
| **S3** | Hands-on Labs | `LO4` | Assignment/Lab | 180 mins | 3h | Offline |

**Expected Outputs & Deliverables:**
- **Output: Failure Analysis Report**
  - Context failure scenarios
  - Hallucination/root cause analysis
  - Compression/retrieval mitigation strategy
  - Improvement recommendations

---

#### Day 10
- **Total Duration:** 8 Hours (480 mins)
- **Target Learning Outcomes:** `LO4`

| Session | Activity & Topic Content | LO | Delivery Type | Duration | Hours | Format |
| :---: | :--- | :---: | :---: | :---: | :---: | :---: |
| **S1** | Presentation: knowledge | `LO4` | Guides/Review | 180 mins | 3h | Virtual |
| **S2** | Agent Design Reflection | `LO4` | Assignment/Lab | 120 mins | 2h | Offline |
| **S3** | Hands-on Labs | `LO4` | Assignment/Lab | 180 mins | 3h | Offline |

**Expected Outputs & Deliverables:**
- **Output: Concept Map + Improvement Plan**
  - Knowledge map of reasoning and context engineering concepts
  - Identified weak areas
  - Preparation checklist for hands-on lab
  - Improvement plan

**Logistics & Preparation Notes:**
- *Chuẩn bị tài liệu thực hành (Soạn tài liệu Hands-on)*

---

## Week 3: RAG Engineering (30 Jul - 05 Aug)

### Unit 6: RAG Engineering

#### Day 11
- **Total Duration:** 8 Hours (480 mins)
- **Target Learning Outcomes:** `LO5`

| Session | Activity & Topic Content | LO | Delivery Type | Duration | Hours | Format |
| :---: | :--- | :---: | :---: | :---: | :---: | :---: |
| **S1** | • Document ingestion pipeline, chunking strategies, embeddings & vector search | `LO5` | Concept/Lecture | 180 mins | 3h | Virtual |
| **S2** | RAG Pipeline Design Review | `LO5` | Assignment/Lab | 120 mins | 2h | Offline |
| **S3** | Hands-on Labs | `LO5` | Assignment/Lab | 180 mins | 3h | Offline |

**Expected Outputs & Deliverables:**
- **Output: RAG Architecture Diagram**
  - Document ingestion flow
  - Chunking strategy
  - Embedding and vector search flow
  - Retrieval architecture and failure points

---

#### Day 12
- **Total Duration:** 8 Hours (480 mins)
- **Target Learning Outcomes:** `LO5`

| Session | Activity & Topic Content | LO | Delivery Type | Duration | Hours | Format |
| :---: | :--- | :---: | :---: | :---: | :---: | :---: |
| **S1** | • Metadata filtering & access control, citation-based answer generation<br>• Hybrid search<br>• Naive RAG | `LO5` | Self-learning | 180 mins | 3h | Online |
| **S2** | Retrieval Strategy Evaluation | `LO5` | Assignment/Lab | 120 mins | 2h | Offline |
| **S3** | Hands-on Labs | `LO5` | Assignment/Lab | 180 mins | 3h | Offline |

**Learning Materials & Resources:**
- [01. LangChain fundamentals](https://app.datacamp.com/learn/courses/developing-llm-applications-with-langchain)
- [02. Naive RAG (Vector & BM25 retrieval)](https://app.datacamp.com/learn/courses/retrieval-augmented-generation-rag-with-langchain)
- [03. Advanced LLMs with Retrieval Augmented Generation (RAG): Practical Projects for AI Applications](https://www.linkedin.com/learning/advanced-llms-with-retrieval-augmented-generation-rag-practical-p)

**Expected Outputs & Deliverables:**
- **Output: Retrieval Design Matrix**
  - Naive RAG vs Hybrid Search comparison
  - Metadata filtering and ACL strategy
  - Citation-based answer design
  - Retrieval quality risks

---

#### Day 13
- **Total Duration:** 8 Hours (480 mins)
- **Target Learning Outcomes:** `LO5`

| Session | Activity & Topic Content | LO | Delivery Type | Duration | Hours | Format |
| :---: | :--- | :---: | :---: | :---: | :---: | :---: |
| **S1** | • Multi-index RAG<br>• Graph RAG | `LO5` | Concept/Lecture | 180 mins | 3h | Virtual |
| **S2** | Advanced RAG Architecture Analysis | `LO5` | Assignment/Lab | 120 mins | 2h | Offline |
| **S3** | Hands-on Labs | `LO5` | Assignment/Lab | 180 mins | 3h | Offline |

**Expected Outputs & Deliverables:**
- **Output: Architecture Comparison Report**
  - Multi-index RAG analysis
  - Graph RAG analysis
  - Trade-off comparison
  - Recommended architecture

---

#### Day 14
- **Total Duration:** 8 Hours (480 mins)
- **Target Learning Outcomes:** `LO5`

| Session | Activity & Topic Content | LO | Delivery Type | Duration | Hours | Format |
| :---: | :--- | :---: | :---: | :---: | :---: | :---: |
| **S1** | • Graph knowledge stores (Neo4j / Apache AGE / Memgraph)<br>• Lab Demo: Naive RAG, Graph RAG | `LO5` | Concept/Lecture | 180 mins | 3h | Virtual |
| **S2** | Graph Knowledge Design | `LO5` | Assignment/Lab | 120 mins | 2h | Offline |
| **S3** | Hands-on Labs | `LO5` | Assignment/Lab | 180 mins | 3h | Offline |

**Expected Outputs & Deliverables:**
- **Output: Knowledge Graph Model**
  - Entity model
  - Relationship model
  - Graph store selection note
  - Retrieval path example

---

#### Day 15
- **Total Duration:** 8 Hours (360 mins)
- **Target Learning Outcomes:** `LO5`

| Session | Activity & Topic Content | LO | Delivery Type | Duration | Hours | Format |
| :---: | :--- | :---: | :---: | :---: | :---: | :---: |
| **S1** | RAG Design Consolidation | `LO5` | Assignment/Lab | 120 mins | 2h | Offline |
| **S2** | Hands-on Labs | `LO5` | Assignment/Lab | 240 mins | 6h | Offline |

**Expected Outputs & Deliverables:**
- **Output: Complete RAG Review Package**
  - Consolidated RAG architecture
  - Key design decisions
  - Retrieval/grounding improvement backlog
  - Preparation notes for hands-on lab

**Logistics & Preparation Notes:**
- *Chuẩn bị tài liệu thực hành (Soạn tài liệu Hands-on)*

---

## Week 4: Tool Calling & Agentic Workflow Design (06 Aug - 12 Aug)

### Unit 7: Tool Calling & API Integration

#### Day 16
- **Total Duration:** 8 Hours (480 mins)
- **Target Learning Outcomes:** `LO6`

| Session | Activity & Topic Content | LO | Delivery Type | Duration | Hours | Format |
| :---: | :--- | :---: | :---: | :---: | :---: | :---: |
| **S1** | Tool schema design, read vs write separation, argument validation | `LO6` | Concept/Lecture | 120 mins | 2h | Virtual |
| **S2** | Timeout / retry / rate-limit, result summarization | `LO6` | Self-learning | 120 mins | 2h | Online |
| **S3** | Tool Schema Design Review | `LO6` | Assignment/Lab | 120 mins | 2h | Offline |
| **S4** | Hands-on Labs | `LO6` | Assignment/Lab | 120 mins | 2h | Offline |

**Learning Materials & Resources:**
- [01. Tool calling / Timeout / retry / rate-limit](https://app.datacamp.com/learn/courses/developing-ai-systems-with-the-openai-api)

**Expected Outputs & Deliverables:**
- **Output: Tool Specification Package**
  - Tool schema for read/write actions
  - Argument validation rules
  - Read/Write separation design
  - Timeout/retry/rate-limit checklist

---

#### Day 17
- **Total Duration:** 8 Hours (480 mins)
- **Target Learning Outcomes:** `LO6`

| Session | Activity & Topic Content | LO | Delivery Type | Duration | Hours | Format |
| :---: | :--- | :---: | :---: | :---: | :---: | :---: |
| **S1** | Human approval for write actions<br>MCP Principle & Demo | `LO6` | Concept/Lecture | 180 mins | 3h | Virtual |
| **S2** | Approval Workflow Design | `LO6` | Assignment/Lab | 120 mins | 2h | Offline |
| **S3** | Hands-on Labs | `LO6` | Assignment/Lab | 180 mins | 3h | Offline |

**Expected Outputs & Deliverables:**
- **Output: Approval Flow Diagram**
  - Human approval flow for risky write actions
  - Audit checkpoints
  - Permission and control notes
  - Risk mitigation checklist

**Logistics & Preparation Notes:**
- *Chuẩn bị tài liệu thực hành (Soạn tài liệu Hands-on)*

---

### Unit 8: Agentic Workflow Design

#### Day 18
- **Total Duration:** 8 Hours (480 mins)
- **Target Learning Outcomes:** `LO6`

| Session | Activity & Topic Content | LO | Delivery Type | Duration | Hours | Format |
| :---: | :--- | :---: | :---: | :---: | :---: | :---: |
| **S1** | • Agetic workflow vs agent decisions<br>• Router pattern, planner-executor pattern | `LO6` | Concept/Lecture | 180 mins | 3h | Virtual |
| **S2** | Workflow Pattern Analysis | `LO6` | Assignment/Lab | 120 mins | 2h | Offline |
| **S3** | Hands-on Labs | `LO6` | Assignment/Lab | 180 mins | 3h | Offline |

**Expected Outputs & Deliverables:**
- **Output: Workflow Decision Matrix**
  - Agentic workflow vs agent decision comparison
  - Router pattern analysis
  - Planner-Executor analysis
  - Pattern selection rationale

---

#### Day 19
- **Total Duration:** 8 Hours (480 mins)
- **Target Learning Outcomes:** `LO6`

| Session | Activity & Topic Content | LO | Delivery Type | Duration | Hours | Format |
| :---: | :--- | :---: | :---: | :---: | :---: | :---: |
| **S1** | Graph orchestration (LangGraph / Agno / OpenAI Agents) | `LO6` | Self-learning | 180 mins | 3h | Online |
| **S2** | Agent Orchestration Design | `LO6` | Assignment/Lab | 120 mins | 2h | Offline |
| **S3** | Hands-on Labs | `LO6` | Assignment/Lab | 180 mins | 3h | Offline |

**Learning Materials & Resources:**
- [01. LangChain ReAct Agent & LangGraph fundamental](https://app.datacamp.com/learn/courses/designing-agentic-systems-with-langchain)
- [02. Multi-Agent Systems with LangGraph](https://app.datacamp.com/learn/courses/multi-agent-systems-with-langgraph)

**Expected Outputs & Deliverables:**
- **Output: Agent Workflow Diagram**
  - Nodes and state definition
  - Execution flow
  - Tool/action integration points
  - State transition note

---

#### Day 20
- **Total Duration:** 8 Hours (480 mins)
- **Target Learning Outcomes:** `LO6, LO11`

| Session | Activity & Topic Content | LO | Delivery Type | Duration | Hours | Format |
| :---: | :--- | :---: | :---: | :---: | :---: | :---: |
| **S1** | • ReAct loop<br>• Reflection loop + success/error metrics | `LO6` | Concept/Lecture | 120 mins | 2h | Virtual |
| **S2** | Topic revision | `LO6` | Assignment/Lab | 120 mins | 2h | Offline |
| **S3** | Hands-on: mock project increment | `LO6, LO11` | Assignment/Lab | 240 mins | 4h | Offline |

**Logistics & Preparation Notes:**
- *Chuẩn bị tài liệu thực hành (Soạn tài liệu Hands-on)*

---

## Week 5: Memory & Context Engineering (13 Aug - 19 Aug)

### Unit 9: Memory & Context Engineering

#### Day 21
- **Total Duration:** 9 Hours (540 mins)
- **Target Learning Outcomes:** `LO7, LO11`

| Session | Activity & Topic Content | LO | Delivery Type | Duration | Hours | Format |
| :---: | :--- | :---: | :---: | :---: | :---: | :---: |
| **S1** | • Memory System Design<br>• Short-term conversation state, conversation summarization, intent-state tracking<br>• Long-term semantic memory, memory update policy, stale-memory detection | `LO7` | Concept/Lecture | 180 mins | 3h | Virtual |
| **S2** | Memory Architecture Design | `LO7` | Assignment/Lab | 120 mins | 2h | Offline |
| **S3** | Hands-on: mock project increment (cont) | `LO7, LO11` | Assignment/Lab | 240 mins | 4h | Offline |

**Expected Outputs & Deliverables:**
- **Output: Memory Architecture Diagram**
  - Working memory design
  - Short-term memory and intent tracking
  - Long-term semantic memory
  - Memory update/staleness policy

---

#### Day 22
- **Total Duration:** 9 Hours (540 mins)
- **Target Learning Outcomes:** `LO7, LO11`

| Session | Activity & Topic Content | LO | Delivery Type | Duration | Hours | Format |
| :---: | :--- | :---: | :---: | :---: | :---: | :---: |
| **S1** | • Concrete vector store impl (FAISS / pgvector)<br>• Memory tooling — Redis (cache) + SQLite (persist) | `LO7` | Self-learning | 180 mins | 3h | Online |
| **S2** | Topic revision | `LO7` | Assignment/Lab | 120 mins | 2h | Offline |
| **S3** | Hands-on: mock project increment (cont) | `LO7, LO11` | Assignment/Lab | 240 mins | 4h | Offline |

**Learning Materials & Resources:**
- [01. FAISS tutorial](https://www.pinecone.io/learn/series/faiss/faiss-tutorial/)
- [02. Vector Search with PostgreSQL (pgvector)](https://www.datacamp.com/tutorial/pgvector-tutorial)
- [03. Redis for AI](https://redis.io/docs/latest/develop/ai/)

---

#### Day 23
- **Total Duration:** 9 Hours (540 mins)
- **Target Learning Outcomes:** `LO7, LO11`

| Session | Activity & Topic Content | LO | Delivery Type | Duration | Hours | Format |
| :---: | :--- | :---: | :---: | :---: | :---: | :---: |
| **S1** | • Full memory-layer model (working / episodic / procedural)<br>• Vector DB breadth (Pinecone / Weaviate / Milvus) + Graph mem (Falkor) | `LO7` | Self-learning | 180 mins | 3h | Online |
| **S2** | Memory Storage Strategy | `LO7` | Assignment/Lab | 120 mins | 2h | Offline |
| **S3** | Hands-on: mock project increment (cont) | `LO7, LO11` | Assignment/Lab | 240 mins | 4h | Offline |

**Learning Materials & Resources:**
- [01. AI Agent Memory skills](https://www.linkedin.com/learning/agentic-ai-planning-and-reasoning-design-patterns)
- [02. Building AI Applications with Pinecone](https://app.datacamp.com/learn/courses/building-ai-applications-with-pinecone)
- [03. Falkor with LangGraph](https://www.falkordb.com/blog/graphrag-langchain-langgrap/)

**Expected Outputs & Deliverables:**
- **Output: Storage Selection Matrix**
  - Redis cache usage
  - FAISS/pgvector comparison
  - SQLite persistence strategy
  - Storage decision rationale

---

#### Day 24
- **Total Duration:** 8 Hours (480 mins)
- **Target Learning Outcomes:** `LO7`

| Session | Activity & Topic Content | LO | Delivery Type | Duration | Hours | Format |
| :---: | :--- | :---: | :---: | :---: | :---: | :---: |
| **S1** | Memory Knowledge Presentation Prep | `LO7` | Assignment/Lab | 120 mins | 2h | Offline |
| **S2** | Preparation for Presentation | `LO7` | Assignment/Lab | 180 mins | 3h | Offline |
| **S3** | Presentation: knowledge | `LO7` | Guides/Review | 180 mins | 3h | Virtual |

**Expected Outputs & Deliverables:**
- **Output: Presentation Package**
  - Presentation outline
  - Architecture summary
  - Design rationale
  - Demo explanation script

---

#### Day 25
- **Total Duration:** 8 Hours (480 mins)
- **Target Learning Outcomes:** `LO7, LO11`

| Session | Activity & Topic Content | LO | Delivery Type | Duration | Hours | Format |
| :---: | :--- | :---: | :---: | :---: | :---: | :---: |
| **S1** | Memory Integration Review | `LO7` | Assignment/Lab | 180 mins | 3h | Offline |
| **S2** | Hands-on: mock project increment (cont) | `LO7, LO11` | Assignment/Lab | 300 mins | 5h | Offline |

**Learning Materials & Resources:**
- Full Memory system for Final project

**Expected Outputs & Deliverables:**
- **Output: Integration Readiness Report**
  - Memory integration checklist
  - Remaining gaps and risks
  - Test points
  - Improvement plan for mock project

---

## Week 6: Evaluation for LLM & Agent Systems (20 Aug - 26 Aug)

### Unit 10: Evaluation for LLM & Agent Systems

#### Day 26
- **Total Duration:** 8 Hours (480 mins)
- **Target Learning Outcomes:** `LO8, LO11`

| Session | Activity & Topic Content | LO | Delivery Type | Duration | Hours | Format |
| :---: | :--- | :---: | :---: | :---: | :---: | :---: |
| **S1** | • Golden dataset, RAG eval, answer-quality rubric<br>• Tool-selection accuracy, task success rate, adversarial tests | `LO8` | Self-learning | 120 mins | 2h | Online |
| **S2** | Evaluation Framework Design | `LO8` | Assignment/Lab | 120 mins | 2h | Offline |
| **S3** | Hands-on: mock project increment (cont) | `LO8, LO11` | Assignment/Lab | 240 mins | 4h | Offline |

**Learning Materials & Resources:**
- [01. Golden Dataset Creation Guide](https://github.com/drewelewis/ai-evaluating-indexing-strategies/blob/main/guides/golden-dataset-gui)
- [02. Complete Guide to Evaluating Large Language Models (LLMs)](https://www.linkedin.com/learning/complete-guide-to-evaluating-large-language-models-llms/evaluatin)

**Expected Outputs & Deliverables:**
- **Output: Evaluation Package**
  - Golden dataset sample
  - Answer-quality rubric
  - Tool-selection/task-success metrics
  - Adversarial test list

---

#### Day 27
- **Total Duration:** 8 Hours (480 mins)
- **Target Learning Outcomes:** `LO8, LO11`

| Session | Activity & Topic Content | LO | Delivery Type | Duration | Hours | Format |
| :---: | :--- | :---: | :---: | :---: | :---: | :---: |
| **S1** | • Trace & Replay system<br>• Observability system (dedicated dashboards) | `LO8` | Self-learning | 120 mins | 2h | Online |
| **S2** | • Langfuse, Phoenix | `LO8` | Self-learning | 120 mins | 2h | Online |
| **S3** | Hands-on: mock project increment (cont) | `LO8, LO11` | Assignment/Lab | 240 mins | 4h | Offline |

**Learning Materials & Resources:**
- [01. Foundation: Introduction to Agent Observability & Evaluations](https://academy.langchain.com/courses/intro-to-langsmith)
- [01. Langfuse tutorial](https://www.datacamp.com/tutorial/langfuse)
- [02. Phoenix overview](https://colab.research.google.com/github/Arize-ai/phoenix/blob/main/tutorials/ai_evals_course/phoen)

---

#### Day 28
- **Total Duration:** 8 Hours (480 mins)
- **Target Learning Outcomes:** `LO8`

| Session | Activity & Topic Content | LO | Delivery Type | Duration | Hours | Format |
| :---: | :--- | :---: | :---: | :---: | :---: | :---: |
| **S1** | Evaluation Result Analysis | `LO8` | Assignment/Lab | 120 mins | 2h | Offline |
| **S2** | Preparation for Presentation | `LO8` | Assignment/Lab | 180 mins | 3h | Offline |
| **S3** | Presentation: knowledge | `LO8` | Guides/Review | 180 mins | 3h | Virtual |

**Expected Outputs & Deliverables:**
- **Output: Evaluation Report**
  - Result interpretation
  - Failure diagnostics
  - Trace/replay analysis notes
  - Improvement recommendations

---

#### Day 29
- **Total Duration:** 8 Hours (480 mins)
- **Target Learning Outcomes:** `LO8, LO11`

| Session | Activity & Topic Content | LO | Delivery Type | Duration | Hours | Format |
| :---: | :--- | :---: | :---: | :---: | :---: | :---: |
| **S1** | Workshop: Evaluation for LLM & Agent Systems | `LO8` | Seminar/Workshop | 180 mins | 3h | Virtual |
| **S2** | Quality Improvement Planning | `LO8` | Assignment/Lab | 120 mins | 2h | Offline |
| **S3** | Hands-on: mock project increment (cont) | `LO8, LO11` | Assignment/Lab | 180 mins | 3h | Offline |

**Expected Outputs & Deliverables:**
- **Output: Improvement Roadmap**
  - Evaluation findings
  - Prioritized improvement actions
  - Validation plan
  - Mock project evaluation backlog

---

#### Day 30
- **Total Duration:** 8 Hours (480 mins)
- **Target Learning Outcomes:** `LO8, LO11`

| Session | Activity & Topic Content | LO | Delivery Type | Duration | Hours | Format |
| :---: | :--- | :---: | :---: | :---: | :---: | :---: |
| **S1** | Hands-on: mock project increment (cont) | `LO8, LO11` | Assignment/Lab | 480 mins | 8h | Offline |

**Logistics & Preparation Notes:**
- *Chuẩn bị tài liệu thực hành (Soạn tài liệu Hands-on)*

---

## Week 7: LLMOps, Production Deployment & Governance (27 Aug - 02 Sep)

### Unit 11: LLMOps & Production Deployment

#### Day 31
- **Total Duration:** 8 Hours (480 mins)
- **Target Learning Outcomes:** `LO9`

| Session | Activity & Topic Content | LO | Delivery Type | Duration | Hours | Format |
| :---: | :--- | :---: | :---: | :---: | :---: | :---: |
| **S1** | • Dockerized services, config & secrets management<br>• LLM Production challenges: Scale, Cost, Latency, Safety<br>• LLM Deployment Options: API-base, self-hosted, Hybrid<br>• Cost optimization: caching, model tiering, prompt optimization | `LO9` | Self-learning | 120 mins | 2h | Online |
| **S2** | Deployment Strategy Analysis | `LO9` | Assignment/Lab | 180 mins | 3h | Offline |
| **S3** | Local Deployment - Self-hosting:<br>• Setup local env: ollama or vLLM, models download, verify script<br>• Implement prompt caching | `LO9` | Assignment/Lab | 180 mins | 3h | Offline |

**Learning Materials & Resources:**
- [01. Intermediate docker](https://app.datacamp.com/learn/courses/intermediate-docker)

**Expected Outputs & Deliverables:**
- **Output: Deployment Decision Package**
  - Deployment architecture
  - API-based/self-hosted/hybrid decision matrix
  - Cost optimization plan
  - TPS/TTFT baseline and monitoring notes

---

#### Day 32
- **Total Duration:** 8 Hours (480 mins)
- **Target Learning Outcomes:** `LO9`

| Session | Activity & Topic Content | LO | Delivery Type | Duration | Hours | Format |
| :---: | :--- | :---: | :---: | :---: | :---: | :---: |
| **S1** | Local Deployment - Self-hosting:<br>Model tiering(routing)<br>• Prompt optimization<br>• Evaluation & monitoring: TPS, TTFT | `LO9` | Assignment/Lab | 480 mins | 8h | Offline |

---

### Unit 12: Security, Governance & Safety

#### Day 33
- **Total Duration:** 8 Hours (480 mins)
- **Target Learning Outcomes:** `LO10, LO11`

| Session | Activity & Topic Content | LO | Delivery Type | Duration | Hours | Format |
| :---: | :--- | :---: | :---: | :---: | :---: | :---: |
| **S1** | • Guardrails:<br>• Prompt injection awareness<br>• Permission model for tools<br>• Human approval for risky actions<br>• Sensitive data handling<br>• Audit logging<br>• Prompt-injection awareness<br>• Memory protection (anti memory-poisoning) | `LO10` | Concept/Lecture | 180 mins | 3h | Virtual |
| **S2** | Security Control Mapping | `LO10` | Assignment/Lab | 120 mins | 2h | Offline |
| **S3** | Hands-on: mock project increment (cont) | `LO10, LO11` | Assignment/Lab | 180 mins | 3h | Offline |

**Expected Outputs & Deliverables:**
- **Output: Security Control Matrix**
  - Risks and controls
  - Prompt injection defenses
  - Tool permission and approval policies
  - Sensitive data and audit requirements

---

#### Day 34
- **Total Duration:** 8 Hours (480 mins)
- **Target Learning Outcomes:** `LO10, LO11`

| Session | Activity & Topic Content | LO | Delivery Type | Duration | Hours | Format |
| :---: | :--- | :---: | :---: | :---: | :---: | :---: |
| **S1** | • Sandboxed code/tool execution<br>• Policy engine integration<br>• Formal threat modeling | `LO10` | Self-learning | 180 mins | 3h | Online |
| **S2** | Threat Modeling Review | `LO10` | Assignment/Lab | 120 mins | 2h | Offline |
| **S3** | Hands-on: mock project increment (cont) | `LO10, LO11` | Assignment/Lab | 180 mins | 3h | Offline |

**Learning Materials & Resources:**
- [01. Agent Governance Toolkit (21 tutorials)](https://microsoft.github.io/agent-governance-toolkit/tutorials/)

**Expected Outputs & Deliverables:**
- **Output: Threat Model Report**
  - Threat scenarios
  - Attack vectors
  - Sandboxed execution controls
  - Policy engine enforcement flow

---

#### Day 35
- **Total Duration:** 8 Hours (480 mins)
- **Target Learning Outcomes:** `LO10, LO11`

| Session | Activity & Topic Content | LO | Delivery Type | Duration | Hours | Format |
| :---: | :--- | :---: | :---: | :---: | :---: | :---: |
| **S1** | Preparation for Presentation | `LO10` | Assignment/Lab | 120 mins | 2h | Offline |
| **S2** | Presentation: knowledge | `LO10` | Guides/Review | 180 mins | 3h | Virtual |
| **S3** | Hands-on: mock project increment (cont) | `LO10, LO11` | Assignment/Lab | 180 mins | 3h | Offline |

**Logistics & Preparation Notes:**
- *Chuẩn bị tài liệu thực hành (Soạn tài liệu Hands-on)*

---

## Week 8: Capstone Mock Project & Final Evaluation (03 Sep - 09 Sep)

### Unit 13: Mock Project (Capstone)

#### Day 36 – Day 40: Capstone Mock Project & Final Evaluation
- **Total Duration:** 40 Hours (2400 mins)
- **Target Learning Outcomes:** `LO6, LO7, LO8, LO9, LO10, LO11`

| Session | Activity & Topic Content | LO | Delivery Type | Duration | Hours | Format |
| :---: | :--- | :---: | :---: | :---: | :---: | :---: |
| **S1** | Hands-on: mock project increment (cont) | `LO6,LO7,LO8,LO9,LO10,LO11` | Assignment/Lab | 1500 mins | 25h | Offline |
| **S2** | Mock project Guide/Review | `LO6,LO7,LO8,LO9,LO10,LO11` | Guides/Review | 300 mins | 5h | Virtual |
| **S3** | Final Mock Interview | `LO6,LO7,LO8,LO9,LO10,LO11` | Exam | 600 mins | 10h | Virtual |

**Expected Outputs & Deliverables:**
- **Frontend:** React or Next.js chat UI with source display and approval controls.
- **Backend:** FastAPI agent service with typed request/response contracts.
- **RAG layer:** document ingestion, chunking, embeddings, vector database, and metadata filtering.
- **Tool layer:** controlled API wrappers for ERP/CRM/database/reporting systems.
- **State layer:** conversation state, task state, memory store, and evaluation logs.
- **Observability:** traces for prompts, retrieval, tool calls, model responses, latency, cost, and failures.
- **Security:** identity, authorization, permission-scoped tools, audit logs, and human approval for side effects.

**Logistics & Preparation Notes:**
- *Phỏng vấn Mock Interview: 30 phút / học viên (30 mins/candidate)*

---
