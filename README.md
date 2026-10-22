# Software Engineer, Cloud-Native and AI Roadmap

Version 4.0. A path from a working application to a system you can deploy, monitor, and change on Azure.

---

## Contents

- [Start here](#start-here)
- [Phases](#phases)
- [Portfolio](#portfolio)

---

## Start here

This plan is for a software engineer who wants to ship scalable applications on Azure, then add production AI and enterprise integration. Architecture is how you organise the parts. Cloud engineering is how you deploy, secure, and run them. You practice both on one system.

Understand the problem, implement it, and write down what you gave up. Finish a phase's build before you start the next one. There is no week-number deadline.

Specialist algorithms and a second cloud are out of this plan. Kubernetes waits until a workload needs a cluster.

### Already underway

- **Docker** is Phase 1. It packages the application. Keep going, and still do the API, data, and tests in that phase.
- **LangChain** is the Phase 1 agent, through the LangGraph course. Use it locally in that app. Hosted models, retrieval, and evaluation are Phase 5.
- **n8n** is optional proof when a concept is about one part calling another. The phase build comes first. n8n does not replace Boomi.

Use n8n in Phase 1 (webhook to your API and database), Phase 2 (a slow read versus a cached read, plus a timeout branch), and Phase 6 (retries and a failed call). Skip it for code structure, tests, Azure hosting, Terraform, Kubernetes, and model evaluation.

### The path

1. [Application architecture](#phase-1-application-architecture) — one application you can change without splitting it
2. [Performance](#phase-2-performance) — a measured fix, not extra infrastructure by habit
3. [Azure](#phase-3-azure) — Container Apps, identity, secrets, and monitoring
4. [Delivery](#phase-4-delivery) — a pipeline, evidence when something breaks, and a recovery note
5. [AI](#phase-5-ai) — agents, retrieval, and an evaluation of the answers
6. [Integration](#phase-6-integration) — a workflow that survives a slow partner, and Kubernetes only if a cluster is required

Finished means you can design, deploy, monitor, and change that one system, and explain when it needs a cache, a queue, or a cluster.

---

## Phases

Open one phase at a time. Work from Goal through Build.

---

### Phase 1: Application architecture

<details>
<summary>Phase 1 — one application you can change without splitting it</summary>

#### Goal

Build one deployable application: a Python API with a clear shape, tests, and a LangGraph agent inside it. Docker packages it.

Done when a change to one module does not force a rewrite of the others, and you have written down why it is still one application.

#### Key Concepts

##### Modular monolith

One deployable app, divided into modules. SOLID and dependency injection are how those modules stay replaceable.

- **Why:** You can change a part without splitting the system into services.
- **When:** This phase's API. Split later only if Phase 6 shows independent deployability is worth the failures.
- **Trade-off:** Modules are not deployed separately, and the boundaries need discipline.
- **Learn more:** [Architecture styles](https://learn.microsoft.com/en-us/azure/architecture/guide/architecture-styles/)

##### API contract

REST, HTTP methods, validation, pagination, and idempotency. The contract is what n8n, and later Boomi, will call.

- **Why:** Callers need a predictable way to send and retry work.
- **When:** Every endpoint on this API.
- **Trade-off:** Versioning, validation, and duplicate detection add work.
- **Learn more:** [Web API design best practices](https://learn.microsoft.com/en-us/azure/architecture/best-practices/api-design)

##### Data

Schema, transactions, indexes, and the choice between relational tables and a document or key-value store.

- **Why:** The API needs a system of record with relationships, or a shape that tables fight.
- **When:** Relational for orders, customers, and submissions. Key-value for a hot lookup. Document when one aggregate varies and you do not need multi-row transactions.
- **Trade-off:** Relational schemas are rigid. Other stores give up joins or transactions.
- **Learn more:** [Understand data store models](https://learn.microsoft.com/en-us/azure/architecture/data-guide/technology-choices/understand-data-store-models)

##### Where state lives

The HTTP edge does not keep session data. State sits in the database or in the LangGraph checkpoint.

- **Why:** You can replace an instance without losing the user's work.
- **When:** This API, from the first version.
- **Trade-off:** The store becomes a dependency.
- **Learn more:** [Design principles](https://learn.microsoft.com/en-us/azure/architecture/guide/design-principles/)

##### Latency, throughput, and a rough size

Latency is how long one request takes. Throughput is how many you finish in a period. Estimate requests per second, storage, and bandwidth before you pick services.

- **Why:** A design you cannot size is a guess.
- **When:** Before you add a cache, a queue, or a second instance.
- **Trade-off:** Estimates go stale, and false precision wastes time.
- **Learn more:** [Latency versus throughput](https://github.com/donnemartin/system-design-primer#latency-vs-throughput)

##### Architecture decision record

A short note of a choice, the context, and the consequences. The first one is why this app stays a monolith.

- **Why:** Later you will not remember why you refused to split it.
- **When:** Each significant choice, starting in this phase.
- **Trade-off:** Trivial choices do not need a record.
- **Learn more:** [Architecture decision records](https://adr.github.io/)

#### Courses

1. [Shell Scripts for Beginners (KodeKloud)](https://kodekloud.com/courses/shell-scripts-for-beginners/) — paid
2. [Introduction to Git (Microsoft Learn)](https://learn.microsoft.com/en-us/training/modules/intro-to-git/)
3. [Docker Get Started workshop](https://docs.docker.com/get-started/workshop/)
4. [Foundation: Introduction to LangGraph – Python (LangChain Academy)](https://academy.langchain.com/courses/intro-to-langgraph)

#### Build

- [ ] Write shell scripts for local setup
- [ ] Build the Python API and a LangGraph workflow in one deployable app
- [ ] Add tests for the main API behaviour
- [ ] Package the app with Docker Compose
- [ ] Write the ADR for staying a monolith
- [ ] Push the code to GitHub
- [ ] Optional: an n8n webhook that calls the API and writes a row

</details>

---

### Phase 2: Performance

<details>
<summary>Phase 2 — a measured fix, not extra infrastructure by habit</summary>

#### Goal

Find the slow part of the Phase 1 app and fix that part. Add a cache, a CDN, or another instance only when the measurement says the current design is the limit.

Done when you can point at a number, name the bottleneck, and say why the fix matches it.

#### Key Concepts

##### Bottlenecks

Profile the request path before you add components. The slow part might be a query, a chatty API, or the work you do on every call.

- **Why:** Extra infrastructure does not fix a wasteful query.
- **When:** Before every performance change in this phase.
- **Trade-off:** Profiling takes time, and a lab number is not production traffic.
- **Learn more:** [Performance versus scalability](https://github.com/donnemartin/system-design-primer#performance-vs-scalability)

##### Queries and connections

Use indexes for the reads you actually run. Keep a pool of database connections instead of opening one per request.

- **Why:** A full scan and a new connection on every call dominate latency long before you need a second database.
- **When:** After a profile shows the database or connection setup on the slow path.
- **Trade-off:** Indexes speed reads and slow writes. A pool that is too large can exhaust the database.
- **Learn more:** [SQL Server index design guide](https://learn.microsoft.com/en-us/sql/relational-databases/sql-server-index-design-guide)

##### Cache, only after you measure

Keep a hot read in a faster store. Set a TTL, choose what happens on an update, and treat LRU as the usual eviction rule. HTTP caching and a CDN are the same idea, closer to the client, for public or static responses.

- **Why:** The database should not answer the same read on every request.
- **When:** A profile shows a repeated read that can be slightly stale.
- **Trade-off:** Invalidation and stale data. A CDN does not help personalised responses.
- **Learn more:** [Cache-Aside pattern](https://learn.microsoft.com/en-us/azure/architecture/patterns/cache-aside)

##### Stateless instances and load balancing

More copies of the app only work if no copy holds the session. A load balancer spreads requests across those copies.

- **Why:** One process has a ceiling, and a replacement instance should not need local session data.
- **When:** The profile shows the app process, not the database, at its limit.
- **Trade-off:** Sticky sessions fight this design. More copies cost money and need a shared store.
- **Learn more:** [Design to scale out](https://learn.microsoft.com/en-us/azure/architecture/guide/design-principles/scale-out)

##### Rate limiting and backpressure

Cap how fast callers hit you, or how fast you call someone else. Token bucket, leaky bucket, and sliding window are ways to count that cap. Backpressure tells the caller to slow down, for example HTTP 429 and `Retry-After`.

- **Why:** Unlimited retries and bursts take down the dependency or your own app.
- **When:** A public endpoint, or any client of a throttled API.
- **Trade-off:** Real bursts get rejected, and callers must honour the signal.
- **Learn more:** [Rate Limiting pattern](https://learn.microsoft.com/en-us/azure/architecture/patterns/rate-limiting-pattern)

#### Courses

No new workshop. Measure the Phase 1 application.

#### Build

- [ ] Profile one slow request and write down the bottleneck
- [ ] Fix that bottleneck in the app or the query
- [ ] Add a cache only if the measurement justifies it, and note how it expires
- [ ] Optional: an n8n run that compares a repeated read with a cached read, and branches on timeout

</details>

---

### Phase 3: Azure

<details>
<summary>Phase 3 — Container Apps, identity, secrets, and monitoring</summary>

#### Goal

Run the same container on Azure with a managed identity, secrets in Key Vault, and logs you can read. Do this deploy once on purpose. Terraform comes in the next phase.

Done when the app is running on Container Apps and the process does not hold a stored password.

#### Key Concepts

##### Identity

Entra ID says who is calling. RBAC says what that caller may do. Least privilege means the app gets only the roles it uses.

- **Why:** A deployed app that anyone can call, or that can touch every resource, is not finished.
- **When:** The user or service that calls this API, and the app's own identity in Azure.
- **Trade-off:** Narrow roles take longer to get right.
- **Learn more:** [Microsoft identity platform](https://learn.microsoft.com/en-us/entra/identity-platform/v2-overview)

##### Secrets and managed identity

Key Vault holds secrets. A managed identity lets the app read them without a password stored in config.

- **Why:** Connection strings in source control leak.
- **When:** Every secret the container needs.
- **Trade-off:** You now depend on Entra and Key Vault being reachable.
- **Learn more:** [Managed identities](https://learn.microsoft.com/en-us/entra/identity/managed-identities-azure-resources/overview)

##### Managed database

Use a managed database for the system of record instead of a database you patch yourself.

- **Why:** Backups, patching, and capacity become a service setting.
- **When:** The Phase 1 database moves to Azure with the app.
- **Trade-off:** You give up full control of the server, and you pay for the tier you pick.
- **Learn more:** [Understand data store models](https://learn.microsoft.com/en-us/azure/architecture/data-guide/technology-choices/understand-data-store-models)

##### Container Apps

Container Apps runs the Docker image without a cluster to administer. App Service fits a non-container app. Functions fit a short job with a trigger. This roadmap's app is already a container, so Container Apps is the host.

- **Why:** You need the same image in Azure before you operate a cluster.
- **When:** This phase. Move to AKS in Phase 6 only if a workload needs a cluster.
- **Trade-off:** You do not control the nodes. A private network is still your job if the data must stay off the public internet.
- **Learn more:** [Deploy containers to Azure Container Apps](https://learn.microsoft.com/en-us/training/modules/deploy-containers-azure-container-apps/)

##### Azure Monitor

Logs and metrics from the running container tell you whether the deploy worked.

- **Why:** A successful CLI command is not the same as a healthy app.
- **When:** As soon as the container is deployed.
- **Trade-off:** Telemetry costs money and can capture secrets if you log carelessly.
- **Learn more:** [Azure Monitor overview](https://learn.microsoft.com/en-us/azure/azure-monitor/fundamentals/overview)

##### Well-Architected review

Check the running app against reliability, security, cost, operations, and performance.

- **Why:** "It deployed" is not the same as a system you can trust.
- **When:** After the first Container Apps deploy, and again after Phase 4.
- **Trade-off:** Improving one pillar can raise cost or complexity.
- **Learn more:** [Azure Well-Architected Framework](https://learn.microsoft.com/en-us/azure/well-architected/)

#### Courses

1. [Describe cloud concepts](https://learn.microsoft.com/en-us/training/paths/microsoft-azure-fundamentals-describe-cloud-concepts/)
2. [Describe Azure architecture and services](https://learn.microsoft.com/en-us/training/paths/azure-fundamentals-describe-azure-architecture-services/)
3. [Configure and secure Azure Key Vault](https://learn.microsoft.com/en-us/training/modules/configure-secure-key-vault/)
4. [Secure your Azure resources with Azure RBAC](https://learn.microsoft.com/en-us/training/modules/secure-azure-resources-with-rbac/)
5. [Deploy containers to Azure Container Apps](https://learn.microsoft.com/en-us/training/modules/deploy-containers-azure-container-apps/)
6. [Introduction to the Azure Well-Architected Framework](https://learn.microsoft.com/en-us/training/modules/azure-well-architected-introduction/)

#### Build

- [ ] Configure the Azure CLI and a resource group
- [ ] Store secrets in Key Vault and read them with a managed identity
- [ ] Give the app a least-privilege RBAC assignment
- [ ] Deploy the API container to Container Apps
- [ ] Read the container logs in Azure Monitor

</details>

---

### Phase 4: Delivery

<details>
<summary>Phase 4 — a pipeline, evidence when something breaks, and a recovery note</summary>

#### Goal

Make the Container Apps environment repeatable, ship a change through a pipeline, and show how you would recover when a dependency fails.

Done when a git push can deploy, and you have a load-test number plus a written recovery for one broken dependency.

#### Key Concepts

##### CI/CD

Every change takes the same path: build, test, and deploy.

- **Why:** Manual deploys drift and hide mistakes.
- **When:** From this phase on.
- **Trade-off:** The pipeline needs its own secrets, maintenance, and a way back.
- **Learn more:** [What is continuous delivery?](https://learn.microsoft.com/en-us/devops/deliver/what-is-continuous-delivery)

##### Infrastructure as code

Describe the resource group, Key Vault, registry, and Container Apps environment in Terraform, after you have deployed them once and understand them.

- **Why:** A clicked environment cannot be reviewed or rebuilt with confidence.
- **When:** The environment from Phase 3.
- **Trade-off:** Another language. Bicep is the Azure-native alternative this plan does not take.
- **Learn more:** [What is infrastructure as code?](https://learn.microsoft.com/en-us/devops/deliver/what-is-infrastructure-as-code)

##### Logs, metrics, traces, and alerts

Logs say what happened. Metrics say how often and how slow. Traces follow one request. Alerts fire when a metric crosses a line you chose.

- **Why:** You cannot fix a production failure from memory.
- **When:** The deployed API.
- **Trade-off:** Cost, noise, and the risk of storing secrets in telemetry.
- **Learn more:** [Azure Monitor overview](https://learn.microsoft.com/en-us/azure/azure-monitor/fundamentals/overview)

##### Health and shutdown

A health check tells the platform when to stop sending traffic. Graceful shutdown finishes the request already in hand.

- **Why:** A deploy or a crash should not cut off work at random.
- **When:** The container you deploy from the pipeline.
- **Trade-off:** A shallow health check stays green while the app is useless.
- **Learn more:** [Design principles](https://learn.microsoft.com/en-us/azure/architecture/guide/design-principles/)

##### Retries and timeouts

Retry a transient failure, wait longer between tries, and stop calling a dependency that is clearly down. Every outbound call needs a timeout.

- **Why:** Networks fail briefly, and a call with no timeout waits forever.
- **When:** Calls to the database, Key Vault, and any partner API.
- **Trade-off:** Naive retries amplify an outage and can duplicate work. A circuit breaker adds thresholds you must tune.
- **Learn more:** [Transient fault handling](https://learn.microsoft.com/en-us/azure/architecture/best-practices/transient-faults)

##### Backup, load, and cost

Know how to restore the database, what load does to latency, and what the environment costs. RPO is how much data you can lose. RTO is how long you can be down.

- **Why:** A system that only works when nothing is wrong is unfinished.
- **When:** Before you call this phase done, and again before you add a second region. A second region is not part of this plan.
- **Trade-off:** Tighter recovery and heavier tests cost money and time.
- **Learn more:** [Architecture strategies for disaster recovery](https://learn.microsoft.com/en-us/azure/well-architected/reliability/disaster-recovery)

#### Courses

1. [Introduction to GitHub Actions](https://learn.microsoft.com/en-us/training/modules/introduction-to-github-actions/)
2. [Create your first pipeline (Azure Pipelines)](https://learn.microsoft.com/en-us/azure/devops/pipelines/create-first-pipeline)
3. [Terraform Get Started on Azure (HashiCorp)](https://developer.hashicorp.com/terraform/tutorials/azure-get-started)
4. [Enable Azure Monitor OpenTelemetry](https://learn.microsoft.com/en-us/azure/azure-monitor/app/opentelemetry-enable)

#### Build

- [ ] Run tests on pull requests
- [ ] Build and push the image to a container registry
- [ ] Recreate the Phase 3 environment with Terraform
- [ ] Deploy that image to Container Apps from the pipeline
- [ ] Send logs, metrics, and a health check to Application Insights
- [ ] Load-test the API, break one dependency, and write how you would recover

</details>

---

### Phase 5: AI

<details>
<summary>Phase 5 — agents, retrieval, and an evaluation of the answers</summary>

#### Goal

Add retrieval and a hosted model to the LangGraph agent already in the app. Use a managed identity. Measure whether the answers are grounded.

Done when a question returns an answer tied to your documents, and you can show the retrieval and answer metrics.

#### Key Concepts

##### Agents and tool calling

The agent decides which tool to call. LangGraph makes the steps, state, and branches visible. LangChain is the library underneath, which you are already using.

- **Why:** Some tasks need a choice of tools, and a hidden loop is hard to test.
- **When:** The workflow from Phase 1 that must read or write a real system. Use a fixed sequence when the steps are known.
- **Trade-off:** Less predictable, harder to test, and a larger permission surface.
- **Learn more:** [LangGraph overview](https://docs.langchain.com/oss/python/langgraph/overview)

##### Retrieval-augmented generation

Fetch the relevant text and put it in the prompt so the model answers from your material.

- **Why:** The model does not know your private or current documents.
- **When:** A question-answering feature on this system.
- **Trade-off:** Retrieval quality, permissions, indexing, latency, and token cost become your problem.
- **Learn more:** [Retrieval augmented generation overview](https://learn.microsoft.com/en-us/azure/search/retrieval-augmented-generation-overview)

##### Vector search

Find text by meaning, not only by the same words. Azure AI Search fits managed hybrid search and Azure access control. PGVector fits when Postgres is already the system of record and you want one less service.

- **Why:** Users do not phrase questions the way the documents do.
- **When:** The retrieval step of this phase.
- **Trade-off:** Embeddings and an index to operate. Search is another Azure bill. PGVector leaves more search behaviour for you to build.
- **Learn more:** [Vector search overview](https://learn.microsoft.com/en-us/azure/search/vector-search-overview)

##### Evaluation

Measure whether the right documents were retrieved and whether the answer matches them.

- **Why:** A fluent answer can still be wrong or cite the wrong document.
- **When:** Before you call this feature production.
- **Trade-off:** You need labelled questions and time. A demo can skip this and fail later.
- **Learn more:** [Select, deploy, and evaluate models](https://learn.microsoft.com/en-us/training/modules/model-catalog-evaluate/)

##### Where the model runs

Azure OpenAI keeps identity, region, and operations inside Azure. A model you run yourself keeps data on your side and can cost less in tokens.

- **Why:** The host decides who can call the model and who patches it.
- **When:** Azure OpenAI for this system. A local model for an experiment or a hard isolation rule.
- **Trade-off:** Hosted means quota, price, and vendor limits. Local means GPUs and uptime you own.
- **Learn more:** [Develop a generative AI chat app with Microsoft Foundry](https://learn.microsoft.com/en-us/training/modules/foundry-sdk/)

#### Courses

1. [Develop a generative AI chat app with Microsoft Foundry](https://learn.microsoft.com/en-us/training/modules/foundry-sdk/)
2. [Optimize generative AI model performance with Microsoft Foundry](https://learn.microsoft.com/en-us/training/modules/optimize-generative-ai-model-performance/) — includes grounding with RAG
3. [Select, deploy, and evaluate Microsoft Foundry models](https://learn.microsoft.com/en-us/training/modules/model-catalog-evaluate/)

#### Build

- [ ] Provision Azure OpenAI and Azure AI Search with Terraform
- [ ] Build the retrieval path and connect it to the LangGraph agent
- [ ] Call the model with workload identity
- [ ] Record retrieval and answer metrics for a small question set

</details>

---

### Phase 6: Integration

<details>
<summary>Phase 6 — a workflow that survives a slow partner, and Kubernetes only if a cluster is required</summary>

#### Goal

Accept work from outside the API, survive a partner that is slow or down, and write the result back. Use the n8n workflow as the local picture, then make the same decisions in Boomi and Service Bus.

Done when a failed partner call is visible, retryable, and does not corrupt the system of record. Stand up AKS only if the Boomi runtime or a second independently deployed part needs a cluster.

#### Key Concepts

##### Sync, async, and queues

A sync call waits. A queue lets the caller continue and lets a worker run later. Pub/sub is for several listeners of one fact.

- **Why:** A slow partner should not hold the user's request open.
- **When:** Sync when the caller needs the id now. A queue for enrichment, notification, and long AI runs.
- **Trade-off:** Async work is harder to trace, and readers may see stale results for a while.
- **Learn more:** [Asynchronous messaging options](https://learn.microsoft.com/en-us/azure/architecture/guide/technology-choices/messaging)

##### Idempotency, retries, and dead letters

A repeated message must not create a second side effect. Messages that cannot be processed go to a dead-letter path you watch.

- **Why:** Queues retry, and a poison message should not block the rest.
- **When:** Every consumer in this phase, including the n8n error branch.
- **Trade-off:** You store keys to detect duplicates, and someone must reprocess the dead-letter path.
- **Learn more:** [Service Bus dead-letter queues](https://learn.microsoft.com/en-us/azure/service-bus-messaging/service-bus-dead-letter-queues)

##### Saga and transactional outbox

A saga is a multi-step business action where a later failure needs a compensating step. An outbox writes the business change and the event in one database transaction, then publishes the event.

- **Why:** You cannot wrap your database and a partner API in one transaction.
- **When:** A flow that must update your system and notify another, without losing the event if the process dies between the two writes.
- **Trade-off:** Compensation and a publisher to operate. The read side can lag.
- **Learn more:** [CQRS pattern](https://learn.microsoft.com/en-us/azure/architecture/patterns/cqrs)

##### Boomi and webhooks

Boomi is the enterprise runtime for partners that already speak in its flows. A webhook is how those systems push an event at you. n8n is the local practice tool for the same shape.

- **Why:** The integration edge of this career is Boomi, not a second copy of the API.
- **When:** The flow that must accept an enterprise event, call the AI API, and write back.
- **Trade-off:** Another product to run, and a mapping layer that can hide failures.
- **Learn more:** [Event-driven architecture style](https://learn.microsoft.com/en-us/azure/architecture/guide/architecture-styles/event-driven)

##### AKS, only when a cluster is needed

Container Apps is still the host if one container and its revisions are enough. AKS is for a Boomi Molecule that requires a cluster, or for several parts that must deploy on their own. Service discovery then is a Kubernetes Service. A microservice is that split, and it is worth it only when independent deployability beats the new failure modes.

- **Why:** A cluster is an operations surface, not a badge.
- **When:** Molecule or a real second service. Until then, stay on Container Apps.
- **Trade-off:** Networking, deploys, and debugging get harder as soon as you split.
- **Learn more:** [Microservices](https://martinfowler.com/articles/microservices.html)

##### Copies of data

Replication keeps extra copies for reads and for a node loss. Partitioning splits data so one machine is not the ceiling. Consistency is whether a read sees the latest write. During a partition you are choosing which of consistency and availability you give up.

- **Why:** One database is a ceiling and a single failure point once the earlier phases are actually at that limit.
- **When:** After measurement, not before the first Azure deploy.
- **Trade-off:** Lag, cross-partition queries, and behaviour that is harder to explain.
- **Learn more:** [Sharding pattern](https://learn.microsoft.com/en-us/azure/architecture/patterns/sharding)

#### Courses

1. [Queue and process AI operations with Azure Service Bus](https://learn.microsoft.com/en-us/training/modules/queue-process-operations-service-bus/)
2. [Learn Kubernetes basics](https://kubernetes.io/docs/tutorials/kubernetes-basics/) — when you take the AKS build item
3. [Deploy a containerized application on Azure Kubernetes Service](https://learn.microsoft.com/en-us/training/modules/aks-deploy-container-app/1-introduction) — same condition
4. [Installing a cloud cluster with elastic scaling in Kubernetes (Boomi)](https://help.boomi.com/docs/Atomsphere/Integration/Atom,%20Molecule,%20and%20Atom%20Cloud%20setup/int-Installing_a_cloud_cluster_with_elastic_scaling_in_kubernetes)
5. [Runtime cluster system requirements (Boomi Molecule)](https://help.boomi.com/docs/Atomsphere/Integration/Atom,%20Molecule,%20and%20Atom%20Cloud%20setup/r-atm-Molecule_system_requirements_41f9a675-ab11-4f3b-bf51-1655394aba5b)
6. [Boomi Runtime Management](https://help.boomi.com/docs/Atomsphere/Integration/Integration%20management/c-atm-Atom_Management_b38a3a90-d7f6-4df0-8c00-e75a178dfdfa)

#### Build

- [ ] Optional: extend the n8n workflow with a retry and a dead-letter path
- [ ] Put the same work on Service Bus, with idempotent handling
- [ ] Accept an enterprise webhook in Boomi, call the LangGraph API, and write the result back
- [ ] If Molecule or a second service needs a cluster, finish the Kubernetes courses and deploy it to AKS. If not, write the ADR that says Container Apps is still enough
- [ ] Draw the [C4 context](https://c4model.com/) for this flow

</details>

---

## Portfolio

One system, three stages. Each stage continues the last. Do not start a stage before the phases that feed it.

For every stage, commit three things: an architecture diagram, an ADR for the significant choice, and a measured result.

### Stage 1: The running application

**After:** Phases 1–4.

The API, its data, Container Apps, the pipeline, and the load test from Phase 4.

### Stage 2: Retrieval and agents

**After:** Phase 5.

The same system, plus Azure OpenAI, retrieval, workload identity, and the evaluation numbers.

### Stage 3: The integration

**After:** Phase 6.

The same system, plus the queue or Boomi flow, the failure you handled, and the ADR for AKS or for staying on Container Apps.

### What to include with each stage

- The problem, in a few sentences
- A diagram. Stage 3 uses the C4 context from Phase 6
- The ADR: what you chose, what you refused, and the cost
- A measured result: latency, a failed dependency, token use, or what it cost to run
- How to tell it is healthy: the log, metric, or alert you would open first
