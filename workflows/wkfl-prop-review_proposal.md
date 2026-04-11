This workflow belongs to the Proposals shard. Ensure you have @init-prop.md in context before continuing.

# Workflow: Review Proposal

Facilitate human review of a proposal and record the decision. This is a **decision** workflow — the human decides, the agent facilitates.

# Input

- Proposal artifact in `open` status
- (Optional) Specific questions or concerns to address

# Actions

## Stage 1: Present

- Set status to `reviewing`
- Summarize the proposal for the reviewer: motivation, proposed approach, key trade-offs, and recommendation
- Highlight any areas of uncertainty or risk that need human judgment
- Add a review entry to the Proposal Log

## Stage 2: Discuss

- Facilitate discussion — answer questions, provide additional context, explore alternatives
- If the reviewer requests changes to the proposal, update the relevant sections
- Track discussion points in the Proposal Log

## Stage 3: Decide

- Record the human's decision:
  - **Approved** — set status to `approved`, populate `decision` with rationale, set `decision-date`
  - **Rejected** — set status to `rejected`, populate `decision` with rationale, set `decision-date`
  - **Deferred** — set status to `deferred`, populate `decision` with rationale and conditions for revisiting, set `decision-date`
- Fill in the **Decision** section of the proposal body with the full rationale
- Add a decision entry to the Proposal Log
- If approved, inform the user they can use the realize_proposal workflow to create a task

# Output

- Proposal with a recorded decision
- Decision rationale in both frontmatter and body

# Notes

- The agent does not make the decision — the human does
- If the reviewer needs more information before deciding, the agent should research and update the proposal
- A proposal can be re-reviewed: moving from `deferred` back to `reviewing` is valid
