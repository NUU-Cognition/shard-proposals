---
id: c8f3b5d2-4e9a-5f7b-0c1d-6e8f2a3b4c5d
tags:
  - "#dashboard"
  - "#prop/proposals"
  - "#managed/shard/prop"
  - "#read-only"
---

```dataviewjs
function formatName(p) {
  return p.file.name.replace(/^\(Proposal\)\s*/, '');
}

function statusIcon(status) {
  const icons = {
    'draft': '📝',
    'open': '📬',
    'reviewing': '🔎',
    'approved': '✅',
    'rejected': '❌',
    'deferred': '⏸️',
    'deprecated': '🚫'
  };
  return icons[status] || '📝';
}

function proposalNumber(p) {
  const match = p.file.name.match(/^\(Proposal\)\s*(\d+)/);
  return match ? parseInt(match[1]) : 9999;
}

function formatDate(d) {
  if (!d) return "—";
  return String(d).split('T')[0];
}

const proposals = dv.pages('#prop/proposal').where(p => p.file.path.startsWith('Mesh/Types/Proposals/'));

const activeStatuses = ['open', 'reviewing', 'draft'];

for (const status of activeStatuses) {
  const label = status.charAt(0).toUpperCase() + status.slice(1);
  dv.header(1, statusIcon(status) + ' ' + label);
  const group = proposals.where(p => p.status === status)
    .array().sort((a, b) => proposalNumber(a) - proposalNumber(b));
  if (group.length === 0) {
    dv.paragraph("*None*");
  } else {
    dv.table(["#", "Proposal", "Increment"],
      group.map(p => [
        proposalNumber(p),
        dv.fileLink(p.file.path, false, formatName(p)),
        p.increment ?? "—"
      ])
    );
  }
}

// Decided
dv.header(1, "✅ Approved");
const approved = proposals.where(p => p.status === 'approved')
  .array().sort((a, b) => proposalNumber(b) - proposalNumber(a));
if (approved.length === 0) {
  dv.paragraph("*None*");
} else {
  dv.table(["#", "Proposal", "Decision Date", "Spawned Task"],
    approved.map(p => [
      proposalNumber(p),
      dv.fileLink(p.file.path, false, formatName(p)),
      formatDate(p['decision-date']),
      p['spawned-task'] ?? "—"
    ])
  );
}

dv.header(1, "❌ Rejected");
const rejected = proposals.where(p => p.status === 'rejected')
  .array().sort((a, b) => proposalNumber(b) - proposalNumber(a));
if (rejected.length === 0) {
  dv.paragraph("*None*");
} else {
  dv.table(["#", "Proposal", "Decision Date"],
    rejected.map(p => [
      proposalNumber(p),
      dv.fileLink(p.file.path, false, formatName(p)),
      formatDate(p['decision-date'])
    ])
  );
}

dv.header(1, "⏸️ Deferred");
const deferred = proposals.where(p => p.status === 'deferred')
  .array().sort((a, b) => proposalNumber(b) - proposalNumber(a));
if (deferred.length === 0) {
  dv.paragraph("*None*");
} else {
  dv.table(["#", "Proposal", "Decision Date"],
    deferred.map(p => [
      proposalNumber(p),
      dv.fileLink(p.file.path, false, formatName(p)),
      formatDate(p['decision-date'])
    ])
  );
}
```
