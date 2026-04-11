This workflow belongs to the Proposals shard. Ensure you have @init-prop.md in context before continuing.

# Workflow: Realize Proposal

Take an approved proposal and create a Projects task from it. This bridges the proposal system into the execution system.

# Input

- Proposal artifact in `approved` status
- (Optional) Additional context or scope refinements for the task

# Prerequisites

- The Projects shard must be loaded (@init-proj.md)
- The proposal must be in `approved` status

# Actions

## Stage 1: Prepare

- Read the approved proposal fully
- Load the Projects shard: @init-proj.md
- Determine the task increment (use the proposal's increment unless overridden)

## Stage 2: Create Task

- Get the next task number: `flint helper type newnumber Task`
- Create a new task using @tmp-proj-task-v0.1.md
- Set the task status to `todo`
- Populate the task:
  - **Context** — include a wikilink to the source proposal and a summary of the motivation
  - **Related Documents** — link to the source proposal
  - **Task Description** — derived from the proposal's Proposed Approach, scoped to actionable implementation
  - **Task Requirements** — concrete checkboxes derived from the proposal's approach
  - **Definition of Done** — verifiable criteria based on the proposal's recommendation
  - **Notes** — reference the proposal for full background
- Add a Task Log entry noting the task was created from the proposal

## Stage 3: Link Back

- Update the proposal's `spawned-task` frontmatter field with a wikilink to the new task
- Add a Proposal Log entry noting the task was created
- Report the created task to the user

# Output

- New Projects task in `todo` status, linked to the source proposal
- Proposal updated with `spawned-task` field

# Notes

- The task should be self-contained enough to work without reading the full proposal, but should link back for context
- If the proposal's scope is large, consider suggesting multiple tasks rather than one monolithic task
- The realize workflow does not change the proposal's status — it remains `approved`
