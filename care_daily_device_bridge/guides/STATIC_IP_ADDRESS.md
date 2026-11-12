# Give Home Assistant a Fixed IP Address

The **MQTT Server** in Care Daily Edge runs on your Home Assistant machine.
Devices you set up to use it remember that machine's IP address, such as
`192.168.1.50`, and connect to that address every time.

Most home routers hand out addresses automatically, which is called DHCP, and
a router can give a machine a different address after a restart or a power
cut. If Home Assistant's address changes, your devices keep trying the old one
and stop reporting until they are set up again. The **Dynamic IP (DHCP)
Detected** warning on the MQTT Server page is there to catch this before it
happens.

The fix is to make sure Home Assistant always gets the same address. There
are two ways to do that, and you only need one:

| | Option A: reserve the address in your router | Option B: set a static address in Home Assistant |
| --- | --- | --- |
| Where you make the change | Your router's app or admin page | Home Assistant |
| Best for | Most homes | Routers that cannot reserve addresses |
| Risk | Low. Home Assistant's own settings do not change. | A wrong value can cut off access to Home Assistant until it is fixed on the machine itself. |

## Before you start

Write down Home Assistant's current IP address. You can find it in either
place:

- In Care Daily Edge, on the **MQTT Server** page: it is in the warning and in
  the **Broker Host** field.
- In Home Assistant, under **Settings** > **System** > **Network**: open
  **IPv4** in the **Configure network interfaces** card.

If devices are already set up and working, keep this address. Giving Home
Assistant the address it has now means those devices keep working without any
other change.

## Option A: reserve the address in your router (recommended)

A reservation tells your router to always give Home Assistant the same
address. Nothing changes in Home Assistant.

1. Open your router's app or its admin page in a web browser. The router's
   label or manual tells you how to reach it.
2. Find the list of connected devices. Routers call it something like
   **Clients**, **Devices**, **DHCP clients** or **LAN**. Home Assistant
   usually shows up as **homeassistant**; you can also find it by the address
   you wrote down.
3. Choose that device and look for an option such as **DHCP reservation**,
   **Address reservation**, **Reserve IP**, **Static lease** or **Fixed IP**.
   Reserve the address it has now.
4. Save the change.

Every router is different. If you cannot find the setting, search the web for
your router's brand and model together with "DHCP reservation", or check its
manual.

> [!NOTE]
> The **Dynamic IP (DHCP) Detected** warning stays on the MQTT Server page
> after you reserve the address. Home Assistant still asks the router for an
> address, and now always gets the same one, but Care Daily Edge cannot see
> your router's settings to know that. Once the address is reserved, you can
> ignore the warning.

## Option B: set a static address in Home Assistant

Use this if your router cannot reserve addresses. Take care with each value:
if one is wrong, Home Assistant can drop off your network until the change is
undone on the machine itself. See
[I can't reach Home Assistant after setting a static address](#i-cant-reach-home-assistant-after-setting-a-static-address).

1. In Home Assistant, go to **Settings** > **System** > **Network**.
2. In the **Configure network interfaces** card, open **IPv4**. If the card
   has more than one tab, use the one whose **IPv4** section shows the address
   you wrote down.
3. While **Automatic** is still selected, the current settings are shown
   greyed out. Write down the **IP address**, **Netmask**, **Gateway address**
   and **DNS server**.
4. Select **Static** and fill in:
   - **IP address**: an address that no other device on your network uses.
     The safest choice is one outside the range your router hands out
     automatically; the router's DHCP settings show that range. Keeping the
     current address means devices you have already set up keep working, but
     the router may later give that address to another device as well.
   - **Netmask**, **Gateway address** and **DNS server**: the values you wrote
     down in step 3.
5. Select **Save**. Home Assistant warns that you might lose the connection;
   that is expected while it applies the new address.
6. If you changed the address, open Home Assistant at the new one, for example
   `http://192.168.1.50:8123`, or at `http://homeassistant.local:8123`.

If you chose a different address from the one devices were set up with, set
those devices up again so they learn the new address.

## Check that it worked

1. Optional, but the surest test: restart the machine and confirm the address
   survives. Go to **Settings** > **System**, select the power button in the
   top-right corner, and choose **Reboot system** (you may need to open
   **More options** first). Home Assistant is unavailable for a few minutes
   while it restarts.
2. In Care Daily Edge, open **MQTT Server** and check that **Broker Host** shows
   the address you expect.
3. With option B, the **Dynamic IP (DHCP) Detected** warning is gone. With
   option A it stays, as explained above.

## Troubleshooting

### I can't reach Home Assistant after setting a static address

- Try `http://homeassistant.local:8123` in your browser. It finds Home
  Assistant by name, whatever its address.
- If that does not work, the static settings most likely do not match your
  network. Connect a keyboard and screen to the Home Assistant machine, if it
  has a screen connection, and at the `ha >` prompt run:

  ```text
  network update default --ipv4-method auto
  ```

  (In a terminal that does not show the `ha >` prompt, type
  `ha network update default --ipv4-method auto` instead.) This switches the
  network connection back to automatic, and the router gives Home Assistant an
  address again. Then try option B again, or use option A.
- If your machine has no screen connection, or you are not sure, contact
  support as described below.

### My devices stopped connecting after Home Assistant's address changed

Give Home Assistant its old address back, using option A or option B with that
address. Devices usually reconnect on their own once Home Assistant is back at
the address they know. If you cannot use the old address, set the devices up
again so they learn the new one.

## Need help?

- **Email:** [support@caredaily.ai](mailto:support@caredaily.ai). No account
  needed.
- **GitHub:** if you have a GitHub account, you can also
  [open an issue](https://github.com/CareDailyAI/HomeAssistant/issues/new).

For everything else about the add-on, see the [add-on documentation](../DOCS.md).
