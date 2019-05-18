# rtl-sdr-raspberry
Install RTL-SDR on Raspberry

pi@raspberry:~/ sudo apt-get update
pi@raspberry:~/ sudo apt-get upgrade

pi@raspberry:~/ sudo apt-get install -y git-core git cmake libusb-1.0-0-dev build-essential

pi@raspberry:~/ git clone git://git.osmocom.org/rtl-sdr.git
pi@raspberry:~/ cd rtl-sdr/
pi@raspberry:~/rtl-sdr $ mkdir build
pi@raspberry:~/rtl-sdr $ cd build
pi@raspberry:~/rtl-sdr/build $ cmake ../ -DINSTALL_UDEV_RULES=ON
pi@raspberry:~/rtl-sdr/build $ make
pi@raspberry:~/rtl-sdr/build $ sudo make install
pi@raspberry:~/rtl-sdr/build $ sudo ldconfig

pi@raspberry:~/sudo nano /etc/modprobe.d/blacklist-rtl.conf

Copy and paste:

#
#file blacklist-rtl.conf
#
blacklist dvb_usb_rtl28xxu
blacklist rtl2832
blacklist rtl2830
#

Save and Close (Ctrl+O e Ctrl+X)

pi@raspberry:~/sudo reboot

Test, example of result:

pi@raspberry:~/ rtl_test -t
Found 1 device(s):
0: Realtek, RTL2838UHIDIR, SN: 00000001

Using device 0: Generic RTL2832U OEM
Found Micro R820T tuner
Supported gain values (29): 0.0 0.9 1.4 2.7 3.7 7.7 8.7 12.5 14.4 15.7 16.6 19.7 20.7 22.9 25.4 28.0 29.7 32.8 33.8 36.4 37.2 38.6 40.2 42.1 43.4 43.9 44.5 48.0 49.6
[R82XX] PLL not locked!
Sampling at 2048000 S/s.
