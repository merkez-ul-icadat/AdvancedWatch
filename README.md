# AdvancedWatch
[![travis-ci build status](https://travis-ci.org/merkez-ul-icadat/AdvancedWatch.svg?branch=master)](https://travis-ci.org/merkez-ul-icadat/AdvancedWatch)

From scratch in Eclipse

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
