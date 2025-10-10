# Rpi Process Base Final

do the kali (other OS imager) install then:
sudo apt update
sudo apt full-upgrade -y
sudo apt install -y brcmfmac-nexmon-dkms firmware-nexmon
sudo reboot

Cloned opendroneid into downloads
git clone https://github.com/opendroneid/opendroneid-core-c.git

ran the following with no issues:
sudo apt-get install libgps-dev libnl-genl-3-dev libgtest-dev cmake
git submodule update --init
mkdir build && cd build
cmake ../.
make -j

https://github.com/sxjack/unix_rid_capture
ran the Debian script -> chmod +x "name" -> ./name
moved opendronid.c & .h into the file from the previously cloned repo

ran:
cmake . 
sudo apt install libbluetooth-dev (this was the issue the whole thyme)
make
sudo setcap cap_net_raw+eip rid_capture

sudo airmon-ng check kill
sudo airmon-ng start wlan0
sudo airodump-ng wlan0mon

sudo iw dev wlan0mon set channel 1 

run -> sudo ./rid_capture -x wlan1 -w wlan0mon

# Making a backup
run: lsbsk

% make note of which sd is which. DO NOT overwrite the OG unless enough stable progress has been made.
% example
original sd -> mmcblk0
backup sd -> sda

run: sudo umount /dev/sda*
run: sudo dd if=/dev/mmcblk0 of=/dev/sda bs=4M status=progress conv=fsync
run: sync
