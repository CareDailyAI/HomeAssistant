# Care Daily Device Bridge Documentation

This add-on bridges your Home Assistant devices to the Care Daily Cloud platform for real-time monitoring and analytics.

## Installation

1. Click **Install** on the add-on page.
2. Once installed, you can enable **Show in sidebar** for quick access to the configuration panel.
3. Click **Start** to start the add-on.

## First-Time Setup Wizard Flow

When you open the Web UI (**Open Web UI**) for the first time, the interactive **First-Time Setup Wizard** automatically opens to guide you through full configuration in 4 easy steps:

### 1. Step 1: Select Cloud Server
Choose your target Care Daily cloud server from the discovered list of environments.

### 2. Step 2: Authenticate Account
Enter your Care Daily account credentials (email or phone number and password) to authenticate with the cloud.

### 3. Step 3: Select Location & Register Device
- Choose your home location from the location dropdown list.
- Click **Register & Connect →** to register your gateway device. The bridge automatically fetches and stores your secure MQTT connection credentials.

### 4. Step 4: Configure Devices & Cloud Options
- **Target Cloud Server**: Confirm or select the cloud server where your devices will be assigned.
- **Set selected cloud as default**: (Enabled by default) Automatically sets the selected cloud server as the default target.
- **Add all existing devices to selected cloud**: (Enabled by default) Automatically exposes all existing Home Assistant devices and assigns them to the selected cloud.
- **Automatically add future devices**: (Enabled by default) Automatically assigns any newly discovered Home Assistant devices to the cloud upon startup.
- Click **Finish & Save Devices →** to complete the setup.

---

### Dismissing or Re-opening the Wizard

* **Dismissing the Wizard**: If you prefer to configure the bridge manually, click **Dismiss Wizard** in the footer or the **×** button in the top-right header. You can also toggle the **Dismiss setup wizard** setting in **System Configuration**.
* **Re-opening the Wizard**: To re-launch the setup wizard at any time, navigate to the Web UI with `?setup=1` (e.g. `http://<bridge-ip>:5000/?setup=1`).

---

## Manual Configuration & Management

If you choose to manage settings manually or make adjustments after completing the wizard:

1. **Cloud Configuration**:
   - Log in using your Care Daily Cloud credentials.
   - Select your location, register the app device, and retrieve MQTT settings.
2. **Home Assistant Devices**:
   - Select individual Home Assistant entities to expose or hide from the cloud.
3. **Selected Devices**:
   - Assign exposed devices to target registered cloud instances or update entity mappings.
4. **System Configuration**:
   - Customize Hub Name, Time Zone, Heartbeat Interval, Auto-Add Future Devices, Nightly Sync Time, or toggle Setup Wizard Dismissal.

## Configuration Options

The add-on supports the following options via the **Configuration** tab in Home Assistant:

* **`db_path`**: The file path where the local database is stored (Default: `/data/care_daily_bridge.db`).
* **`ha_refresh_interval`**: The rate (in seconds) at which the bridge refreshes entity state information from Home Assistant.
* **`care_daily_cloud_base_url`**: Supported Care Daily cloud platform API endpoints.
* **`hub_name`**: Optional custom display name for the Home Assistant bridge hub.
* **`time_zone`**: System time zone for timestamp conversions.
* **`hub_area`**: Default Home Assistant area/location assigned to the virtual hub device.
* **`auto_add_future_devices`**: Automatically expose and assign newly discovered Home Assistant entities to the cloud on startup.
* **`nightly_sync_time`**: Scheduled daily synchronization time (e.g. `03:00`).
* **`heartbeat_interval_seconds`**: Interval (in seconds) between gateway health status heartbeats.
* **`max_devices_per_message`**: Maximum number of devices included per MQTT registry payload (Default: `10`).
* **`registry_add_inter_chunk_delay_seconds`**: Delay (in seconds) between successive bulk device onboarding chunks to prevent rate-limiting (Default: `60.0`).
* **`setup_wizard_enabled`**: Enable automated First-Time Setup Wizard execution on startup.

## Troubleshooting

### Add-on won't start
* Check the **Log** tab at the top of the add-on page for detailed error logs.
* Ensure the database path is set to a writable directory (e.g. `/data/care_daily_bridge.db`).

### Devices are not updating in the cloud
* Ensure you have selected and saved the target devices on the Home Assistant Devices page.
* Check the add-on logs to verify that the MQTT connection to the Care Daily Cloud was established successfully.

### Changing Ports
* If the default port `5000` conflicts with another add-on or integration on your system, go to the **Configuration** tab, change the Host port mapping (under Network) to a different port, and restart the add-on.

### Need Help?
If you encounter any other issues or have questions, please open a new issue on GitHub: [Create a new issue](https://github.com/CareDailyAI/HomeAssistant/issues/new).
