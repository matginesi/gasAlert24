# WiFi Configuration dragino

If pre-existent data are present, please reset dragino:

- Press toggle button while dragino is running for about 30 seconds.

## Setting up dragino

Connect to dragino access point.
Open on your browser: [10.130.1.1](10.130.1.1)

| Login user and password | |
| --- | --- |
| user: | root |
| pass: | dragino |

## Setting up WiFi connection

- Network > *Internet Access*
  - Select WiFi connection
  - Set WiFi password and SSID
  - Set a page for ping test (like www.google.it)
  - **Save**
- Network > *Access Point*
  - Disable WiFi AP
  - **Save**
- Unsaved changes
  - **Save & Apply**
  - Wait for about 2 minutes and reboot.

## Setting up WLAN connection

- Network > *Internet Access*
  - Select WLAN connection
- Unsaved changes
  - **Save & Apply**
  - Wait for about 2 minutes and reboot.

## Setting up TTN data

- Open [TheThingsNetwork](thethingsnetwork.org) and go to Gateways settings.
- Register a new Gateway with **legacy packed worwarder**
- Copy the address on the back of the dragino and add a number like between (00 00) and (FF FF).
- Add a description.
- Set *Frequency Plan*
- Register your gateway.

Open on your browser dragino IP (based on your network).

- Sensor > LoraWAN
  - Server address: (example) router.eu.thethings.network
  - **Save & Apply**
- Sensor > IOT Server
  - IoT Server: LoRaWAN
  - **Save & Apply**
