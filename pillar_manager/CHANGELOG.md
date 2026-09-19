# Changelog

All notable changes to the Pillar Manager add-on are documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## v1.0.3

### Added
- Automated multi-architecture container release builds (`linux/amd64` and `linux/arm64`).
- Candidate image publishing to `ghcr.io/pillar-integrated/pillar-manager-candidate`.
- Release record generation with source commit SHA, release tag, and image index digests.
- Container runtime smoke test validating Node >= 22, native WebSocket/fetch, and Ingress server startup.
- Promotion workflow to copy tested candidate images to public `ghcr.io/pillar-integrated/pillar-manager` without rebuilding.
- Public GHCR first-publish package visibility bootstrap verification.
- Safe idempotent retries and serialized public promotion concurrency guards.

## v1.0.2

### Added
- Configuration-driven initial installation of Pillar Cards via Add-on Configuration tab (`enable_pillar_cards`).
- Native translation labels in `translations/en.yaml`.
- Authoritative configuration indicator in Ingress web dashboard.

### Fixed
- Fixed Green startup failure by pinning Node.js 22 on Alpine with `tini` as PID 1.
- Restored official branding artwork (`icon.png` and `logo.png`).

## v1.0.1

### Changed
- Unified repository structure with `pillar_manager/` as the single authoritative add-on source directory.
- Hardened PKZIP parser against Zip Slip path traversal and duplicate entries.

## v1.0.0

### Added
- Initial release of Pillar Manager for Home Assistant.
- Direct Lovelace resource management without HACS.
- Ingress web dashboard with one-click install and rollback capabilities.
- Automated media directory creation (`/media/pillar/rooms`, `/media/pillar/scenes`).
