# Software Engineer, Cloud-Native and AI Roadmap

Version 3.0. An execution-first learning plan for software engineering, Azure, Kubernetes, production AI, and Boomi integration.

---

## Contents

- [Executive Summary](#executive-summary)
- [The Career Stack](#the-career-stack)
- [How to use this plan](#how-to-use-this-plan)
- [System and architectural design](#system-and-architectural-design)
- [Phases](#phases)
- [Portfolio Projects](#portfolio-projects)
- [Portfolio Case Study Documentation Standard](#portfolio-case-study-documentation-standard)
- [Final Outcome](#final-outcome)

---

## Executive Summary

This roadmap starts with system design and architectural design, then uses each phase to go deeper and build the decision. The outcome is a software engineer who can design, deploy, and integrate cloud-native and AI-powered applications.

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

[System and architectural design](#system-and-architectural-design) is the broad pass. Depth stays inside the phases as decision notes and Architecture Center articles. This is not a design-interview track and not a multi-region build.

### Emphasis Path

For this career direction, put the most weight on:

System Design → APIs → Databases → Distributed Systems → Event-Driven Architecture → Azure → Security → AI Architecture

That line is the topic order. [System and architectural design](#system-and-architectural-design) is where those topics are defined. The phases are where each one is practiced. The combination fits Azure, Boomi, Business Central, APIs, Docker, Python/PHP, and LangGraph.

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

## How to use this plan

Read [System and architectural design](#system-and-architectural-design), including its links, before Phase 1. That section is the broad pass: what the two skills are, why you use them, and the concepts. The links there are articles, not workshops.

Each phase is then the depth. Research, courses, and the hands-on build live in the same place. Open one phase at a time and work **top to bottom**:

1. **Overview** — how this phase’s ideas fit together
2. **Concept glossary** — what each term is, why it exists, when to use it, and what you give up
3. **Courses** — named modules you click and complete (not catalogue pages)
4. **Build** — the checklist that proves you can apply it

Do not start a course until the overview and glossary for that phase make sense. Do not move to the next phase until the build checklist is done.

Research terms as **engineering decisions**, not isolated definitions:

- Why would I use Redis instead of querying SQL?
- When should I use Azure Service Bus instead of calling an API directly?
- When should I choose a modular monolith instead of microservices?
- When is a slightly stale read acceptable?

Enough data-structures knowledge (arrays, maps, queues, Big O) to reason about performance and challenge AI-generated code is useful throughout. It is not a LeetCode-first path and is not a separate phase.

---

## System and architectural design

Read this section, including the links, before Phase 1. It is the broad pass. Each phase then goes deeper: glossary, courses, and a build. These links are articles. Tool workshops stay in the phases (Docker, Git, LangGraph Academy, Terraform, AKS, pipelines, OpenTelemetry, Service Bus, Boomi).

### What they are, and why

Architectural design chooses the shape: which parts exist, where the boundaries are, and how those parts are allowed to talk. You use it so a change in one place does not force a rewrite of everything else, and so another engineer can see the structure.

System design chooses how that shape behaves under real constraints: growth, failure, stale data, and recovery. You use it so the structure still works when traffic, dependencies, or a region misbehave.

They are two questions about one system. A shape that ignores load and failure will not hold. A scaling trick that ignores boundaries becomes a pile of coupled services.

Start with [Design principles](https://learn.microsoft.com/en-us/azure/architecture/guide/design-principles/) and [Azure architecture styles](https://learn.microsoft.com/en-us/azure/architecture/guide/architecture-styles/). The lists below attach one article to each concept. Several concepts share a page. Read the article once.

### Architectural design

- **Modular structure.** A layered app, a modular monolith, or microservices. Deepened in Phases 1 and 3. Layered and modular monolith: [Architecture styles](https://learn.microsoft.com/en-us/azure/architecture/guide/architecture-styles/). Microservices: [Martin Fowler](https://martinfowler.com/articles/microservices.html).
- **API contract.** REST, HTTP semantics, pagination, and idempotency. Phase 1. REST, HTTP, and pagination: [Web API design best practices](https://learn.microsoft.com/en-us/azure/architecture/best-practices/api-design). Idempotency: [Web API implementation](https://learn.microsoft.com/en-us/azure/architecture/best-practices/api-implementation).
- **API gateway.** One front door for routing, auth, and throttling. Phase 4. [API gateways](https://learn.microsoft.com/en-us/azure/architecture/microservices/design/gateway).
- **Identity boundary.** Who is calling, and what they may do. Phase 2. Authentication and OAuth: [Microsoft identity platform](https://learn.microsoft.com/en-us/entra/identity-platform/v2-overview). Authorization: [OWASP API Security Top 10](https://api-security.owasp.org/editions/2023/en/0x11-t10/).
- **Cloud shape.** A Well-Architected review, and which Azure service matches the design. Phase 2. [Azure Well-Architected Framework](https://learn.microsoft.com/en-us/azure/well-architected/).
- **Delivery shape.** Containers, infrastructure as code, and CI/CD. Phases 1, 3, and 4. Containers: [Docker overview](https://docs.docker.com/get-started/docker-overview/). Infrastructure as code: [What is infrastructure as code?](https://learn.microsoft.com/en-us/devops/deliver/what-is-infrastructure-as-code). CI/CD: [What is continuous delivery?](https://learn.microsoft.com/en-us/devops/deliver/what-is-continuous-delivery).
- **Event-driven integration.** Sync versus async, queues, pub/sub, outbox, saga, and CQRS. Phase 6. Sync versus async: [Interservice communication](https://learn.microsoft.com/en-us/azure/architecture/microservices/design/interservice-communication). Queues and pub/sub: [Asynchronous messaging options](https://learn.microsoft.com/en-us/azure/architecture/guide/technology-choices/messaging). Dead-letter queues: [Service Bus dead-letter queues](https://learn.microsoft.com/en-us/azure/service-bus-messaging/service-bus-dead-letter-queues). Events, producers, consumers, and sagas: [Event-driven architecture style](https://learn.microsoft.com/en-us/azure/architecture/guide/architecture-styles/event-driven). Outbox and CQRS: [CQRS pattern](https://learn.microsoft.com/en-us/azure/architecture/patterns/cqrs).
- **Design record.** C4 diagrams and Architecture Decision Records. Phase 6. [C4 model](https://c4model.com/). [Architecture decision records](https://adr.github.io/).
- **AI boundary.** Where the agent, tools, retrieval, and vector search sit. Phases 1 and 5. Agents and tool calling: [LangGraph overview](https://docs.langchain.com/oss/python/langgraph/overview). RAG: [Retrieval augmented generation overview](https://learn.microsoft.com/en-us/azure/search/retrieval-augmented-generation-overview). Vector search: [Vector search overview](https://learn.microsoft.com/en-us/azure/search/vector-search-overview).

### System design

- **Design walkthrough and trade-offs.** Constraints, components, data flow, failure, and a rough size. No option wins every column. Phase 1. Walkthrough: [Design principles](https://learn.microsoft.com/en-us/azure/architecture/guide/design-principles/). Trade-offs: [Cloud Design Patterns](https://learn.microsoft.com/en-us/azure/architecture/patterns/).
- **State placement.** A stateless HTTP edge, with state in a store or a checkpoint. Phase 1. Covered by [Design principles](https://learn.microsoft.com/en-us/azure/architecture/guide/design-principles/).
- **Data.** Relational, NoSQL (document and key-value), and indexes. Phase 1. Relational and NoSQL: [Understand data store models](https://learn.microsoft.com/en-us/azure/architecture/data-guide/technology-choices/understand-data-store-models). Indexes: [SQL Server index design guide](https://learn.microsoft.com/en-us/sql/relational-databases/sql-server-index-design-guide).
- **Copies and splits.** Replication, partitioning, and strong versus eventual consistency. Phase 3. Replication is the data form of redundancy in [Design principles](https://learn.microsoft.com/en-us/azure/architecture/guide/design-principles/). Partitioning: [Sharding pattern](https://learn.microsoft.com/en-us/azure/architecture/patterns/sharding). Consistency: [Understand data store models](https://learn.microsoft.com/en-us/azure/architecture/data-guide/technology-choices/understand-data-store-models).
- **Scale and availability.** Vertical scale, horizontal scale, and load balancing. Phase 3. Scale and availability: [Design to scale out](https://learn.microsoft.com/en-us/azure/architecture/guide/design-principles/scale-out) and [Well-Architected Reliability](https://learn.microsoft.com/en-us/azure/well-architected/reliability/). Load balancing: [Load balancing options](https://learn.microsoft.com/en-us/azure/architecture/guide/technology-choices/load-balancing-overview).
- **Speed.** Caching and a CDN. Phase 4. [Cache-Aside pattern](https://learn.microsoft.com/en-us/azure/architecture/patterns/cache-aside).
- **Resilience.** Retry, backoff, circuit breaker, rate limiting, and backpressure. Phase 4. Retry and backoff: [Retry pattern](https://learn.microsoft.com/en-us/azure/architecture/patterns/retry). Circuit breaker: [Circuit Breaker pattern](https://learn.microsoft.com/en-us/azure/architecture/patterns/circuit-breaker). Rate limiting and backpressure: [Rate Limiting pattern](https://learn.microsoft.com/en-us/azure/architecture/patterns/rate-limiting-pattern).
- **Seeing the system.** Logs, metrics, and traces. Phase 4. [Azure Monitor overview](https://learn.microsoft.com/en-us/azure/azure-monitor/fundamentals/overview).
- **Recovery.** SLAs, RPO, and RTO. Phase 4. [Architecture strategies for disaster recovery](https://learn.microsoft.com/en-us/azure/well-architected/reliability/disaster-recovery).

---

## Phases

1. [Phase 1: Local Foundations](#phase-1-local-foundations-and-agent-logic) — application shape: API contract, modular monolith, state, and data choice
2. [Phase 2: Azure Identity and Networking](#phase-2-azure-fundamentals-identity-and-networking) — trust boundary and cloud shape: identity, secrets, network, Well-Architected
3. [Phase 3: IaC and AKS](#phase-3-infrastructure-as-code-and-container-orchestration) — more than one copy: scale, availability, replication, partitioning, consistency
4. [Phase 4: CI/CD and Production](#phase-4-production-delivery-and-cicd-automation) — production behavior: resilience, observability, delivery, recovery
5. [Phase 5: Production AI](#phase-5-production-ai-engineering-and-enterprise-rag) — AI architecture: agents, RAG, and vector search
6. [Phase 6: Boomi Integration](#phase-6-enterprise-integration-edge-boomi) — boundaries between systems: events, messaging, and the written design

---

### Phase 1: Local Foundations and Agent Logic

<details>
<summary>Open Phase 1 — overview, glossary, courses, build</summary>

**Goal:** Design the application shape: the API contract, a modular monolith, where state lives, and which data store you use. Docker and LangGraph are how you build it.

**Feeds:** [Portfolio Project 1](#project-1-cloud-native-microservice) (and the LangGraph core of [Project 2](#project-2-cloud-native-stateful-ai-platform))

#### Overview

You are building a local Python API that runs a stateful agent and ships in Docker. The definitions and reading links are in [System and architectural design](#system-and-architectural-design). This phase applies the walkthrough and the store choice. The API is the contract (REST, HTTP, pagination, idempotency). The codebase shape is a modular monolith: one deployable app with clear modules, kept mostly stateless at the HTTP edge, with state in the agent graph or a relational database. Read the glossary, then take the courses in order.

#### Concept glossary

##### API design

###### REST

An architectural style for exposing resources over HTTP.

- **Why it is used:** Clients and services need a shared, predictable interface for integration.
- **When to use it:** Request-response APIs for web, mobile, and enterprise integrations (including Boomi and Business Central).
- **Trade-offs:** Network latency, versioning, security, and distributed failures.
- **Learn more:** [Web API design best practices](https://learn.microsoft.com/en-us/azure/architecture/best-practices/api-design) — also the reading for HTTP methods and pagination.

###### HTTP methods and status codes

Standard HTTP semantics such as GET, POST, PUT, PATCH, DELETE, and response codes.

- **Why it is used:** Consumers need predictable API behaviour.
- **When to use it:** All HTTP APIs.
- **Trade-offs:** Misusing HTTP semantics (for example POST for reads) confuses clients and caches.

###### Pagination

Returning manageable subsets of large result sets, often with filtering.

- **Why it is used:** Returning thousands of records at once is slow and expensive.
- **When to use it:** Collection endpoints that can return large amounts of data.
- **Trade-offs:** Adds complexity to APIs and clients.

###### Idempotency

Repeating the same request does not create unintended additional effects.

- **Why it is used:** Networks and clients retry requests.
- **When to use it:** Payments, orders, webhooks, message consumers, and any retried write.
- **Trade-offs:** Often requires identifiers and duplicate-detection state.
- **Learn more:** [Web API implementation](https://learn.microsoft.com/en-us/azure/architecture/best-practices/api-implementation).

##### Software architecture

###### Layered / N-tier architecture

Separating presentation, business logic, and data-access responsibilities.

- **Why it is used:** Separating responsibilities makes a codebase easier to understand and change.
- **When to use it:** Traditional business applications and many web APIs.
- **Trade-offs:** Layers can become rigid; a change may need to cross several layers.

###### Modular monolith

A single deployable application divided into strongly separated modules.

- **Why it is used:** You get modularity without distributed-system complexity.
- **When to use it:** A strong default for a new business application, including this phase’s API.
- **Trade-offs:** Modules are not independently deployable; boundaries require discipline.

##### System design

###### System design fundamentals

Designing the major components of a system and how they interact. Walk the design before you pick services: constraints, main components, data flow, failure modes, and a rough size (requests and data).

- **Why it is used:** Applications need planning beyond individual functions and classes.
- **When to use it:** When designing a new system or a significant feature.
- **Trade-offs:** More design effort upfront; risk of over-engineering.
- **Learn more:** [Design principles](https://learn.microsoft.com/en-us/azure/architecture/guide/design-principles/).

###### Architecture trade-offs

Comparing alternative designs against requirements and constraints. No option is best at everything.

- **Why it is used:** Every option gives something up, so the choice has to be explicit.
- **When to use it:** Every significant architecture decision.
- **Trade-offs:** You accept a weakness in exchange for a more important benefit.
- **Learn more:** [Cloud Design Patterns](https://learn.microsoft.com/en-us/azure/architecture/patterns/).

###### Stateful vs stateless

Stateful services retain session or state on a particular instance; stateless services do not.

- **Why it is used:** State affects how easily you scale and replace instances.
- **When to use it:** Keep the HTTP edge stateless. Put state in a database, cache, or LangGraph checkpoint.
- **Trade-offs:** State still has to live somewhere; that store becomes a dependency.

##### Data

###### Relational databases

Structured data stored in related tables.

- **Why it is used:** Business data usually has relationships and consistency requirements.
- **When to use it:** Customers, orders, payments, inventory, and ERP/CRM-shaped data.
- **Trade-offs:** Rigid schemas and some scaling limits.

###### NoSQL

Non-relational storage, such as a document store or a key-value store.

- **Why it is used:** Some workloads need a flexible shape or a fast lookup more than they need joins.
- **When to use it:** Key-value (for example Redis) for hot lookups and cache, when you can give up queries and relationships. Document when one aggregate varies in shape and you do not need multi-row transactions. Relational stays the default for orders, customers, and ERP-shaped data.
- **Trade-offs:** Relationships, consistency, and transactions differ by product.
- **Learn more:** [Understand data store models](https://learn.microsoft.com/en-us/azure/architecture/data-guide/technology-choices/understand-data-store-models).

###### Indexes

Data structures that let a database locate rows without scanning the whole table.

- **Why it is used:** Full table scans become expensive as data grows.
- **When to use it:** Columns used in searches, joins, sorting, or filtering, based on real queries.
- **Trade-offs:** Use storage and make writes slower.

##### Delivery

###### Containers

Packaging an application and its dependencies into an isolated runtime unit.

- **Why it is used:** The same artefact should run on your laptop and later on AKS.
- **When to use it:** Portable application deployment and any cloud/container platform.
- **Trade-offs:** Networking, persistent storage, and orchestration add complexity.

##### AI

###### Agents

An AI-controlled workflow that decides which tools or actions to use to reach a goal.

- **Why it is used:** Some tasks need a dynamic sequence of decisions, not a fixed script.
- **When to use it:** When the path is not known in advance. Prefer a deterministic workflow when the steps are known.
- **Trade-offs:** Less predictable, harder to test, often more expensive, and a larger security surface.

###### Tool calling

Allowing a model to request execution of predefined functions.

- **Why it is used:** Models cannot see your APIs or data unless you give them controlled tools.
- **When to use it:** AI that must read or write real systems.
- **Trade-offs:** Permissions, validation, hallucinated tool calls, and error handling become critical.

###### LangGraph

A graph runtime for stateful agent workflows (nodes, edges, state, memory, interrupts).

- **Why it is used:** You need explicit control over steps, retries, and human-in-the-loop, not a hidden agent loop.
- **When to use it:** Multi-step agents where state and branching must be visible and testable.
- **Trade-offs:** More structure than a linear chain; overkill for a single prompt-and-response call.

#### Courses (in order)

Complete these after the glossary. Each link opens that course or module.

1. [Shell Scripts for Beginners (KodeKloud)](https://kodekloud.com/courses/shell-scripts-for-beginners/) — **paid**
2. [Introduction to Git (Microsoft Learn)](https://learn.microsoft.com/en-us/training/modules/intro-to-git/)
3. [Docker Get Started workshop](https://docs.docker.com/get-started/workshop/)
4. [Foundation: Introduction to LangGraph – Python (LangChain Academy)](https://academy.langchain.com/courses/intro-to-langgraph)

#### Build

- [ ] Write shell scripts to automate local setup and environment tasks
- [ ] Build a Python API using LangGraph to manage a stateful agent workflow
- [ ] Package the API and dependencies using Docker Compose
- [ ] Push code and container configurations to a well-structured GitHub repository

</details>

---

### Phase 2: Azure Fundamentals, Identity, and Networking

<details>
<summary>Open Phase 2 — overview, glossary, courses, build</summary>

**Goal:** Decide the trust boundary and the cloud shape: who can call the app, where secrets live, which network paths exist, and whether the design meets the Well-Architected Framework. Azure CLI, Key Vault, Entra ID, and VNets are how you apply it.

**Feeds:** The Azure account, identity, and network that [Project 1](#project-1-cloud-native-microservice) and later projects run on.

#### Overview

Cloud resources are useless if anyone can reach them or if secrets live in source control. This phase is the security and network floor: who is the caller (authentication), what they may do (authorisation / RBAC), where secrets live (Key Vault), and which network paths exist (VNets, subnets, public vs private endpoints). Well-Architected is the checklist you use to judge whether a design is production-shaped, not just “it deployed.” Read the glossary, then take the courses in order.

#### Concept glossary

##### Networking

###### DNS

The system that maps names such as `api.example.com` to addresses.

- **Why it is used:** People and certificates use names; machines route with addresses.
- **When to use it:** Every public or private hostname you expose.
- **Trade-offs:** Misconfigured DNS is a common outage; TTL and caching delay changes.

###### TCP/IP

The protocols that move packets between hosts and keep connections reliable (TCP) or not (UDP).

- **Why it is used:** Almost every API, database, and container talk sits on this stack.
- **When to use it:** You need it whenever you debug ports, timeouts, or “connection refused.”
- **Trade-offs:** Reliability (TCP) costs latency; you still have to handle disconnects.

###### HTTP / HTTPS

The application protocol for web and most REST APIs; HTTPS is HTTP over TLS.

- **Why it is used:** A shared request/response model for clients and APIs.
- **When to use it:** Browser apps, REST APIs, and most webhooks.
- **Trade-offs:** Chatty request/response; you must terminate TLS and handle headers, methods, and status codes correctly.

###### TLS

Encryption and identity for data in transit (the “S” in HTTPS).

- **Why it is used:** Stop eavesdropping and prove you are talking to the intended host.
- **When to use it:** Any traffic that leaves a trusted network boundary — which is almost all cloud traffic.
- **Trade-offs:** Certificates must be issued, rotated, and trusted; mis-issued certs take services down.

###### Subnets and NSGs

Subnets slice a VNet; network security groups allow or deny traffic by port, protocol, and source.

- **Why it is used:** Not every resource should be reachable from the internet or from every other subnet.
- **When to use it:** When you place App Service, AKS, databases, or private endpoints on a VNet.
- **Trade-offs:** Too-tight rules break apps; too-open rules erase the isolation.

###### Public vs private endpoints

A public endpoint is reachable from the internet; a private endpoint brings the service onto your VNet.

- **Why it is used:** Key Vault, storage, and data stores often should not have a public data-plane.
- **When to use it:** Secrets, databases, and internal APIs. Keep public only what must be public.
- **Trade-offs:** Private endpoints add cost, DNS, and network complexity.

##### Identity and access

###### Authentication

Establishing who a user or application is.

- **Why it is used:** Systems need a verified identity before they grant anything.
- **When to use it:** Almost every protected API or Azure resource.
- **Trade-offs:** Credentials, identity providers, and tokens must be managed securely.

###### Authorisation

Deciding what an authenticated identity is allowed to do.

- **Why it is used:** Being signed in should not mean access to everything.
- **When to use it:** Whenever users or services need different privileges (RBAC, least privilege).
- **Trade-offs:** Permission models become complicated if roles are invented ad hoc.

###### OAuth 2.0 / OpenID Connect

OAuth delegates access; OpenID Connect adds an identity layer on top.

- **Why it is used:** Apps can access APIs and sign users in without sharing passwords.
- **When to use it:** Modern web apps, APIs, SSO, and third-party integrations.
- **Trade-offs:** Flows, scopes, and tokens take time to learn; a wrong flow is a security bug.

##### Cloud architecture

###### Well-Architected design

Evaluating a workload across reliability, security, cost, operations, and performance.

- **Why it is used:** “It runs” is not the same as production-ready.
- **When to use it:** Designing and reviewing any production Azure workload.
- **Trade-offs:** Improving one pillar (for example reliability) can raise cost or complexity.

###### Azure architecture mapping

Choosing Azure services that match the design: App Service or Functions for compute, Key Vault for secrets, VNets for isolation, Managed Identity instead of stored credentials.

- **Why it is used:** Conceptual designs only become real when they map onto services your company actually runs.
- **When to use it:** Every time you turn a diagram into a resource list.
- **Trade-offs:** Each service has limits, pricing, and identity/network rules; picking by popularity wastes money.

#### Courses (in order)

Complete these after the glossary. Each link opens that learning path or module.

1. [Introduction to Cloud Infrastructure: Describe cloud concepts](https://learn.microsoft.com/en-us/training/paths/microsoft-azure-fundamentals-describe-cloud-concepts/)
2. [Introduction to Cloud Infrastructure: Describe Azure architecture and services](https://learn.microsoft.com/en-us/training/paths/azure-fundamentals-describe-azure-architecture-services/)
3. [Fundamentals of computer networking](https://learn.microsoft.com/en-us/training/modules/network-fundamentals/)
4. [Introduction to Azure Virtual Networks](https://learn.microsoft.com/en-us/training/modules/introduction-to-azure-virtual-networks/)
5. [Configure and secure Azure Key Vault](https://learn.microsoft.com/en-us/training/modules/configure-secure-key-vault/)
6. [Secure your Azure resources with Azure RBAC](https://learn.microsoft.com/en-us/training/modules/secure-azure-resources-with-rbac/)
7. [Introduction to the Azure Well-Architected Framework](https://learn.microsoft.com/en-us/training/modules/azure-well-architected-introduction/)

#### Build

- [ ] Configure Azure CLI and manage resource groups
- [ ] Store and retrieve secrets from Azure Key Vault
- [ ] Configure Entra ID RBAC for applications
- [ ] Design a VNet with public and private subnets

</details>

---

### Phase 3: Infrastructure as Code and Container Orchestration

<details>
<summary>Open Phase 3 — overview, glossary, courses, build</summary>

**Goal:** Design for more than one copy: scale, availability, replication, partitioning, consistency, and when a microservice is worth it. Terraform and AKS are how you build it.

**Feeds:** [Portfolio Project 1](#project-1-cloud-native-microservice) — ACR, AKS, and Terraform.

#### Overview

Phase 1 packaged an app; this phase places it on a cluster you can recreate. Terraform makes the VNet, Key Vault, ACR, and AKS repeatable. Kubernetes (CKAD focus: Pods, Deployments, Services) is how the container actually runs. Microservices, scaling, and load balancing become real once you have more than one instance. With more than one copy you also choose replication, partitioning, and whether reads must be strongly consistent. Prefer a modular monolith until independent deployability is worth the extra failure modes. Read the glossary, then take the courses in order.

#### Concept glossary

##### Delivery

###### Infrastructure as Code

Defining infrastructure in versioned configuration (Terraform or Bicep) instead of clicking in a portal.

- **Why it is used:** Hand-built environments drift and cannot be reviewed.
- **When to use it:** Any environment you might need to recreate (dev, staging, production).
- **Trade-offs:** Another language to learn; infrastructure changes need the same review discipline as application code.

###### Microservices

Splitting business capabilities into independently deployable services.

- **Why it is used:** Large systems or teams may need to deploy and scale parts independently.
- **When to use it:** Only when that independence is worth distributed-system cost.
- **Trade-offs:** Networking, data consistency, deployment, observability, and debugging get much harder.
- **Learn more:** [Martin Fowler: Microservices](https://martinfowler.com/articles/microservices.html).

##### Scale and availability

###### Scalability

A system’s ability to handle a growing workload.

- **Why it is used:** Users, requests, and data grow.
- **When to use it:** Systems that will grow or see variable demand.
- **Trade-offs:** More infrastructure and a more complex design.

###### Availability

How consistently a system stays up and reachable.

- **Why it is used:** Some workloads cannot tolerate long downtime.
- **When to use it:** Business-critical APIs and integrations.
- **Trade-offs:** Redundancy costs money and operational complexity.

###### Vertical scaling

Giving one machine more CPU, RAM, or disk.

- **Why it is used:** It is the simplest way to add capacity.
- **When to use it:** Smaller systems, or when one larger node is enough.
- **Trade-offs:** Hardware limits, cost, and a possible single point of failure.

###### Horizontal scaling

Adding more instances rather than enlarging one instance.

- **Why it is used:** One machine has a ceiling; more replicas also help availability.
- **When to use it:** Cloud apps with growing or spiky traffic (AKS replica counts).
- **Trade-offs:** The app must be safe to run on many instances (stateless edge, shared state store).

###### Load balancing

Distributing requests across those instances.

- **Why it is used:** Horizontal scale only works if traffic is shared.
- **When to use it:** When more than one replica serves the same workload (Kubernetes Service / Ingress).
- **Trade-offs:** Extra infrastructure; sticky sessions fight stateless design.

###### Replication

Extra copies of data, for reads and for surviving a node loss.

- **Why it is used:** One copy is a single point of failure, and reads can outgrow the primary.
- **When to use it:** When availability or read scale needs more than one copy. This is the data form of redundancy from the design principles.
- **Trade-offs:** Writes and replication lag become your problem.
- **Learn more:** [Design principles](https://learn.microsoft.com/en-us/azure/architecture/guide/design-principles/).

###### Partitioning

Splitting data so one machine, or one hotspot, is not the ceiling.

- **Why it is used:** A single store has a size and throughput limit.
- **When to use it:** When one database or one key is the bottleneck.
- **Trade-offs:** Cross-partition queries and transactions get harder.
- **Learn more:** [Sharding pattern](https://learn.microsoft.com/en-us/azure/architecture/patterns/sharding).

###### Consistency

Whether a read sees the latest write. Strong means it does. Eventual means it might not, for a while.

- **Why it is used:** Copies of data can disagree until replication catches up.
- **When to use it:** Strong when the reader must see the latest write. Eventual when a slightly stale read is acceptable in exchange for availability.
- **Trade-offs:** Strong consistency costs latency and availability. Eventual consistency is harder to program and debug.
- **Learn more:** [Understand data store models](https://learn.microsoft.com/en-us/azure/architecture/data-guide/technology-choices/understand-data-store-models).

#### Courses (in order)

Complete these after the glossary. Each link opens that tutorial or module.

1. [Learn Kubernetes basics](https://kubernetes.io/docs/tutorials/kubernetes-basics/)
2. [Deploy a containerized application on Azure Kubernetes Service](https://learn.microsoft.com/en-us/training/modules/aks-deploy-container-app/1-introduction)
3. [Terraform Get Started on Azure (HashiCorp)](https://developer.hashicorp.com/terraform/tutorials/azure-get-started)

#### Build

- [ ] Provision ACR, Key Vault, VNet, and AKS using Terraform
- [ ] Push Docker images to Azure Container Registry
- [ ] Create `deployment.yaml` and `service.yaml` manifests
- [ ] Deploy applications to AKS using workload identity

</details>

---

### Phase 4: Production Delivery and CI/CD Automation

<details>
<summary>Open Phase 4 — overview, glossary, courses, build</summary>

**Goal:** Design production behavior: resilience, observability, delivery, and recovery. Pipelines are how you ship it.

**Feeds:** The pipeline and telemetry for [Portfolio Project 1](#project-1-cloud-native-microservice).

#### Overview

A production architecture includes how software is released. The path is: git push → lint and test → Terraform plan/apply → Docker build and push → AKS deploy. Observability (logs, metrics, traces) is how you answer what broke. Resilience (retry, backoff, circuit breaker, cache, rate limiting, backpressure) is how the running system survives blips. Recovery objectives say how much data you can lose and how long you can be down, which is a bigger decision than a retry. Requirements and SLAs are the constraints you design against. Read the glossary, then take the courses in order.

#### Concept glossary

##### Delivery

###### CI/CD

Automating build, test, and deploy so every change follows the same path.

- **Why it is used:** Manual releases are slow and inconsistent.
- **When to use it:** Nearly every actively maintained production app.
- **Trade-offs:** Pipelines need maintenance, secrets, and rollback design.

##### Observability

###### Logging

Recording events and context from the running application.

- **Why it is used:** After deploy you need evidence of what happened.
- **When to use it:** All production applications.
- **Trade-offs:** Cost, noise, and the risk of logging secrets.

###### Metrics

Numeric measurements such as request rate, latency, and error rate.

- **Why it is used:** Logs do not show overall health cheaply.
- **When to use it:** Production monitoring and alerting.
- **Trade-offs:** Metrics say something is wrong; they often do not say why.

###### Distributed tracing

Following one request across processes (API, agent, search, model).

- **Why it is used:** Latency and failures hide in the hops between services.
- **When to use it:** Distributed systems, integrations, and anything on AKS with more than one component.
- **Trade-offs:** Extra instrumentation and telemetry storage.

##### Resilience

###### Retry

Automatically repeating an operation after a temporary failure.

- **Why it is used:** Networks, APIs, and databases fail briefly.
- **When to use it:** Transient failures where a repeat is safe (idempotent calls).
- **Trade-offs:** Naive retries amplify outages and can duplicate work.

###### Exponential backoff

Increasing the wait between retries.

- **Why it is used:** Immediate retries can crush an already unhealthy dependency.
- **When to use it:** Together with retries against remote services.
- **Trade-offs:** Recovery takes longer.

###### Circuit breaker

Stopping calls to a dependency after repeated failures, then probing later.

- **Why it is used:** Calling a known-dead service wastes resources and spreads failure.
- **When to use it:** Remote dependencies that can go down for a while.
- **Trade-offs:** Adds state and thresholds you must tune.

###### Caching

Keeping frequently read data in faster storage.

- **Why it is used:** Databases and APIs are slower or more expensive than memory.
- **When to use it:** Hot reads that do not always need a fresh fetch.
- **Trade-offs:** Stale data and cache invalidation.

###### CDN

A cache placed near clients for public or static reads.

- **Why it is used:** The same response should not travel from the origin for every distant caller.
- **When to use it:** Public or static content that many clients read, and that can be slightly stale.
- **Trade-offs:** Invalidation delay, and it does not help private or personalised responses.
- **Learn more:** [Cache-Aside pattern](https://learn.microsoft.com/en-us/azure/architecture/patterns/cache-aside).

###### Rate limiting

A cap on how fast callers can hit you, or how fast you call someone else.

- **Why it is used:** Unlimited traffic takes down the dependency or your own service.
- **When to use it:** Public APIs, and any client that calls a throttled downstream service.
- **Trade-offs:** Legitimate bursts get rejected, and you must define the limit.
- **Learn more:** [Rate Limiting pattern](https://learn.microsoft.com/en-us/azure/architecture/patterns/rate-limiting-pattern).

###### Backpressure

A signal that tells producers to slow down, instead of retrying harder.

- **Why it is used:** Retries against an overloaded dependency make the outage worse.
- **When to use it:** When a dependency returns a throttle or overload signal, such as HTTP 429 and `Retry-After`.
- **Trade-offs:** Work waits longer, and callers must honour the signal.
- **Learn more:** [Rate Limiting pattern](https://learn.microsoft.com/en-us/azure/architecture/patterns/rate-limiting-pattern).

###### API gateway

One front door for routing, authentication, and throttling.

- **Why it is used:** Every service should not reimplement the same edge rules.
- **When to use it:** On AKS, Ingress can be that door. A managed gateway fits when many external clients need auth, throttling, and a published API.
- **Trade-offs:** Another hop, and a gateway you do not need is extra cost and configuration.
- **Learn more:** [API gateways](https://learn.microsoft.com/en-us/azure/architecture/microservices/design/gateway).

##### Requirements

###### Requirements and SLAs

Functional needs, non-functional constraints (latency, uptime), and the service level you commit to.

- **Why it is used:** With AI-generated code, the engineer still decides what “done” means.
- **When to use it:** Before you design the pipeline, the cluster size, or the retry policy.
- **Trade-offs:** Tight SLAs cost redundancy and operational effort.

###### Recovery objectives

RPO is how much data you can lose. RTO is how long you can be down. Disaster recovery is the plan for losing a whole region or site.

- **Why it is used:** Retries and extra replicas do not cover a region failure.
- **When to use it:** When the business states a downtime and data-loss budget that a single region cannot meet.
- **Trade-offs:** A second region costs money and operational complexity. This is a principles decision, not a multi-region build on this roadmap.
- **Learn more:** [Architecture strategies for disaster recovery](https://learn.microsoft.com/en-us/azure/well-architected/reliability/disaster-recovery).

#### Courses (in order)

Complete these after the glossary. Each link opens that module or procedure.

1. [Introduction to GitHub Actions](https://learn.microsoft.com/en-us/training/modules/introduction-to-github-actions/)
2. [Create your first pipeline (Azure Pipelines)](https://learn.microsoft.com/en-us/azure/devops/pipelines/create-first-pipeline)
3. [Enable Azure Monitor OpenTelemetry for .NET, Node.js, Python, and Java applications](https://learn.microsoft.com/en-us/azure/azure-monitor/app/opentelemetry-enable)

#### Build

```text
Git push
  → Lint and test
  → Terraform plan / apply
  → Docker build and push
  → AKS deployment
```

- [ ] Run automated unit tests on pull requests
- [ ] Build and push Docker images to ACR
- [ ] Automate Terraform deployments
- [ ] Automate AKS deployments
- [ ] Configure Application Insights, logging, and health checks

</details>

---

### Phase 5: Production AI Engineering and Enterprise RAG

<details>
<summary>Open Phase 5 — overview, glossary, courses, build</summary>

**Goal:** Design the AI boundary: where agents, retrieval, and vector search sit in a production RAG system on Azure, and how you evaluate the answers.

**Feeds:** [Portfolio Project 2](#project-2-cloud-native-stateful-ai-platform)

#### Overview

A model call is not a product. RAG retrieves organisational text, embeds it, and grounds the prompt so answers cite current private knowledge. You will provision Azure OpenAI and Azure AI Search with Terraform, attach the Phase 1 LangGraph agent with workload identity, and measure retrieval and answer quality. Read the glossary before you pick Search vs PGVector or a hosted model vs a local one.

#### Concept glossary

##### AI architecture

###### RAG

Retrieval-augmented generation: fetch relevant documents and pass them to the model as context.

- **Why it is used:** The model does not know your private or current company data.
- **When to use it:** Knowledge assistants, document Q&A, and enterprise AI.
- **Trade-offs:** Retrieval quality, permissions, indexing, latency, and cost all become your problem.

###### Vector search

Finding items by similarity of embeddings, not only exact keywords.

- **Why it is used:** The same meaning can use completely different words.
- **When to use it:** Semantic search and most RAG systems (often with keyword/hybrid search).
- **Trade-offs:** Needs embedding and index infrastructure; not always better than lexical search.

###### Embeddings

Numeric vectors that represent the meaning of text (or other content).

- **Why it is used:** They are what vector search compares.
- **When to use it:** Indexing documents and queries for RAG.
- **Trade-offs:** Embedding model choice, token cost, and re-embedding when the model changes.

###### Grounding and evaluation

Grounding means the answer is tied to retrieved sources. Evaluation measures whether retrieval and answers are actually good.

- **Why it is used:** Fluent answers can still be wrong or leak the wrong document.
- **When to use it:** Before you call a RAG system production.
- **Trade-offs:** You need labelled questions, metrics, and time; demos skip this and fail later.

###### Azure OpenAI vs calling a model locally

Hosted Azure OpenAI versus a model process you run yourself.

- **Why it is used:** Azure OpenAI gives managed identity, regional compliance, and operational cover. Local models avoid data leaving your box and can cut token cost.
- **When to use it:** Azure OpenAI for company production on this roadmap. Local models for experiments or strict isolation.
- **Trade-offs:** Hosted = quota, cost, and vendor limits. Local = GPUs, patching, and you own uptime.

###### Azure AI Search vs PGVector

A managed search service with vector and hybrid search, versus vectors in PostgreSQL.

- **Why it is used:** You need an index that your RAG pipeline can query.
- **When to use it:** Azure AI Search when you want managed hybrid search and Azure IAM. PGVector when SQL is already the system of record and you want one less service.
- **Trade-offs:** Search is another Azure resource and pricing SKU. PGVector keeps ops in Postgres but you build more of the search features yourself.

#### Courses (in order)

Complete these after the glossary. Each link opens that module.

1. [Develop a generative AI chat app with Microsoft Foundry](https://learn.microsoft.com/en-us/training/modules/foundry-sdk/)
2. [Optimize generative AI model performance with Microsoft Foundry](https://learn.microsoft.com/en-us/training/modules/optimize-generative-ai-model-performance/) — includes grounding with RAG
3. [Select, deploy, and evaluate Microsoft Foundry models](https://learn.microsoft.com/en-us/training/modules/model-catalog-evaluate/)

#### Build

- [ ] Provision Azure OpenAI and Azure AI Search using Terraform
- [ ] Build an end-to-end RAG solution
- [ ] Connect LangGraph agents using Azure workload identity
- [ ] Implement evaluation metrics for retrieval quality and answer quality

</details>

---

### Phase 6: Enterprise Integration Edge (Boomi)

<details>
<summary>Open Phase 6 — overview, glossary, courses, build</summary>

**Goal:** Design the boundaries between systems: events, messaging, outbox, saga, CQRS, and a written design. Boomi on AKS is how you connect them.

**Feeds:** [Portfolio Project 3](#project-3-enterprise-ai-integration-platform)

#### Overview

Enterprise systems already emit events (an order created, a customer updated). You do not poll them with a cron job if you can subscribe. This phase is messaging plus Boomi: Atom or Molecule on AKS receives a webhook, maps JSON/XML, calls the AI API, and writes the result back. Sync versus async is the first cut; a queue plus an outbox, a saga, or CQRS is how you keep that async work consistent. Queues versus pub/sub, and dead-letter queues, are the other decisions. Document the result with C4 diagrams and ADRs so another engineer can understand it. Read the glossary, then take the courses in order.

#### Concept glossary

##### Messaging

###### Events

A record that something happened, such as `OrderCreated`.

- **Why it is used:** Other systems can react without being called directly.
- **When to use it:** When several consumers may care that a business fact occurred.
- **Trade-offs:** Event flows are harder to trace than a single request.
- **Learn more:** [Event-driven architecture style](https://learn.microsoft.com/en-us/azure/architecture/guide/architecture-styles/event-driven).

###### Producer / consumer

Producers publish; consumers react.

- **Why it is used:** The announcer should not know every listener.
- **When to use it:** Event-driven and integration architectures (Boomi → AI → ERP).
- **Trade-offs:** Consumers must handle retries, duplicates, and failure.
- **Learn more:** [Event-driven architecture style](https://learn.microsoft.com/en-us/azure/architecture/guide/architecture-styles/event-driven).

###### Synchronous vs asynchronous

Sync: call and wait. Async: hand work off and continue.

- **Why it is used:** Some calls need an immediate answer; others should not block the caller.
- **When to use it:** Sync for “create this now and return the id.” Async for emails, enrichment, and long AI runs.
- **Trade-offs:** Sync couples availability. Async means eventual consistency and harder debugging.
- **Learn more:** [Interservice communication](https://learn.microsoft.com/en-us/azure/architecture/microservices/design/interservice-communication).

###### Message queue

A buffer: one producer, competing consumers process later.

- **Why it is used:** Producer and consumer need not be up at the same time.
- **When to use it:** Work that can wait, or where the downstream system can fail for a while.
- **Trade-offs:** Extra infrastructure; duplicates, ordering, and monitoring.
- **Learn more:** [Asynchronous messaging options](https://learn.microsoft.com/en-us/azure/architecture/guide/technology-choices/messaging).

###### Publish / subscribe

One event, many independent subscribers.

- **Why it is used:** Several systems should react to the same fact.
- **When to use it:** Fan-out (notify CRM, warehouse, and AI from one `OrderCreated`).
- **Trade-offs:** Harder to see the full flow.
- **Learn more:** [Asynchronous messaging options](https://learn.microsoft.com/en-us/azure/architecture/guide/technology-choices/messaging).

###### Dead-letter queue

Storage for messages that cannot be processed.

- **Why it is used:** Poison messages should not vanish or block the healthy queue.
- **When to use it:** Any reliable integration or Service Bus / Boomi workload.
- **Trade-offs:** You must watch the DLQ and have a reprocess plan.
- **Learn more:** [Service Bus dead-letter queues](https://learn.microsoft.com/en-us/azure/service-bus-messaging/service-bus-dead-letter-queues).

###### Transactional outbox

Write the business change and the event in the same database transaction, then publish the event from that record.

- **Why it is used:** Saving the row and then publishing can lose the event if the process dies between the two writes.
- **When to use it:** When a state change must reliably notify another system.
- **Trade-offs:** A publisher process, and consumers must tolerate duplicates.
- **Learn more:** [CQRS pattern](https://learn.microsoft.com/en-us/azure/architecture/patterns/cqrs).

###### Saga

A multi-step business process in which each step can fail and needs a compensating action.

- **Why it is used:** One distributed transaction across services is not available.
- **When to use it:** When a business outcome needs several services, and a later step can force an earlier step to undo.
- **Trade-offs:** Compensation logic, and a harder path to see the whole process.
- **Learn more:** [Event-driven architecture style](https://learn.microsoft.com/en-us/azure/architecture/guide/architecture-styles/event-driven).

###### CQRS

Separate the write model from a read model when their shapes or scale differ.

- **Why it is used:** The query that serves a screen is often not the shape of the transaction that changed the data.
- **When to use it:** When reads and writes diverge enough that one model fights both jobs.
- **Trade-offs:** The read side lags the write, and you now have two models to keep aligned.
- **Learn more:** [CQRS pattern](https://learn.microsoft.com/en-us/azure/architecture/patterns/cqrs).

##### Documentation

###### C4 model

Context, Container, Component, and Code views of a system.

- **Why it is used:** Different people need different levels of detail.
- **When to use it:** Explaining Project 3 (and earlier projects) to someone else.
- **Trade-offs:** Diagrams go stale if you do not update them.
- **Learn more:** [C4 model](https://c4model.com/).

###### ADRs

Architecture Decision Records: short docs of a choice, context, and consequences.

- **Why it is used:** Six months later you will not remember why you picked Molecule or Service Bus.
- **When to use it:** Each significant trade-off (AKS vs App Service, Search vs PGVector).
- **Trade-offs:** Process overhead if you ADR trivial choices.
- **Learn more:** [Architecture decision records](https://adr.github.io/).

#### Courses (in order)

Complete these after the glossary. Each link opens that procedure or module.

1. [Queue and process AI operations with Azure Service Bus](https://learn.microsoft.com/en-us/training/modules/queue-process-operations-service-bus/)
2. [Installing a cloud cluster with elastic scaling in Kubernetes (Boomi)](https://help.boomi.com/docs/Atomsphere/Integration/Atom,%20Molecule,%20and%20Atom%20Cloud%20setup/int-Installing_a_cloud_cluster_with_elastic_scaling_in_kubernetes)
3. [Runtime cluster system requirements (Boomi Molecule)](https://help.boomi.com/docs/Atomsphere/Integration/Atom,%20Molecule,%20and%20Atom%20Cloud%20setup/r-atm-Molecule_system_requirements_41f9a675-ab11-4f3b-bf51-1655394aba5b)
4. [Boomi Runtime Management](https://help.boomi.com/docs/Atomsphere/Integration/Integration%20management/c-atm-Atom_Management_b38a3a90-d7f6-4df0-8c00-e75a178dfdfa)

#### Build

- [ ] Deploy a Boomi Atom or Molecule cluster onto AKS
- [ ] Create an integration flow that accepts enterprise webhooks
- [ ] Route payloads to a LangGraph AI service running on AKS
- [ ] Write AI-enriched responses back into enterprise systems

</details>

---

## Portfolio Projects

Three projects, each building on the last. Start a project only after the phases that feed it.

### Project 1: Cloud-Native Microservice

**Start after:** Phases 1–4.

```text
Python API
  → Docker
  → Terraform (AKS + ACR)
  → GitHub Actions pipeline
```

#### Deliverables

- Containerised API
- Infrastructure as Code
- CI/CD pipeline
- AKS deployment

### Project 2: Cloud-Native Stateful AI Platform

**Start after:** Phase 5 (LangGraph work from Phase 1 carries forward).

```text
LangGraph agents
  → Azure OpenAI
  → Azure AI Search
  → Workload identity
```

#### Deliverables

- Stateful multi-agent workflow
- Enterprise RAG system
- Azure OpenAI integration
- Azure AI Search integration

### Project 3: Enterprise AI Integration Platform

**Start after:** Phase 6.

```text
Enterprise event
  → Boomi Molecule on AKS
  → LangGraph AI service
  → Enterprise system update
```

#### Deliverables

- Event-driven integration
- AI middleware layer
- Enterprise system automation
- End-to-end AI workflow

---

## Portfolio Case Study Documentation Standard

Every repository should include a production-grade `README.md` containing the following. Use the Phase 6 C4 and ADR glossary when you write this.

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
- Relational vs key-value for a hot read
- A sync call vs a queue plus an outbox

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
