# AdvancedWatch
[![travis-ci build status](https://travis-ci.org/merkez-ul-icadat/AdvancedWatch.svg?branch=master)](https://travis-ci.org/merkez-ul-icadat/AdvancedWatch)
[![Quality Gate Status](https://sonarcloud.io/api/project_badges/measure?project=merkez-ul-icadat_AdvancedWatch&metric=alert_status)](https://sonarcloud.io/dashboard?id=merkez-ul-icadat_AdvancedWatch)

From scratch in Eclipse

![](https://github.com/Xinyuan-LilyGO/TTGO-T-Watch/blob/master/img/1.jpg)

T-Watch is an ESP32-based smart watch hardware designed by Shenzhen Xinyuan Electronics Co., Ltd. Hardware configuration with main core SOC (ESP32), 16MBytes large flash, 8MBytes external SPRAM, integrated multi-channel programmable power management chip ( AXP202), onboard three-axis accelerometer (BMA423), built-in step counter algorithm and other multi-function GSensor, with a variety of different configurations of internal replaceable backplane, such as LORA, GPS, SIM, SD

# PinOut
| Name        | Pins |
| ----------- | ---- |
| TFT CS      | 5    |
| TFT SCLK    | 18   |
| TFT MOSI    | 19   |
| TFT MISO    | -1   |
| TFT DC      | 27   |
| TFT RST     | -1   |
| TFT BL      | 12   |
| SD CS       | 13   |
| SD MOSI     | 15   |
| SD MISO     | 2    |
| SD SCLK     | 14   |
| TOUCH SDA   | 23   |
| TOUCH SCL   | 32   |
| SENSOR SDA  | 21   |
| SENSOR SCL  | 22   |
| UART TX     | 33   |
| UART RX     | 34   |
| USER BUTTON | 36   |
| RTC INT     | 37   |
| TOUCH INT   | 38   |
| AXP202 INT  | 35   |
| BMA423 INT  | 39   |

##  Button description:
**PEK KEY**: facing the screen, right upper right
- (on state) -> long press for four seconds to shut down
- (off state) -> long press for three seconds to boot

**USER KEY** : Close to the Type-C interface
- (on state) -> long press for two seconds to release, deep sleep

## Note:
- BLE only supports the corresponding UUID of the connection and cannot connect to the UUID that does not exist in the program. BLE server reference code [Soil-BLE-Server](https://github.com/lewisxhe/simple-ble)
  
- WIFI connection is only used as time synchronization

- `AXP202X_Library` will have set the DCDC3 output enable to normally open, because DCDC3 will supply power to the ESP32 main chip. If using other methods of control, please be careful not to turn off DCDC3, otherwise it will not be able to burn the program.
  
## Known issue
- Updating the GPS information screen for a long time will cause the program to run away
- BLE connection sometimes causes the program to run away
- The S7XG module only implements ping-pong sending and receiving, and the LORAWALN function is not implemented. For details, refer to the example in the datasheet.

## Low power consumption:
- In standby mode (using the M6/M8 GPS module backplane), the display is off and the current minimum power consumption is approximately ~3 mA. Detailed step reference code closes the screen section

## Resource
- [BMA423 Datasheet](https://ae-bst.resource.bosch.com/media/_tech/media/datasheets/BST-BMA423-DS000.pdf)
- [PCF8563 Datasheet](https://www.nxp.com/docs/en/data-sheet/PCF8563.pdf)
- [ESP32 Datasheet](https://www.espressif.com/sites/default/files/documentation/esp32_datasheet_en.pdf)
- [AXP202 Datasheet](http://www.x-powers.com/en.php/Info/support/article_id/30)
- [LCD Datasheet](http://www.newhavendisplay.com/appnotes/datasheets/LCDs/ST7789V.pdf)
- [FT5206 Datasheet](https://newhavendisplay.com/app_notes/FT5x06.pdf)

##  Using library files
- [TFT_eSPI](https://github.com/lewisxhe/TFT_eSPI)
- [TinyGPSPlus](https://github.com/mikalhart/TinyGPSPlus)
- [lvgl](https://github.com/lewisxhe/lvgl)
- [FT5206_Library](https://github.com/lewisxhe/FT5206_Library)
- [AXP202X_Library](https://github.com/lewisxhe/AXP202X_Library)
- [PCF8563_Library](https://github.com/lewisxhe/PCF8563_Library)
- [BMA423_Library](https://github.com/lewisxhe/BMA423_Library)
- [S7xG_Library](https://github.com/lewisxhe/S7xG_Library)
- [Button2](https://github.com/lewisxhe/Button2)

# Architecture diagram
![https://raw.githubusercontent.com/Xinyuan-LilyGO/TTGO_TWatch_Library/master/images/pins.png](https://raw.githubusercontent.com/Xinyuan-LilyGO/TTGO_TWatch_Library/master/images/pins.png)

# Core Board Pinout
**TFT**

| ESP32 Core | GPIO5 | GPIO19 | GPIO18 | GPIO27 |
| :--------: | :---: | :----: | :----: | :----: |
|  ST7789V   |  CS   |  MOSI  |  SCLK  |   DC   |

**Button**

| ESP32 Core  | GPIO36 |
| :---------: | :----: |
| User Button | Button |

**Sensor**

| ESP32 Core | GPIO21 | GPIO22 |  GPIO39   |
| :--------: | :----: | :----: | :-------: |
|   BMA423   |  SDA   |  SCL   | Interrupt |

**PMU**

| ESP32 Core | GPIO21 | GPIO22 |  GPIO35   |
| :--------: | :----: | :----: | :-------: |
|   AXP202   |  SDA   |  SCL   | Interrupt |

**RTC**

| ESP32 Core | GPIO21 | GPIO22 |  GPIO37   |
| :--------: | :----: | :----: | :-------: |
|  PCF8563   |  SDA   |  SCL   | Interrupt |

**TOUCH**

| ESP32 Core | GPIO23 | GPIO32 |  GPIO38   |
| :--------: | :----: | :----: | :-------: |
|  FT6236U   |  SDA   |  SCL   | Interrupt |

**TF Card**

| ESP32 Core | GPIO13 | GPIO15 | GPIO2 | GPIO14 |
| :--------: | :----: | :----: | :---: | :----: |
|  TF Card   |   CS   |  MOSI  | MISO  |  SCLK  |

# Bottom plate Pinout

**S7XG_Lora & GPS**

| ESP32 Core | GPIO33 | GPIO34 |
| :--------: | :----: | :----: |
| S7XG_Lora  |   TX   |   RX   |
* Onboard SD card slot
