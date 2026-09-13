# Development Stages

Follow this order strictly. Preserve the live minimal interface at every step.

## Stage 1 — Catalogue & Metadata Foundation
- Define controlled Mood list (5–8 values)
- Create Tracks schema in Airtable (or equivalent)
- Implement `is_playable` gate
- No public playback of unapproved tracks

## Stage 2 — Approved Original Music Ingestion
- Ingest only tracks with confirmed audio + metadata + rights
- Batch review process
- Distinguish planned / draft / review / approved / published

## Stage 3 — Reliable Playback & Queue Engine
- Play / Pause / Next / Previous / Seek
- Queue management
- Smooth transitions & crossfading
- Gain + automatic gain
- Repeat protection
- Hidden behind the minimal UI

## Stage 4 — Listener Commands & Saved Music
- Explicit commands (genre / mood / moment)
- Save / unsave
- Device-level welcome flag
- Basic listening history

## Stage 5 — Context-Based Recommendations
- Modular context engine
- Time-of-day + basic mood/history signals
- Internal explanation + confidence

## Stage 6 — Weather & Time Adaptation
- AccuWeather integration (permission-based)
- Day/night + seasonal signals

## Stage 7 — Event Intelligence
- Local & worldwide event signals (high-level)

## Stage 8 — Analytics & Refinement
- Mixpanel (or equivalent) events
- Recommendation acceptance loops

## Stage 9 — Artist Onboarding & Rights
- SoundBreak collaboration flow
- Full rights tracking

## Stage 10 — Scalable Audio Delivery
- Cloudflare production pipeline
- Caching, CDN, performance

---

**Before every change**
1. Read the current project
2. Preserve the working visual interface
3. Identify the exact requested modification
4. Change only what was requested
5. Do not redesign adjacent elements
6. Do not add speculative visible features
7. Build and verify
8. Publish only the validated revision
