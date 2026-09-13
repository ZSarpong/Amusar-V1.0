# Catalogue Module

- Load only tracks where `review_status === "published"` and audio + rights are confirmed.
- Enforce the `is_playable` gate at every query.
- Never surface planned, draft, or review tracks to the playback engine.
- Support filtering by mood, genre, energy, bpm range, explicit status.
