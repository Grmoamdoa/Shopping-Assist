# Next Steps

## Robust Shared List Sync

Completed:

- Item-level `updatedAt` timestamps are refreshed whenever item details, purchase status, notes, image, price, or quantity change.
- Item-level import merge rules keep the newest version when both sides edit the same item.
- Delete tombstones with `deletedAt` keep removed items from reappearing from older shared copies.
- Import summary UI reports added, updated, deleted, retained, unchanged, and orphaned records after file or share-link imports.

Remaining future option:

- A conflict review UI could still be added later if users need to inspect both sides before accepting newest-wins merges.

Stress test findings:

- Three simulated users repeatedly adding, editing, purchasing, deleting, and importing the same list converged to the same item records after full exchange.
- Large add-heavy sharing also converged, but around 450 active item records produced a share link estimate above the current reliability limit, so JSON export is the better path for larger shared lists.
- Tombstones are necessary for sync correctness, but long-lived heavily edited lists may eventually need tombstone cleanup or compaction after all collaborators have received deletions.

Safest follow-up improvements completed:

- Import summaries now include plain-language "changes to notice" when a newer edit, newer deletion, retained deletion, or kept local item affects the result.
- Imports warn when shared data contains dates more than a day ahead, because device clock issues can make newest-change decisions surprising.
- Oversized share links now explain that larger lists or lists with photos should be shared with JSON export instead.

## Import Authoring Help

Completed:

- The Import menu includes a downloadable sample JSON file for users or AI tools that want to generate compatible lists externally.
- The sample JSON now includes item `updatedAt` fields and a deleted-item example.
- The Import menu includes a schema guide covering list, group, item, and tombstone fields.

Remaining future option:

- If the schema grows, move the guide into a standalone document with versioned examples.
