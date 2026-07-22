# Architecture notes

## Storage layout

The deployment separates transient downloads from organized media:

| Host path | Purpose |
| --- | --- |
| `/cache_downloads` | Completed download staging on SSD |
| `/cache_downloads_incomplete` | Incomplete download staging on SSD |
| `/srv/midias/filmes` | Final movie library |
| `/srv/midias/series` | Final series library |
| `/srv/midias/animes` | Final anime library |
| `/srv/midias/mangas` | Final manga library |
| `/srv/docker/<service>/config` | Persistent container configuration |

These paths are configurable in the public Compose example through `.env`.

## Media workflow

1. Sonarr or Radarr requests a release through the configured indexer integration.
2. qBittorrent downloads the content into SSD staging.
3. Sonarr or Radarr imports, renames, and organizes the completed content.
4. Bazarr searches for subtitles against the final library.
5. Jellyfin indexes the organized files and exposes them to clients.

## Manga workflow

The manga subsystem is a separate Python application composed of provider adapters, an update worker, cover generation, and a local management API. Chapters are normalized into CBZ archives and stored in a Jellyfin-visible library.

Provider availability and terms can change. Any deployment must respect the relevant source's terms, copyright, and local law.

## Deployment targets

- **Ubuntu Server:** primary and validated target.
- **Windows with WSL2:** experimental bootstrap path.
- **Other Linux distributions:** possible, but not covered by the private installer validation.

## Boundaries of the public edition

The public repository demonstrates system design and deployment structure. It excludes service databases, production configuration, credentials, licensing code, customer-specific settings, and private automation used by the complete installer.
