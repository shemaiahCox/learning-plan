# Software Engineer, Cloud-Native and AI Roadmap

Version 5.0. One evolving application from local development to Azure, production AI, and enterprise integration.

---

## Contents

- [How to use this plan](#how-to-use-this-plan)
- [Current status](#current-status)
- [Progress](#progress)
- [Phases](#phases)
- [Portfolio](#portfolio)
- [Monthly review](#monthly-review)

---

## How to use this plan

Work on **one portfolio application** across all phases. Finish a phase’s **Build** and **Evidence** before you open the next phase. There is no week-by-week schedule.

- Tick items as you complete them and **commit** progress to Git.
- Tick **Phase complete** only when every required **Build** and **Evidence** item in that phase is done.
- **Optional** items support integration practice (n8n); they do not replace the main build.
- Out of scope: specialist algorithms, a second cloud, and Kubernetes until a real workload needs a cluster.

**n8n (optional):** Phase 1 — webhook to API and DB; Phase 2 — cached vs uncached read and timeout branch; Phase 6 — retries and failed call. Skip n8n for structure, tests, Azure, Terraform, Kubernetes, and model evaluation. n8n does not replace Boomi.

---

## Current status

| Item | Status |
| --- | --- |
| **Active phase** | [Phase 1 — Application architecture](#phase-1-application-architecture) |
| [Docker Get Started workshop](https://docs.docker.com/get-started/workshop/) | Done (training) |
| **n8n** | In progress (learning) |
| **Phase 1 application packaged in Docker** | Not done yet — training ≠ packaged app |

**Next focus:** Python API, tests, migrations, LangGraph in the app, then a `Dockerfile` and Compose for local run.

---

## Progress

Tick when the phase is fully complete (all required Build + Evidence).

- [ ] [Phase 1 — Application architecture](#phase-1-application-architecture)
- [ ] [Phase 2 — Performance](#phase-2-performance)
- [ ] [Phase 3 — Azure](#phase-3-azure)
- [ ] [Phase 4 — Delivery](#phase-4-delivery)
- [ ] [Phase 5 — AI](#phase-5-ai)
- [ ] [Phase 6 — Integration](#phase-6-integration)

---

## Phases

Each phase follows: **Outcome → Learn → Courses → Build → Evidence → Phase complete**. Open the section for detail.

---

### Phase 1: Application architecture

<details open>
<summary>Phase 1 — one application you can change without splitting it</summary>

#### Outcome

One deployable **Python API** with clear module boundaries, **auth**, **migrations**, **tests**, and a **LangGraph** workflow inside the same app.

**Done when:** a change in one module does not force a rewrite of the others; secrets and credentials are not in source control; you have an ADR explaining why the app stays a modular monolith.

#### Learn

##### Modular monolith

One deployable app, divided into modules. SOLID and dependency injection keep boundaries replaceable.

- **Why:** Change a part without splitting into services prematurely.
- **When:** This phase’s API. Revisit split only if Phase 6 proves independent deployability is worth the cost.
- **Trade-off:** Modules are not deployed separately; boundaries need discipline.
- **Learn more:** [Architecture styles](https://learn.microsoft.com/en-us/azure/architecture/guide/architecture-styles/)

##### API contract

REST, validation, pagination, idempotency. The contract is what n8n and later Boomi call.

- **Why:** Predictable send, retry, and error behaviour for integrators.
- **When:** Every endpoint.
- **Trade-off:** Versioning, validation, and duplicate detection add work.
- **Learn more:** [Web API design best practices](https://learn.microsoft.com/en-us/azure/architecture/best-practices/api-design)

##### Data and migrations

Schema, transactions, indexes, and store choice. **Migrations** version the schema the same way Git versions code.

- **Why:** The API needs a reliable system of record; deploys must not rely on manual SQL.
- **When:** Relational for relational data; other stores only with a written reason.
- **Trade-off:** Migrations must be backward-compatible or coordinated with deploys.
- **Learn more:** [Understand data store models](https://learn.microsoft.com/en-us/azure/architecture/data-guide/technology-choices/understand-data-store-models)

##### Authentication and authorization

Who may call the API (authN) and what they may do (authZ). Start simple (API keys or JWT); grow with Entra in Phase 3.

- **Why:** Unauthenticated APIs are not production-shaped.
- **When:** Before you expose the app beyond localhost.
- **Trade-off:** Token handling and role design take ongoing care.
- **Learn more:** [Microsoft identity platform](https://learn.microsoft.com/en-us/entra/identity-platform/v2-overview)

##### Where state lives

The HTTP layer stays stateless. State lives in the database or LangGraph checkpoint store.

- **Why:** Replace an instance without losing work.
- **When:** From the first version.
- **Trade-off:** The store is a hard dependency.
- **Learn more:** [Design principles](https://learn.microsoft.com/en-us/azure/architecture/guide/design-principles/)

##### Testing pyramid

Unit tests for logic, integration tests for DB and HTTP, contract tests for stable API shapes.

- **Why:** Refactoring and later phases depend on fast feedback.
- **When:** As you build each feature, not at the end.
- **Trade-off:** Integration tests need fixtures and isolation.
- **Learn more:** [pytest documentation](https://docs.pytest.org/en/stable/)

##### Packaging: Dockerfile and Compose

A **Dockerfile** defines the app image. **Docker Compose** runs the app plus local dependencies (database, cache) for development.

- **Why:** Same artefact locally and in Azure later.
- **When:** After the app runs on the host; Compose wires dependencies.
- **Trade-off:** Compose is for dev; production host comes in Phase 3.
- **Learn more:** [Docker Get Started workshop](https://docs.docker.com/get-started/workshop/)

##### Quality gates locally

Format, lint, and type-check before commit or in CI later.

- **Why:** Consistent style and fewer silent type bugs.
- **When:** Before the first shared branch or PR.
- **Trade-off:** Tooling setup once; rules must stay enforced.
- **Learn more:** [Python typing](https://docs.python.org/3/library/typing.html)

##### Latency, throughput, and rough sizing

Estimate RPS, storage, and bandwidth before adding cache, queue, or scale-out.

- **Why:** Designs you cannot size are guesses.
- **When:** Before Phase 2 infrastructure additions.
- **Trade-off:** Estimates go stale; avoid false precision.
- **Learn more:** [Latency versus throughput](https://github.com/donnemartin/system-design-primer#latency-vs-throughput)

##### Architecture decision record (ADR)

Short note: context, choice, consequences. First ADR: why this stays one deployable application.

- **Learn more:** [Architecture decision records](https://adr.github.io/)

#### Courses

- [ ] [Shell Scripts for Beginners (KodeKloud)](https://kodekloud.com/courses/shell-scripts-for-beginners/) — paid
- [ ] [Introduction to Git (Microsoft Learn)](https://learn.microsoft.com/en-us/training/modules/intro-to-git/)
- [x] [Docker Get Started workshop](https://docs.docker.com/get-started/workshop/)
- [ ] [Foundation: Introduction to LangGraph – Python (LangChain Academy)](https://academy.langchain.com/courses/intro-to-langgraph)

#### Build

- [ ] Local setup scripts (shell)
- [ ] Python API with modular structure and dependency injection at boundaries
- [ ] Database schema with **versioned migrations**
- [ ] **Authentication** on protected routes; document who may call what
- [ ] **Unit**, **integration**, and **API contract** tests for main behaviour
- [ ] **Lint, format, and type-check** in the repo (document how to run)
- [ ] LangGraph workflow inside the same application
- [ ] **`Dockerfile`** for the API image
- [ ] **Docker Compose** for local app + database (and dependencies)
- [ ] ADR: stay a modular monolith
- [ ] Code on GitHub
- [ ] *Optional:* n8n webhook → API → database row *(in progress: n8n learning)*

#### Evidence

- [ ] Short README: run locally, run tests, run with Compose
- [ ] Link or path to first ADR in the repo
- [ ] One paragraph: module boundaries and what you refused to split

#### Phase complete

- [ ] **Phase 1 complete**

</details>

---

### Phase 2: Performance

<details>
<summary>Phase 2 — a measured fix, not extra infrastructure by habit</summary>

#### Outcome

Find the slow path in the Phase 1 app and fix what measurement points at. Add cache, CDN, or scale-out only when the numbers justify it.

**Done when:** you cite a profile or benchmark, name the bottleneck, and explain why the fix matches it.

#### Learn

##### Bottlenecks

Profile before new components. Slowness may be query, chatty IO, or per-request work.

- **Learn more:** [Performance versus scalability](https://github.com/donnemartin/system-design-primer#performance-vs-scalability)

##### Queries and connections

Indexes for real queries; connection pooling instead of connect-per-request.

- **Learn more:** [SQL Server index design guide](https://learn.microsoft.com/en-us/sql/relational-databases/sql-server-index-design-guide)

##### Cache after measurement

Cache-aside, TTL, invalidation. HTTP cache and CDN for public/static content.

- **Learn more:** [Cache-Aside pattern](https://learn.microsoft.com/en-us/azure/architecture/patterns/cache-aside)

##### Stateless instances and load balancing

Scale app processes only when session state is externalised.

- **Learn more:** [Design to scale out](https://learn.microsoft.com/en-us/azure/architecture/guide/design-principles/scale-out)

##### Rate limiting and backpressure

429, `Retry-After`, token bucket — protect your API and upstream dependencies.

- **Learn more:** [Rate Limiting pattern](https://learn.microsoft.com/en-us/azure/architecture/patterns/rate-limiting-pattern)

#### Courses

No new course. Measure the Phase 1 application.

#### Build

- [ ] Profile one slow request; write the bottleneck
- [ ] Fix bottleneck in code or query
- [ ] Add cache **only if** justified; document TTL and invalidation
- [ ] *Optional:* n8n compares uncached vs cached read; timeout branch

#### Evidence

- [ ] Before/after numbers (latency or throughput) in the repo or ADR
- [ ] Note what you **did not** add and why measurement did not require it

#### Phase complete

- [ ] **Phase 2 complete**

</details>

---

### Phase 3: Azure

<details>
<summary>Phase 3 — Container Apps, identity, secrets, and monitoring</summary>

#### Outcome

Run the same container on **Azure Container Apps** with **managed identity**, secrets in **Key Vault**, observable logs, and **cost controls**. One intentional manual deploy before Terraform in Phase 4.

**Done when:** the app runs in Azure with no long-lived secrets in config; you can read health-related logs; budget or teardown steps are documented.

#### Learn

##### Identity and least privilege

Entra ID for callers and services; RBAC scoped to what the app actually uses.

- **Learn more:** [Microsoft identity platform](https://learn.microsoft.com/en-us/entra/identity-platform/v2-overview)

##### Secrets and managed identity

Key Vault + managed identity instead of connection strings in settings.

- **Learn more:** [Managed identities](https://learn.microsoft.com/en-us/entra/identity/managed-identities-azure-resources/overview)

##### Managed database

Move the system of record to a managed offering (e.g. Azure Database for PostgreSQL).

- **Learn more:** [Understand data store models](https://learn.microsoft.com/en-us/azure/architecture/data-guide/technology-choices/understand-data-store-models)

##### Container Apps

Host for this roadmap’s container image. AKS only in Phase 6 if required.

- **Learn more:** [Deploy containers to Azure Container Apps](https://learn.microsoft.com/en-us/training/modules/deploy-containers-azure-container-apps/)

##### Azure Monitor and cost

Logs and metrics for deploy verification; **budgets, tags, and a teardown checklist** so lab spend stays controlled.

- **Learn more:** [Azure Monitor overview](https://learn.microsoft.com/en-us/azure/azure-monitor/fundamentals/overview) · [Cost management](https://learn.microsoft.com/en-us/azure/cost-management-billing/costs/cost-mgt-best-practices)

##### Well-Architected review

Reliability, security, cost, operations, performance — after first deploy and again after Phase 4.

- **Learn more:** [Azure Well-Architected Framework](https://learn.microsoft.com/en-us/azure/well-architected/)

#### Courses

- [ ] [Describe cloud concepts](https://learn.microsoft.com/en-us/training/paths/microsoft-azure-fundamentals-describe-cloud-concepts/)
- [ ] [Describe Azure architecture and services](https://learn.microsoft.com/en-us/training/paths/azure-fundamentals-describe-azure-architecture-services/)
- [ ] [Configure and secure Azure Key Vault](https://learn.microsoft.com/en-us/training/modules/configure-secure-key-vault/)
- [ ] [Secure your Azure resources with Azure RBAC](https://learn.microsoft.com/en-us/training/modules/secure-azure-resources-with-rbac/)
- [ ] [Deploy containers to Azure Container Apps](https://learn.microsoft.com/en-us/training/modules/deploy-containers-azure-container-apps/)
- [ ] [Introduction to the Azure Well-Architected Framework](https://learn.microsoft.com/en-us/training/modules/azure-well-architected-introduction/)

#### Build

- [ ] Azure CLI, resource group, **resource tags**
- [ ] Key Vault secrets; app reads them via **managed identity**
- [ ] Least-privilege **RBAC** for the app identity
- [ ] Managed database; run Phase 1 **migrations** against it
- [ ] Deploy API container to **Container Apps**
- [ ] **Entra-secured** or documented auth for the deployed API
- [ ] Logs in **Azure Monitor**; note where to check after a deploy
- [ ] **Budget alert** or documented cost cap; **teardown** steps for lab resources

#### Evidence

- [ ] Screenshot or CLI transcript: successful deploy without secrets in repo
- [ ] Checklist: which identity can access which resource
- [ ] Well-Architected notes (even brief) for security and cost pillars

#### Phase complete

- [ ] **Phase 3 complete**

</details>

---

### Phase 4: Delivery

<details>
<summary>Phase 4 — pipeline, staging, rollback, and recovery</summary>

#### Outcome

**GitHub Actions** builds, tests, and deploys to Azure using **OIDC** (no long-lived pipeline secrets). Environment is **Terraform-managed**. Staging or slot-based deploy, **safe migrations**, rollback path, observability, load test, and a written recovery for one broken dependency.

**Done when:** a merge to main can deploy through the pipeline; you have load-test numbers; you have a recovery note; health checks and Application Insights serve different purposes and both exist.

#### Learn

##### CI/CD with GitHub Actions

Build, test, deploy on every change. This plan standardises on **GitHub Actions** (not Azure Pipelines) unless your employer mandates otherwise.

- **Learn more:** [Introduction to GitHub Actions](https://learn.microsoft.com/en-us/training/modules/introduction-to-github-actions/) · [Use GitHub Actions to connect to Azure](https://learn.microsoft.com/en-us/azure/developer/github/connect-from-azure)

##### Infrastructure as code

Terraform for resource group, registry, Key Vault, Container Apps environment — after you understood Phase 3 manually.

- **Learn more:** [Terraform Get Started on Azure (HashiCorp)](https://developer.hashicorp.com/terraform/tutorials/azure-get-started)

##### Health probes vs telemetry

**Liveness/readiness probes** tell the platform whether to route traffic. **Application Insights** (metrics, traces, logs) tells you what happened in production. Both are required; neither replaces the other.

- **Learn more:** [Health Endpoint Monitoring pattern](https://learn.microsoft.com/en-us/azure/architecture/patterns/health-endpoint-monitoring) · [Enable Azure Monitor OpenTelemetry](https://learn.microsoft.com/en-us/azure/azure-monitor/app/opentelemetry-enable)

##### Staging, rollback, and migrations

Deploy to a non-production revision or environment first. **Rollback** = previous image revision. **Migrations** run in a controlled step; document backward-compatible rules.

- **Learn more:** [What is continuous delivery?](https://learn.microsoft.com/en-us/devops/deliver/what-is-continuous-delivery)

##### Retries, timeouts, circuit breaking

Every outbound call has a timeout; retries only where idempotent.

- **Learn more:** [Transient fault handling](https://learn.microsoft.com/en-us/azure/architecture/best-practices/transient-faults)

##### Backup, load, and cost

RPO/RTO awareness; load test; know monthly run cost.

- **Learn more:** [Disaster recovery](https://learn.microsoft.com/en-us/azure/well-architected/reliability/disaster-recovery)

#### Courses

- [ ] [Introduction to GitHub Actions](https://learn.microsoft.com/en-us/training/modules/introduction-to-github-actions/)
- [ ] [Terraform Get Started on Azure (HashiCorp)](https://developer.hashicorp.com/terraform/tutorials/azure-get-started)
- [ ] [Enable Azure Monitor OpenTelemetry](https://learn.microsoft.com/en-us/azure/azure-monitor/app/opentelemetry-enable)

#### Build

- [ ] Tests on pull requests (same gates as local)
- [ ] **OIDC** federated credential; pipeline deploys without stored Azure client secret
- [ ] Build and push image to **Azure Container Registry**
- [ ] **Terraform** recreates Phase 3 environment
- [ ] Pipeline: **staging** deploy → smoke test → **production** deploy (or documented equivalent)
- [ ] **Rollback** procedure documented and exercised once
- [ ] **Migration step** in pipeline or runbook
- [ ] **Health endpoints** wired to Container Apps probes
- [ ] **Application Insights**: logs, metrics, traces; at least one alert
- [ ] Container **image vulnerability scan** (registry or workflow)
- [ ] Load-test the API; break one dependency; write **recovery** steps

#### Evidence

- [ ] Link to a green pipeline run from a merge
- [ ] Load-test summary (RPS, p95 latency, or error rate)
- [ ] Recovery note for the dependency you broke
- [ ] ADR or doc: GitHub Actions + OIDC vs stored secrets

#### Phase complete

- [ ] **Phase 4 complete**

</details>

---

### Phase 5: AI

<details>
<summary>Phase 5 — retrieval, grounded answers, evaluation, and AI safety</summary>

#### Outcome

Add **RAG** and **Azure OpenAI** to the existing LangGraph agent. Call models with **managed identity**. Measure retrieval and answer quality on a **small labelled set**. Address **prompt injection**, **document-level permissions**, and **tool least privilege**.

**Done when:** answers cite your data; you publish retrieval and answer metrics; you document what an attacker could not do via the agent.

#### Learn

##### Agents and tool calling

LangGraph for visible steps and state; restrict tools to minimum required operations.

- **Learn more:** [LangGraph overview](https://docs.langchain.com/oss/python/langgraph/overview)

##### Retrieval-augmented generation

Fetch relevant text into the prompt; handle indexing and refresh.

- **Learn more:** [Retrieval augmented generation overview](https://learn.microsoft.com/en-us/azure/search/retrieval-augmented-generation-overview)

##### Vector search

Azure AI Search vs PGVector — choose and record in an ADR.

- **Learn more:** [Vector search overview](https://learn.microsoft.com/en-us/azure/search/vector-search-overview)

##### Evaluation

Labelled questions: precision/recall on retrieval, groundedness or judge on answers.

- **Learn more:** [Select, deploy, and evaluate models](https://learn.microsoft.com/en-us/training/modules/model-catalog-evaluate/)

##### AI safety for production

Prompt injection mitigations, per-user document ACLs, no secrets in prompts, audit logging for tool calls.

- **Learn more:** [Azure OpenAI safety](https://learn.microsoft.com/en-us/azure/ai-foundry/openai/concepts/safety-system-message-templates)

##### Where the model runs

Azure OpenAI for this system; document quota and cost.

- **Learn more:** [Develop a generative AI chat app with Microsoft Foundry](https://learn.microsoft.com/en-us/training/modules/foundry-sdk/)

#### Courses

- [ ] [Develop a generative AI chat app with Microsoft Foundry](https://learn.microsoft.com/en-us/training/modules/foundry-sdk/)
- [ ] [Optimize generative AI model performance with Microsoft Foundry](https://learn.microsoft.com/en-us/training/modules/optimize-generative-ai-model-performance/) — includes RAG
- [ ] [Select, deploy, and evaluate Microsoft Foundry models](https://learn.microsoft.com/en-us/training/modules/model-catalog-evaluate/)

#### Build

- [ ] Terraform: Azure OpenAI + search (or PGVector path documented)
- [ ] Retrieval path into LangGraph agent
- [ ] Model calls via **managed identity** (no API keys in app settings)
- [ ] **10–20 labelled questions** with expected sources or answer traits
- [ ] Metrics table: retrieval hit rate, groundedness or human spot-check score
- [ ] **Prompt-injection** test case documented (what you tried, what happened)
- [ ] **Document permissions** enforced in retrieval path
- [ ] Tools limited to required scopes; log tool invocations

#### Evidence

- [ ] Published evaluation summary in repo
- [ ] ADR: search technology and model host
- [ ] Security note: trust boundaries for user content vs system prompts

#### Phase complete

- [ ] **Phase 5 complete**

</details>

---

### Phase 6: Integration

<details>
<summary>Phase 6 — queues, Boomi, failures; AKS only if required</summary>

#### Outcome

Accept external work, survive slow or failing partners, and keep the system of record consistent. Practice with n8n locally; implement with **Service Bus** and **Boomi**. **AKS** only if Molecule or a second independently deployed service requires it.

**Done when:** failed partner calls are visible, retryable, and idempotent; dead-letter path is monitored; C4 context diagram exists.

#### Learn

##### Sync, async, and queues

- **Learn more:** [Asynchronous messaging options](https://learn.microsoft.com/en-us/azure/architecture/guide/technology-choices/messaging)

##### Idempotency, retries, dead letters

- **Learn more:** [Service Bus dead-letter queues](https://learn.microsoft.com/en-us/azure/service-bus-messaging/service-bus-dead-letter-queues)

##### Saga and transactional outbox

Multi-step flows and reliable publish-after-commit.

- **Learn more:** [Transactional outbox pattern](https://microservices.io/patterns/data/transactional-outbox.html)

##### Boomi and webhooks

Enterprise runtime for partner flows; n8n as local rehearsal only.

- **Learn more:** [Event-driven architecture style](https://learn.microsoft.com/en-us/azure/architecture/guide/architecture-styles/event-driven)

##### AKS when needed

Stay on Container Apps until cluster ops are justified.

- **Learn more:** [Microservices](https://martinfowler.com/articles/microservices.html)

##### Copies of data (when measured)

Replication and partitioning only after evidence — not before first Azure deploy.

- **Learn more:** [Sharding pattern](https://learn.microsoft.com/en-us/azure/architecture/patterns/sharding)

#### Courses

- [ ] [Queue and process AI operations with Azure Service Bus](https://learn.microsoft.com/en-us/training/modules/queue-process-operations-service-bus/)
- [ ] [Learn Kubernetes basics](https://kubernetes.io/docs/tutorials/kubernetes-basics/) — *if* AKS build applies
- [ ] [Deploy a containerized application on Azure Kubernetes Service](https://learn.microsoft.com/en-us/training/modules/aks-deploy-container-app/1-introduction) — *if* AKS build applies
- [ ] [Boomi: Kubernetes cluster install](https://help.boomi.com/docs/Atomsphere/Integration/Atom,%20Molecule,%20and%20Atom%20Cloud%20setup/int-Installing_a_cloud_cluster_with_elastic_scaling_in_kubernetes)
- [ ] [Boomi Molecule system requirements](https://help.boomi.com/docs/Atomsphere/Integration/Atom,%20Molecule,%20and%20Atom%20Cloud%20setup/r-atm-Molecule_system_requirements_41f9a675-ab11-4f3b-bf51-1655394aba5b)
- [ ] [Boomi Runtime Management](https://help.boomi.com/docs/Atomsphere/Integration/Integration%20management/c-atm-Atom_Management_b38a3a90-d7f6-4df0-8c00-e75a178dfdfa)

#### Build

- [ ] *Optional:* n8n — retry and dead-letter branch
- [ ] **Service Bus** queue/topic with **idempotent** consumer
- [ ] **Transactional outbox** or documented alternative for publish-after-DB-write
- [ ] Boomi: webhook in → LangGraph API → write back
- [ ] Monitor dead-letter queue; runbook for reprocessing
- [ ] **AKS:** deploy only if required; else **ADR** — Container Apps remains sufficient
- [ ] [C4 context](https://c4model.com/) diagram for the full flow

#### Evidence

- [ ] Trace or screenshot: one message through success and one through retry/DLQ
- [ ] ADR: sync vs async boundary; AKS yes/no
- [ ] C4 diagram committed

#### Phase complete

- [ ] **Phase 6 complete**

</details>

---

## Portfolio

One system, three stages. Do not start a stage until its phases are done. After **each phase**, you may commit incremental evidence (diagram snippet, ADR, or metric) — you do not need to wait until Stage 1.

**Every stage includes:** problem statement, diagram, ADR for the big choice, measured result, and “first place I look when unhealthy” (log, metric, or alert).

### Incremental evidence (tick as you go)

- [ ] Phase 1: local run + ADR in repo
- [ ] Phase 2: before/after performance note
- [ ] Phase 3: Azure architecture one-pager or diagram
- [ ] Phase 4: pipeline + load-test + recovery note
- [ ] Phase 5: evaluation summary
- [ ] Phase 6: C4 context + integration failure story

### Stage 1: The running application

**After:** Phases 1–4.

API, data, Container Apps, GitHub Actions pipeline, load test, recovery note.

- [ ] **Stage 1 portfolio complete**

### Stage 2: Retrieval and agents

**After:** Phase 5.

Same system plus RAG, Azure OpenAI, managed identity, evaluation numbers.

- [ ] **Stage 2 portfolio complete**

### Stage 3: The integration

**After:** Phase 6.

Queue or Boomi flow, handled failure, AKS or stay-on-Container-Apps ADR.

- [ ] **Stage 3 portfolio complete**

---

## Monthly review

Industry and roadmap audits are **advisory only**. They do not edit this file automatically.

Point your automation at **[LEARNING-PLAN-SCAN.md](LEARNING-PLAN-SCAN.md)**. It reads this `README.md`, posts a short Slack summary with numbered recommendations, and waits for you to approve changes via a PR.

DevPulse (`devpulse-agent.md`) stays separate: daily language and runtime refresh for assessments and code reading — not part of the monthly roadmap audit.