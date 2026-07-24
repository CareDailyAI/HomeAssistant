# Care Daily Device Bridge Documentation

This add-on bridges your Home Assistant devices to the Care Daily Cloud platform for real-time monitoring and analytics.

## Installation

1. Click **Install** on the add-on page.
2. Once installed, you can enable **Show in sidebar** for quick access to the configuration panel.
3. Click **Start** to start the add-on.

## Configuration

After starting the add-on:

1. Click **Open Web UI** in the Home Assistant interface.
2. Navigate to the **App Configuration** page:
   - Select your Care Daily Cloud environment, enter your credentials, and log in.
   - Select your location.
   - Register the app device and fetch the MQTT settings.
3. Go to the **Home Assistant Devices** page:
   - Select the Home Assistant devices you want to expose to the cloud.
   - Click **Save** to persist the list.
4. Go to the **Selected Devices** page:
   - Assign each exposed device to a registered cloud destination.

### Options

The add-on supports the following options via the **Configuration** tab in Home Assistant:

* **`db_path`**: The file path where the local database is stored (Default: `/data/care_daily_bridge.db`).
* **`ha_refresh_interval`**: The rate (in seconds) at which the bridge refreshes entity state information from Home Assistant.
* **`care_daily_cloud_base_url`**: Supported Care Daily cloud platform API endpoints.

## Troubleshooting

### Add-on won't start
* Check the **Log** tab at the top of the add-on page for detailed error logs.
* Ensure the database path is set to a writable directory (e.g. `/data/care_daily_bridge.db`).

### Devices are not updating in the cloud
* Ensure you have explicitly selected and saved the target devices on the App Configuration page.
* Check the add-on logs to verify that the MQTT connection to the Care Daily Cloud was established successfully.

### Changing Ports
* If the default port `5000` conflicts with another add-on or integration on your system, go to the **Configuration** tab, change the Host port mapping (under Network) to a different port, and restart the add-on.

### Need Help?
If you encounter any other issues or have questions, please open a new issue on GitHub: [Create a new issue](https://github.com/CareDailyAI/HomeAssistant/issues/new).
