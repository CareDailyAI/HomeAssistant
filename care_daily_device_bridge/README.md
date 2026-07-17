# Care Daily Device Bridge - Home Assistant Addon

This addon bridges your Home Assistant devices to the Care Daily Cloud platform for real-time monitoring and analytics.

## Installation

### Install from Repository

Click the badge below to automatically add this repository to your Home Assistant instance:

[![Add Repository to My Home Assistant](https://my.home-assistant.io/badge/supervisor_add_addon_repository.svg)](https://my.home-assistant.io/redirect/supervisor_add_addon_repository/?repository_url=https%3A%2F%2Fgithub.com%2FCareDailyAI%2FHomeAssistant)

Alternatively, you can add it manually:

1. Navigate to your Home Assistant dashboard.
2. Go to **Settings** → **Add-ons** → **Add-on Store**.
3. Click the three dots (overflow menu) in the top-right corner and select **Repositories**.
4. Copy and paste the repository URL:
   ```text
   https://github.com/CareDailyAI/HomeAssistant
   ```
5. Click **Add**. The repository will now appear in your list.
6. Find "Care Daily Device Bridge" in the Add-on Store and click **Install**.


## Configuration

After installation:

1. **Start the addon** (it will create the initial database)
2. **Open the Web UI** by clicking "Open Web UI" or navigating to the addon's port
3. **Configure your Care Daily Cloud credentials**:
   - Navigate to the Configuration page
   - Enter your Care Daily Cloud API credentials
   - Select devices to monitor
4. **Save** and the bridge will start syncing data

### Configuration Options

The addon supports the following configuration options (in the Configuration tab):

- `ha_refresh_interval`: How often the bridge refreshes Home Assistant state and UI data (default: `10` seconds, clamped between `2` and `3600`).
- `care_daily_cloud_base_url`: The Care Daily cloud base URLs used for discovery (defaults to `https://app.peoplepowerco.com`, `https://eu.caredaily.ai`, `https://sboxall.peoplepowerco.com`).

## Architecture Support

This addon supports the following architectures:

- ✅ `aarch64` (ARM 64-bit: Raspberry Pi 4/5, Home Assistant Green, ODROID-N2)
- ✅ `amd64` (x86 64-bit: Intel/AMD processors)

**Note:** Older architectures (armv7, armhf, i386) are no longer supported by Home Assistant.

## Features

- 🔄 Real-time device state synchronization
- 🌐 MQTT integration with Care Daily Cloud
- 📊 Device health monitoring
- 🔐 Secure credential management
- 🎯 Selective device exposure
- 📈 Virtual hub health reporting (WiFi, disk, battery, versions)

## Troubleshooting

### Addon won't start

1. Check the logs in the **Log** tab
2. Ensure the database path is writable
3. Verify your Care Daily Cloud credentials are correct

### Devices not syncing

1. Check that devices are selected in the Configuration page
2. Verify MQTT credentials are valid
3. Check the addon logs for error messages

### Port conflicts

If port 5000 is already in use:

1. Go to the **Configuration** tab
2. Change the port mapping to a different port (e.g., 5001)
3. Restart the addon

## Support

For issues, feature requests, or questions:

- GitHub Issues: [Report an issue](https://github.com/CareDailyAI/HomeAssistant/issues)

