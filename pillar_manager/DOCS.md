# Pillar Manager Documentation

Pillar Manager is an integrated Home Assistant add-on for installing, updating, and managing dashboard card packages without HACS.

## Supported Packages

Pillar Manager provides independent lifecycle management for:
- **Pillar Cards**: Core Pillar cards for rooms, scenes, and dashboards.
  - Install path: `<config>/www/community/pillar/`
  - Dashboard Lovelace resource: `/local/community/pillar/pillar-cards.js?v=<version>`
  - Media directories: `/media/pillar/rooms/` and `/media/pillar/scenes/`
- **Bunker Cards**: Bunker management, command, and status card collection.
  - Install path: `<config>/www/community/bunker/`
  - Dashboard Lovelace resource: `/local/community/bunker/bunker-cards.js?v=<version>`
  - Media directory: `/media/pillar/bunker/`

## Configuration Options

Manage packages via Home Assistant **Settings** → **Add-ons** → **Pillar Manager** → **Configuration**:
- `enable_pillar_cards` (default: `false`): Enable automated download and management of Pillar Cards.
- `enable_bunker_cards` (default: `false`): Enable automated download and management of Bunker Cards.
- `auto_update` (default: `false`): Enable background updates when new releases appear in the public catalog.
- `check_interval_hours` (default: `6`): Frequency in hours for scheduled catalog checks (1–24).

> **Note**: After modifying configuration options, save and restart the add-on for changes to take effect.

## Features

- **No HACS Required**: Direct card package management using Home Assistant Core WebSocket API and Ingress.
- **Private & Public Workflows**: Install cards directly from private development ZIP bundles or from verified public GitHub release catalogs.
- **Resource Management**: Automatically creates and updates Lovelace module resources by ID without duplicate entries.
- **Safety & Recovery**: Automatic backup of previous releases before upgrading, one-click rollback, and offline file repair.
- **Media Preservation**: Ensures required media folders exist while strictly preserving all customer files.
- **Independent Failure Isolation**: Issues in one package do not affect other packages.

## Dashboard Refresh Notice

After installing or updating cards, open browser dashboards cache JavaScript modules. Hard refresh your browser (Ctrl+F5 on Windows, Cmd+Shift+R on Mac) or reload the companion app page to execute the newly deployed version.
