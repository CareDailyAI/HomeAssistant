# Care Daily Edge Documentation

This add-on bridges your Home Assistant devices to the Care Daily Cloud platform for real-time monitoring and analytics.

<a href="https://github.com/CareDailyAI/HomeAssistant/blob/main/care_daily_device_bridge/docs/installation-guide.pdf" target="_blank" rel="noopener noreferrer">📄 Open the Installation Guide (PDF, opens in a new tab)</a>

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
   - Turn **Early Preview Features** on or off (see below).

## Early Preview Features

Some features ship turned off while they are still being finished. To try one, go to **App Configuration** > **Early Preview Features**, check the feature, and select **Save Early Preview Features**. Your choice is kept across restarts and add-on updates until you change it.

> [!WARNING]
> Early preview features may contain bugs or stability issues, and they can change or be removed in a future update.

| Feature | What it adds |
| --- | --- |
| **MQTT Server** | Installs and manages a local Mosquitto MQTT broker for devices on your network, and adds **MQTT Server** to the sidebar. Devices that use it need Home Assistant to keep the same IP address; see [Give Home Assistant a Fixed IP Address](https://github.com/CareDailyAI/HomeAssistant/blob/main/care_daily_device_bridge/guides/STATIC_IP_ADDRESS.md). |

## Configuration Options

The add-on supports the following options via the **Configuration** tab in Home Assistant.

<!-- BEGIN GENERATED: addon-options -->
<!-- Do not edit inside this block. Regenerate with `python -m tools.docs generate`. -->

Generated from `config.yml` by `python -m tools.docs generate`. Descriptions come from `docs/_data/doc_annotations.yml`.

| Option | Type | Required | Default | Description |
| --- | --- | --- | --- | --- |
| `allowed_device_categories` | list of str | yes | `hardware`, `mobile_app`, `service`, `kiosk_display` | Care Daily device categories the bridge is allowed to expose. Entities outside these categories are filtered out before publishing. |
| `attribute_blacklist_contains` | list of str | yes | `_com.`, `_org.`, `_net.`, `_io.` | An entity attribute whose name contains any of these strings is dropped before publishing. Matching is case-sensitive. |
| `attribute_blacklist_keys` | list of str | yes | `icon`, `entity_picture`, `display_precision`, `release_summary`, `release_url`, `attribution`, `editable`, `min`, `max`, `step` | Entity attribute names dropped before publishing, so Home Assistant bookkeeping never reaches cloud telemetry. A name must match in full; letter case is ignored. |
| `attribute_blacklist_prefixes` | list of str | yes | `android.`, `com.`, `appInfo_`, `largeIcon_`, `infoText_` | An entity attribute whose name starts with any of these strings is dropped before publishing. Matching is case-sensitive. |
| `attribute_blacklist_suffixes` | list of str | yes | `_is_clearable` | An entity attribute whose name ends with any of these strings is dropped before publishing. Matching is case-sensitive. |
| `auto_add_future_devices` | bool | no | `false` | Automatically expose and assign newly discovered Home Assistant entities to the cloud on startup. |
| `care_daily_cloud_base_url` | list of str | yes | `https://app.peoplepowerco.com`, `https://sboxall.peoplepowerco.com` | Care Daily cloud platform API endpoints offered during cloud discovery. |
| `cloud_id` | int | no | none | Setup-wizard prefill: numeric id of the cloud instance to preselect for unattended setup. Leave unset for interactive setup. |
| `cloud_url` | str | no | `https://sboxall.peoplepowerco.com` | Setup-wizard prefill: base URL of the cloud instance to preselect for unattended setup. |
| `command_opt_in_domains` | list of str | yes | empty list | Deprecated and retained for backward compatibility. Previously opted into security-critical domains; commands forwarded by Care Daily Cloud are now trusted directly, with security filtering performed upstream before dispatch to Home Assistant. |
| `db_path` | str | no | `/data/devices.db` | File path where the local SQLite database is stored. Must be writable. |
| `excluded_entity_domains` | list of str | yes | `button`, `update`, `scene`, `automation`, `script`, `conversation`, `tts`, `todo`, `notify` | Home Assistant entity domains never published to the cloud. The defaults are domains Care Daily Cloud does not consume yet, or that describe Home Assistant itself rather than a physical device; widen the list as cloud support expands. |
| `ha_refresh_interval` | int | yes | `10` | Interval, in seconds, at which the bridge refreshes entity state information from Home Assistant. |
| `heartbeat_interval_seconds` | int | no | `60` | Interval, in seconds, between gateway health status heartbeats. |
| `hub_area` | str | no | empty string | Default Home Assistant area assigned to the virtual hub device. |
| `hub_name` | str | no | empty string | Optional custom display name for the Home Assistant bridge hub. |
| `location_id` | int | no | none | Setup-wizard prefill: numeric id of the Care Daily location to register against for unattended setup. |
| `location_name` | str | no | empty string | Setup-wizard prefill: Care Daily location name to register against when no `location_id` is supplied. |
| `max_devices_per_message` | int | no | `10` | Maximum number of devices included per MQTT registry payload. |
| `nightly_sync_time` | str | no | `03:00` | Scheduled daily synchronization time in 24-hour `HH:MM` form, for example `03:00`. |
| `passcode` | str | no | redacted | Setup-wizard prefill: one-time passcode used for passcode login during unattended setup. Treat as a credential; prefer leaving it unset and logging in from the Web UI. |
| `password` | password | no | redacted | Setup-wizard prefill: Care Daily account password used for unattended setup. Treat as a credential; prefer leaving it unset and logging in from the Web UI. |
| `registry_add_inter_chunk_delay_seconds` | float | no | `60.0` | Delay, in seconds, between successive bulk device onboarding chunks, used to avoid cloud rate limiting. |
| `session_cookie_secure` | bool | no | `false` | Mark the session cookie `Secure`. Set this only when the Web UI is genuinely reached over HTTPS; over plain http the browser drops a Secure cookie and the session breaks outright. |
| `setup_wizard_enabled` | bool | no | `false` | Run cloud login, device registration and MQTT credential retrieval automatically at startup from stored credentials (headless setup). Also requires `cloud_id`, `cloud_url`, `username` and `password` (or `passcode`), plus `location_id` or `location_name`. |
| `show_experimental_features` | bool | no | `false` | Show Experimental Features. Off by default. Experimental features are not ready for production and may be unstable. While this is off, App Configuration does not show Early Preview Features, the sidebar lists no preview, and every preview's pages answer 404, even on an install that turned a preview on earlier. Turn it on to show the Early Preview Features section, where each preview can then be turned on separately. |
| `time_zone` | str | no | empty string | System time zone used for timestamp conversions. |
| `username` | str | no | empty string | Setup-wizard prefill: Care Daily account email or phone number used for unattended setup. |

Defaults shown as `redacted` hold credentials. Set them through the add-on **Configuration** tab, never by committing a value to this repository.

<!-- END GENERATED: addon-options -->

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
If you run into any other problem or have a question:

* **Email:** [support@caredaily.ai](mailto:support@caredaily.ai). No account needed. Include the add-on version shown on the **Info** tab.
* **GitHub:** if you have a GitHub account, you can also [open an issue](https://github.com/CareDailyAI/HomeAssistant/issues/new).
