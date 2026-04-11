# Proposals Shard

Structured research documents that capture ideas, options, and trade-offs before committing to implementation. Proposals bridge the gap between free-form ideation (Notepads) and executable work (Tasks). The lifecycle is simple: draft a proposal, revise it until it's solid, then consume it by turning it into a task.

## Two Concerns

The Proposals shard serves two distinct purposes:

| Concern | What it does | Status |
|---------|-------------|--------|
| **Research** | Gather context from codebase, existing artifacts, and user input; write a detailed proposal covering motivation, options, and recommendation | Built — create_proposal workflow is operational |
| **Consumption** | Revise proposals iteratively, then consume (turn into task), discard, or defer | Built — revise and consume workflows are operational |

### Research workflows and skills

| Tool | Type | Purpose |
|------|------|---------|
| Create Proposal | Workflow | Gather context and write a full proposal document |
| Capture As Proposal | Skill | Retroactively record existing discussion or research as a proposal |

### Consumption workflows and skills

| Tool | Type | Purpose |
|------|------|---------|
| Revise Proposal | Workflow | Launch an agent to revise and improve a draft proposal |
| Consume Proposal | Workflow | Create a Projects task from a proposal |
| Deprecate Proposal | Skill | Mark a proposal as discarded or no longer relevant |

## Proposals and Increments

Every proposal should belong to an increment. The `increment` frontmatter field links the proposal to its parent increment using wikilink syntax:

```yaml
increment: "[[(Increment) 6.13 - Shard Session Architecture]]"
```

When creating a proposal, determine the increment:
1. If the user specifies one, use that
2. If the proposal clearly relates to an active increment, use that
3. Otherwise, default to the current adhoc increment (e.g., `6.A`)

## Proposal Lifecycle

```
drafting → draft → consumed | discarded | deferred
```

| Status | Meaning |
|--------|---------|
| `drafting` | Agent is actively creating the proposal (initial generation) |
| `draft` | Proposal exists, ready for revision cycles |
| `consumed` | Turned into a task — the goal |
| `discarded` | No longer relevant or not worth pursuing |
| `deferred` | Will be revisited later |

### Lifecycle Flow

1. **Drafting**: A stub is created and an agent is launched to write the full proposal. The proposal sits in `drafting` until the agent finishes.
2. **Draft**: The proposal is complete. The core action is **Revise** — launch an agent to improve the draft. This can repeat as many times as needed.
3. **Terminal**: From Draft, the proposal can be:
   - **Consumed** — turned into a Projects task via the consume workflow
   - **Discarded** — no longer relevant
   - **Deferred** — will be revisited later

### Consumption Fields

When a proposal is consumed:
- Set `consumed-by` to a wikilink to the created task (e.g. `"[[(Task) 502 Refactor Proposal Workflow]]"`)

### Proposals vs Notepads

| Aspect | Proposal | Notepad |
|--------|----------|---------|
| Purpose | Structured research document | Free-form brainstorming |
| Lifecycle | Draft → Revise → Consume/Discard/Defer | active → archived |
| Output | Task (when consumed) | Ideas and exploration |
| Structure | Fixed sections (motivation, options, recommendation) | Free-form with branching |

## Checkbox Tracking

When working on proposals, agents must tick off checkbox items (`- [ ]` → `- [x]`) immediately upon completing each section or criterion. This keeps the proposal file as the single source of truth for progress.

# Dashboards

| Dashboard | Purpose | Maintained By |
|-----------|---------|---------------|
| `(Dashboard) Proposals.md` | All proposals grouped by status | DataviewJS |

# Skills

| Skill | File | Purpose |
|-------|------|---------|
| Capture As Proposal | `sk-prop-capture_as_proposal.md` | Capture existing discussion as a proposal |
| Deprecate Proposal | `sk-prop-deprecate_proposal.md` | Mark a proposal as discarded or no longer relevant |

# Workflows

| Workflow | File | Purpose |
|----------|------|---------|
| Create Proposal | `wkfl-prop-create_proposal.md` | Research and write a full proposal |
| Revise Proposal | `wkfl-prop-revise_proposal.md` | Revise and improve a draft proposal |
| Consume Proposal | `wkfl-prop-consume_proposal.md` | Create a Projects task from a proposal |

# Templates

| Template | File | Purpose |
|----------|------|---------|
| Proposal | `tmp-prop-proposal-v0.1.md` | Standard proposal artifact |
