# Amusar Engine Modules

Intelligence lives here. Keep the public interface minimal.

```
src/engine/
├── context/          # Context engine (weather, time, mood, events, history)
├── catalogue/        # Track loading, filtering, is_playable gate
├── playback/         # Queue, transitions, gain, crossfade, seek
├── listener/         # Commands, saves, history, device flags
├── analytics/        # Event emission (Mixpanel-ready)
└── index.ts          # Public engine API (ANALYZE · SEARCH · PLAY)
```

**Rules**
- No incomplete engine controls exposed publicly.
- Context decisions stay internal (explanation + confidence).
- Only published + confirmed tracks are returned by catalogue.
- Location requires permission + safe fallback.
