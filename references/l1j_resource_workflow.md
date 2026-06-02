# L1J Resource Coordination

Use this reference only to coordinate Lineage/L1J resource work inside a
checkpoint.

For extraction, lookup, archive inspection, TW13081901 parsing, item image
resolution, actor action manifests, sound overlays, and generated manifests,
use `l1j-sprite-resource-kit` as the source authority.

If this reference and `l1j-sprite-resource-kit` disagree, the kit wins.

## Harness Responsibilities

- Define the checkpoint scope and stop condition.
- Require profile-first lookup through `l1j-sprite-resource-kit`.
- Require kit scripts and indexes instead of loading full TW13081901 or client
  archive inventories into model context.
- Record source ids, source paths, generated outputs, verification evidence,
  risks, and owner review needs.
- Keep generated files out of the project root unless the project convention
  explicitly requires them there.
- Keep Git staging focused on the checkpoint.

## Required Routing

Use the kit for:

- client profile list/show/validate
- `polyid`, `gfxid`, `invgfx`, and `grdgfx` resolution
- item UI and ground/drop image lookup
- TW13081901 actor/action lookup
- PAK/IDX inspection
- SPX/SPR/TIL parsing or export
- protected text/XML decode
- source-backed manifest generation

Do not duplicate kit extraction rules in this harness. If a resource rule needs
to change, update `l1j-sprite-resource-kit` first, then keep this reference as a
thin coordination layer.

## Closeout

Use this shape for L1J resource checkpoints:

```text
State:
Profile:
Source ids:
Generated output:
Verified:
Not verified:
Risks:
Needs owner judgment:
Next checkpoint:
Git / handover:
```
