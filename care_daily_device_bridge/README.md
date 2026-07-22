# Care Daily Bridge

Care Daily Bridge is a Home Assistant app for selecting Home Assistant entities, mapping them to Care Daily cloud destinations, and managing Care Daily cloud connectivity from a web UI.

This README covers Home Assistant app usage only. Local execution and Docker workflows live in `docs/README.md`.

## What The App Does

- Discovers Home Assistant entities.
- Lets operators choose which entities should be exposed.
- Monitors bridge hardware health (WiFi, Power, Battery).
- Supports per-device MQTT topic and cloud destination mapping.
- Supports remote device control commands (e.g., turn on/off/brightness) from Care Daily cloud.
- Discovers and manages Care Daily cloud instances.
- Handles cloud authentication and cloud connection status from the UI.

## App Configuration

Set these values from the app `Configuration` tab in Home Assistant.

| Option | Default | What it is for |
| --- | --- | --- |
| `ha_refresh_interval` | `10` | How often the bridge refreshes Home Assistant state and UI data, in seconds. The runtime clamps the value to a minimum of 2 seconds and a maximum of 3600 seconds. |
| `care_daily_cloud_base_url` | `["https://app.peoplepowerco.com", "https://eu.caredaily.ai", "https://sboxall.peoplepowerco.com"]` | The Care Daily cloud base URLs the bridge uses for cloud discovery and connection setup. |

Home Assistant provides the supervisor token used for API access, so the app does not require Home Assistant URL or token fields in its configuration.

## Publishing Releases

Releases are automatically calculated and published by GitHub Actions pipelines based on **Conventional Commits** pushed to the repository.

### Release Commit Rules

To trigger a release build on `main`, commit subjects (or bodies) must follow Conventional Commits format:

| Commit Type | Version Bump | Example |
| --- | --- | --- |
| `fix:`, `perf:`, `refactor:`, `revert:` | **Patch** (e.g., `v0.3.0` &rarr; `v0.3.1`) | `fix: resolve MQTT reconnection delay` |
| `feat:` | **Minor** (e.g., `v0.3.0` &rarr; `v0.4.0`) | `feat: support new device type` |
| `BREAKING CHANGE:` or `!:` | **Major** (e.g., `v0.3.0` &rarr; `v1.0.0`) | `feat!: update payload contract` |

> [!NOTE]
> Commits using `chore:`, `docs:`, `style:`, `test:`, or `ci:` do **not** trigger a version bump and will cause the release publishing step to be skipped.

### Release Workflows

- **Stable Release (`publish-stable.yml`)**: Pushing qualifying commits (`feat:`, `fix:`, etc.) to `main` calculates the next semantic version, tags the commit, updates configuration metadata, and publishes the image to GitHub Container Registry (`ghcr.io`).
- **Prerelease (`publish-prerelease.yml`)**: Manually dispatched on feature/fix branches to compute and publish prerelease builds (e.g., `v0.3.1-beta.1`).

