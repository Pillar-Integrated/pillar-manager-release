# Pillar Add-ons for Home Assistant

Official distribution repository for **Pillar Manager** and dashboard packages.

## Installation

1. In your Home Assistant instance, navigate to **Settings** → **Add-ons** → **Add-on Store**.
2. Click the three-dots menu (⋮) in the top-right corner and select **Repositories**.
3. Add the following repository URL:
   ```
   https://github.com/Pillar-Integrated/pillar-manager-release
   ```
4. Click **Add**, then close the dialog.
5. In the Add-on Store, find **Pillar Manager** and click **Install**.
6. Once installation completes, enable **Start on boot** and **Watchdog**, then click **Start**.
7. Click **Open Web UI** or access Pillar Manager directly from the sidebar.

## Requirements & Permissions
- No HACS, SSH, host networking, or container privilege escalation required.
- Prebuilt multi-architecture container images (`aarch64` and `amd64`) are pulled directly from GitHub Container Registry (`ghcr.io`) without requiring customer registry credentials.

## Documentation
See [Pillar Manager Documentation](pillar_manager/DOCS.md) for full details.
