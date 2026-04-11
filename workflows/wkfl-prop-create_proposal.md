This workflow belongs to the Proposals shard. Ensure you have @init-prop.md in context before continuing.

# Workflow: Create Proposal

Gather context from the codebase, existing artifacts, and user input, then write a detailed proposal document. This is a **research** workflow — the agent investigates before writing.

# Input

- User's idea, question, or change description (the seed prompt)
- (Optional) Increment to assign the proposal to
- (Optional) Related artifacts or codebase areas to investigate

# Actions

## Stage 1: Research

- Explore the codebase and existing artifacts related to the user's prompt
- Read relevant documents, code, and prior discussions
- Identify the current state, alternatives, and trade-offs
- Build a mental model of the problem space

## Stage 2: Write Proposal

- Get the next proposal number: `flint helper type newnumber Proposal`
- Create the proposal using @tmp-prop-proposal-v0.1.md
- Set status to `open`
- Set the increment (user-specified, contextually relevant, or adhoc)
- Fill in all sections:
  - **Context & Motivation** — why this proposal exists
  - **Current State** — what exists today and what the gaps are
  - **Proposed Approach** — the recommended path forward, in detail
  - **Alternatives Considered** — other options and why they were not recommended
  - **Trade-offs & Risks** — what you gain and give up
  - **Recommendation** — a concise summary of the recommendation
- Leave the **Decision** section empty (populated during review)
- Add a creation entry to the Proposal Log
- Present the proposal to the user for review

## Stage 3: Refine

- Converse with the user to refine the proposal
- Update sections based on feedback
- Once the user is satisfied, the proposal stays in `open` status, ready for the review_proposal workflow

# Output

- Complete proposal in `open` status
- All sections populated with research findings

# Notes

- This workflow must work in headless mode (Orbh) — no interactive terminal checkpoints when launched from a plate
- If the agent needs human input during research, use a deferred question (`flint orbh request`) and set the proposal to `draft`
- The agent should make contact with reality: read actual code, check actual configs, verify actual state
