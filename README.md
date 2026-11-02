# loko-data (update branch)

Remote schedule-data updates for Loko (train tracker).

- `manifest.json` — the delta chain (base checkpoint + delta entries).
- `deltas/` — small encrypted row-level deltas (AES-256-GCM, same key
  as the shipped asset). A delta blob contains no readable schedule
  data; the manifest contains only hashes, dates, and row counts.

No full database snapshot here: a fresh install gets its snapshot
from the app itself (the shipped asset). Clients that fall too far
behind the chain wait for the next app update.

See `docs/data-rebuild.md` in the (private) loko repo for the release
procedure. Do not rewrite chain history: deltas only append.
