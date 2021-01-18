# mangoPi_v2
![Image of mangoPi_side](https://github.com/crispymangoes/mangoPi_v2/blob/main/mangoPi_rev2.JPG)
The mangoPi is a FPGA development board designed to be for beginners. This repo combined with my [YouTube channel](https://www.youtube.com/channel/UCeLSZnDQhn2w7gunQxIRu9Q/videos), Crispy Mangoes, will allow you to understand the inner workings of this FPGA development board, as well as how to use it.Please note that this project is still very much in development, so the PCB design, and schematic have issues that will be fixed with the version 3 of this board. I'll be uploading my progress to my YouTube channel, so check it out if you are interested.

## Legal
* Open-Source and released under the [Creative Commons Attribution Share-Alike License](https://creativecommons.org/licenses/by-sa/4.0/).
* Raspberry Pi is a trademark of the Raspberry Pi Foundation. I am by no means associated with the Raspberry Pi Foundation. The mangoPi is an FPGA development board that is compatible with the Raspberry Pi Compute Module 3+. 

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

## Editing the Revision 2
There are a few issues with the revision 2, so if you did want to take this design and move forward with it, then I have outlined what works, what does not work below, and what I have not tested yet.
### Notes
* (WORKS)Pi bus that connects to the FPGA
  * I used a 7.8MHz SPI Clock to communicate with the FPGA. Though in testing I was able to get it up to 31.2MHz
* (KINDA WORKS)SRAM
  * The SRAM can theoretically run at 200MHz(which gives you the 7.2Gbps bandwitdth), but with my verilog code I could only read and write data with a 100MHZ clock
* (WORKS)ADC functions as expected
* (WORKS)98 GPIO and buttons
  * Everything works but the buttons I picked kinda suck so I'd choose a different model
* (KINDA WORKS)DisplayPort
  * I was able to connect a display port cable to the TX and RX connectors, and set a counting variable through the connection, but noticed a few issues
   * The value would almost always be shifted by a random number of bits
   * When I tried to use two GTP transceivers at once things went really funky and stopped working
   * I think the GTP transceviers need more power the IC I use to supply the 1.2V line can only output 300mA
* (UNKNOWN) Ethernet
  * My plan was to use the AXI Ethernet IP to test if the ethernet worked, but the IP doesn't work if the IO voltage used is 3V3, but the IO bank connected to the Ethernet PHY is 3V3. So you would need to connect that IO bank to 2V5 or 1V8 in order to test it
* (UNKNOWN) FT2232HQ
  * I did not get around to testing this because of time constraints, and I am also unsure what use this IC will have on the board since the Compute Module can pretty much do everything that this IC would be needed for. I think, I am still pretty new to all this stuff so I could be completely wrong :)
* (DOES NOT WORK)Pi Camera Connector
  * I think that the camera connector was installed backwards. When I tested it, there was no camera detected, but if I flipped the camera then the 3V3 line was shorted to ground. I tried fixing this and flipping the connector, but I kinda screwed up the connector and solder connection in the process so it still does not work. Though I am pretty sure the only issue with it is the orientation of the connector(which should be oriented correctly in the above images of the board).
* (WORKS) All other Pi interfaces
  * I mainly develop headless with VS code, but have not had any issues with any other Pi interfaces.
