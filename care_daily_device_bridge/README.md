# Care Daily Edge - Home Assistant Addon

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
3. **Step 3: Select Location & Register**: Pick your home location and click **Register & Connect →**. The edge gateway registers your device and automatically retrieves and stores secure MQTT cloud connection settings.
4. **Step 4: Configure Devices & Cloud**:
   - Confirm your target cloud server.
   - Choose whether to set the selected cloud as default.
   - Choose whether to automatically expose and assign all existing Home Assistant devices.
   - Choose whether to automatically add newly discovered future devices.
   - Click **Finish & Save Devices →** to complete setup.

> 💡 **Closing, Dismissing and Re-opening**: The top-right **×** hides the wizard for this visit only — it opens again next time you visit the devices page. **Dismiss Wizard** stops it opening automatically, the same as the **Dismiss setup wizard** setting in App Configuration. To re-open it, go to **App Configuration** and click **Launch Setup Wizard**.

---

## Configuration Options

The addon supports the following configuration options (in the Configuration tab):

- `db_path`: Database file path (default: `/data/devices.db`)

The full option list, with defaults, is in the add-on's **Documentation** tab ([DOCS.md](DOCS.md#configuration-options)).

## Architecture Support

This addon supports the following architectures:

- ✅ `aarch64` (ARM 64-bit: Raspberry Pi 4/5, Home Assistant Green, ODROID-N2)
- ✅ `amd64` (x86 64-bit: Intel/AMD processors)

**Note:** 32-bit ARM (`armv7`/`armhf`) and `i386` are not built or published for this add-on.

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

### Reaching the Web UI directly

The addon is served through Home Assistant Ingress and does not publish port 5000 to your network, so it cannot conflict with anything. Use **Open Web UI** or the sidebar panel.

If you specifically need direct access from outside Home Assistant:

1. Go to the **Configuration** tab
2. Set a Host port under **Network** (e.g., 5000, or 5001 if that is taken)
3. Restart the addon

Direct access bypasses Home Assistant's authentication — see the **Documentation** tab before enabling it.

## Support

For issues, feature requests, or questions:

- GitHub Issues: [Report an issue](https://github.com/CareDailyAI/HomeAssistant/issues)
- Documentation: See `/docs` folder for detailed technical documentation

## Development

See [README_DEVELOPER.md](../guides/README_DEVELOPER.md) for development setup and testing instructions.
