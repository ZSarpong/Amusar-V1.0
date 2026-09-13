# Amusar V1.0 — Expanded Data Model

## 1. Catalogue / Track Metadata

### Tracks table (Airtable / DB)

| Field | Type | Required | Notes |
|-------|------|----------|-------|
| track_id | Text (unique) | Yes | e.g. `MUS-001` |
| title | Text | Yes | |
| artist | Link / Text | Yes | |
| featured_artists | Multi-link | No | |
| producer | Text / Link | No | |
| composer | Text / Link | No | |
| publisher | Text | No | |
| genre | Single select | Yes | |
| subgenre | Text | No | |
| mood | Single select | Yes | Controlled list (5–8 values) |
| style | Text / Multi | No | |
| language | Single select | Yes | `en`, `instrumental`, etc. |
| bpm | Number | Recommended | |
| musical_key | Text | Recommended | e.g. `Am`, `C#m` |
| duration_seconds | Number | Yes | |
| explicit_status | Single select | Yes | `clean` / `explicit` / `radio_edit` |
| version_type | Single select | Yes | `original` / `instrumental` / `clean` / `explicit` / `radio` |
| release_date | Date | Recommended | |
| track_number | Number | No | |
| file_format | Single select | Yes | `mp3` / `wav` / `flac` / `aac` |
| codec | Text | Yes | |
| bitrate | Number | Yes | kbps |
| sample_rate | Number | Yes | Hz |
| channels | Number | Yes | 1 or 2 |
| audio_file_url | URL | Yes | Cloudflare location |
| cover_artwork_url | URL | Recommended | |
| lyrics | Long text | No | |
| copyright_owner | Text | Yes | |
| master_rights_owner | Text | Yes | |
| publishing_rights_owner | Text | Yes | |
| territory_restrictions | Multi / Text | No | |
| licensing_status | Single select | Yes | |
| distribution_status | Single select | Yes | |
| review_status | Single select | Yes | `planned` → `draft` → `review` → `approved` → `published` |
| is_playable | Formula / Checkbox | — | Only true when published + audio + rights confirmed |
| created_at / updated_at | Date-time | System | |
| notes | Long text | No | Internal |

**Supporting tables**: Artists, Moods, Versions

**Hard rule**: A track is only countable / playable after audio file + metadata + rights are confirmed.

---

## 2. Listener Profile & Behaviour

### Listeners / Devices
- listener_id / device_id (anonymous preferred)
- first_visit_at, welcome_presented (boolean)
- preferred_moods, preferred_genres (derived)
- last_active_at, total_plays, total_listening_seconds
- saved_track_ids, playlist_ids

### Interaction Events
- play_start, play_progress, skip, complete, save, unsave, repeat
- explicit_command (raw or parsed {genre, mood, moment})
- session_start / session_end

---

## 3. Context Snapshot (Engine Input)

```json
{
  "timestamp": "ISO-8601",
  "time_of_day": "morning | afternoon | evening | night",
  "is_daylight": true,
  "season": "spring | summer | autumn | winter",
  "weather": {
    "condition": "clear | cloudy | rain | snow | storm | ...",
    "temperature_c": 18.5,
    "feels_like_c": 17.0,
    "severe": false
  },
  "location": {
    "permission_granted": true,
    "city": "optional",
    "region": "optional",
    "country": "optional",
    "lat": null,
    "lon": null
  },
  "activity": "unknown | working | commuting | relaxing | exercising | sleeping | ...",
  "mood": "user_stated | inferred | unknown",
  "local_events": [],
  "worldwide_events": [],
  "listening_history_summary": {
    "recent_moods": ["calm", "energetic"],
    "recent_skips": 2,
    "last_tracks": ["MUS-003", "MUS-017"]
  },
  "explicit_request": null
}
```

Location access requires permission + safe fallback. Never expose sensitive coordinates publicly.

---

## 4. Context Engine Output (Internal)

```json
{
  "recommended_queue": ["MUS-012", "MUS-005", "MUS-041"],
  "target_gain": 0.85,
  "transition_duration_ms": 2500,
  "energy_level": 0.4,
  "mood_classification": "calm_focus",
  "shuffle_behaviour": "light | full | none",
  "playback_priority": "context | explicit | history | default",
  "explanation": "Rainy evening + recent calm history → selected low-energy ambient set",
  "confidence": 0.78
}
```

Kept internal for analysis and tuning.

---

## 5. Playback & Session State (Runtime)

- current_track_id, position_seconds, duration_seconds
- is_playing, queue, history_in_session
- shuffle, repeat_mode, gain, crossfade_ms, auto_gain_enabled

Controls remain hidden behind the minimal experience until explicitly requested.

---

## 6. Analytics Events (Mixpanel-style)

Core early events:
- `amusar_welcome_shown`
- `enter_with_sound_clicked`
- `track_play_start` / `track_skip` / `track_complete`
- `track_save` / `track_unsave`
- `explicit_request_submitted`
- `context_decision_made`
- `session_duration`
- recommendation acceptance / rejection (inferred)

---

## 7. Operational / Rights

- Artists table (onboarding, SoundBreak linkage)
- Editorial workflow states + timestamps
- Cloudflare object keys / CDN URLs
- External discovery links (Spotify / Apple Music IDs only)
- System flags: autoplay_blocked, location_permission, welcome_flag, engine_version
