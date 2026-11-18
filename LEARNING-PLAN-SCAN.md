# Learning Plan Scan — Monthly Roadmap Audit

Internal brief. This file is not a course. An automation checks out this repository, reads **[README.md](README.md)** only (not `devpulse-agent.md`), and posts one **advisory** summary to Slack. It does **not** edit the repo, commit, or open a pull request during the scan.

---

## Objective

Act as an independent software engineering researcher and **learning-roadmap auditor** for the roadmap in `README.md`.

Answer:

**Does this roadmap still teach the capabilities that matter for cloud-native, AI, and enterprise integration work in the UK market over the next 3–5 years?**

Recommend what to **KEEP, ADD, REMOVE, DEPRIORITISE, REORDER, REPLACE, or CLARIFY** — with evidence. Do not chase every new tool. Do not invent job statistics or salaries.

---

## Scope

### In scope

- Full read of `README.md` (phases, courses, build lists, evidence, portfolio, progress checkboxes).
- UK job listings and employer career pages (sampled, recent).
- Official documentation and reputable engineering sources (CNCF, cloud vendors, established consultancies).
- Resource freshness (deprecated courses, broken links if checkable).
- Whether each phase’s **Outcome**, **Build**, and **Evidence** match employer expectations for **demonstrable** skills.

### Out of scope

- Editing `README.md` or any file in the repository during the scan run.
- Opening pull requests during the scan run.
- Auditing or changing **DevPulse** (`devpulse-agent.md`).
- Network administration, pure data science, or academic ML research tracks.
- Recommending a second cloud or Kubernetes unless README’s conditional AKS path is under-supported.

---

## Evidence rules

| Rule | Requirement |
| --- | --- |
| **Recency** | Prefer sources from the last **18 months**. Older only for stable fundamentals. |
| **UK jobs** | Sample **at least 12** UK postings across **at least 4** role families (e.g. Software Engineer, Cloud Engineer, AI Engineer, Integration Engineer). Mix London and outside London if data allows. |
| **Confidence** | Label each finding **High**, **Medium**, or **Low**. |
| **No invention** | Do not fabricate salaries, demand percentages, or employer requirements. |
| **Multi-source** | Material roadmap changes need **two independent** supporting signals (e.g. job repeat + official doc or two job families). |
| **Access** | If GitHub or a source is unreachable, state the limitation and avoid speculative edits. |

---

## Decision labels

For each important roadmap item, assign one label:

| Label | Meaning |
| --- | --- |
| **KEEP** | Still right; no change |
| **ADD** | Missing capability |
| **REMOVE** | No longer worth the time in this plan |
| **DEPRIORITISE** | Useful but less urgent than other work |
| **REORDER** | Move earlier or later in the phase sequence |
| **REPLACE** | Better resource, tool, or wording |
| **CLARIFY** | Same intent; clearer outcome or checkbox |

---

## Report limits

- **At most 5** substantive README recommendations per monthly run (numbered **R1–R5**).
- **At most 3** items for **30-day focus** (practical, not reading-only).
- **Watchlist:** up to 5 developments worth monitoring but **not** yet curriculum changes.
- If nothing material changed since the last report, say so in one sentence and keep the report short.

---

## Compare with previous run

If a prior scan report is available (attachment, Slack history, or file the operator provides), note:

- Which prior recommendations were implemented in `README.md`.
- Which are still open.
- What **new** evidence appeared since that report.

If no prior report exists, state **first baseline run**.

---

## Slack message format

Post **one** Slack message. Use this structure (plain text; Slack will render fenced blocks if needed).

```
[Learning Plan Scan] YYYY-MM-DD

Verdict: (one sentence — direction still appropriate / needs adjustment / major gap)

Changes since last scan: (bullet list or "First run" / "No material change")

Recommendations (max 5):
R1. [LABEL] Short title
    Evidence: (one line + source link + date + confidence)
    README: Phase N / section — proposed change in one sentence
R2. ...
(omit R3–R5 if not needed)

30-day focus:
1. ...
2. ...
3. ...

Watchlist (not for README yet):
- ...

Sources:
- Title — URL — date accessed
```

Do **not** include long essays. The operator reviews R-numbers in Slack and later approves which to implement.

---

## Approval and implementation (separate run)

The monthly scan **does not** apply changes.

When the operator approves specific IDs (e.g. `R1, R3`):

1. Create a branch.
2. Edit **only** `README.md` (unless operator extends scope).
3. Open a **single PR** with a short summary mapping each ID to edits.
4. Preserve checkbox style and phase structure (Outcome → Learn → Courses → Build → Evidence → Phase complete).

---

## Decision-making rules

1. Do not confuse hype with UK employer demand.
2. Do not assume AI removes engineering fundamentals.
3. Do not expand the roadmap without removing or deprioritising something else when time is fixed.
4. Prefer transferable skills over single-vendor trivia unless README already committed to that vendor (Azure, Boomi).
5. Respect README’s single-application portfolio model.
6. Treat n8n as **optional** reinforcement; Boomi and Service Bus are the integration destination.
7. Distinguish **verified** trends from interpretation.
8. Stop recommending items already present in `README.md` unless **CLARIFY** or **REPLACE** is justified.
9. Recommend stopping time on something when evidence supports it, not only new adds.
10. Cap changes at five recommendations; prioritise impact on employability and portfolio evidence.

---

## Research areas (use as lenses, not a checklist every month)

Rotate depth by month; every run still samples UK jobs.

- Software architecture, APIs, testing, security, observability
- Azure, containers, identity, IaC, CI/CD (GitHub Actions, OIDC)
- AI engineering: RAG, agents, evaluation, safety, cost
- Enterprise integration: messaging, idempotency, Boomi, event-driven design
- AI-native development and Forward Deployed Engineering — verify demand before roadmap changes; default **watchlist** unless evidence is strong

---

## Saved automation prompt

```
Check out this repository. Read LEARNING-PLAN-SCAN.md and README.md from that checkout. Follow LEARNING-PLAN-SCAN.md exactly.

Run on the schedule configured for this automation (monthly). Use evidence rules and UK job sampling described in the brief.

Post one Slack message using the format in LEARNING-PLAN-SCAN.md. Advisory only: do not edit the repository, commit, or open a pull request.

If the operator later approves recommendation IDs in a separate implementation run, amend README.md on a branch and open a PR for those IDs only.
```

---

## Repository layout reference

| File | Purpose |
| --- | --- |
| `README.md` | Canonical learning roadmap — **only file this scan amends after approval** |
| `LEARNING-PLAN-SCAN.md` | This audit brief |
| `devpulse-agent.md` | Daily technical refresher — **ignored by this scan** |