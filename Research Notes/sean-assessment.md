# Research Note – Halo Agents Slice (Definition, Taxonomy, Trust Boundaries)

Branch: `sean-assessment` ·

---

## Issue: Where to introduce Halo Agents in the Atlas

### Description

Halo Agents are introduced across multiple Sky posts as a new Agent type and as the primary tokenization wrapper for external assets, but the original Atlas did not yet encode them as first-class concepts.

The question was where to place the canonical definition and governance narrative: only in the Definitions section (A.0.1.1), only in the Agent Scope (A.6), only in Prime Agent artifacts, or some combination of these.

The constraints were:

- Avoid redefining "Halo Agent" in multiple places in slightly different ways.
- Keep the Atlas structure predictable (definitions vs scope vs artifacts).
- Satisfy the brief's requirement that Halo Agents be readable as a self-contained concept while minimizing disruption to existing sections.

### Resolution

I split responsibilities across three locations:

- **A.0.1.1.47 – Halo Agent (HA)** (`content/A/0/1/1/47/document.md`): holds the precise *dictionary* definition (nested inside Prime artifacts, wraps external assets, operates within Laniakea, monitored via Sentinel).
- **A.6.2 – Halo Agents** (`content/A/6/2/document.md`): provides the *governance narrative* for Halos (role, position in the agent stack, risk hierarchy, collateralization constraints at a high level, and lifecycle/governance interfaces), implemented in five subsections:
  - A.6.2.1 – Definition And Purpose (`content/A/6/2/1/document.md`)
  - A.6.2.2 – Position In The Agent Framework (`content/A/6/2/2/document.md`)
  - A.6.2.3 – Risk Hierarchy And Trust Boundaries (`content/A/6/2/3/document.md`)
  - A.6.2.4 – Collateralization And Tokenization Constraints (`content/A/6/2/4/document.md`)
  - A.6.2.5 – Lifecycle And Governance Interfaces (`content/A/6/2/5/document.md`)
- **A.6.1.1.1 – Nested Halo Agent Artifacts** (`content/A/6/1/1/1/document.md`) (+ sub-docs): defines the *minimum artifact structure* each Prime must maintain for the Halo Agents it envelops.

This keeps the concept consistent: definitions live in A.0.1.1, agent-scope behaviour and trust boundaries in A.6.2, and concrete artifact requirements in A.6.1.1.1, while avoiding repeated or conflicting definitions.

---

## Issue: How far to push the Macroagent / Microagent taxonomy

### Description

The Sky Agent Framework Overhaul distinguishes Macroagents (artifacts directly in A.6, "L2 for governance") and Microagents (artifacts nested under Macroagents, "L3 for governance").

The Atlas previously did not encode this split explicitly. Introducing Halos as Microagents under Primes raised the question: should the entire Agent taxonomy be refactored around macro/micro, or should this be introduced minimally to support Halos?

Constraints:

- The assessment is a narrow slice, not a full Agent Framework rewrite.
- Macro/micro is important to understand where Halos sit, but over-refactoring A.6 could create scope creep and risk conflicts with future edits.

### Resolution

I introduced Macroagent and Microagent **only at the definitions layer** and used them where strictly necessary:

- **A.0.1.1.42 – Macroagent** (`content/A/0/1/1/42/document.md`): defined as agents whose artifacts live directly in A.6, explicitly listing Generator Agents, Prime Agents, and Executor Agents as Macroagents.
- **A.0.1.1.43 – Microagent** (`content/A/0/1/1/43/document.md`): defined as agents whose artifacts are enveloped inside Macroagent artifacts, listing Halo Agents and Proto-Agents as Microagents.
- **A.0.1.1.39 – Agent** (`content/A/0/1/1/39/document.md`): updated to reference the macro/micro split and to hook into the Agent Creation Primitive for Proto-Agents.
- **A.6.2.2 – Position In The Agent Framework** (`content/A/6/2/2/document.md`): uses these definitions to place Halos explicitly as Microagents nested under Prime Agents, without restructuring other A.6 content.

I did **not** refactor the rest of A.6 around macro/micro; instead, I used the new definitions to support the Halo narrative while keeping the overall scope constrained.

Related definitions added to support the taxonomy without expanding scope:

- **A.0.1.1.44 – Generator Agent** (`content/A/0/1/1/44/document.md`)
- **A.0.1.1.45 – Prime Agent** (`content/A/0/1/1/45/document.md`) — renumbered from former A.0.1.1.42
- **A.0.1.1.46 – Executor Agent** (`content/A/0/1/1/46/document.md`) — renumbered from former A.0.1.1.43

---

## Issue: How to treat supporting concepts outside the slice scope

### Description

Several important concepts sit adjacent to the Halo Agents slice but are not themselves the main focus of this edit, including:

- Proto-Agent
- Sky Generated Asset
- Generate Sky Asset Primitive
- Sentinel
- Laniakea

These are all referenced in the external Sky posts and are needed to make the Halo narrative intelligible, but each of them also has significant depth and future surface area. The question was how to handle these concepts so that:

- The Halo slice can reference them without dangling or inconsistent terminology.
- The Atlas is not forced to adopt a full technical or economic specification for each one in this PR.
- Future iterations retain flexibility to evolve these concepts without having to unwind overly detailed definitions introduced here.

### Resolution

I chose to **define each supporting concept lightly in A.0.1.1** and then reference those definitions from the Halo-related sections, while deliberately avoiding deep specification:

| Document | Location |
|----------|----------|
| A.0.1.1.48 – Proto-Agent | `content/A/0/1/1/48/document.md` |
| A.0.1.1.60 – Sky Generated Asset | `content/A/0/1/1/60/document.md` |
| A.0.1.1.61 – Generate Sky Asset Primitive | `content/A/0/1/1/61/document.md` |
| A.0.1.1.62 – Sentinel | `content/A/0/1/1/62/document.md` |
| A.0.1.1.63 – Laniakea | `content/A/0/1/1/63/document.md` |

In all cases, the intent is:

- To give each concept a **stable name and minimal definition** so it can be referenced consistently from Halo-related text.
- To **leave room for later iterations** to add dedicated Articles or NR-style documents that go into depth (e.g., full Sentinel configuration taxonomy, full Laniakea design, detailed Sky Generated Asset economics) without being constrained by premature detail in this slice.

Proto-Agent remains a stub ("formal definition will be specified in a future iteration"); the other four carry short operational definitions sufficient for cross-referencing from A.0.1.1.47, A.6.2, and A.6.1.1.1.

---

## Issue: How to express Halo Agents' position in the risk hierarchy

### Description

External materials emphasize a risk hierarchy roughly of the form "Sky → Generator → Prime → Halo", with multiple capital layers and an explicit loss waterfall.

The question was how to reflect Halo Agents' position in that hierarchy at the Atlas level, without freezing specific numerical parameters or full waterfall mechanics that are likely to evolve.

Constraints:

- The Atlas should encode governance-relevant ordering and trust boundaries.
- Detailed capital structure and percentages belong in risk / collateral parameter documents and may change frequently.
- The Halo slice should make clear that Halos sit at the "edge" of the stack and are designed for leveraged / exotic assets.

### Resolution

I took a **qualitative ordering** approach:

- In **A.6.2.3 – Risk Hierarchy And Trust Boundaries** (`content/A/6/2/3/document.md`), I:
  - Stated that losses are to be absorbed first by those closest to the decisions that created them.
  - Placed Halo Agents at the edge of the risk stack, designed to host complex/exotic assets and leveraged strategies.
  - Explained that losses arising from Halo activity are *expected* to be absorbed first within the Halo's own structure, then by the Prime Agents that envelop them, then by higher-risk capital such as Generator Agents, before reaching systemic buffers and USDS holders.

I did not:

- Encode exact capital layers, buffer targets, or waterfall percentages.
- Override any existing or future risk-framework sections that may define a more granular ordering.

This balances clarity about **where Halos sit** with flexibility for the risk framework to evolve independently.

---

## Issue: How prescriptive to be about Halo collateralization and tokenization rules

### Description

The Overhaul and related posts discuss constraints on Halo tokens (e.g. minimum free float, maximum Prime concentration) and how they interact with the Allocation System.

The question was whether to encode specific numeric thresholds in the Atlas Halo sections or to keep collateralization rules high-level and delegate numbers to risk/collateral parameter articles.

Constraints:

- Risk parameters (like free float percentages and concentration caps) are operational and likely to change as the ecosystem scales.
- Hard-coding numbers in A.6.2 would require frequent Atlas edits for routine risk-parameter updates.
- The Atlas should still make it clear that Halos cannot unilaterally decide their own collateralization conditions.

### Resolution

I encoded **structure, not numbers**:

- In **A.6.2.4 – Collateralization And Tokenization Constraints** (`content/A/6/2/4/document.md`), I:
  - Stated that Halo tokens can be eligible as collateral in the Allocation System (**A.2.2.9.1**, `content/A/2/2/9/1/document.md), **subject to** the collateral framework and risk parameters defined elsewhere (Allocation System and collateral parameter Articles).
  - Clarified that a Halo token that falls outside those parameters cannot be used as collateral until brought back within permitted ranges.
  - Explicitly noted that detailed numerical parameters (free float, concentration limits, haircuts, capacity) live in those risk/collateral documents and are updated via standard risk governance, not unilaterally by any Halo.
  - Distinguished tokenized vs non-tokenized Halos and tied tokenized Halos to the Agent Creation Fee provisions (**A.2.3.1.2.1.2.5 – Agent Creation Fees**, `content/A/2/3/1/2/1/2/5/document.md`).

Additionally, in **A.6.1.1.1.3 – Risk Limits And Collateral Eligibility** (`content/A/6/1/1/1/3/document.md`), I required Prime Agent Artifacts to reference:

- The Halo's own risk/limits artifacts.
- The collateral eligibility parameters that apply to the Halo token as set in Allocation System / collateral Articles.

This gives a clear governance path (and expectations) without hard-coding specific values.

---

## Issue: Whether Halo Agent Artifacts should appear as a top-level list under A.6

### Description

Given that Halos are a new Agent type, there were two plausible ways to reflect them under the Agent Scope:

1. Add "Halo Agent Artifacts" as a top-level list alongside Prime, Executor, and Generator artifacts under A.6.1.
2. Treat Halo Agent artifacts as **nested** under Prime Agent artifacts only, consistent with the "Microagent inside Macroagent" model.

Constraints:

- The macro/micro distinction suggests nested structure, not peer structure.
- Users should be able to locate Halo artifacts via the Prime Agents that control them.
- A.6.1 is already organized as lists of Macroagent artifacts (Primes, Executors, Generators).

### Resolution

I chose the nested approach:

- Kept **A.6.1 – Agent Artifacts** (`content/A/6/1/document.md`) as a list of **Macroagent** artifacts:
  - **A.6.1.1 – List Of Prime Agent Artifacts** (`content/A/6/1/1/document.md`)
  - **A.6.1.2 – List Of Executor Agent Artifacts** (`content/A/6/1/2/document.md`)
  - **A.6.1.3 – List Of Generator Agent Artifacts** (`content/A/6/1/3/document.md`) — stub for future iterations
- Added **A.6.2 – Halo Agents** (`content/A/6/2/document.md`) as a sibling Article under **A.6 – The Agent Scope** (`content/A/6/document.md`) for the governance narrative (see first issue above).
- Under **A.6.1.1**, I inserted **A.6.1.1.1 – Nested Halo Agent Artifacts** (`content/A/6/1/1/1/document.md`) as the first child, which states that:
  - Prime artifacts must include the artifacts of any Halo Agents they envelop.
  - Halos are Microagents nested under Prime artifacts, not standalone entries in the Agent Scope.
  - For each Halo, the Prime must satisfy the sub-requirements in A.6.1.1.1.1–A.6.1.1.1.4.
- **A.6.1.1.1.1–A.6.1.1.1.4** then define the minimum artifact references:
  - A.6.1.1.1.1 – Mandate And Configuration Requirements (`content/A/6/1/1/1/1/document.md`)
  - A.6.1.1.1.2 – Halo Token Issuance And Prime Limits (`content/A/6/1/1/1/2/document.md`)
  - A.6.1.1.1.3 – Risk Limits And Collateral Eligibility (`content/A/6/1/1/1/3/document.md`)
  - A.6.1.1.1.4 – Reporting And Sentinel Integration (`content/A/6/1/1/1/4/document.md`)

Inserting A.6.1.1.1 required renumbering the existing Prime Agent entries (Spark, Grove, etc.) from A.6.1.1.1–A.6.1.1.8 to **A.6.1.1.2–A.6.1.1.9** under `content/A/6/1/1/`.

This preserves the macro/micro intent: Halos live under Primes in the artifact tree, rather than as a fourth top-level artifact list, while still making their required artifacts explicit.
