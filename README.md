### 8821cu ( 8821cu.ko )

### Linux Driver for the RealTek RTL8811CU, RTL8821CU and RTL8731AU Chipsets.

- v5.8.1.7 (Realtek) (2020-09-29)
- Plus updates from the Linux community

### Features:

- IEEE 802.11 b/g/n/ac WiFi compliant
- 802.1x, WEP, WPA TKIP and WPA2 AES/Mixed mode for PSK and TLS (Radius)
- WPA3-SAE (Personal)
- WPS - PIN and PBC Methods
- IEEE 802.11b/g/n/ac Client mode
  * Support wireless security for WEP, WPA TKIP and WPA2 AES PSK
  * Support site survey scan and manual connect
  * Support WPA/WPA2 TLS client
  * Support power saving mode
- Soft AP mode
- WiFi-Direct
- MU-MIMO
- Mesh
- Wake on WLAN
- Supported interface modes:
  * IBSS
  * Managed
  * AP (WiFi Hotspot) (Master mode)
  * Monitor
  * P2P-client
  * P2P-GO
- Log level control
- LED control
- Power saving control
- VHT control (allows 80 MHz channel width in AP mode)

### Compatible CPUs:

- x86, amd64
- ARM, ARM64

### Compatible Kernels:

- Kernels: 2.6.24 - 5.8 (Realtek)
- Kernels: 5.9 - 5.10

### Tested Linux Distributions:

- Raspberry Pi OS (12-02-2020) (ARM 32 bit) (kernel 5.4)

- LMDE 4 (Linux Mint based on Debian) (kernel 4.19)

- Linux Mint 20 (Linux Mint based on Ubuntu) (kernel 5.4)
- Linux Mint 19.3 (Linux Mint based on Ubuntu) (kernel 5.4)

- Ubuntu 20.10 (kernel 5.8)
- Ubuntu 20.04 (kernel 5.4)
- Ubuntu 18.04 (kernel 5.4)

### Download Locations for Tested Linux Distributions:

- Raspberry Pi OS - https://www.raspberrypi.org/
- Linux Mint - https://linuxmint.com/
- Ubuntu - https://ubuntu.com/

### Tested Hardware:
```
- Cudy WU700 AC650 High Gain USB WiFi Adapter:
  https://www.amazon.com/Cudy-WU700-650Mbps-Wireless-Compatible/dp/B07XXQVQH1
```
```
- BrosTrend 650Mbps Long Range Linux WiFi Adapter (Model #: AC5L):
  https://www.amazon.com/BrosTrend-600Mbps-Wireless-Internet-AC2/dp/B01GC8XH0S
```
```
- EDUP EP-AC1651 USB WiFi Adapter AC650 Dual Band USB 2.0 Nano:
  https://www.amazon.com/gp/product/B0872VF2D8
```
```
- EDUP EP-AC1635 USB WiFi Adapter AC600 Dual Band USB 2.0:
  https://www.amazon.com/gp/product/B075R7BFV2
```

### Compatible Devices:

Note: Some adapter makers change the chipsets in their products while keeping the same model number so please check to confirm that the product you plan to buy has the chipset you are expecting.

* Cudy WU700
* BrosTrend AC5L
* EDUP EP-AC1651
* EDUP EP-AC1635
* D-Link - DWA-171C
* TOTOLINK A650UA v3
* Numerous additional products that are based on the supported chipsets

### Installation Information:

The installation instructions that are provided are for the novice user. Experienced users are welcome to alter the installation to meet their needs.

The installation instructions require that your system has access to the internet. There are numerous ways to enable temporary internet access depending on your hardware and situation. One method is to use tethering from a phone. Another method is to keep an ultra cheap adapter in your toolkit that uses an in-kernel (plug and play) driver. Here is one: https://www.canakit.com/raspberry-pi-wifi.html.

The installation instructions require the use of the terminal. The quick way to open a terminal: Ctrl+Alt+T (hold down on the Ctrl and Alt keys then press the T key).

The installation instructions make use of DKMS. DKMS is a system utility which will automatically recompile and install this kernel module when a new kernel is installed. DKMS is provided by and maintained by Dell.

It is recommended that you do not delete the driver directory after installation as the directory contains documentation (README.md) and scripts that you may need in the future.

### Installation Steps:

Step 1: Open a terminal (Ctrl+Alt+T)

Step 2: Update the system:
```bash
$ sudo apt-get update
```
Step 3: Install the required packages (select the option for the OS you are using):

Option for Raspberry Pi OS:
```bash
$ sudo apt-get install -y raspberrypi-kernel-headers bc build-essential dkms git
```
Option for LMDE (Debian based):
```bash
$ sudo apt-get install -y linux-headers-$(uname -r) build-essential dkms git
```
Option for Linux Mint (Ubuntu based) or Ubuntu (all flavors):
```bash
$ sudo apt-get install -y dkms git
```
Option for Arch-based distributions (Manjaro):
```bash
$ sudo pacman -S --noconfirm linux-headers dkms git
```
Step 4: Create a directory to hold the downloaded driver:

Note: The technique used in this document is to create a directory in the home directory called `src`.
```bash
$ mkdir src
```
Step 5: Move to the newly created directory:
```bash
$ cd ~/src
```
Step 6: Download the driver:
```bash
$ git clone https://github.com/morrownr/8821cu.git
```
Step 7: Move to the newly created driver directory:
```bash
$ cd ~/src/8821cu
```
Step 8: Run a preparation script if needed:

The Raspberry Pi OS requires a preparation script.

For 32 bit Raspberry Pi OS: (Please skip this step if you are not installing to Raspberry Pi 32 bit)
```bash
$ sudo ./raspi32.sh

```
For 64 bit Raspberry Pi OS: (Please skip this step if you are not installing to Raspberry Pi 64 bit)
```bash
$ sudo ./raspi64.sh

```
Step 9: Run the installation script:
```bash
$ sudo ./install-driver.sh
```
Step 10: Reboot:
```bash
$ sudo reboot
```
### Removal of the Driver:

Step 1: Open a terminal (Ctrl+Alt+T)

Step 2: Move to the driver directory:
```bash
$ cd ~/src/8821cu
```
Step 3: Run the removal script:
```bash
$ sudo ./remove-driver.sh
```
Step 4: Reboot:
```bash
$ sudo reboot
```
### Driver Options:

A file called `8821cu.conf` will be installed in `/etc/modeprob.d` by default.

Location: `/etc/modprobe.d/8821cu.conf`

This file will be read and applied to the driver on each system boot.

To change the driver options, there are two options:

Option 1: Edit `8821cu.conf` with a text editor using a terminal interface.

Example:
```
$ sudo nano /etc/modprobe.d/8821cu.conf
```
Option 2: From the driver directory, run the `./edit-options.sh` script:
```bash
$ sudo ./edit-options.sh
```
The driver options are as follows:

 -----

 Log level options: ( rtw_drv_log_level )
```
 0 = NONE (default)
 1 = ALWAYS
 2 = ERROR
 3 = WARNING
 4 = INFO
 5 = DEBUG
 6 = MAX
```
 Note: You can save a log of RTW log entries by running the following in a terminal:

 $ sudo ./save-log.sh

 -----

 LED control options: ( rtw_led_ctrl )
```
 0 = Always off
 1 = Normal blink (default)
 2 = Always on
```
 -----

 VHT enable options: ( rtw_vht_enable )
```
  0 = Disable
  1 = Enable (default)
  2 = Force auto enable (use caution)
```
 Notes:
 - Unless you know what you are doing, don't change the default for rtw_vht_enable.
 - A non-default setting can degrade performance greatly in some operational modes.
 - For AP mode, such as when you are using Hostapd, setting this option to 2 will
   allow 80 MHz channel width.

 -----

  Power saving options: ( rtw_power_mgnt )
```
 0 = Disable power saving
 1 = Power saving on, minPS (default)
 2 = Power saving on, maxPS
```
 Note: 0 may be useful in unattended server setups or if dropouts are experienced.

 -----

### Entering Monitor Mode with 'iw' and 'ip':

Start by making sure the system recognizes the WiFi interface:
```bash
$ sudo iw dev
```

Note: The output shows the WiFi interface name and the current mode among other things. The interface name may be something like `wlx00c0cafre8ba` and is required for the below commands. The interface name `wlan0` will be used in the instructions below but you need to substitute your interface name.

Take the interface down:
```bash
$ sudo ip link set wlan0 down
```

Set monitor mode:
```bash
$ sudo iw wlan0 set monitor control
```

Bring the interface up:
```bash
$ sudo ip link set wlan0 up
```

Verify the mode has changed:
```bash
$ sudo iw dev
```

### Reverting to Managed Mode with 'iw' and 'ip':

Take the interface down:
```bash
$ sudo ip link set wlan0 down
```

Set managed mode:
```bash
$ sudo iw wlan0 set type managed
```

Bring the interface up:
```bash
$ sudo ip link set wlan0 up
```

Verify the mode has changed:
```bash
$ sudo iw dev
```

### ----------------------------- Various Tidbits of Information -----------------------------


### How to disable onboard WiFi on Raspberry Pi 3B, 3B+, 3A+, 4B and Zero W.

Add the following line to /boot/config.txt:
```
dtoverlay=disable-wifi
```


### How to forget a saved WiFi network on a Raspberry Pi

1. Edit wpa_supplicant.conf:
```bash
$ sudo nano /etc/wpa_supplicant/wpa_supplicant.conf
```
2. Delete the relevant WiFi network block (including the 'network=' and opening/closing braces.

3. Press ctrl-x followed by 'y' and enter to save the file.

4. Reboot


### Recommended Router Settings for WiFi:

Note: These are general recommendations based on years of experience but may not apply to your situation so testing to see if any help fix your problem is recommended.

Security: Use WPA2-AES. Do not use WPA or WPA2 mixed mode or TKIP.

Channel Width for 2.4G: Use 20 MHz fixed width. Do not use 40 MHz or 20/40 automatic.

Channel width for 5G: Using a 40 MHz fixed width may help in some situations.

Channels for 2.4G: Use 1 or 6 or 11. Do not use automatic channel selection.

Mode for 2.4G: Use G/N or B/G/N. Do not use N only.

Network names: Do not set the 2.4G Network and the 5G Network to the same name. Note: Many routers come with both networks set to the same name.

Power Saving: Set to off. This can help in some situations. If you try turning it off and you see no improvement then set it back to on so as to save electricity.

After making these changes, reboot the router.


### Set regulatory domain to correct setting in OS:

Check the current setting:
```bash
$ sudo iw reg get
```

If you get 00, that is the default and may not provide optimal performance.

Find the correct setting here: http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2

Set it temporarily:
```bash
$ sudo iw reg set US
```
Note: Substitute your country code if you are not in the United States.

Set it permanently:
```bash
$ sudo nano /etc/default/crda

Change the last line to read:

REGDOMAIN=US
```
