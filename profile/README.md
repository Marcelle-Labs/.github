# Marcelle Labs

Independent engineering lab for AI-native systems and production software.

[marcellelabs.io](https://marcellelabs.io)

## What we do

**Design → Build → Evaluate → Ship.**

We take a technical problem through architecture, implementation, evaluation,
deployment and verification — and we publish the evidence for each stage rather than
asserting the outcome. Every system below states what its evidence establishes and,
explicitly, what it does not.

## Selected engineering

### Interlock

**Problem.** Two agent actions can each be locally valid and still break a shared
constraint when they land together. Local validity does not compose.

**System.** Interlock reads revision-bound environment evidence before shared-state
mutation and selects a deterministic coordination decision.

| | |
| --- | --- |
| Repository | [`Marcelle-Labs/interlock`](https://github.com/Marcelle-Labs/interlock) |
| Controlled experiment | [`experiments/hac-330`](https://github.com/Marcelle-Labs/interlock/tree/main/experiments/hac-330) |
| Frozen cloud evidence packet | [`cloud-run.public.json`](https://github.com/Marcelle-Labs/interlock/blob/75253e38791e69f7e2a4bb3a041044a9114c32f0/experiments/hac-342/evidence/cloud-run.public.json) — pinned to a commit, not a branch |
| Independent verifier | [`verify-public-packet.mjs`](https://github.com/Marcelle-Labs/interlock/blob/75253e38791e69f7e2a4bb3a041044a9114c32f0/experiments/hac-342/bin/verify-public-packet.mjs) |
| Claim boundary | [`DISCLOSURE.md`](https://github.com/Marcelle-Labs/interlock/blob/main/DISCLOSURE.md) |
| CI | [`ci.yml`](https://github.com/Marcelle-Labs/interlock/blob/main/.github/workflows/ci.yml) |

The local counterfactual (HAC-330) and the recorded Google Cloud traversal (HAC-340)
are separate runs, and the repository says so. Neither is evidence for the other. This
is a bounded experiment, not a safety or production-readiness guarantee.

### Never Ask Twice

**Problem.** Support customers repeat their SLA, setup, open issue and escalation
contact every time they come back, because the agent reconstructs context from nothing
each session.

**System.** A support memory agent with explicit working, episodic and semantic memory
tiers, a forgetting policy with validity windows and provenance, budgeted recall, and
an MCP surface.

| | |
| --- | --- |
| Repository | [`Marcelle-Labs/never-ask-twice`](https://github.com/Marcelle-Labs/never-ask-twice) |
| Memory model | [`docs/memory-model.md`](https://github.com/Marcelle-Labs/never-ask-twice/blob/main/docs/memory-model.md) |
| Forgetting policy | [`docs/forgetting-policy.md`](https://github.com/Marcelle-Labs/never-ask-twice/blob/main/docs/forgetting-policy.md) |
| Evaluation | deterministic memory ON/OFF ablation — `pnpm eval` |
| Live deployment | Alibaba Function Compute — [`/health`](https://never-awice-api-kvsvpczulb.us-east-1.fcapp.run/health) reports `mode: "qwen-live"` |
| Deployment record | [`deploy/alibaba-fc.md`](https://github.com/Marcelle-Labs/never-ask-twice/blob/main/deploy/alibaba-fc.md) |
| CI | [`ci.yml`](https://github.com/Marcelle-Labs/never-ask-twice/blob/main/.github/workflows/ci.yml) |

The ablation is measured inside the described evaluation setup on synthetic fixtures.
It is not a general claim about memory in other products.

### Vreko

[Vreko](https://vreko.dev) is the developer-intelligence product built at Marcelle
Labs. The core application is **proprietary**. Selected interfaces are public so the
integration surface can be inspected and depended on:

- [`vreko-dev/vreko-cli`](https://github.com/vreko-dev/vreko-cli) — `@vreko/cli`
- [`vreko-dev/mcp-server`](https://github.com/vreko-dev/mcp-server) — `vreko-mcp-server`
- [`vreko-dev/vscode`](https://github.com/vreko-dev/vscode) — VS Code extension

Organization: [`vreko-dev`](https://github.com/vreko-dev) ·
Documentation: [docs.vreko.dev](https://docs.vreko.dev)

## Open ecosystem work

Qwynn Marcelle separately stewards **[workspace.json](https://workspacejson.dev)**, an
Apache-2.0 open standard for committed repository intelligence.

**workspace.json is not a Marcelle Labs product.** It is an independent standard with
its own organization, governance and release authority at
[`workspacejson`](https://github.com/workspacejson). Marcelle Labs systems consume it
at pinned revisions like any other external dependency — Interlock records that
boundary in [`provenance/manifest.json`](https://github.com/Marcelle-Labs/interlock/blob/main/provenance/manifest.json),
and CI enforces it.

## How to evaluate this organization

Start with a claim, then follow it to the artifact. Every system above links its
experiment, its verifier, its deployment record and its stated limits. If a claim here
does not resolve to something you can open and check, treat that as a defect and open
an issue.
