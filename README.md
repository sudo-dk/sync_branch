This repository contains the source code of Tirex MGM Phase-1 AC Charger.

in this repository BLE is integrated with User Registration and OTA Functionality .
This is the  lastest working code of MGM Phase1

-> Signature verification functionality is updated 
-> Bug fixes in User registration process
-> Advertisment begins only after receiving Serial number

Note: The MTU size of BLE is increased upto 500

=> The UR Functionality is tested and working with Charger board <=
  ------------------------------------------
  |   ESP32 Feature      |     (Yes/No)    |  
  | ---------------------|-----------------|
  | Ping - Pong          |     No          |
  | Serial Num Adv.      |     Yes         |
  | User Registration    |     Yes         |
  | OTA_ESP32            |     Yes         |
  | OTA_KM34             |     Yes         |
  | OTA_Merged           |     Yes         |
  | Data Download        |     No          |
  | Device Details       |     Yes         |
  | Security             |     Yes         |
  ------------------------------------------

==========================================================================================================================
### Setup the Hardware
Note: In this project UART0 is used for communication between ESP32 and KM34 and USB Serial is used for Debug Logs

Pin Configuration is as follows:
  -------------------------------------------
  |   ESP32 PIN Fun.      |      GPIO       |  
  | ----------------------|-----------------|
  | Transmit Data (TxD)   |       21        |
  | Receive Data (RxD)    |       22        |
  | Ground                |       GND       |
  | D+                    |       19        |
  | D-                    |       18        |
  | Ground                |       GND       |
  -------------------------------------------

==========================================================================================================================

### Build and Flash:

Build the project and flash it to the board,

To Flash using binary files using the following method:

Binary files can be found in build folder of the project.
Note: For binary files following addresses are used:
  -------------------------------------------------------
  |           Binary files             |    Address     |  
  | -----------------------------------|----------------|
  | bootloader.bin                     |     0x0        |
  | partition_table.bin                |     0x8000     |
  | ota_data_initial.bin               |     0xd000     |
  | MGM_Phase1.bin(application binary) |     0x10000    |
  -------------------------------------------------------

'''
python -m esptool --chip esp32c3 -b 460800 --before default_reset --after hard_reset write_flash --flash_mode dio --flash_size 4MB --flash_freq 80m 0x0 build\bootloader\bootloader.bin 0x8000 build\partition_table\partition-table.bin 0xd000 build\ota_data_initial.bin 0x10000 build\MGM_ESP_Demo.bin
'''
