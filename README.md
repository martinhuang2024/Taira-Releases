# Taira Releases

Public distribution repository for Taira Windows binaries and update metadata.

The Taira source repository remains private. This repository contains release metadata and downloadable binaries only.

Expected release assets:

- `TairaSetup-<version>.exe` — Windows x64 installer
- `Taira-Windows-<version>.zip` — updater payload
- `windows-stable.json` — signed stable update manifest
- `SHA256SUMS.txt` — release checksums

Taira checks this endpoint for stable updates:

`https://github.com/martinhuang2024/Taira-Releases/releases/latest/download/windows-stable.json`

Update manifests are signed with Ed25519. The private signing key must never be committed or uploaded here.
