# Next Steps

## Robust Shared List Sync

The current import flow preserves independent item additions by merging items by `id` and appending incoming-only items. A more complete collaboration model should add:

- Item-level `updatedAt` timestamps, refreshed whenever item details, purchase status, notes, image, price, or quantity change.
- Item-level merge rules that keep the newest version when both sides edit the same item.
- Delete tombstones with `deletedAt` so removed items do not reappear from older shared copies.
- An optional import summary or conflict review UI for cases where both users changed the same item or list metadata.

## Import Authoring Help

The Import menu now includes a downloadable sample JSON file for users or AI tools that want to generate compatible lists externally. Future docs could expand this into a short schema guide with required fields, optional fields, and examples for grouped and ungrouped lists.
