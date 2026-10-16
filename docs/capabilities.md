# Autotech capabilities

## Media management

Unified discovery and lifecycle automation for movies, series, anime, and manga: selection, download coordination, import, renaming, organization, metadata, covers, subtitles, and Jellyfin library refresh.

## Platform engineering

Production targets for Windows and Linux with platform-specific installers, persistent storage, filesystem boundaries, local services, networking, Docker Compose, and systemd integration.

## Product engineering

Licensing, activation, subscriptions, support, updater coordination, release channels, manifests, checkpoints, rollback, and customer-facing product boundaries are treated as product systems rather than isolated scripts.

## User experience

Deep Jellyfin customization, Autotech visual identity, custom navigation, Discover, Downloads, onboarding, support, custom libraries and covers, and PT-BR / EN internationalization.

## Backend development

Python services and local APIs connect discovery providers, download clients, storage, media processing, manga workflows, metadata, and library refreshes. The manga subsystem includes provider abstraction, multi-source retrieval, chapter normalization, CBZ packaging, cover generation, metadata, scheduled updates, and a local API.

## Infrastructure

Containerized services include Jellyfin, Sonarr, Radarr, qBittorrent, Jackett, Bazarr, and FlareSolverr. The Autotech layer coordinates these services across Windows and Linux while preserving staging and organized-library boundaries.

## Release engineering

Platform releases are versioned independently and validated with manifests, cryptographic signatures, SHA-256 checks, smoke tests, backups, checkpoints, rollback procedures, and update infrastructure. Production source and secrets remain private.
