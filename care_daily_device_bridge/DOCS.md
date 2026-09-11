# Care Daily Edge Documentation

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
- Click **Register & Connect →** to register your gateway device. The edge gateway automatically fetches and stores your secure MQTT connection credentials.

### 4. Step 4: Configure Devices & Cloud Options
- **Target Cloud Server**: Confirm or select the cloud server where your devices will be assigned.
- **Set selected cloud as default**: (Enabled by default) Automatically sets the selected cloud server as the default target.
- **Add all existing devices to selected cloud**: (Enabled by default) Automatically exposes all existing Home Assistant devices and assigns them to the selected cloud.
- **Automatically add future devices**: (Enabled by default) Automatically assigns any newly discovered Home Assistant devices to the cloud upon startup.
- Click **Finish & Save Devices →** to complete the setup.

---

### Dismissing or Re-opening the Wizard

* **Closing it for now**: The **×** in the top-right header hides the wizard for this visit only. It opens again the next time you go to the Home Assistant Devices page, so use this to look at the page behind it without giving anything up.
* **Dismissing the Wizard**: **Dismiss Wizard** in the footer stops it opening automatically from then on. This is the same setting as the **Dismiss setup wizard** checkbox in **App Configuration**, so you can reverse it there.
* **Re-opening the Wizard**: Go to **App Configuration** and click **Launch Setup Wizard**. This runs the wizard once, whatever the **Dismiss setup wizard** setting says.
* **Bringing the Wizard back permanently**: On the same page, uncheck **Dismiss setup wizard** and save. The wizard then displays automatically on the Home Assistant Devices page again until you dismiss it or finish it.

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

* **`db_path`**: The file path where the local database is stored (Default: `/data/devices.db`).
* **`ha_refresh_interval`**: The rate (in seconds) at which the edge gateway refreshes entity state information from Home Assistant (Default: `10`; clamped to 2–3600).
* **`care_daily_cloud_base_url`**: Supported Care Daily cloud platform API endpoints.
* **`hub_name`**: Optional custom display name for the Home Assistant edge hub (Default: empty, which falls back to `Care Daily Edge`).
* **`time_zone`**: System time zone for timestamp conversions (Default: empty).
* **`hub_area`**: Default Home Assistant area/location assigned to the virtual hub device (Default: empty).
* **`auto_add_future_devices`**: Automatically expose and assign newly discovered Home Assistant entities to the cloud on startup (Default: `false`).
* **`nightly_sync_time`**: Scheduled daily synchronization time (Default: `03:00`).
* **`heartbeat_interval_seconds`**: Interval (in seconds) between gateway health status heartbeats (Default: `60`).
* **`max_devices_per_message`**: Maximum number of devices included per MQTT registry payload (Default: `10`).
* **`registry_add_inter_chunk_delay_seconds`**: Delay (in seconds) between successive bulk device onboarding chunks to prevent rate-limiting (Default: `60.0`).
* **`allowed_device_categories`**: List of enabled device categories (`hardware`, `mobile_app`, `service`, `kiosk_display`).
* **`excluded_entity_domains`**: Entity domains that are never published to the cloud. The defaults (`button`, `update`, `scene`, `automation`, `script`, `conversation`, `tts`, `todo`, `notify`) are domains Care Daily Cloud does not consume yet, or that describe Home Assistant itself rather than a physical device. Adjust the list as cloud support expands.
* **`command_opt_in_domains`**: Security-critical domains this deployment re-enables for remote control. Empty by default, which means neither the cloud MQTT command channel nor the Web UI's test-command button may operate a `lock`, `alarm_control_panel`, `valve`, or `water_heater` — naming one here opts that single domain in. Domains that run user-defined actions (`script`, `scene`, `automation`, `button`, `input_button`, `remote`, `homeassistant`) cannot be opted in at all, because their effect is not visible in the command and enabling them would bypass every other entry in the list.
* **`session_cookie_secure`**: Set to `true` when the Web UI is reached over HTTPS so the session cookie is marked `Secure` (Default: `false`).
* **`setup_wizard_enabled`**: Run cloud login, device registration, and MQTT credential retrieval automatically at startup from stored credentials (headless setup). When enabled, also provide `cloud_url`, `username`, and `password` (or `passcode`), plus `location_name`. See the [Operator Quickstart](../guides/README_OPERATOR.md) for the full headless key list and environment-variable equivalents.
* **`attribute_blacklist_keys`**, **`attribute_blacklist_contains`**, **`attribute_blacklist_prefixes`**, **`attribute_blacklist_suffixes`**: Four independent lists of entity-attribute filters applied before publishing, so that Home Assistant bookkeeping (app package names, icons, release notes) never reaches cloud telemetry. Each ships a default list; see [MQTT Attribute Mapping](../architecture/MQTT_ATTRIBUTE_MAPPING.md#filtered-attributes) for the shipped values and the matching rules.

## Troubleshooting

### Add-on won't start
* Check the **Log** tab at the top of the add-on page for detailed error logs.
* Ensure the database path is set to a writable directory. `/data` is the add-on's persistent volume and is always writable, so keep `db_path` under it (the default is `/data/devices.db`).

### Devices are not updating in the cloud
* Ensure you have selected and saved the target devices on the Home Assistant Devices page.
* Check the add-on logs to verify that the MQTT connection to the Care Daily Cloud was established successfully.

### Automatic restarts (Watchdog)
* The add-on exposes a health endpoint that Home Assistant checks while the add-on runs.
* Turn on **Watchdog** on the add-on page to have Supervisor restart the add-on automatically if it stops responding.

### Direct Port Access
* The add-on is reached through Home Assistant Ingress, and port `5000` is **not** published to your network by default. Use **Open Web UI** or the sidebar panel; no host port is involved and nothing can conflict with it.
* If you need to reach the Web UI directly (for example from a script outside Home Assistant), go to the **Configuration** tab, set a Host port under **Network**, and restart the add-on. The UI is then also available at `http://<home-assistant-host>:<port>/`.
* Direct access bypasses Home Assistant's authentication. If you publish a port, set **`session_cookie_secure`** appropriately and treat the UI as network-reachable.

### Need Help?
If you encounter any other issues or have questions, please open a new issue on GitHub: [Create a new issue](https://github.com/CareDailyAI/HomeAssistant/issues/new).
