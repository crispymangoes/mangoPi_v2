# mangoPi_v2
![Image of mangoPi_side](https://github.com/crispymangoes/mangoPi_v2/blob/main/mangoPi_rev2.JPG)
The mangoPi is a FPGA development board designed to be for beginners. This repo combined with my [YouTube channel](https://www.youtube.com/channel/UCeLSZnDQhn2w7gunQxIRu9Q/videos), Crispy Mangoes, will allow you to understand the inner workings of this FPGA development board, as well as how to use it.Please note that this project is still very much in development, so the PCB design, and schematic have issues that will be fixed with the version 3 of this board. I'll be uploading my progress to my YouTube channel, so check it out if you are interested.
## Legal
Raspberry Pi is a trademark of the Raspberry Pi Foundation. I am by no means associated with the Raspberry Pi Foundation. The mangoPi is an FPGA development board that is compatible with the Raspberry Pi Compute Module 3+. 

## The Story
Hi I'm Ryan aka Crispy. I am a self taught electronic enthusiast, with a degreee in Mechanical Engineering from Colorado School of Mines.Two years ago I started my search for a FPGA development board for beginners. While I found a ton of boards, I also found two big issues with them. The boards either lacked the peripherals and features that I needed, or they simply did not have enough documentation or tutorials in order for me to understand HOW to use my board.I searched for a year and tried a few FPGA development boards along the way, until I finally decided to make my own.

![Image of mangoPi_side](https://github.com/crispymangoes/mangoPi_v2/blob/main/mangoPi_rev2_top.JPG)
## Features
### FPGA
* Xilinx XC7A35T-1FGG484C
* Raspberry Pi Compute Module 3+ with a 36 bit wide bus
  * Programs the FPGA using the Pi's SPI interface
  * 32.5Mbps data transfer between Pi and FPGA using SPI
* 4 Mb Cypress SRAM
  * 7.2 Gbps interface between FPGA and SRAM
* DisplayPort using FPGA GTP transceivers
* Gigabit Ethernet
* 98 GPIO Pins
  * 16 can be used to make 8 ADC pairs for reading voltages
  * 16 are connected to LEDs which can be disabled if you just want to use the pins for GPIO
* 5 general purpose buttons
* FT2232HQ USB to FIFO/SPI/UART
### Compute Module
* HDMI output
* 4 USB 2.0 ports
* Camera connector for use with Pi Camera
* Micro SD to hold OS, bitsreams, etc...

## How to open the EasyEDA project files
* Download Project_mangoPi Rev 2.0_2021-01-18_18-53-02.zip
* Extract files wherever you want to store them
* In EasyEDA go to File -> Open -> EasyEDA
* Navigate to where you extracted the folder. You should see two json files, one for the PCB and the other for the schematic
* Hold ctrl and select both of the files and click open
* Once opened you will need to save them. You can add them to an existing project folder, or make a new one. 
