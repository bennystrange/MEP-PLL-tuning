# Command line interface for the LMX2028

This repository contains instructions for direct SPI interfacing with the TI LMX2820EVM RF Synthesizer via the FT232H.

### Install libusb
Run the following  
```
sudo apt-get install libusb-1.0
```

### Set up udev rules
Navigate to your udev rules directory  
```
sudo nano /etc/udev/rules.d/11-ftdi.rules
```

Add the following lines  
```
SUBSYSTEM=="usb", ATTR{idVendor}=="0403", ATTR{idProduct}=="6001", GROUP="plugdev", MODE="0666"  
SUBSYSTEM=="usb", ATTR{idVendor}=="0403", ATTR{idProduct}=="6011", GROUP="plugdev", MODE="0666"  
SUBSYSTEM=="usb", ATTR{idVendor}=="0403", ATTR{idProduct}=="6010", GROUP="plugdev", MODE="0666"  
SUBSYSTEM=="usb", ATTR{idVendor}=="0403", ATTR{idProduct}=="6014", GROUP="plugdev", MODE="0666"  
SUBSYSTEM=="usb", ATTR{idVendor}=="0403", ATTR{idProduct}=="6015", GROUP="plugdev", MODE="0666"
```

### Install pyftdi
Run the following  
```
pip3 install pyftdi
```

### Install Blinka
Run the following  
```
pip3 install adafruit-blinka
```

### Set the environment variable
Run the following  
```
export BLINKA_FT232H=1
```

### Upload tuner.py
Navigate to your working directory for this program  
Upload the tuner.py file  
```
wget https://github.com/bennystrange/MEP-PLL-tuning/raw/main/tuner.py
```

### Run the program
```
python3 tuner.py
```
**NOTES:**  
* The LMX2820 will default to 6 GHz on program run  
* Ctrl-C will NOT clear registers
