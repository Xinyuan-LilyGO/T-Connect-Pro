<!--
 * @Description: None
 * @Author: LILYGO_L
 * @Date: 2023-09-11 16:13:14
 * @LastEditTime: 2025-02-05 11:55:51
 * @License: GPL 3.0
-->
<h1 align = "center">T-Connect-Pro</h1>

## **[English](./README.md) | 中文**

## 版本迭代:
| Version                               | Update date                       |
| :-------------------------------: | :-------------------------------: |
| T-Connect-Pro_V1.0                      | 2025-02-05                    |

## 购买链接

| Product                     | SOC           |  FLASH  |  PSRAM   | Link                   |
| :------------------------: | :-----------: |:-------: | :---------: | :------------------: |
| T-Connect-Pro_V1.0   | ESP32S3R8 |   16M   | 8M (Octal SPI) |  [NULL]()   |

## 目录
- [描述](#描述)
- [预览](#预览)
- [模块](#模块)
- [软件部署](#软件部署)
- [引脚总览](#引脚总览)
- [相关测试](#相关测试)
- [常见问题](#常见问题)
- [项目](#项目)

## 描述

T-Connect-Pro基于主控芯片ESP32S3，由3层板子堆叠组合而成的产品，功能丰富多样，板载3种不同通信模块：CAN、RS485、RS232实现远距离传输，拥有一个以太网接口、一个继电器接口、一个Lora模块（SX1262），配备LCD屏幕使得操作更加便捷。

## 预览

### 实物图

## 模块

### 1. MCU

* 芯片：ESP32-S3-R8
* PSRAM：8M (Octal SPI) 
* FLASH：16M
* 相关资料：
    >[Espressif ESP32-S3 Datasheet](https://www.espressif.com.cn/sites/default/files/documentation/esp32-s3_datasheet_en.pdf)

### 2. 屏幕

<!-- * 尺寸：英寸LCD屏幕 -->
* 分辨率：222x480px
* 屏幕类型：TFT、LCD
* 驱动芯片：ST7796
* 总线通信协议：标准SPI
* 依赖库：
    >[Arduino_GFX-1.4.6](https://github.com/moononournation/Arduino_GFX)

### 3. 触摸

* 芯片：CST226SE
* 总线通信协议：IIC
* 依赖库：
    >[Arduino_DriveBus-1.1.2](https://github.com/Xk-w/Arduino_DriveBus)

### 4. Lora

* 模块：HPD16A
* 芯片：SX1262
* 使用总线通信协议：标准SPI
* 相关资料：
    >[HPD16A_V1.1](./information/HPDTEK_HPD16A_TCXO_V1.1.pdf)  <br /> 
    >[SX1262_V2.1](./information/DS_SX1261-2_V2_1.pdf)
* 依赖库：
    >[RadioLib-6.6.0](https://github.com/jgromes/RadioLib)

### 5. CAN

* 模块：TD501MCANFD
* 使用总线通信协议：TWAI
* 相关资料：
    >[TD501MCANFD](./information/TD501MCANFD_MORNSUN.pdf)

### 6. RS485

* 模块：TD501D485H-A
* 使用总线通信协议：UART
* 相关资料：
    >[TD501D485H-A](./information/TD501D485H-A_K-CUT.pdf)

### 7. RS232

* 模块：TD501D232H
* 使用总线通信协议：UART
* 相关资料：
    >[TD501D232H](./information/TD501D232H_WJ146289.pdf)

### 8. 以太网

* 芯片：W5500
* 使用总线通信协议：标准SPI
* 依赖库：
    >[Ethernet_V2.0.0](http://www.arduino.cc/en/Reference/Ethernet)

## 软件部署

### 示例支持

| Example | `[Platformio IDE][espressif32-v6.5.0]`<br />`[Arduino IDE][esp32_v2.0.14]` | Description | Picture |
| ------  | ------ | ------ | ------ | 
| [CAN](./examples/CAN) |  <p align="center">![alt text][supported] | | |
| [CST226SE](./examples/CST226SE) |  <p align="center">![alt text][supported] | | |
| [Ethernet_HTTP](./examples/Ethernet_HTTP) |  <p align="center">![alt text][supported] | | |
| [Ethernet_Relay](./examples/Ethernet_Relay) |  <p align="center">![alt text][supported] | | |
| [Ethernet_Scan](./examples/Ethernet_Scan) |  <p align="center">![alt text][supported] | | |
| [GFX](./examples/GFX) |  <p align="center">![alt text][supported] | | |
| [GFX_SX1262](./examples/GFX_SX1262) |  <p align="center">![alt text][supported] | | |
| [Original_Test](./examples/Original_Test) |  <p align="center">![alt text][supported] | 出厂程序 | |
| [Relay](./examples/Relay) |  <p align="center">![alt text][supported] | | |
| [RS485](./examples/RS485) |  <p align="center">![alt text][supported] | | |
| [RS485_2](./examples/RS485_2) |  <p align="center">![alt text][supported] | | |
| [SX126x_Channel_Activity_Detection_Blocking](./examples/SX126x_Channel_Activity_Detection_Blocking) |  <p align="center">![alt text][supported] | | |
| [SX126x_Channel_Activity_Detection_Interrupt](./examples/SX126x_Channel_Activity_Detection_Interrupt) |  <p align="center">![alt text][supported] | | |
| [SX126x_PingPong](./examples/SX126x_PingPong) |  <p align="center">![alt text][supported] | | |
| [SX1262_Receive_Interrupt](./examples/SX1262_Receive_Interrupt) |  <p align="center">![alt text][supported] | | |

[supported]: https://img.shields.io/badge/-supported-green "example"

| Firmware | Description | Picture |
| ------  | ------  | ------ |
| [Original_Test](./firmware/(Lora带宽调整为125Khz)[T-Connect-Pro_V1.0][Original_Test]_firmware_202501200954.bin) | 出厂程序 |  |

### PlatformIO
1. 安装[VisualStudioCode](https://code.visualstudio.com/Download)，根据你的系统类型选择安装。

2. 打开VisualStudioCode软件侧边栏的“扩展”（或者使用<kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>X</kbd>打开扩展），搜索“PlatformIO IDE”扩展并下载。

3. 在安装扩展的期间，你可以前往GitHub下载程序，你可以通过点击带绿色字样的“<> Code”下载主分支程序，也通过侧边栏下载“Releases”版本程序。

4. 扩展安装完成后，打开侧边栏的资源管理器（或者使用<kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>E</kbd>打开），点击“打开文件夹”，找到刚刚你下载的项目代码（整个文件夹），点击“添加”，此时项目文件就添加到你的工作区了。

5. 打开项目文件中的“platformio.ini”（添加文件夹成功后PlatformIO会自动打开对应文件夹的“platformio.ini”）,在“[platformio]”目录下取消注释选择你需要烧录的示例程序（以“default_envs = xxx”为标头），然后点击左下角的“<kbd>[√](image/4.png)</kbd>”进行编译，如果编译无误，将单片机连接电脑，点击左下角“<kbd>[→](image/5.png)</kbd>”即可进行烧录。

### Arduino
1. 安装[Arduino](https://www.arduino.cc/en/software)，根据你的系统类型选择安装。

2. 打开项目文件夹的“example”目录，选择示例项目文件夹，打开以“.ino”结尾的文件即可打开Arduino IDE项目工作区。

3. 打开右上角“工具”菜单栏->选择“开发板”->“开发板管理器”，找到或者搜索“esp32”，下载作者名为“Espressif Systems”的开发板文件。接着返回“开发板”菜单栏，选择“ESP32 Arduino”开发板下的开发板类型，选择的开发板类型由“platformio.ini”文件中以[env]目录下的“board = xxx”标头为准，如果没有对应的开发板，则需要自己手动添加项目文件夹下“board”目录下的开发板。

4. 打开菜单栏“[文件](image/6.png)”->“[首选项](image/6.png)”，找到“[项目文件夹位置](image/7.png)”这一栏，将项目目录下的“libraries”文件夹里的所有库文件连带文件夹复制粘贴到这个目录下的“libraries”里边。

5. 在 "工具 "菜单中选择正确的设置，如下表所示。

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

6. 选择正确的端口。

7. 点击右上角“<kbd>[√](image/8.png)</kbd>”进行编译，如果编译无误，将单片机连接电脑，点击右上角“<kbd>[→](image/9.png)</kbd>”即可进行烧录。

### firmware烧录
1. 打开项目文件“tools”找到ESP32烧录工具，打开。

2. 选择正确的烧录芯片以及烧录方式点击“OK”，如图所示根据步骤1->2->3->4->5即可烧录程序，如果烧录不成功，请按住“BOOT-0”键再下载烧录。

3. 烧录文件在项目文件根目录“[firmware](./firmware/)”文件下，里面有对firmware文件版本的说明，选择合适的版本下载即可。

<p align="center" width="100%">
    <img src="image/10.png" alt="example">
    <img src="image/11.png" alt="example">
</p>


## 引脚总览

| 屏幕引脚  | ESP32S3引脚|
| :------------------: | :------------------:|
| MOSI         | IO11       |
| MISO         | IO13       |
| DC         | IO41       |
| SCLK         | IO12       |
| CS         | IO21       |
| BL         | IO46       |

| 触摸引脚  | ESP32S3引脚|
| :------------------: | :------------------:|
| SDA         | IO39      |
| SCL         | IO40       |
| RST         | IO47      |
| INT         | IO3       |

| 以太网引脚  | ESP32S3引脚|
| :------------------: | :------------------:|
| MOSI         | IO11       |
| MISO         | IO13       |
| RST         | IO48       |
| SCLK         | IO12       |
| CS         | IO10       |
| INT         | IO9       |

| Lora引脚  | ESP32S3引脚|
| :------------------: | :------------------:|
| MOSI         | IO11       |
| MISO         | IO13       |
| RST         | IO42       |
| SCLK         | IO12       |
| CS         | IO14       |
| INT/DIO1         | IO45       |
| BUSY         | IO38       |

| RS485引脚  | ESP32S3引脚|
| :------------------: | :------------------:|
| UART_TX         | IO17       |
| UART_RX         | IO18       |

| RS232引脚  | ESP32S3引脚|
| :------------------: | :------------------:|
| UART_TX         | IO4       |
| UART_RX         | IO5       |

| CAN引脚  | ESP32S3引脚|
| :------------------: | :------------------:|
| TWAI_TX         | IO6      |
| TWAI_RX         | IO7       |

## 相关测试

## 常见问题

* Q. 看了以上教程我还是不会搭建编程环境怎么办？
* A. 如果看了以上教程还不懂如何搭建环境的可以参考[LilyGo-Document](https://github.com/Xinyuan-LilyGO/LilyGo-Document)文档说明来搭建。

<br />

* Q. 为什么打开Arduino IDE时他会提醒我是否要升级库文件？我应该升级还是不升级？
* A. 选择不升级库文件，不同版本的库文件可能不会相互兼容所以不建议升级库文件。

<br />

* Q. 为什么我的板子上“Uart”接口没有输出串口数据，是不是坏了用不了啊？
* A. 因为项目文件默认配置将USB接口作为Uart0串口输出作为调试，“Uart”接口连接的是Uart0，不经配置自然是不会输出任何数据的。<br />PlatformIO用户请打开项目文件“platformio.ini”，将“build_flags = xxx”下的选项“-DARDUINO_USB_CDC_ON_BOOT=true”修改成“-DARDUINO_USB_CDC_ON_BOOT=false”即可正常使用外部“Uart”接口。<br />Arduino用户打开菜单“工具”栏，选择USB CDC On Boot: “Disabled”即可正常使用外部“Uart”接口。

<br />

* Q. 为什么我的板子一直烧录失败呢？
* A. 请按住“BOOT-0”按键重新下载程序。

## 项目
* [T-Connect-Pro_V1.0](./project/T-Connect-Pro_V1.0.pdf)
