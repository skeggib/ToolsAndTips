# Raspberry Pi

## Headless Raspbian install

[Headless Raspberry Pi 4 SSH WiFi Setup - desertbot.io](https://desertbot.io/blog/headless-raspberry-pi-4-ssh-wifi-setup/)

1. Download Raspbian: [https://www.raspberrypi.org/downloads/raspbian/]()
2. Burn the image the the SD card (using `dd` or [balenaEtcher](https://www.balena.io/etcher/))
3. Enable ssh by creating an empty file named `ssh` in the root of the boot disk
4. Configure the wifi authentification in the `wpa_supplicant.conf` file in the root of the boot disk (replace the country, ssid and psk):

```
country=US
ctrl_interface=DIR=/var/run/wpa_supplicant GROUP=netdev
update_config=1

network={
    ssid="NETWORK-NAME"
    psk="NETWORK-PASSWORD"
}
```
