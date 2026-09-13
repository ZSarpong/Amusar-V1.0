# Airtable Tracks Table — Field List

Copy these fields when creating the base.

## Core Identity
- track_id (Single line text) — Primary field, unique
- title (Single line text)
- artist (Single line text or Link to Artists)
- featured_artists (Multiple select or Link to Artists)
- producer (Single line text)
- composer (Single line text)
- publisher (Single line text)

## Classification
- genre (Single select)
- subgenre (Single line text)
- mood (Single select) — use the controlled list from docs/moods.md
- style (Multiple select or Long text)
- language (Single select: en, instrumental, other)
- bpm (Number)
- musical_key (Single line text)

## Audio & Technical
- duration_seconds (Number)
- explicit_status (Single select: clean, explicit, radio_edit)
- version_type (Single select: original, instrumental, clean, explicit, radio)
- file_format (Single select: mp3, wav, flac, aac)
- codec (Single line text)
- bitrate (Number)
- sample_rate (Number)
- channels (Number)
- audio_file_url (URL)
- cover_artwork_url (URL)

## Rights & Status
- copyright_owner (Single line text)
- master_rights_owner (Single line text)
- publishing_rights_owner (Single line text)
- territory_restrictions (Single line text or Multiple select)
- licensing_status (Single select)
- distribution_status (Single select)
- review_status (Single select: planned, draft, review, approved, published)
- is_playable (Formula) — `IF(AND({review_status}="published", {audio_file_url}!=""), TRUE(), FALSE())`

## Meta
- release_date (Date)
- track_number (Number)
- lyrics (Long text)
- notes (Long text)
- created_at (Created time)
- updated_at (Last modified time)
