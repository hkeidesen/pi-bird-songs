Birdsong Player
This repository contains scripts and services for automatically playing bird songs and connecting to a Bluetooth device on a Raspberry Pi.

Prerequisites
mplayer: Use sudo apt-get install mplayer to install if not installed.
Bluetooth: Make sure your device has Bluetooth capabilities and it's turned on. You can turn it on using sudo systemctl start bluetooth.
Instructions
Clone this repository to your local system.
bash
Copy code
git clone https://github.com/YourUsername/BirdsongPlayer.git
Navigate to the cloned repository:
bash
Copy code
cd BirdsongPlayer
Make the script files executable:
bash
Copy code
chmod +x play_bird_songs.sh
chmod +x connect_bluetooth.sh
Edit the service files bluetooth_reconnect.service and birdsound.service and replace /path/to/ with the actual path to the scripts connect_bluetooth.sh and play_bird_songs.sh respectively.

Move the service files to /etc/systemd/system/.

bash
Copy code
sudo mv bluetooth_reconnect.service /etc/systemd/system/
sudo mv birdsound.service /etc/systemd/system/
Enable and start the services:
bash
Copy code
sudo systemctl enable bluetooth_reconnect.service
sudo systemctl enable birdsound.service

sudo systemctl start bluetooth_reconnect.service
sudo systemctl start birdsound.service
The bluetooth_reconnect.service will now run at boot and automatically connect to the specified Bluetooth device, and birdsound.service will play the bird songs in a loop.
Note: Ensure the target Bluetooth device (with the MAC address mentioned in connect_bluetooth.sh) is turned on and within range of the Raspberry Pi.

Troubleshooting
In case the services are not working as expected, use the following commands to check their status:

lua
Copy code
sudo systemctl status bluetooth_reconnect.service
sudo systemctl status birdsound.service
This will show the current status of the service and the last few lines of output. Any error messages related to the service will be displayed here.
