![preview](https://raw.githubusercontent.com/amanpoudel665-tech/cloud-to-disk-sync/main/preview.svg)

# PlaylistPillar

## Overview

**PlaylistPillar** is a self-hosted, metadata‑preserving music catalog engine that transforms your streaming‑platform playlists into durable, browsable archives you control. Unlike typical downloaders that treat songs as disposable files, PlaylistPillar treats every track like a museum artifact: it retains album art, embedded metadata, release‑year tags, and even cross‑references track listings against public discography databases. Built on a lightweight Docker foundation, this tool gives you a private, offline‑friendly library that stays organized, searchable, and immune to platform‑side deletions.

[![Download](https://raw.githubusercontent.com/amanpoudel665-tech/cloud-to-disk-sync/main/button.svg)](https://amanpoudel665-tech.github.io/cloud-to-disk-sync/)

## Why PlaylistPillar Exists

Streaming services are landlords, not owners. One licensing dispute, one account shutdown, or one region block can wipe years of curation in an instant. PlaylistPillar exists to decouple your love for music discovery from the fragility of cloud‑dependent APIs. It preserves the *context* of a playlist—not just the audio—so your carefully sorted mood mixes, workout lists, and deep‑cut explorations remain intact on your own infrastructure.

## Core Philosophy

**Preservation > Downloading**  
The tool focuses on fidelity of structure. When you archive a playlist, PlaylistPillar maintains the original ordering, track metadata, and album artwork. If a song disappears from the streaming service, your local copy still shows the cover, artist, album, and track number—so you always know exactly what you had.

## Key Features

- **Metadata‑First Architecture** – Every export includes embedded ID3 tags, album art (JPEG/PNG), and release year from MusicBrainz and Discogs cross‑references.
- **Docker‑Native Deployment** – Runs in any Docker environment with a single `compose.yaml` configuration; no system‑level dependencies needed.
- **Responsive Web Dashboard** – Manage archives, view storage usage, and browse imported playlists from any device via a clean, mobile‑friendly interface.
- **Multi‑Language Interface** – Dashboard and export logs available in English, Spanish, French, German, Japanese, and Portuguese.
- **24/7 Background Worker** – Once you queue a playlist, the worker handles rate‑limiting, retries, and progress tracking without blocking your browser session.
- **Playlist Diff Engine** – Re‑scan a previously archived playlist to see which tracks were removed, added, or changed since your last export.
- **Export Formats** – Save your archives as structured folders (`Artist / Album / Track.mp3`) or as a single compressed `.pillar` bundle with embedded metadata.

## 24/7 Customer Support

We believe infrastructure should never keep you from your music. PlaylistPillar includes a built‑in diagnostics module that generates a support‑ready snapshot of your configuration—logs, container health, and network status—which you can share directly with our team. Response time is typically under two hours, and we provide live chat within the dashboard during business hours (UTC‑5 to UTC+2). No ticket number required; just click the support icon.

## Use Cases

- **Collectors** who want to archive rare or region‑locked releases before they vanish from streaming platforms.  
- **DJs and Podcasters** who need to freeze a playlist’s exact track order and metadata for broadcast logs or cue sheets.  
- **Fans of Obscure Music** who discover albums that stream only in certain countries—PlaylistPillar keeps those finds accessible forever.  
- **Families** sharing a single Docker host where each member maintains their own curated archives without interfering with others’ libraries.

## Getting Started in 3 Steps

1. **Configure your environment** – Provide your streaming‑platform API token (optional, for faster metadata enrichment) and set your storage volume in `compose.yaml`.  
2. **Launch the dashboard** – Point your browser to the assigned port, then paste a playlist link or upload a `.txt` file containing URLs.  
3. **Let the pillar build** – The system processes tracks in the background, preserving artwork and metadata, then notifies you via the dashboard when your archive is ready.

## Repository Structure

```
playlistpillar/
├── backend/                    # Python‑based metadata engine (Flask + Celery)
│   ├── workers/                # Background task handlers
│   ├── models/                 # Database schemas (SQLite / PostgreSQL)
│   └── metadata_enricher/      # MusicBrainz & Discogs fallback logic
├── frontend/                   # Vue.js dashboard with dark/light themes
│   ├── components/             # Reusable UI elements
│   └── locales/                # Internationalization files
├── docker/                     # Dockerfile, compose.yaml, .env.example
├── docs/                       # API reference, architecture diagrams
├── tests/                      # Unit and integration test suites
└── LICENSE                     # MIT
```

## Roadmap for 2026

- **Batch import wizards** – Import dozens of playlists at once from a CSV or JSON export.  
- **Offline AI tagging** – On‑device machine learning to suggest genre and mood tags for tracks missing metadata.  
- **Playlist mirroring** – Automatically re‑archives your most‑used playlists every weekend.  
- **Mobile companion app** – Browse and export archives directly from iOS/Android.

## Technical Highlights

- **No external rate‑limit pain** – The backend queues requests in a token‑bucket pattern, respecting service limits without dropping tracks.  
- **SQLite by default, PostgreSQL optional** – Start small, grow without service disruption.  
- **Artwork optimization** – Album covers are compressed to WebP (with PNG fallback) to save disk space while retaining quality.  
- **Checksum integrity** – Each exported track includes a SHA‑256 hash recorded in a sidecar manifest, so you can verify nothing corrupted over time.

## FAQ

**How much storage does a playlist need?**  
Approximately 80–120 MB per hour of music at 320 kbps, plus 1–3 MB per album for artwork. A 50‑song playlist typically uses 300–450 MB.

**Can I migrate my existing downloads?**  
Yes. Place your current music folders into the volume, and PlaylistPillar will scan them, infer playlist structure from folder names, and enrich any missing metadata.

**Does it require an internet connection?**  
Only during initial metadata enrichment. Once a track is archived, it can be browsed fully offline.

**Is my API token stored securely?**  
Tokens are encrypted at rest using AES‑256 and never logged. You may also choose to skip API authentication entirely by using anonymous public metadata lookups (slower but zero data exposure).

## License

This project is licensed under the MIT License. You are free to use, modify, and distribute it for personal or commercial purposes, provided the original copyright notice is preserved.

[LICENSE](https://opensource.org/licenses/MIT)

## Disclaimer

**Note on streaming service compliance**  
PlaylistPillar is designed for personal archival use and does not bypass geographic restrictions, DRM, or subscription tiers. All metadata enrichment is performed against public, openly‑available databases. Users are responsible for ensuring that their usage complies with the terms of service of any integrated platform. The maintainers assume no liability for misuse.

---

*Built for the 2026 era of music ownership—where your library outlives any subscription.*  
[![Download](https://raw.githubusercontent.com/amanpoudel665-tech/cloud-to-disk-sync/main/button.svg)](https://amanpoudel665-tech.github.io/cloud-to-disk-sync/)