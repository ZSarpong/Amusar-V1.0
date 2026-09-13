# Context Engine

Modular input → decision output.

## Inputs (Context Snapshot)
See `schemas/context-snapshot.example.json`

- time_of_day / is_daylight / season
- weather (condition, temperature, severe)
- location (permission-gated)
- activity / mood
- local & worldwide events
- listening_history_summary
- explicit_request

## Outputs
See `schemas/context-output.example.json`

- recommended_queue
- target_gain
- transition_duration_ms
- energy_level
- mood_classification
- shuffle_behaviour
- playback_priority
- explanation (internal)
- confidence

Keep explanations internal for analysis only.
