# Skill: Capture As Proposal

Retroactively capture existing work, discussion, or research as a proposal artifact. Use this when a decision discussion has already happened informally and should be recorded as a formal proposal.

# Input

- Existing discussion, research, or decision context to capture
- (Optional) Decision status if a decision was already made

# Actions

- Create a proposal using the @tmp-prop-proposal-v0.1.md template. Get the next proposal number with `flint helper type newnumber Proposal`.
- Set the `increment` field to link to the parent increment using `[[Hyperlink]]` syntax. To determine the increment:
  1. If the discussion was under a specific increment, use that
  2. If the proposal clearly relates to an active increment, use that
  3. Otherwise, default to the latest `.A` adhoc increment
- Populate all sections from the existing discussion or research
- If a decision was already made:
  - Set status to the appropriate decision status (`approved`, `rejected`, or `deferred`)
  - Populate the `decision`, `decision-date`, and Decision section
  - If approved and a task already exists, set `spawned-task`
- If no decision has been made, set status to `open`
- Add a Proposal Log entry noting this was captured retroactively
- Report the created proposal to the user
