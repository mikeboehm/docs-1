# Wifi Guide

## Connecting a Device to WiFi

![Wifi Settings](/img/screenshots/wifi-settings.png)

To connect your devices to a WiFi network choose 'Wireless LAN', put in your
network's SSID and, if the network is encrypted, enter a passphrase.

__NOTE:__ The device will automatically determine your network's encryption (if
any) and connect using the provided passphrase, there's no need to specify the
encryption type.

###Changing your SSID and/or Passphrase

On the Raspberry Pi and Beaglebone, it is possible to change your wifi SSID or Passphrase after downloading the `.img`. 

Currently this can be done using the small config [writer tool](https://github.com/petrosagg/resin-net-config). This is a temporary tool and will be phased out very soon.

Your `network.config` file should look something like this, but `[SSID]` and `[passphrase]` should be substituted for your network settings.
```
[service_home_wifi]
Type = wifi
Name = [SSID]
Passphrase = [passphrase]
```

### Multiple WiFi Connections

Though we currently don't support multiple WiFi SSIDs through the user
interface, this can be achieved by manually editing a configuration file on your SD card. See the [custom network guide][custom-network] for details on how to do this.

## Raspberry Pi

The [Raspberry Pi][rpi] can be expanded to connect to a WiFi network by
installing an adapter:-

### Known Working Devices

* [Pi Hut USB WiFi Adapter][pi-hut-usb] - Small form-factor and works right out
  of the box!
* [TP-Link Nano Router][nano-router] - Though this isn't strictly a WiFi
  adapter, it does enable you to connect to WiFi network using the ethernet port
  of the Pi and is known to work correctly with Resin.io. As a result no further
  configuration is required.
* [Adafruit Miniature Wifi (802.11B/G/N) Module][adafruit]
* [EP-N8531][epn8531]
* Generally speaking, WiFi devices listed over at the [elinux rpi wifi page][elinux] or devices which use one of the `linux-firmware-ath9k`, `linux-firmware-ralink` and `linux-firmware-rtl8192cu` firmwares should work correctly.

### Beaglebone Black

Always run the Beaglebone black from a 5VDC 1A minimum supply when using a Wifi Dongle. You may need to use an extension cable to move the dongle away from the planes of the PCB, as often times there is too much interference for the wifi dongles to work correctly. Sometimes standoffs will work. We also have had instances where when placed in a metal case, there can be Wifi issues as well. It will also help to use a dongle with a real antenna on it.

Have a look at this list of [wifi dongles][bbb-wifi-list] that are known to be compatible with the beaglebone black.

### Configuration

__Important Note:__ Wifi adapters drain a lot of power which unfortunately
causes power issues with the Raspberry Pi if you try to *hotswap* them in
(adding a WiFi adapter to your Pi *after* power-on), so __ensure__ you connect
your WiFi device prior to switching on your Pi to avoid instability.

### Troubleshooting

If you have issues connecting with the WiFi device, first check to ensure the
SSID and passphrase are correct. If they are, try rebooting with an ethernet
cable plugged in, then booting again with just WiFi.

__NOTE:__ There is a known bug in the connection manager ConnMan, which makes it impossible for resin devices to connect to wifi routers that have no passphrase at all. For the time being please try use password protected wifi networks to connect your devices.

If neither of these approaches work, please let us know!

[custom-network]:/pages/configuration/custom-network.md

[rpi]:http://www.raspberrypi.org/
[nano-router]:http://www.amazon.com/TP-LINK-TL-WR702N-Wireless-Repeater-150Mpbs/dp/B007PTCFFW
[adafruit]:http://www.adafruit.com/products/814
[epn8531]:http://www.amazon.com/BestDealUSA-EP-N8531-150Mbps-802-11n-Wireless/dp/B00AT7S060
[elinux]:http://elinux.org/RPi_USB_Wi-Fi_Adapters
[pi-hut-usb]:http://thepihut.com/products/usb-wifi-adapter-for-the-raspberry-pi
[bbb-wifi-list]:http://elinux.org/Beagleboard:BeagleBoneBlack#WIFI_Adapters
