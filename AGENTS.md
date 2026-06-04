Skills are organized into bucket folders under `skills/`:

- `engineering/` — daily code work
- `productivity/` — daily non-code workflow tools
- `misc/` — kept around but rarely used
- `personal/` — tied to my own setup, not promoted
- `in-progress/` — drafts not yet ready to ship
- `deprecated/` — no longer used

Only skills that are **new or modified** relative to upstream (`mattpocock/skills`) must have an entry in `.claude-plugin/plugin.json`. Unmodified upstream skills must not appear there.

Every skill in `engineering/`, `productivity/`, or `misc/` that is new or modified must have a reference in the top-level `README.md` under the "Modified Skills" section. Skills in `personal/`, `in-progress/`, and `deprecated/` must not appear in either.

Each skill entry in the top-level `README.md` must link the skill name to its `SKILL.md`.

Each bucket folder has a `README.md` that lists every skill in the bucket with a one-line description, with the skill name linked to its `SKILL.md`.
