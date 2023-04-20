# Geyserwise MAX IoT - Local network firmware
Geyserwise max IoT panel with Wifi and MQTT communication.

## Firmware
Use the latest firmware from the [firmware](./firmware/) directory. A simple way to do that is to use a Wemos D1 mini and flash it via USB. Setting up WIFI and MQTT. 

And then desoldering it from the D1 mini using a hot air station. Before transplanting it to the display board.
## Example replacement
**Care!!** you want to use a hot air station if you can to remove the old chip. The ESP12 is a drop-in replacement for the chip it ships with.

You can also use a Wemos D1 mini to burn the firmware, then transplant the chip to this PCB.

This PCB is fairly sensitive, so take care not to bubble the PCB when lifting the old one.

[A great video on replacing Tuya based wifi chips](https://www.youtube.com/watch?v=d_HpkIiWC3Y&ab_channel=digiblurDIY)

![a4a5bd2e928cde07002df260528d5dc72f08261d](https://user-images.githubusercontent.com/3243014/183018265-a6c1255a-5d1d-4866-90fb-7c0b67b4b9d1.jpeg)

## WIFI
When the device starts up, it will be in AP mode. Join this wifi device, and it will open your browser to complete the WIFI setup. 

![bcfab1686717fb0ed1b7b80175327d8421673d4a](https://user-images.githubusercontent.com/3243014/183018742-6bc05e29-fab0-46b3-b8bc-b254f5ac3cf9.jpeg)

![19c7df2ff6e08e8f0023bca099860e5e15098f41](https://user-images.githubusercontent.com/3243014/183018749-933d93c7-fd7b-402e-9b3f-cb42b4a491eb.jpeg)

 - Set your home Wifi details
 - Set your MQTT server (home assistant mosquitto for example)

![a9702b9e7a9399120115262e955376e57db9ed7b](https://user-images.githubusercontent.com/3243014/183018758-35b827db-b694-406e-9929-b5eb52ad24b9.jpeg)

Once it successfully connects to your MQTT server, you should be able to see the device on your network. 

Check your router for the new IP address, which you can browse to to manage the device / reboot it, upload new firmware. 

## MQTT explorer example
![Screenshot 2022-08-05 at 08 31 10](https://user-images.githubusercontent.com/3243014/183018238-c2636b6b-c90b-44f5-bb92-38d4509a08a3.png)
![Screenshot 2022-08-05 at 08 31 02](https://user-images.githubusercontent.com/3243014/183018247-2067188f-b38c-41bf-b003-810c07d436d2.png)

## Home assistant
See the sample configs, found in the [home assistant](./home%20assistant/) folder.

### MQTT sensors
This makes use of MQTT sensors, MQTT select and MQTT climate.  

Add this to your `configuration.yaml`, check your configuration and reload your home assistance instance. It should start pulling information into HA. 

Be sure to merge it with your existing MQTT configuration if you have.

[home assistant/configuration.yaml](home%20assistant/configuration.yaml)

![MQTT Climate Integration](./home%20assistant/mqtt_climate_integration.png)

### Lovelace Dashboard

The example dashboard makes use of the [mushroom cards](https://github.com/piitaya/lovelace-mushroom), be sure to install that if you would like to make use of it. Also available through [HACS](https://hacs.xyz/)

[home assistant/lovelace_dashboard.yaml](home%20assistant/lovelace_dashboard.yaml)
![Lovelace Dashboard](./home%20assistant/lovelace_dashboard.png)
