# Pillar Manager Documentation

Pillar Manager is an integrated Home Assistant add-on for installing, updating, and managing Pillar dashboard card packages without HACS.

## Features

- **No HACS Required**: Direct card package management using Home Assistant Core WebSocket API and Ingress.
- **Private & Public Workflows**: Install cards directly from private development ZIP bundles or from the verified public GitHub release catalog.
- **Resource Management**: Automatically creates and updates `/local/community/pillar/pillar-cards.js?v=<version>` Lovelace module resources by ID without duplicate entries.
- **Safety & Recovery**: Automatic backup of previous releases before upgrading, one-click rollback, and offline file repair.
- **Media Preservation**: Ensures required `/media/pillar/rooms` and `/media/pillar/scenes` folders exist while strictly preserving all customer media.

## Dashboard Refresh Notice

After installing or updating cards, open browser dashboards cache JavaScript modules. Hard refresh your browser (Ctrl+F5 on Windows, Cmd+Shift+R on Mac) or reload the companion app page to execute the newly deployed version.
