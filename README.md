# orange-pi-zero
## Raspbian setup on the SD card
- Download latest supported Raspbian from https://www.armbian.com/orange-pi-zero/#kernels-archive
- Install 7-zip to extract the file later: `sudo apt-get install p7zip-full
- Extract the 7z file: `7z e FILE_NAME`
- Insert SD card, and check the location with `dmesg` (eg. /dev/sdb1)
- Write file to SD card: `sudo dd bs=4M if=IMG_FILE_NAME of=SD_CARD_LOCATION`
- To find the IP Address of the Orange Pi later, it is easiest to check the new network connections
- Install nmap: `sudo apt-get install nmap`
- Check for network devices + save to file: `nmap -sn 192.168.0.0/24 > initial_scan` (replace IP address with your network range and subnet)
- Insert SD into Orange Pi Zero, connect ethernet cable + power up. Wait for ~5 minutes, and scan again to look for new devices
- `nmap -sn 192.168.0.0/24 > after_scan`
- Compare the two files to look for new devices. Once you have a shortlist, try to ssh
- `ssh root@192.168.0.10` if it asks you for a password, enter the default of `1234`
- Using guide, set new password for root and set up a new user/password
- Disconnect (`ctrl + d`) and log in using the new user: `ssh user@192.168.0.10`
