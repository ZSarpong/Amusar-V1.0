# Amusar V1.0

**Music intelligence engine for [Muusio.com](https://muusio.com)**  
Primary system: **ANALYZE · SEARCH · PLAY**

> Build Amusar as an intelligent music environment that analyzes a listener’s situation and plays the right music for that moment.

---

## Core Principles

- Single-page, single-viewport, no scrolling
- Black background, dominated by the Muusio animation
- Minimal, cinematic, uncluttered interface
- Intelligence operates **behind** the interface
- Never claim music, integrations, or features exist until implemented and verified

### Visible interface (non-negotiable)
1. Existing full-screen Muusio animation
2. Small `MUUSIO.COM` signature
3. Status text: `AMUSAR V1.0 · ENGINE UNDER DEVELOPMENT`
4. AMUSAR V1.0 information trigger
5. Sound control: `ENTER WITH SOUND` → `SOUND ON` when active

All additional information opens inside the existing full-screen transparent popup.

---

## Development Stages (Current Priority)

1. **Catalogue and metadata foundation**
2. Approved original music ingestion
3. Reliable playback and queue engine
4. Listener commands and saved music
5. Context-based recommendations
6. Weather and time adaptation
7. Event intelligence
8. Analytics and recommendation refinement
9. Artist onboarding and rights management
10. Scalable audio delivery

---

## Catalogue Rules

- Target: 50 excellent original songs, 10–20 artists, 5–8 coherent moods
- Never display an uncreated song as completed
- Never describe planned songs as playable
- Never duplicate one song and pretend the copies are different
- Only count a song after its audio file, metadata **and** rights status are confirmed
- Clearly distinguish: planned → draft → review → approved → published

---

## First-Listen Experience

1. Attempt to deliver the Amusar welcome introduction
2. Transition gently into the selected music
3. Fade music in smoothly
4. Remember that the introduction has been presented on that device
5. On later visits, proceed directly to the music experience

Browsers may block autoplay → preserve `ENTER WITH SOUND` as the clear one-tap entry.

---

## Welcome Message (polished meaning)

> Hello. I am Amusar, a music intelligence developed by Muusio Technology with one aim: to entertain. Tell me the genre, mood or moment you are in for. I will analyze, search and play the right music for you. This is our welcome note from the whole Muusio team. We are grateful to have you on board.

---

## Repository Structure

```
Amusar-V1.0/
├── README.md
├── docs/
│   ├── data-model.md          # Full expanded data requirements
│   └── development-stages.md
├── schemas/
│   ├── track.json             # Example track record
│   ├── context-snapshot.json  # Context engine input
│   └── context-output.json    # Context engine output
└── .gitignore
```

---

## Connected Services (roles)

| Service       | Responsibility                                      |
|---------------|-----------------------------------------------------|
| SoundBreak    | Licensed music creation, artist collaboration       |
| Airtable      | Catalogue records, metadata, rights, editorial status |
| Cloudflare    | Production audio storage, delivery, caching         |
| AccuWeather   | Permission-based weather signals                    |
| Mixpanel      | Plays, skips, saves, completion, retention analytics |
| Spotify / Apple Music | Approved linking & discovery only (not full catalogue streaming) |

---

**Status**: Engine under development.  
Live site: [muusio.com](https://muusio.com)
