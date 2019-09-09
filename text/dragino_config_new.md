
# Dragino Configuration

1. Connecto to dragino wifi
2. Open website at address:
   - dragino-`<same code of WiFi Access Point>`
3. Username: root, Password: dragino
4. Sensor -> IoT Server
   - IoT Server: LoRaWAN
   - Log Debug Info: `<any value>`
   - Save
5. Sensor -> LoRa / LoRaWAN
   - Server Address: `eu.thethings.network` (check)
   - Gateway ID: `<same number of gateway from The Things Newtork>`
   - Mail Address: `<your.email@email.com>`
6. Network -> Internet Access
   - Access Internet Via: WiFi Client
   - SSID: `<ssid of the network>`
   - Encryption: WPA2 (check)
   - Password: `<password of the network>`
   - Display Net Connection: `<any website like www.google.com>`
   - Save
7. Network -> Access Point
   - Enable WiFi AP: uncheck
   - Save
8. USAVED CHANGES
   - Check all CHANGES
   - Save & Apply
9. Wait until dragino's Access Point is disabled
10. Power off and power on dragino.
