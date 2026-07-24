# Care Daily Device Bridge - Home Assistant Addon

This addon bridges your Home Assistant devices to the Care Daily Cloud platform for real-time monitoring and analytics.

## Installation

## How to Add This Repository to Home Assistant

To install add-ons from this repository, you can add it to your Home Assistant instance automatically by clicking the badge below:

[![Open your Home Assistant instance and show the add add-on repository dialog with a specific repository URL pre-filled.](https://my.home-assistant.io/badges/supervisor_add_addon_repository.svg)](https://my.home-assistant.io/redirect/supervisor_add_addon_repository/?repository_url=https%3A%2F%2Fgithub.com%2FCareDailyAI%2FHomeAssistant)

Alternatively, you can add it manually:

1. Navigate to your Home Assistant dashboard.
2. Go to **Settings** > **Add-ons** > **Add-on Store**.
3. Click the three dots (overflow menu) in the top-right corner and select **Repositories**.
4. Copy and paste the URL of this repository:
   ```text
   https://github.com/CareDailyAI/HomeAssistant
   ```
5. Click **Add**. The repository will now appear in your list of repositories.
6. Close the dialog. The Care Daily add-ons will now be visible and available for installation in the Add-on Store.

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

- `db_path`: Database file path (default: `/data/care_daily_bridge.db`)

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

- GitHub Issues: [Report an issue](https://github.com/peoplepower/home-assistant/issues)
- Documentation: See `/docs` folder for detailed technical documentation

## Development

See [DEVELOPER_README.md](docs/DEVELOPER_README.md) for development setup and testing instructions.
