# Software Engineer, Cloud-Native and AI Roadmap

**Version 2.0**

An execution-first learning plan for software engineering, Azure, Kubernetes, production AI, and Boomi integration.

---

## Contents

- [Executive Summary](#executive-summary)
- [The Career Stack](#the-career-stack)
- [How to Research](#how-to-research)
- [Research Roadmap](#research-roadmap)
- [Sequential Execution Plan](#sequential-execution-plan)
- [Concept Reference](#concept-reference)
- [Portfolio Projects](#portfolio-projects)
- [Portfolio Case Study Documentation Standard](#portfolio-case-study-documentation-standard)
- [Final Outcome](#final-outcome)

---

## Executive Summary

This roadmap is a direct path to becoming a credible software engineer who can build, deploy, and integrate cloud-native and AI-powered applications.

| Track | Path |
| --- | --- |
| **Primary trajectory** | Software Engineer → Cloud-Native Engineer → AI Engineer, with a Boomi enterprise integration edge |
| **Core platform stack** | Azure, AKS, Docker, Terraform, GitHub Actions, Azure DevOps |
| **AI focus** | LLMs, LangGraph, RAG, agents, vector search, managed identity, evaluation frameworks |
| **Integration edge** | Boomi runtimes, Molecule on AKS, API integration, enterprise systems |

**Target career path:** Software Engineer → Cloud-Native Engineer → AI Engineer → Enterprise AI Integration Specialist.

### Scope Strategy

Focus on application-layer engineering and execution. Avoid deep administrative paths such as:

- Certified Kubernetes Administrator (CKA) — use **CKAD** instead
- Azure Networking Specialist (AZ-700)
- Jenkins administration
- Heavy data-science theory

### Emphasis Path

For this career direction, put the most weight on:

**System Design → APIs → Databases → Distributed Systems → Event-Driven Architecture → Azure → Security → AI Architecture**

That combination fits Azure, Boomi, Business Central, APIs, Docker, Python/PHP, and LangGraph.

---

## The Career Stack

| Layer | What to learn | Core value | Target outcome |
| --- | --- | --- | --- |
| **1. Software and scripting** | Python, APIs, Git, shell scripting, SQL, testing | Foundational skills for reliable code and automation | Build APIs, automate processes, and manage code |
| **2. Cloud and platform** | Azure CLI, Entra ID (RBAC), Key Vault, VNets, subnets | Security, identity, and networking foundations | Provision and manage Azure resources securely |
| **3. Cloud-native and orchestration** | Docker, Kubernetes (CKAD focus), AKS, container registries | Package, scale, and manage containerised applications | Deploy and manage applications on AKS |
| **4. Automation and CI/CD** | Terraform, GitHub Actions, Azure Pipelines | Automate infrastructure and deployment | Deploy environments and applications through code |
| **5. AI engineering** | LangGraph, deep agents, RAG, Azure OpenAI, vector stores | Production AI application development | Deploy stateful AI agents and RAG systems |
| **6. Integration edge** | Boomi, APIs, runtime / Molecule on AKS | Connect AI services to enterprise platforms | Integrate AI with CRMs, ERPs, and enterprise systems |

---

## How to Research

Do not research topics as isolated definitions ("What is Redis?"). Research them as **engineering decisions**:

- Why would I use Redis instead of querying SQL?
- When should I use Azure Service Bus instead of calling an API directly?
- When should I use Container Apps instead of Azure Functions?
- When should I choose a modular monolith instead of microservices?
- What happens when a service fails halfway through processing an event?

The mindset is **when, why, and what are the trade-offs?** That is the architectural thinking this plan is trying to build.

Each concept in the [Concept Reference](#concept-reference) is written in that format: what it is, why it exists, problems it solves, trade-offs, and when to use it.

---

## Research Roadmap

Research and the hands-on [execution plan](#sequential-execution-plan) run in parallel. Research builds judgement; execution builds proof.

### Research phases

| Research phase | Topics | Goal |
| --- | --- | --- |
| **R1. Core engineering** | Networking, API design, database design, data architecture, software architecture, system design | Understand how applications, data, and APIs fit together |
| **R2. Production systems** | Distributed systems, event-driven architecture, messaging, resilience, security, performance, architecture trade-offs, requirements | Design systems that survive failure, load, and real constraints |
| **R3. Cloud engineering** | Cloud and Azure architecture, Docker, CI/CD, infrastructure as code, observability | Map concepts onto Azure and production delivery |
| **R4. AI engineering** | AI system architecture, RAG, vector search, agents / LangGraph, evaluation | Treat AI as a reliable production component, not a demo API call |

### Priority topics

Priority is career-weighted, not a claim that lower-ranked topics are optional. Stars and colours come from the original plan and are merged here.

| Priority | Topic | Research phase | What to learn | Why it matters | Resources |
| --- | --- | --- | --- | --- | --- |
| 1 | **System design** | R1 | Components, scalability, availability, reliability, stateless vs stateful, resilience, bottlenecks, fault tolerance | Moves you from implementing features to designing how the whole system works | [Azure Application Architecture Fundamentals](https://learn.microsoft.com/en-us/azure/architecture/guide/) · [Design principles for Azure applications](https://learn.microsoft.com/en-us/azure/architecture/guide/design-principles/) |
| 2 | **API design** | R1 | REST, resources, URLs, HTTP methods and status codes, validation, pagination, filtering, versioning, rate limiting, idempotency, contracts, webhooks | APIs are the boundaries between systems — especially important for Boomi and Business Central | [Web API design best practices](https://learn.microsoft.com/en-us/azure/architecture/best-practices/api-design) · [Web API implementation](https://learn.microsoft.com/en-us/azure/architecture/best-practices/api-implementation) |
| 3 | **Database design** | R1 | Tables, relationships, PK/FK, normalisation, indexes, transactions, locking, constraints, query optimisation | AI can generate SQL; you still need to decide how data should be structured and why queries become slow | [Azure data architecture guide](https://learn.microsoft.com/en-us/azure/architecture/data-guide/) · [SQL Server index design guide](https://learn.microsoft.com/en-us/sql/relational-databases/sql-server-index-design-guide) |
| 4 | **Software architecture** | R1 | N-tier, layered / MVC, modular monoliths, microservices, web-queue-worker, event-driven, separation of concerns, dependency injection, clean architecture | Helps you recognise common system shapes and structure a codebase | [Architecture styles](https://learn.microsoft.com/en-us/azure/architecture/guide/architecture-styles/) |
| 5 | **Architecture trade-offs** | R2 | Monolith vs microservices, sync vs async, SQL vs NoSQL, REST vs messaging, serverless vs containers | Senior engineering is choosing the best option under constraints, not collecting technologies | [Design principles](https://learn.microsoft.com/en-us/azure/architecture/guide/design-principles/) · [Cloud design patterns](https://learn.microsoft.com/en-us/azure/architecture/patterns/) |
| 6 | **Distributed systems** | R2 | Latency, partial failures, retries, timeouts, consistency, concurrency, idempotency, caching | Once several systems talk over a network, you design around the fact that parts will fail | [Cloud design patterns](https://learn.microsoft.com/en-us/azure/architecture/patterns/) |
| 7 | **Event-driven architecture and messaging** | R2 | Events, producers, consumers, pub/sub, streams, queues, topics, competing consumers, delivery, retries, dead-letter queues | Decouples applications and is highly relevant to Boomi, integrations, and Azure | [Event-driven architecture](https://learn.microsoft.com/en-us/azure/architecture/guide/architecture-styles/event-driven) · [Martin Fowler: What do you mean by event-driven?](https://martinfowler.com/articles/201701-event-driven.html) · [Asynchronous messaging options](https://learn.microsoft.com/en-us/azure/architecture/guide/technology-choices/messaging) |
| 8 | **Networking fundamentals** | R1 | DNS, TCP/IP, HTTP/HTTPS, TLS, ports, routing, proxies, reverse proxies, load balancers, firewalls | Makes APIs, Docker, cloud networking, and DNS/SSL issues understandable | [Fundamentals of computer networking](https://learn.microsoft.com/en-us/training/modules/network-fundamentals/) |
| 9 | **Cloud architecture** | R3 | Reliability, security, cost, performance, operations, availability, compute, storage, databases, serverless, containers, managed services | Moves you from using Azure resources to architecting cloud systems | [Azure Well-Architected Framework](https://learn.microsoft.com/en-us/azure/well-architected/) · [Well-Architected pillars](https://learn.microsoft.com/en-us/azure/well-architected/pillars) |
| 10 | **Azure architecture** | R3 | Mapping concepts onto App Service, Container Apps, Functions, Azure SQL, Storage, Key Vault, Service Bus, API Management, VNets, Managed Identity | Turns conceptual designs into architectures your company actually uses | [Browse Azure architectures](https://learn.microsoft.com/en-us/azure/architecture/browse/) |
| 11 | **Security architecture** | R2 | Authentication vs authorisation, OAuth 2.0, OIDC, JWT, RBAC, least privilege, secrets, encryption, OWASP, trust boundaries | Security is designed in, not added after development | [OWASP API Security Top 10](https://api-security.owasp.org/editions/2023/en/0x11-t10) · [Microsoft identity platform and OAuth 2.0](https://learn.microsoft.com/en-us/entra/identity-platform/v2-oauth2-auth-code-flow) |
| 12 | **Docker and containers** | R3 | Images, containers, networking, volumes, registries, Dockerfiles, Compose, environment variables, lifecycle | Containers are the bridge into cloud-native deployment | [Docker Get Started](https://docs.docker.com/get-started/) |
| 13 | **CI/CD and DevOps** | R3 | Git → build → test → staging → production, deployment strategies, rollback, environments | A production architecture includes how software is safely deployed | [Azure Pipelines](https://learn.microsoft.com/en-us/azure/devops/pipelines/?view=azure-devops) |
| 14 | **Infrastructure as Code** | R3 | Terraform, Bicep, declarative infrastructure, environments, repeatable deployments | Infrastructure can be versioned and reviewed like application code | [Bicep overview](https://learn.microsoft.com/en-us/azure/azure-resource-manager/bicep/overview) · [Terraform on Azure](https://developer.hashicorp.com/terraform/tutorials/azure-get-started) |
| 15 | **Observability** | R3 | Logs, metrics, traces, correlation IDs, monitoring, alerting, Azure Monitor, Application Insights | After a system has many components you must answer what broke, where, and why | [Azure Monitor](https://learn.microsoft.com/en-us/azure/azure-monitor/overview) |
| 16 | **Performance and scalability** | R2 | Horizontal vs vertical scaling, caching, load balancing, database optimisation, CDNs, asynchronous processing | Design systems that keep performing as traffic and data grow | [Best practices for cloud applications](https://learn.microsoft.com/en-us/azure/architecture/best-practices/index-best-practices) · [Cache-Aside pattern](https://learn.microsoft.com/en-us/azure/architecture/patterns/cache-aside) |
| 17 | **Requirements engineering** | R2 | Functional and non-functional requirements, constraints, SLAs, acceptance criteria, user stories | With AI coding, the engineer decides what actually needs to be built and under which constraints | [Introduction to the Azure Well-Architected Framework](https://learn.microsoft.com/en-us/training/modules/azure-well-architected-introduction/) |
| 18 | **AI system architecture** | R4 | LLMs, RAG, embeddings, vector search, grounding, tool calling, evaluation, guardrails, human-in-the-loop | Build AI as a reliable component of a wider production system | [Azure AI architecture](https://learn.microsoft.com/en-us/azure/architecture/ai-ml/) |
| 19 | **AI agents and LangGraph** | R4 | Agents vs workflows, state, nodes, tools, orchestration, memory, retries | Particularly relevant to LangChain/LangGraph and business automation | [LangGraph overview](https://docs.langchain.com/oss/python/langgraph/overview) |
| 20 | **Data structures and algorithms** | Supporting | Arrays, maps, queues, stacks, trees, graphs, Big O, searching and sorting | Enough to reason about performance and challenge AI-generated code — not a LeetCode-first path | [Collections and data structures](https://learn.microsoft.com/en-us/dotnet/standard/collections/) |
| 21 | **Architecture documentation** | Supporting | C4 model, system context, container and sequence diagrams, ADRs, API docs | Architecture includes communicating the design to other people | [C4 model](https://c4model.com/) |

Supporting patterns that sit inside the topics above (not separate priorities):

- **Resilience:** [Retry pattern](https://learn.microsoft.com/en-us/azure/architecture/patterns/retry) · [Circuit Breaker pattern](https://learn.microsoft.com/en-us/azure/architecture/patterns/circuit-breaker)
- **Data models:** [Understand data store models](https://learn.microsoft.com/en-us/azure/architecture/data-guide/technology-choices/understand-data-store-models)
- **RAG and vector search:** [RAG solution design and evaluation](https://learn.microsoft.com/en-us/azure/architecture/ai-ml/guide/rag/rag-solution-design-and-evaluation-guide) · [Vector search in Azure AI Search](https://learn.microsoft.com/en-us/azure/search/vector-search-overview)

---

## Sequential Execution Plan

Hands-on phases. Complete the checklist before moving on. Research the matching topics from the table above as you build.

### Phase 1: Local Foundations and Agent Logic

**Goal:** Master local code execution, stateful AI agents, containerisation, and version control.

**Key concepts**

| Area | Skills |
| --- | --- |
| Shell scripting and Git | Linux CLI, environment variables, Bash automation, Git branching, rebase, pull request workflows |
| Docker | Dockerfiles, image optimisation, container lifecycles, volume mounts, ports, Docker Compose |
| LangGraph and agents | Stateful graphs, agentic loops, human-in-the-loop, custom tools, memory management |

**Learning resources**

- [Shell Scripts for Beginners (KodeKloud)](https://kodekloud.com/courses/shell-scripts-for-beginners/)
- [Docker Get Started](https://docs.docker.com/get-started/)
- [Docker 101 tutorial](https://www.docker.com/101-tutorial/)
- [Docker Get Started workshop](https://docs.docker.com/get-started/workshop/)
- [Git and GitHub for Beginners (freeCodeCamp)](https://www.freecodecamp.org/news/git-and-github-for-beginners/)
- [LangGraph Academy](https://academy.langchain.com/)
- [LangGraph documentation](https://docs.langchain.com/oss/python/langgraph/overview)

**Phase checklist**

- [ ] Write shell scripts to automate local setup and environment tasks
- [ ] Build a Python API using LangGraph to manage a stateful agent workflow
- [ ] Package the API and dependencies using Docker Compose
- [ ] Push code and container configurations to a well-structured GitHub repository

---

### Phase 2: Azure Fundamentals, Identity, and Networking

**Goal:** Build a secure Azure foundation for application identity, secrets management, and networking.

**Key concepts**

| Area | Skills |
| --- | --- |
| Networking | TCP/IP, DNS, HTTP/HTTPS, TLS/SSL, subnets, NSGs, public vs private endpoints |
| Identity and secrets | Azure CLI, Entra ID (RBAC), managed identities, `DefaultAzureCredential`, Azure Key Vault |
| Core services | Resource groups, VNets, Azure App Service, storage accounts |

**Learning resources**

- [Describe cloud concepts](https://learn.microsoft.com/en-us/training/modules/describe-cloud-compute/)
- [Describe Azure architecture and services](https://learn.microsoft.com/en-us/training/paths/azure-fundamentals-describe-azure-architecture-services/)
- [Describe the core architectural components of Azure](https://learn.microsoft.com/en-us/training/modules/describe-core-architectural-components-of-azure/)
- [Introduction to Azure Virtual Networks](https://learn.microsoft.com/en-us/training/modules/introduction-to-azure-virtual-networks/)
- [Describe Azure compute and networking services](https://learn.microsoft.com/en-us/training/modules/describe-azure-compute-networking-services/)

**Phase checklist**

- [ ] Configure Azure CLI and manage resource groups
- [ ] Store and retrieve secrets from Azure Key Vault
- [ ] Configure Entra ID RBAC for applications
- [ ] Design a VNet with public and private subnets

---

### Phase 3: Infrastructure as Code and Container Orchestration

**Goal:** Automate Azure infrastructure with Terraform and deploy applications onto AKS.

**Key concepts**

| Area | Skills |
| --- | --- |
| Terraform | HCL syntax, providers, state management, remote state (Azure Blob), variables, outputs, modules |
| Kubernetes (CKAD focus) | Pods, Deployments, Services, ConfigMaps, Secrets, Ingress, storage volumes |
| AKS | Cluster setup, Azure Container Registry (ACR), workload identity, pod scaling |

**Learning resources**

- [Learn Kubernetes basics](https://kubernetes.io/docs/tutorials/kubernetes-basics/)
- [Introduction to Azure Kubernetes Service](https://learn.microsoft.com/en-us/training/modules/intro-to-azure-kubernetes-service/)
- [AKS documentation](https://learn.microsoft.com/en-us/azure/aks/)
- [Terraform Get Started on Azure (HashiCorp)](https://developer.hashicorp.com/terraform/tutorials/azure-get-started)

**Phase checklist**

- [ ] Provision ACR, Key Vault, VNet, and AKS using Terraform
- [ ] Push Docker images to Azure Container Registry
- [ ] Create `deployment.yaml` and `service.yaml` manifests
- [ ] Deploy applications to AKS using workload identity

---

### Phase 4: Production Delivery and CI/CD Automation

**Goal:** Create automated delivery pipelines that build, test, provision infrastructure, and deploy applications.

**Pipeline workflow**

```text
Git push
  → Lint and test
  → Terraform plan / apply
  → Docker build and push
  → AKS deployment
```

**Key concepts**

| Area | Skills |
| --- | --- |
| Tooling | GitHub Actions, Azure Pipelines, self-hosted runners, secret management, release gates |
| Observability | Application Insights, OpenTelemetry, Kubernetes logging, `kubectl logs` |

**Learning resources**

- [GitHub Actions quickstart](https://docs.github.com/en/actions/quickstart)
- [What is Azure Pipelines?](https://learn.microsoft.com/en-us/azure/devops/pipelines/get-started/what-is-azure-pipelines)
- [Azure Pipelines documentation](https://learn.microsoft.com/en-us/azure/devops/pipelines/?view=azure-devops)
- [Enable OpenTelemetry in Application Insights](https://learn.microsoft.com/en-us/azure/azure-monitor/app/opentelemetry-enable)

**Phase checklist**

- [ ] Run automated unit tests on pull requests
- [ ] Build and push Docker images to ACR
- [ ] Automate Terraform deployments
- [ ] Automate AKS deployments
- [ ] Configure Application Insights, logging, and health checks

---

### Phase 5: Production AI Engineering and Enterprise RAG

**Goal:** Move from local AI prototypes to production-grade retrieval-augmented generation (RAG) systems.

**Key concepts**

| Area | Skills |
| --- | --- |
| AI engineering | LLM APIs, embeddings, vector indexing, hybrid search, RAG, agentic workflows |
| Managed cloud AI | Azure OpenAI, Azure AI Search, PGVector, prompt evaluation |
| AI observability | Token usage, latency, agent execution tracing, cost management |

**Learning resources**

- [AI Engineer career path (Codecademy)](https://www.codecademy.com/learn/paths/ai-engineer)
- [RAG and indexes in Microsoft Foundry](https://learn.microsoft.com/en-us/azure/foundry/concepts/retrieval-augmented-generation)
- [Develop a RAG solution on Azure — design and evaluation](https://learn.microsoft.com/en-us/azure/architecture/ai-ml/guide/rag/rag-solution-design-and-evaluation-guide)
- [Build a language solution with Azure OpenAI](https://learn.microsoft.com/en-us/training/modules/build-language-solution-azure-openai/)
- [Vector search overview](https://learn.microsoft.com/en-us/azure/search/vector-search-overview)

**Phase checklist**

- [ ] Provision Azure OpenAI and Azure AI Search using Terraform
- [ ] Build an end-to-end RAG solution
- [ ] Connect LangGraph agents using Azure workload identity
- [ ] Implement evaluation metrics for retrieval quality and answer quality

---

### Phase 6: Enterprise Integration Edge (Boomi)

**Goal:** Run Boomi integration runtimes on AKS to connect AI services with enterprise applications.

**Key concepts**

| Area | Skills |
| --- | --- |
| Boomi core | Integrations, API management, connectors, JSON/XML mapping, execution history |
| Runtimes on Kubernetes | Atom deployment, Molecule deployment, StatefulSets, Deployments |
| Enterprise workflow | CRM and ERP event triggers, Boomi APIs, LangGraph workflow invocation |

**Learning resources**

- [Installing a cloud cluster with elastic scaling in Kubernetes](https://help.boomi.com/docs/Atomsphere/Integration/Atom,%20Molecule,%20and%20Atom%20Cloud%20setup/int-Installing_a_cloud_cluster_with_elastic_scaling_in_kubernetes)
- [Boomi Runtime Management](https://help.boomi.com/docs/Atomsphere/Integration/Integration%20management/c-atm-Atom_Management_b38a3a90-d7f6-4df0-8c00-e75a178dfdfa)
- [Runtime cluster system requirements](https://help.boomi.com/docs/Atomsphere/Integration/Atom,%20Molecule,%20and%20Atom%20Cloud%20setup/r-atm-Molecule_system_requirements_41f9a675-ab11-4f3b-bf51-1655394aba5b)
- [Boomi Runtime Quickstarts (Azure Marketplace)](https://azuremarketplace.microsoft.com/en-us/marketplace/apps/boomilp1650401905026.boomi-runtime-quickstarts?tab=overview)

**Phase checklist**

- [ ] Deploy a Boomi Atom or Molecule cluster onto AKS
- [ ] Create an integration flow that accepts enterprise webhooks
- [ ] Route payloads to a LangGraph AI service running on AKS
- [ ] Write AI-enriched responses back into enterprise systems

---

## Concept Reference

Use this as a decision catalogue, not a glossary. Every entry follows: what it is, why it exists, problems it solves, trade-offs, and when to use it.

### System design

#### System design fundamentals

Designing the major components of a system and how they interact.

- **Why it exists:** Applications need planning beyond individual functions and classes.
- **Problems it solves:** Complexity, scalability, reliability, maintainability, and integration.
- **Trade-offs:** More design effort upfront and potential over-engineering.
- **When to use:** When designing a new system or a significant feature.
- **Resource:** [Azure Application Architecture Fundamentals](https://learn.microsoft.com/en-us/azure/architecture/guide/)

#### Scalability

A system's ability to handle increasing workload.

- **Why it exists:** Users, requests, and data can grow.
- **Problems it solves:** Capacity limits and performance degradation under load.
- **Trade-offs:** Increased infrastructure and architectural complexity.
- **When to use:** Systems expected to grow or experience variable demand.
- **Resource:** [Design principles](https://learn.microsoft.com/en-us/azure/architecture/guide/design-principles/)

#### Availability

How consistently a system remains operational and accessible.

- **Why it exists:** Some applications cannot tolerate significant downtime.
- **Problems it solves:** Service interruption from infrastructure or component failure.
- **Trade-offs:** Redundancy increases cost and complexity.
- **When to use:** Business-critical systems.
- **Resource:** [Azure Well-Architected reliability](https://learn.microsoft.com/en-us/azure/well-architected/reliability/)

#### Stateful vs stateless

Stateful services retain session or state locally; stateless services do not rely on a particular instance holding it.

- **Why it exists:** State affects how easily applications scale and recover.
- **Problems it solves:** Stateless designs make distributing requests and replacing instances easier.
- **Trade-offs:** State normally has to live elsewhere, such as a database or cache.
- **When to use:** Statelessness is particularly useful for scalable APIs and web applications.
- **Resource:** [Architecture design principles](https://learn.microsoft.com/en-us/azure/architecture/guide/design-principles/)

#### Architecture trade-offs

Comparing alternative designs against requirements and constraints.

- **Why it exists:** No architecture is universally best.
- **Problems it solves:** Prevents technology selection based purely on trends.
- **Trade-offs:** You usually accept weaknesses in exchange for more important benefits.
- **When to use:** Every significant architecture decision.
- **Resource:** [Cloud design patterns](https://learn.microsoft.com/en-us/azure/architecture/patterns/)

### Software architecture

#### Layered / N-tier architecture

Separating presentation, business logic, and data-access responsibilities.

- **Why it exists:** Separating responsibilities makes applications easier to understand.
- **Problems it solves:** Organisation, maintainability, and separation of concerns.
- **Trade-offs:** Layers can become rigid; changes may cross several layers.
- **When to use:** Traditional business applications and many web applications.
- **Resource:** [Architecture styles](https://learn.microsoft.com/en-us/azure/architecture/guide/architecture-styles/)

#### Modular monolith

A single deployable application divided into strongly separated modules.

- **Why it exists:** You can achieve modularity without distributed-system complexity.
- **Problems it solves:** Poor code organisation and tightly coupled components.
- **Trade-offs:** Modules are not independently deployable; boundaries require discipline.
- **When to use:** Often a strong default for new business applications.
- **Resource:** [Architecture styles](https://learn.microsoft.com/en-us/azure/architecture/guide/architecture-styles/)

#### Microservices

Splitting business capabilities into independently deployable services.

- **Why it exists:** Large systems or teams may need components to deploy and scale independently.
- **Problems it solves:** Independent deployment, scaling, and ownership.
- **Trade-offs:** Networking, data consistency, deployment, observability, and debugging become considerably harder.
- **When to use:** When independent services provide enough benefit to justify distributed-system complexity.
- **Resource:** [Martin Fowler: Microservices](https://martinfowler.com/articles/microservices.html)

### API design

#### REST

An architectural approach commonly used to expose resources through HTTP.

- **Why it exists:** Applications need standard interfaces for communicating.
- **Problems it solves:** Client/server separation and system integration.
- **Trade-offs:** Network latency, versioning, security, and distributed failures.
- **When to use:** Request-response APIs, especially web, mobile, and enterprise integrations.
- **Resource:** [REST API design best practices](https://learn.microsoft.com/en-us/azure/architecture/best-practices/api-design)

#### HTTP methods and status codes

Standard HTTP semantics such as GET, POST, PUT, PATCH, DELETE, and response codes.

- **Why it exists:** Consumers need predictable API behaviour.
- **Problems it solves:** Ambiguous API interfaces.
- **Trade-offs:** Poorly designed APIs can misuse HTTP semantics and confuse consumers.
- **When to use:** All HTTP APIs.
- **Resource:** [REST API design best practices](https://learn.microsoft.com/en-us/azure/architecture/best-practices/api-design)

#### Pagination and filtering

Returning manageable subsets of large result sets.

- **Why it exists:** Returning thousands or millions of records at once is inefficient.
- **Problems it solves:** Performance, bandwidth, and memory consumption.
- **Trade-offs:** Adds complexity to APIs and clients.
- **When to use:** Collection endpoints that can return large amounts of data.
- **Resource:** [REST API design best practices](https://learn.microsoft.com/en-us/azure/architecture/best-practices/api-design)

#### Idempotency

Repeating the same request does not create unintended additional effects.

- **Why it exists:** Networks and distributed systems retry requests.
- **Problems it solves:** Duplicate payments, orders, and processing.
- **Trade-offs:** Often requires identifiers and duplicate-detection state.
- **When to use:** Payments, orders, webhooks, message consumers, and retried operations.
- **Resource:** [Web API implementation](https://learn.microsoft.com/en-us/azure/architecture/best-practices/api-implementation)

### Data architecture

#### Relational databases

Structured data stored in related tables.

- **Why it exists:** Business data frequently contains well-defined relationships and consistency requirements.
- **Problems it solves:** Transactions, relationships, integrity, and complex queries.
- **Trade-offs:** Rigid schemas and certain scaling limitations.
- **When to use:** Customers, orders, payments, inventory, and ERP/CRM data.
- **Resource:** [Azure data architecture guide](https://learn.microsoft.com/en-us/azure/architecture/data-guide/)

#### NoSQL

Non-relational storage models such as document, key-value, and graph.

- **Why it exists:** Some workloads need different data structures or scaling characteristics.
- **Problems it solves:** Flexible schemas and specialised access patterns.
- **Trade-offs:** Relationships, consistency, and transaction capabilities differ by technology.
- **When to use:** When data and access patterns genuinely benefit from a non-relational model.
- **Resource:** [Understand data store models](https://learn.microsoft.com/en-us/azure/architecture/data-guide/technology-choices/understand-data-store-models)

#### Database indexes

Data structures that allow databases to locate records faster.

- **Why it exists:** Scanning an entire table is expensive as data grows.
- **Problems it solves:** Slow queries and lookups.
- **Trade-offs:** Consume storage and make writes more expensive.
- **When to use:** Columns frequently involved in searches, joins, sorting, or filtering, based on workload.
- **Resource:** [SQL Server index design guide](https://learn.microsoft.com/en-us/sql/relational-databases/sql-server-index-design-guide)

### Distributed systems and messaging

#### Synchronous communication

One service calls another and waits for the response.

- **Why it exists:** Some operations require an immediate answer.
- **Problems it solves:** Straightforward request-response workflows.
- **Trade-offs:** The caller depends on the availability and latency of downstream services.
- **When to use:** When an immediate response is genuinely required.
- **Resource:** [Architecture design principles](https://learn.microsoft.com/en-us/azure/architecture/guide/design-principles/)

#### Asynchronous communication

Work is submitted without waiting for the complete operation to finish.

- **Why it exists:** Long-running work should not necessarily block the original request.
- **Problems it solves:** Workload spikes, long processing times, and coupling.
- **Trade-offs:** Harder debugging and eventual consistency.
- **When to use:** Background jobs, integrations, emails, file processing, and long-running workloads.
- **Resource:** [Asynchronous messaging options](https://learn.microsoft.com/en-us/azure/architecture/guide/technology-choices/messaging)

#### Message queue

A buffer where producers send messages for consumers to process later.

- **Why it exists:** Producer and consumer should not necessarily need to operate simultaneously.
- **Problems it solves:** Traffic spikes, temporary outages, and asynchronous processing.
- **Trade-offs:** Additional infrastructure, duplicates, ordering, and monitoring.
- **When to use:** Work that does not require an immediate response, or where downstream systems can fail temporarily.
- **Resource:** [Asynchronous messaging options](https://learn.microsoft.com/en-us/azure/architecture/guide/technology-choices/messaging)

#### Publish / subscribe

A publisher produces something that multiple independent subscribers receive.

- **Why it exists:** Several systems may need to react to the same event.
- **Problems it solves:** One-to-many communication and tight coupling.
- **Trade-offs:** Event flows become harder to trace and debug.
- **When to use:** When multiple systems independently react to the same event.
- **Resource:** [Event-driven architecture](https://learn.microsoft.com/en-us/azure/architecture/guide/architecture-styles/event-driven)

#### Dead-letter queue

Storage for messages that cannot be processed successfully.

- **Why it exists:** Failed messages should not disappear or continuously disrupt healthy processing.
- **Problems it solves:** Poison messages and repeated processing failures.
- **Trade-offs:** Requires monitoring and a reprocessing strategy.
- **When to use:** Reliable messaging and integration workloads.
- **Resource:** [Service Bus dead-letter queues](https://learn.microsoft.com/en-us/azure/service-bus-messaging/service-bus-dead-letter-queues)

### Event-driven architecture

#### Events

A statement that something has happened, such as `OrderCreated`.

- **Why it exists:** Other components may need to respond to business changes.
- **Problems it solves:** Direct dependencies between systems.
- **Trade-offs:** Event flows become harder to understand than straightforward calls.
- **When to use:** When systems need to react to things that have happened.
- **Resource:** [Event-driven architecture](https://learn.microsoft.com/en-us/azure/architecture/guide/architecture-styles/event-driven)

#### Producer / consumer

Producers publish events; consumers react to them.

- **Why it exists:** Separates who announces something happened from who reacts to it.
- **Problems it solves:** Coupling between applications.
- **Trade-offs:** Consumers need to handle retries, duplicates, and failures.
- **When to use:** Event-driven and integration architectures.
- **Resource:** [Event-driven architecture](https://learn.microsoft.com/en-us/azure/architecture/guide/architecture-styles/event-driven)

### Performance, scalability, and resilience

#### Caching

Keeping frequently accessed data in faster storage.

- **Why it exists:** Database or API requests may be slow or expensive.
- **Problems it solves:** Latency and backend load.
- **Trade-offs:** Stale data and difficult cache invalidation.
- **When to use:** Frequently read information that does not always require fresh retrieval.
- **Resource:** [Cache-Aside pattern](https://learn.microsoft.com/en-us/azure/architecture/patterns/cache-aside)

#### Vertical scaling

Giving one machine more CPU, RAM, or other resources.

- **Why it exists:** It is the simplest way to increase capacity.
- **Problems it solves:** Resource constraints.
- **Trade-offs:** Hardware limits, potentially high costs, and possible single points of failure.
- **When to use:** Smaller systems, or where scaling up is sufficient.
- **Resource:** [Design to scale out](https://learn.microsoft.com/en-us/azure/architecture/guide/design-principles/scale-out)

#### Horizontal scaling

Adding more application instances rather than making one instance larger.

- **Why it exists:** Individual machines have limits.
- **Problems it solves:** High traffic, availability, and capacity.
- **Trade-offs:** Applications need to work correctly across multiple instances.
- **When to use:** Cloud applications with growing or variable workloads.
- **Resource:** [Design to scale out](https://learn.microsoft.com/en-us/azure/architecture/guide/design-principles/scale-out)

#### Load balancing

Distributing requests between multiple application instances.

- **Why it exists:** Traffic needs to be shared across horizontally scaled resources.
- **Problems it solves:** Overloaded servers and single-instance dependency.
- **Trade-offs:** Adds infrastructure and state/session considerations.
- **When to use:** When multiple instances serve the same workload.
- **Resource:** [Azure load-balancing options](https://learn.microsoft.com/en-us/azure/architecture/guide/technology-choices/load-balancing-overview)

#### Retry

Automatically repeating an operation after a temporary failure.

- **Why it exists:** Network, API, and database failures are sometimes temporary.
- **Problems it solves:** Transient failures.
- **Trade-offs:** Excessive retries can worsen outages and cause duplicate operations.
- **When to use:** Temporary failures where retrying is safe.
- **Resource:** [Retry pattern](https://learn.microsoft.com/en-us/azure/architecture/patterns/retry)

#### Exponential backoff

Increasing the time between retries.

- **Why it exists:** Immediate retries can overwhelm an unhealthy dependency.
- **Problems it solves:** Retry storms and overloaded systems.
- **Trade-offs:** Recovery can take longer.
- **When to use:** Usually alongside retries against remote services.
- **Resource:** [Retry pattern](https://learn.microsoft.com/en-us/azure/architecture/patterns/retry)

#### Circuit breaker

Temporarily stops requests to a dependency after repeated failures.

- **Why it exists:** Calling a service known to be failing wastes resources and can spread failure.
- **Problems it solves:** Cascading failures.
- **Trade-offs:** Adds state and configuration.
- **When to use:** Remote dependencies that can temporarily become unavailable.
- **Resource:** [Circuit Breaker pattern](https://learn.microsoft.com/en-us/azure/architecture/patterns/circuit-breaker)

### Security

#### Authentication

Establishing who a user or application is.

- **Why it exists:** Systems need verified identities.
- **Problems it solves:** Unauthorised access.
- **Trade-offs:** Credentials, identity providers, and tokens must be securely managed.
- **When to use:** Almost every protected system or API.
- **Resource:** [Microsoft identity platform](https://learn.microsoft.com/en-us/entra/identity-platform/)

#### Authorisation

Deciding what an authenticated identity is allowed to do.

- **Why it exists:** Being authenticated should not provide access to everything.
- **Problems it solves:** Unauthorised resource or action access.
- **Trade-offs:** Permission models can become complicated.
- **When to use:** Whenever different users or services require different privileges.
- **Resource:** [OWASP API Security Top 10](https://api-security.owasp.org/editions/2023/en/0x11-t10)

#### OAuth 2.0 / OpenID Connect

OAuth handles delegated authorisation; OpenID Connect adds an identity and authentication layer.

- **Why it exists:** Applications need standardised ways to delegate access and establish identity without sharing passwords.
- **Problems it solves:** Secure API access and federated identity.
- **Trade-offs:** Flows, scopes, and tokens can initially be difficult to understand.
- **When to use:** Modern web applications, APIs, SSO, and third-party integrations.
- **Resource:** [Microsoft identity platform and OAuth 2.0](https://learn.microsoft.com/en-us/entra/identity-platform/v2-oauth2-auth-code-flow)

### Cloud, containers, and delivery

#### Well-Architected design

Evaluating workloads across reliability, security, cost, operations, and performance.

- **Why it exists:** A technically functioning application is not necessarily production-ready.
- **Problems it solves:** Poor reliability, excessive cost, security weaknesses, and operational issues.
- **Trade-offs:** Improvements in one area can affect another.
- **When to use:** Designing and reviewing production cloud workloads.
- **Resource:** [Azure Well-Architected Framework](https://learn.microsoft.com/en-us/azure/well-architected/)

#### Containers

Packaging an application and its dependencies into an isolated runtime unit.

- **Why it exists:** Applications need consistent environments across developer machines and servers.
- **Problems it solves:** Environment inconsistencies and deployment portability.
- **Trade-offs:** Networking, persistent storage, and orchestration add complexity.
- **When to use:** Portable application deployment and cloud/container platforms.
- **Resource:** [Docker Get Started](https://docs.docker.com/get-started/)

#### CI/CD

Automating building, testing, and deploying software.

- **Why it exists:** Manual deployments are inconsistent and error-prone.
- **Problems it solves:** Deployment mistakes, slow releases, and inconsistent environments.
- **Trade-offs:** Pipelines themselves require maintenance.
- **When to use:** Nearly every actively maintained production application.
- **Resource:** [Azure Pipelines](https://learn.microsoft.com/en-us/azure/devops/pipelines/?view=azure-devops)

#### Infrastructure as Code

Defining infrastructure through machine-readable configuration or code.

- **Why it exists:** Manually created infrastructure becomes inconsistent.
- **Problems it solves:** Reproducibility, auditing, automation, and environment consistency.
- **Trade-offs:** Another tool or language to learn; infrastructure changes require careful review.
- **When to use:** Repeatable dev, staging, and production environments.
- **Resource:** [Bicep overview](https://learn.microsoft.com/en-us/azure/azure-resource-manager/bicep/overview)

### Observability

#### Logging

Recording application events and contextual information.

- **Why it exists:** You need evidence of what happened after software is deployed.
- **Problems it solves:** Troubleshooting and incident investigation.
- **Trade-offs:** Cost, noise, and potential exposure of sensitive information.
- **When to use:** All production applications.
- **Resource:** [Azure Monitor overview](https://learn.microsoft.com/en-us/azure/azure-monitor/overview)

#### Metrics

Numeric measurements such as request rate, latency, and error rate.

- **Why it exists:** Logs alone do not efficiently show overall system health.
- **Problems it solves:** Performance monitoring, trends, and alerting.
- **Trade-offs:** Metrics tell you something is wrong but do not always explain why.
- **When to use:** Production monitoring and alerting.
- **Resource:** [Azure Monitor metrics](https://learn.microsoft.com/en-us/azure/azure-monitor/essentials/data-platform-metrics)

#### Distributed tracing

Following a request as it travels through multiple components or services.

- **Why it exists:** Distributed requests may pass through many systems.
- **Problems it solves:** Finding where latency and failures occur.
- **Trade-offs:** Additional instrumentation, telemetry, and storage.
- **When to use:** Distributed systems, integrations, and microservices.
- **Resource:** [Application Insights overview](https://learn.microsoft.com/en-us/azure/azure-monitor/app/app-insights-overview)

### Architecture documentation

#### C4 model

A hierarchical way of documenting software architecture using Context, Container, Component, and Code views.

- **Why it exists:** Different audiences need different levels of architectural detail.
- **Problems it solves:** Confusing or overly detailed architecture diagrams.
- **Trade-offs:** Diagrams must be kept current.
- **When to use:** Documenting and explaining system architecture.
- **Resource:** [C4 model](https://c4model.com/)

### AI architecture

#### RAG

Retrieval-augmented generation retrieves relevant external information and supplies it as context to an LLM.

- **Why it exists:** Models do not inherently know your current or private organisational knowledge.
- **Problems it solves:** Grounding AI responses in company information.
- **Trade-offs:** Retrieval quality, permissions, indexing, latency, and cost become additional concerns.
- **When to use:** Knowledge assistants, document Q&A, and enterprise AI applications.
- **Resource:** [RAG solution design and evaluation](https://learn.microsoft.com/en-us/azure/architecture/ai-ml/guide/rag/rag-solution-design-and-evaluation-guide)

#### Vector search

Retrieving information using similarity between vector representations rather than only exact keywords.

- **Why it exists:** Similar meaning can be expressed using completely different words.
- **Problems it solves:** Semantic retrieval.
- **Trade-offs:** Requires embedding and indexing infrastructure; not always superior to traditional search.
- **When to use:** Semantic search and many RAG architectures.
- **Resource:** [Vector search overview](https://learn.microsoft.com/en-us/azure/search/vector-search-overview)

#### Tool calling

Allowing an AI model to request execution of predefined functions or tools.

- **Why it exists:** AI sometimes needs external information or needs to perform an action.
- **Problems it solves:** Connecting models to APIs and business systems.
- **Trade-offs:** Security, permissions, validation, hallucinated actions, and error handling become critical.
- **When to use:** AI systems that need controlled interaction with real applications or data.
- **Resource:** [LangChain tools](https://docs.langchain.com/oss/python/langchain/tools)

#### AI agents

An AI-controlled workflow capable of deciding which tools or actions to use to accomplish a goal.

- **Why it exists:** Some problems involve dynamic sequences of decisions rather than fixed workflows.
- **Problems it solves:** Variable multi-step tasks and AI orchestration.
- **Trade-offs:** Less predictable, harder to test, potentially more expensive, and introduces security concerns.
- **When to use:** When the task genuinely requires dynamic reasoning. Prefer deterministic workflows when the steps are known in advance.
- **Resource:** [LangGraph overview](https://docs.langchain.com/oss/python/langgraph/overview)

---

## Portfolio Projects

Three projects, each building on the last. Together they are the execution matrix for the roadmap.

### Project 1: Cloud-Native Microservice

```text
Python API
  → Docker
  → Terraform (AKS + ACR)
  → GitHub Actions pipeline
```

**Deliverables**

- Containerised API
- Infrastructure as Code
- CI/CD pipeline
- AKS deployment

### Project 2: Cloud-Native Stateful AI Platform

```text
LangGraph agents
  → Azure OpenAI
  → Azure AI Search
  → Workload identity
```

**Deliverables**

- Stateful multi-agent workflow
- Enterprise RAG system
- Azure OpenAI integration
- Azure AI Search integration

### Project 3: Enterprise AI Integration Platform

```text
Enterprise event
  → Boomi Molecule on AKS
  → LangGraph AI service
  → Enterprise system update
```

**Deliverables**

- Event-driven integration
- AI middleware layer
- Enterprise system automation
- End-to-end AI workflow

---

## Portfolio Case Study Documentation Standard

Every repository should include a production-grade `README.md` containing the following.

### 1. Problem statement

A clear explanation of the business problem being solved.

### 2. Architecture diagram

Visual representation of the solution architecture. Example flow:

```text
UI / event source
  → Boomi
  → Python API
  → Azure AI Search
  → Azure OpenAI
  → AKS
```

### 3. Deployment evidence

Include screenshots and outputs demonstrating successful deployment:

- GitHub Actions executions
- AKS pod status (`kubectl get pods`)
- API logs
- Infrastructure deployment results

### 4. Engineering trade-offs

Document architectural decisions such as:

- AKS vs App Service
- LangGraph vs linear chains
- Azure AI Search vs PGVector
- Terraform vs manual provisioning

### 5. Observability and costs

Include:

- Application Insights telemetry
- Response latency metrics
- Token consumption
- Infrastructure costs
- Optimisation opportunities

---

## Final Outcome

By completing this roadmap, you will be able to:

- Build production-grade software applications
- Containerise and orchestrate workloads with Docker and AKS
- Provision cloud infrastructure using Terraform
- Implement CI/CD pipelines using GitHub Actions and Azure Pipelines
- Design and deploy enterprise-grade AI systems using Azure OpenAI and RAG
- Integrate AI solutions with enterprise platforms through Boomi
- Demonstrate engineering capability through a portfolio of real-world cloud-native and AI projects

**Target career path:** Software Engineer → Cloud-Native Engineer → AI Engineer → Enterprise AI Integration Specialist.
