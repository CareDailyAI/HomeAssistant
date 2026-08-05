# Care Daily Device Bridge - Home Assistant Addon

This addon bridges your Home Assistant devices to the Care Daily Cloud platform for real-time monitoring and analytics.

## Installation

### How to Add This Repository to Home Assistant

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

---

## 🧙‍♂️ First-Time Setup Wizard

When you open the Web UI (**Open Web UI**) for the first time, an interactive **First-Time Setup Wizard** automatically displays to guide you through complete hub and cloud configuration:

1. **Step 1: Select Cloud Server**: Select your target Care Daily cloud environment from the list of discovered servers.
2. **Step 2: Authenticate Account**: Enter your Care Daily account email or phone number and password to log in.
3. **Step 3: Select Location & Register**: Pick your home location and click **Register & Connect →**. The bridge registers your device and automatically retrieves and stores secure MQTT cloud connection settings.
4. **Step 4: Configure Devices & Cloud**:
   - Confirm your target cloud server.
   - Choose whether to set the selected cloud as default.
   - Choose whether to automatically expose and assign all existing Home Assistant devices.
   - Choose whether to automatically add newly discovered future devices.
   - Click **Finish & Save Devices →** to complete setup.

> 💡 **Dismissing or Re-opening**: You can dismiss the wizard at any time by clicking **Dismiss Wizard** or the top-right **×** button (or via the **Dismiss setup wizard** setting in System Configuration). To re-open the wizard, append `?setup=1` to the Web UI URL.

---

## Configuration Options

The addon supports the following configuration options (in the Configuration tab):

- `db_path`: Database file path (default: `/data/care_daily_bridge.db`)

## Architecture Support

This addon supports the following architectures:

- ✅ `aarch64` (ARM 64-bit: Raspberry Pi 4/5, Home Assistant Green, ODROID-N2)
- ✅ `amd64` (x86 64-bit: Intel/AMD processors)

**Note:** Older architectures (armv7, armhf, i386) are no longer supported by Home Assistant.

## Features

- 🧙‍♂️ **Interactive First-Time Setup Wizard** for step-by-step account login, location selection, and device assignment
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
- Documentation: See `/docs` folder for detailed technical documentation

## Development

See [README_DEVELOPER.md](docs/guides/README_DEVELOPER.md) for development setup and testing instructions.
