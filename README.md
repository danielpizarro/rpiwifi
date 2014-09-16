#Guide to enable WIFI on Raspberry Pi

This guide is for:

 - Raspberry Pi model B
 - Wifi dongle D-Link DWA-123 , Model DWA125D1. Seriously, Box says "DWA-123, and the label on the dongle says DWA-123 and DWA-125D1"

Items you need:
 - 16GB SD card
 - Powered usb hub.
 - Keyboard
 - Ethernet cable with internet connection.
 - Monitor


1) Erase your SD card on macbook pro, format it using disk utility MS-DOS (FAT)

2) copy NOOBS files onto SDCARD. I've used `NOOBS_v1_3_9`

3) Hook everything in place, remember to connect the dongle to the powered hub.

4) Turn on Raspberry pi

5) Install Raspbian. There might be two options for raspbian. select the one that installs from the SD card (it should be faster). Anyway, this step can take several tens of minutes.

6) login to bash, then:

```
sudo apt-get -y update && sudo apt-get -y upgrade && sudo apt-get -y install git build-essential dkms wicd-curses gcc-4.7 cpp-4.7
git clone https://github.com/lwfinger/rtl8188eu
cd rtl8188eu
sudo make all
sudo make install
sudo modprobe 8188eu
```


6.1) if you happen to need linux headers, download the corresponding file from here: 

http://www.niksula.hut.fi/~mhiienka/Rpi/linux-headers-rpi/

then install them using

```
dpkg -i linux-headers-3.12.28+_3.12.28+-2_armhf.deb 
```

7) config your wifi connection:

```
sudo nano /etc/wicd/manager-settings.conf # and check that "wireless_interface = wlan0"
sudo wicd-curses
```