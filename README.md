# xc3sprog-cmod_a7-rpi
Xc3sprog compiled for Raspberry Pi OS with support for Numonyx (Micron) N25Q 0x16 memory which is on the CMOD-A7 FPGA board. It can be installed in /usr/local/bin

This version of xc3sprog is needed to program the SPI flash memory on the CMOD-A7 board. If you want to only program the FPGA (volitle memory) then the Raspberry Pi OS repository version of xc3sprog is sufficient (no need to use my version). First install the FTDI driver library from the Raspberry Pi OS repository.

sudo apt-get install libftdi1

Next the SPI memory needs to be detected. Use the "run_first_spi_flash_cmod_a7.sh" script (which uses the "first.bit" file). The "first.bit" file was created specifically for the CMOD-A7 SPI flash memory (a complicated process done on Vivado using a trivial design). Now you are ready to load your custom bit file into the CMOD-A7.

xc3sprog -c jtaghs1_fast -I your_custom_file.bit

Please note that there is no space between the "-I" switch and "first.bit" when detecting the SPI flash, but when you program your file there will need to be a space. I am not sure why this is the case, just part of the recipe that I discovered.

Enjoy.
