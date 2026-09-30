# Changelog

All notable changes to the Pillar Manager add-on are documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## v2026.9.3.2

### Fixed
- Fixed browser static asset caching across Home Assistant Ingress: appended deterministic version cache-busting query strings (`?v=2026.9.3.2`) to Manager-owned static asset requests (`app.css`, `app.js`, `pillar-logo.png`).
- Configured explicit `Cache-Control: no-cache, no-store, must-revalidate` headers for `index.html` and long-term immutable caching for versioned static assets, preventing stale frontend code from executing following add-on updates without requiring manual hard browser refreshes.
- Fixed theme media-query conflict where unconditional `@media (prefers-color-scheme: dark)` on `:root` partially overrode explicit Home Assistant Light mode when the client browser or OS was set to dark. Restricted media query fallbacks strictly to `:root:not([data-theme])`.
- Added frontend diagnostic marker `FRONTEND_VERSION` logged to console on initialization and CSS version token `--pillar-manager-css-version`.

## v2026.9.3.1

### Fixed
- Fixed fatal temporal-dead-zone JavaScript initialization error (`ReferenceError: Cannot access 'TABS' before initialization`) preventing tab navigation, status polling, and alert configuration management from loading.
- Reorganized frontend startup sequence into a deterministic `initApp()` routine ensuring all state, element references, tab constants, and event handlers are fully initialized before execution.
- Fixed theme synchronization in Home Assistant Ingress: replaced standalone `@media (prefers-color-scheme)` media queries with active Home Assistant frontend theme detection (`home-assistant` element theme state, `meta[name="color-scheme"]`, and container style detection) falling back to browser `prefers-color-scheme` and dark theme.
- Added explicit `html[data-theme="light"]` and `html[data-theme="dark"]` CSS token bindings and real-time observer for live Home Assistant theme toggling without page reloads.
- Restored Bunker Alerts UI loading and interaction via the now accessible Bunker tab.

## v2026.9.3

### Added
- Tabbed interface layout (`Main | Pillar | Bunker`) organizing general Manager settings, Pillar Cards, and Bunker Cards into dedicated views.
- URL hash navigation (`#main`, `#pillar`, `#bunker`) preserving active tab across page reloads and browser history back/forward navigation.
- Automatic system-aware Light and Dark mode theming via `@media (prefers-color-scheme)` with semantic CSS custom properties.
- Dedicated retry action and user-friendly error display for Bunker Alert Configuration failures.

### Changed
- Refactored Alerts Manager to authoritatively derive the Bunker Cards installation directory from the package definition (`getPackageInstallDir(getPackage('bunker-cards'))`).
- Implemented lazy loading of Bunker Alert configuration when opening the Bunker tab, preventing unnecessary polling cycles.
- Improved error handling in `getAlertsConfig()` to return structured diagnostic errors on malformed YAML.

## v2026.9.2

### Added
- Web UI for managing site-specific Bunker alert overrides in Pillar Manager.
- Source-of-truth reader for Pillar-owned `alerts.yaml` with dynamic discovery of configurable alert thresholds, friendly labels, and units.
- Sparse delta generator for site-owned `alerts-overrides.yaml` storing only customized settings differing from Pillar defaults.
- Automatic cleanup and removal of redundant overrides when values are returned to Pillar defaults, including pruning of empty parent hierarchies.
- Automatic deletion of `alerts-overrides.yaml` when all site overrides are removed.
- Visual status indicators distinguishing `PILLAR DEFAULT` vs `SITE OVERRIDE` with effective threshold values.
- Individual "Reset to Pillar Default" per setting and confirmed "Reset All to Pillar Defaults" for the site.
- Obsolete override path detection and warning banner for settings removed in future Bunker releases.
- Quick filter toggle ("Show Overrides Only") to easily view customized thresholds.
- Backend REST API endpoints: `GET /api/bunker/alerts`, `POST /api/bunker/alerts/override`, `POST /api/bunker/alerts/reset`, `POST /api/bunker/alerts/reset-all`.
- Pure-JS zero-dependency YAML parser and serializer (`yaml.js`).

## v2026.9.1

### Added
- Required external Alert Configuration (`alerts.yaml`) support for Bunker Cards releases.
- Multi-asset download and transactional installation ensuring both `bunker-cards.js` and `alerts.yaml` are verified before completion.
- Preservation of site-owned `alerts-overrides.yaml` across installs, upgrades, rollbacks, and repairs.
- Independent management of Bunker Cards (`bunker-cards`) as a second dashboard package.
- Configuration option `enable_bunker_cards` (boolean, default `false`) in Add-on Configuration tab and translations.
- Multi-package architecture with independent versions, provenance, timestamps, rollback backups, and recovery states.
- Dedicated dashboard resource tracking for `/local/community/bunker/bunker-cards.js?v=<version>`.
- Automated media directory creation for `/media/pillar/bunker/`.
- Atomic idempotent migration from single-package state schema to v2 package-scoped schema with safety backup.
- Package-aware ZIP uploads validating archive package identity before installation.
- Dual-package Ingress dashboard displaying dedicated cards and management actions for each package.

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
