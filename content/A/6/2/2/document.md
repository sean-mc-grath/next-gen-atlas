---
id: 0c54e1d3-edb4-4544-bf35-1200c9f88cd6
docNo: A.6.2.2
name: Position In The Agent Framework
type: Core
depth: 4
childType: sections_and_primary_docs
---

##### A.6.2.2 - Position In The Agent Framework [Core]

Halo Agents are Microagents as defined in [A.0.1.1.43 - Microagent](d9e38978-fd7f-4e6d-98e6-45b2f5d6a3ce): their Agent Artifacts are nested inside the Agent Artifacts of Macroagents rather than appearing as standalone entries in the Agent Scope ([A.6 - The Agent Scope](4a08ca6c-e652-49e4-9b79-4831b20e600a)). In practice, Halo Agent Artifacts are enveloped by Prime Agent Artifacts and do not sit alongside Prime, Executor, or Generator Agent Artifacts at the top level of this Scope.

Generator Agents, Prime Agents, and Executor Agents are Macroagents (see [A.0.1.1.42 - Macroagent](08a64545-48f6-4849-b876-bbdba1f74a64)). Generator Agents each manage a single Sky Generated Asset ([A.0.1.1.44 - Generator Agent](7535ee4b-1220-4459-9bdd-2830a611553c) and [A.0.1.1.60 - Sky Generated Asset](c7b49829-2b73-440b-b958-6bee667d596f)); Prime Agents deploy capital using Sky Primitives; Executor Agents provide operational security and GovOps oversight. Halo Agents extend Prime Agents by wrapping specific external assets and tokenization systems into governed products that can be held in Prime portfolios and used, where eligible, as collateral in the [Allocation System](9db14ab7-bb4b-4751-8084-843bd4359f2a).
