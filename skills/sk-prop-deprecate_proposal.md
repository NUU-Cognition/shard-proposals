# Skill: Deprecate Proposal

Mark a proposal as deprecated when it is superseded by another proposal or is no longer relevant.

# Input

- Proposal to deprecate
- (Optional) Reason for deprecation
- (Optional) Superseding proposal reference

# Actions

- Set the proposal `status` to `deprecated`
- Add a deprecation entry to the Proposal Log with:
  - Date (YYYY-MM-DD format)
  - Reason for deprecation
  - Link to superseding proposal if applicable
- If a superseding proposal is specified, add a "Supersedes" note in the Related Documents section of the new proposal
- Report the deprecation to the user

# Notes

- Deprecated proposals remain in the filesystem but are excluded from active dashboard views
- Use this status when a proposal is replaced by a better-scoped proposal, the context has changed, or the topic is no longer relevant
- The proposal number is preserved to maintain referential integrity
