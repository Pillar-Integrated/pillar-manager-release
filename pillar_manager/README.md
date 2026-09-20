# Pillar Manager Add-on

This directory contains the Home Assistant add-on files for Pillar Manager.

- `config.yaml`: Add-on metadata, configuration schema, and Ingress settings.
- `Dockerfile`: Multi-arch Alpine Node.js 22 container definition (`aarch64` and `amd64`).
- `build.yaml`: Supervisor architecture builder configuration.
- `src/`: Backend server, package definitions, installer engine, state store, and Ingress frontend.
  - `src/packages/definitions.js`: Declarative package definitions for Pillar Cards and Bunker Cards.
  - `src/services/state-store.js`: Package-scoped persistent state store with schema migration.
  - `src/services/installer.js`: Package installation, validation, backup, and rollback.
  - `src/services/ha-websocket.js`: Scoped Lovelace resource registration and conflict adoption.
- `DOCS.md`: User documentation displayed in the Home Assistant Add-on Store.

See top-level [README.md](../README.md) for full project documentation and private repository installation steps.
