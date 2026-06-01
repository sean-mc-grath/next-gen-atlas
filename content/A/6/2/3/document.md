---
id: 591ace05-4257-4c74-80bf-1be4d736188e
docNo: A.6.2.3
name: Risk Hierarchy And Trust Boundaries
type: Core
depth: 4
childType: sections_and_primary_docs
---

##### A.6.2.3 - Risk Hierarchy And Trust Boundaries [Core]

The Sky Ecosystem is designed so that losses are absorbed first by those closest to the decisions that created them. Within this structure, Halo Agents sit at the edge of the risk stack: they are intended to host complex or exotic assets and leveraged strategies, while higher layers provide buffers that protect USDS holders and Sky Core. In general, losses arising from Halo Agent activity are expected to be absorbed first within the Halo's own capital structure, then by the Prime Agents that envelop them, then by Generator Agents and other higher-risk capital, before reaching systemic buffers and USDS holders.

Halo Agents may be maintained and developed by external teams and Ecosystem Actors, but they must operate within mandates defined in their Agent Artifacts and in the Prime Agent Artifacts that envelop them. Halo Agents cannot unilaterally modify the guardrails that determine aggregate risk or collateral eligibility; those parameters are set and enforced by Prime Agents, Generator Agents, Executor Agents, and the [Core Council](5a03a0c4-a47a-409c-9b23-52ac93e63d45) under the Atlas, the Sky risk framework, and the [Allocation System](9db14ab7-bb4b-4751-8084-843bd4359f2a). [Sentinel](1b6393b1-7f7f-48ac-b7a0-13f148be290d) provides continuous verification of Halo activity by comparing self-reported data (for example via stl-report) with independent observations (for example via stl-verify), ensuring that discrepancies between "what the Halo reports" and "what the Prime observes" can be detected and acted upon.
