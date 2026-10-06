<!--
 * @Description: None
 * @Author: LILYGO_L
 * @Date: 2023-09-11 16:13:14
 * @LastEditTime: 2025-09-15 10:15:26
 * @License: GPL 3.0
-->
<h1 align = "center">T-Connect-Pro</h1>

## **English | [中文](./README_CN.md)**

## VersionIteration:
| Version                              | Update date                       |
| :-------------------------------: | :-------------------------------: |
| T-Connect-Pro_V1.0                      | 2025-02-05                    |

## Important Notes

### PoE Is Not Supported — Do Not Supply Power Through the Ethernet Port

**T-Connect-Pro does not support Power over Ethernet (PoE). The Ethernet port is for data communication only. Do not supply power to the device through the Ethernet cable. In particular, do not use passive PoE injectors or enable forced PoE power on a switch port, as this may damage the Ethernet port or the mainboard.** Use the device's designated power inputs and specified power ratings.

## Directory
- [Describe](#describe)
- [Preview](#preview)
- [Module](#module)
- [SoftwareDeployment](#SoftwareDeployment)
- [PinOverview](#pinoverview)
- [RelatedTests](#RelatedTests)
- [FAQ](#faq)
- [Project](#project)

## Describe

T-Connect-Pro is a product based on the ESP32S3 main control chip, consisting of three stacked circuit boards. It features a wide range of functions and is equipped with three different communication modules: CAN, RS485, and RS232, enabling long-distance data transmission. The product includes an Ethernet interface, a relay interface, and a LoRa module (SX1262). It also comes with an LCD screen to facilitate easier operation.

## Preview

### Actual Product Image

## Module

### 1. MCU

* Chip: ESP32-S3-R8
* PSRAM: 8M (Octal SPI) 
* FLASH: 16M
* Related documentation: 
    >[Espressif ESP32-S3 Datasheet](https://www.espressif.com.cn/sites/default/files/documentation/esp32-s3_datasheet_en.pdf)

### 2. Screen

<!-- * Size:  -->
* Resolution: 222x480px
* Screen type: TFT、LCD
* Driver chip: ST7796
* Bus communication protocol: Standard SPI
* Dependent libraries: 
    >[Arduino_GFX-1.4.6](https://github.com/moononournation/Arduino_GFX)

### 3. Touch

* Chip: CST226SE
* Bus communication protocol: IIC
* Dependent libraries: 
    >[Arduino_DriveBus-1.1.16]()

### 4. Lora

* Module: HPD16A
* Chip: SX1262
* Bus communication protocol: Standard SPI
* Related documentation: 
    >[HPD16A_V1.1](./information/HPDTEK_HPD16A_TCXO_V1.1.pdf) <br /> 
    >[SX1262_V2.1](./information/DS_SX1261-2_V2_1.pdf)
* Dependent libraries: 
    >[RadioLib-6.6.0](https://github.com/jgromes/RadioLib)

### 5. CAN

* Module: TD501MCANFD
* Bus communication protocol: TWAI
* Related documentation: 
    >[TD501MCANFD](./information/TD501MCANFD_MORNSUN.pdf)

### 6. RS485

* module: TD501D485H-A
* Bus communication protocol: UART
* Related documentation: 
    >[TD501D485H-A](./information/TD501D485H-A_K-CUT.pdf)

### 7. RS232

* module: TD501D232H
* Bus communication protocol: UART
* Related documentation: 
    >[TD501D232H](./information/TD501D232H_WJ146289.pdf)

### 8. Ethernet

* Chip: W5500
* Bus communication protocol: Standard SPI
* Related documentation: 
    >[Ethernet_V2.0.0](http://www.arduino.cc/en/Reference/Ethernet)

## SoftwareDeployment

### Examples Support

| Example | `[Platformio IDE][espressif32-v6.5.0]`<br />`[Arduino IDE][esp32_v2.0.14]` | Description | Picture |
| ------  | ------ | ------ | ------ | 
| [CAN](./examples/CAN) |  <p align="center">![alt text][supported] | | |
| [CST226SE](./examples/CST226SE) |  <p align="center">![alt text][supported] | | |
| [Ethernet_HTTP](./examples/Ethernet_HTTP) |  <p align="center">![alt text][supported] | | |
| [Ethernet_Relay](./examples/Ethernet_Relay) |  <p align="center">![alt text][supported] | | |
| [Ethernet_Scan](./examples/Ethernet_Scan) |  <p align="center">![alt text][supported] | | |
| [GFX](./examples/GFX) |  <p align="center">![alt text][supported] | | |
| [GFX_SX1262](./examples/GFX_SX1262) |  <p align="center">![alt text][supported] | | |
| [Original_Test](./examples/Original_Test) |  <p align="center">![alt text][supported] | Original factory program | |
| [Relay](./examples/Relay) |  <p align="center">![alt text][supported] | | |
| [RS485](./examples/RS485) |  <p align="center">![alt text][supported] | | |
| [RS485_2](./examples/RS485_2) |  <p align="center">![alt text][supported] | | |
| [SX126x_Channel_Activity_Detection_Blocking](./examples/SX126x_Channel_Activity_Detection_Blocking) |  <p align="center">![alt text][supported] | | |
| [SX126x_Channel_Activity_Detection_Interrupt](./examples/SX126x_Channel_Activity_Detection_Interrupt) |  <p align="center">![alt text][supported] | | |
| [SX126x_PingPong](./examples/SX126x_PingPong) |  <p align="center">![alt text][supported] | | |
| [SX1262_Receive_Interrupt](./examples/SX1262_Receive_Interrupt) |  <p align="center">![alt text][supported] | | |
| [raw](./examples/raw) |  <p align="center">![alt text][supported] | | |
| [ttn_abp](./examples/ttn_abp) |  <p align="center">![alt text][supported] | | |
| [ttn_otaa](./examples/ttn_otaa) |  <p align="center">![alt text][supported] | | |

[supported]: https://img.shields.io/badge/-supported-green "example"

| Firmware | Description | Picture |
| ------  | ------  | ------ |
| [Original_Test](./firmware/(屏幕色彩测试项增加黑色背景测试)[T-Connect-Pro_V1.0][Original_Test]_firmware_202502191117.bin) | Original factory program |  |

### PlatformIO
1. Install[VisualStudioCode](https://code.visualstudio.com/Download),Choose installation based on your system type.

2. Open the "Extension" section of the Visual Studio Code software sidebar(Alternatively, use "<kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>X</kbd>" to open the extension),Search for the "PlatformIO IDE" extension and download it.

3. During the installation of the extension, you can go to GitHub to download the program. You can download the main branch by clicking on the "<> Code" with green text, or you can download the program versions from the "Releases" section in the sidebar.

4. After the installation of the extension is completed, open the Explorer in the sidebar(Alternatively, use "<kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>E</kbd>" go open it),Click on "Open Folder," locate the project code you just downloaded (the entire folder), and click "Add." At this point, the project files will be added to your workspace.

5. Open the "platformio.ini" file in the project folder (PlatformIO will automatically open the "platformio.ini" file corresponding to the added folder). Under the "[platformio]" section, uncomment and select the example program you want to burn (it should start with "default_envs = xxx") Then click "<kbd>[√](image/4.png)</kbd>" in the bottom left corner to compile,If the compilation is correct, connect the microcontroller to the computer and click "<kbd>[→](image/5.png)</kbd>" in the bottom left corner to download the program.

### Arduino
1. Install[Arduino](https://www.arduino.cc/en/software),Choose installation based on your system type.

2. Open the "example" directory within the project folder, select the example project folder, and open the file ending with ".ino" to open the Arduino IDE project workspace.

3. Open the "Tools" menu at the top right -> Select "Board" -> "Board Manager." Find or search for "esp32" and download the board files from the author named "Espressif Systems." Then, go back to the "Board" menu and select the development board type under "ESP32 Arduino." The selected development board type should match the one specified in the "platformio.ini" file under the [env] section with the header "board = xxx." If there is no corresponding development board, you may need to manually add the development board from the "board" directory within your project folder.

4. Open menu bar "[File](image/6.png)" -> "[Preferences](image/6.png)" ,Find "[Sketchbook location](image/7.png)"  here,copy and paste all library files and folders from the "libraries" folder in the project directory into the "libraries" folder in this directory.

5. Select the correct settings in the Tools menu, as shown in the table below.

#### ESP32-S3
| Setting                               | Value                                 |
| :-------------------------------: | :-------------------------------: |
| Board                                 | ESP32S3 Dev Module           |
| Upload Speed                     | 921600                               |
| USB Mode                           | Hardware CDC and JTAG     |
| USB CDC On Boot                | Enabled                              |
| USB Firmware MSC On Boot | Disabled                             |
| USB DFU On Boot                | Disabled                             |
| CPU Frequency                   | 240MHz (WiFi)                    |
| Flash Mode                         | QIO 80MHz                         |
| Flash Size                           | 16MB (128Mb)                    |
| Core Debug Level                | None                                 |
| Partition Scheme                | 16M Flash (3MB APP/9.9MB FATFS) |
| PSRAM                                | OPI PSRAM                         |
| Arduino Runs On                  | Core 1                               |
| Events Run On                     | Core 1                               |           

6. Select the correct port.

7. Click "<kbd>[√](image/8.png)</kbd>" in the upper right corner to compile,If the compilation is correct, connect the microcontroller to the computer,Click "<kbd>[→](image/9.png)</kbd>" in the upper right corner to download.

### firmware download
1. Open the project file "tools" and locate the ESP32 burning tool. Open it.

2. Select the correct burning chip and burning method, then click "OK." As shown in the picture, follow steps 1->2->3->4->5 to burn the program. If the burning is not successful, press and hold the "BOOT-0" button and then download and burn again.

3. Burn the file in the root directory of the project file "[firmware](./firmware/)" file,There is a description of the firmware file version inside, just choose the appropriate version to download.

<p align="center" width="100%">
    <img src="image/10.png" alt="example">
    <img src="image/11.png" alt="example">
</p>


## PinOverview

| Screen pins  | ESP32S3 pins|
| :------------------: | :------------------:|
| MOSI         | IO11       |
| MISO         | IO13       |
| DC         | IO41       |
| SCLK         | IO12       |
| CS         | IO21       |
| BL         | IO46       |

| Touch pins  | ESP32S3 pins|
| :------------------: | :------------------:|
| SDA         | IO39      |
| SCL         | IO40       |
| RST         | IO47      |
| INT         | IO3       |

| Ethernet pins  | ESP32S3 pins|
| :------------------: | :------------------:|
| MOSI         | IO11       |
| MISO         | IO13       |
| RST         | IO48       |
| SCLK         | IO12       |
| CS         | IO10       |
| INT         | IO9       |

| Lora pins  | ESP32S3 pins|
| :------------------: | :------------------:|
| MOSI         | IO11       |
| MISO         | IO13       |
| RST         | IO42       |
| SCLK         | IO12       |
| CS         | IO14       |
| INT/DIO1         | IO45       |
| BUSY         | IO38       |

| RS485 pins  | ESP32S3 pins|
| :------------------: | :------------------:|
| UART_TX         | IO17       |
| UART_RX         | IO18       |

| RS232 pins  | ESP32S3 pins|
| :------------------: | :------------------:|
| UART_TX         | IO4       |
| UART_RX         | IO5       |

| CAN pins  | ESP32S3 pins|
| :------------------: | :------------------:|
| TWAI_TX         | IO6      |
| TWAI_RX         | IO7       |

## RelatedTests

## FAQ

* Q. After reading the above tutorials, I still don't know how to build a programming environment. What should I do?
* A. If you still don't understand how to build an environment after reading the above tutorials, you can refer to the [LilyGo-Document](https://github.com/Xinyuan-LilyGO/LilyGo-Document) document instructions to build it.

<br />

* Q. Why does Arduino IDE prompt me to update library files when I open it? Should I update them or not?
* A. Choose not to update library files. Different versions of library files may not be mutually compatible, so it is not recommended to update library files.

<br />

* Q. Why is there no serial data output on the "Uart" interface on my board? Is it defective and unusable?
* A. The default project configuration uses the USB interface as Uart0 serial output for debugging purposes. The "Uart" interface is connected to Uart0, so it won't output any data without configuration.<br />For PlatformIO users, please open the project file "platformio.ini" and modify the option under "build_flags = xxx" from "-D ARDUINO_USB_CDC_ON_BOOT=true" to "-D ARDUINO_USB_CDC_ON_BOOT=false" to enable external "Uart" interface.<br />For Arduino users, open the "Tools" menu and select "USB CDC On Boot: Disabled" to enable the external "Uart" interface.

<br />

* Q. Why is my board continuously failing to download the program?
* A. Please hold down the "BOOT-0" button and try downloading the program again.

## Project
* [T-Connect-Pro_V1.0](./project/T-Connect-Pro_V1.0.pdf)
* [T-Connect-Pro_V1.1](./project/T-Connect-Pro_V1.1.pdf)

