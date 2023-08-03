# Birdsong Player

This repository contains scripts and services for automatically playing bird songs and connecting to a Bluetooth device on a Raspberry Pi.

## Prerequisites

Ensure the following software are installed:

- `mplayer`: This can be installed using the command `sudo apt-get install mplayer` if it is not already installed.
- Bluetooth: Make sure your device has Bluetooth capabilities and it's turned on. You can turn it on using `sudo systemctl start bluetooth`.

## Instructions

1. **Clone this repository **

```
git clone https://github.com/hkeidesen/pi-bird-song.git


cd BirdsongPlayer```

Make the script files executable

```chmod +x play_bird_songs.sh
chmod +x connect_bluetooth.sh
```
Edit the service files bluetooth_reconnect.service and birdsound.service. 
Replace /path/to/ with the actual path to the scripts connect_bluetooth.sh and play_bird_songs.sh


Move the service files to /etc/systemd/system/
```bash
sudo mv bluetooth_reconnect.service /etc/systemd/system/
sudo mv birdsound.service /etc/systemd/system/
```
Enable and start the services
```sudo systemctl enable bluetooth_reconnect.service
sudo systemctl enable birdsound.service

sudo systemctl start bluetooth_reconnect.service
sudo systemctl start birdsound.service
```

Troubleshooting
In case the services are not working as expected, use the following commands to check their status:
```
bash
sudo systemctl status bluetooth_reconnect.service
sudo systemctl status birdsound.service
```
