# ESP32-MicroPython-ssd1306
A fork of the driver for SSD1306 displays to solve "AttributeError: 'Pin' object has no attribute 'high'" when using spi.
解决 SSD1306 使用 SPI 时出现 "AttributeError: 'Pin' object has no attribute 'high'" 的问题



The reason for this error is that ESP32 does not support the use of the high/low method, and all high/low in the ssd1306.py should be replaced with on/off.

# Example Usage

Upload `ssd1306.py` to your ESP32 MCU and run below code.

```python

from machine import Pin,SoftSPI, SPI
from ssd1306 import SSD1306_SPI
 

# 创建 SPI 对象
spi=SoftSPI(baudrate=600000, sck=Pin(18),mosi=Pin(23),miso=Pin(19))

# spi=SPI(2,100000)

oled=SSD1306_SPI(128,64,spi,dc=Pin(2),res=Pin(15),cs=Pin(4))  #创建oled对象
 
# 清屏
oled.fill(0)
# 要显示的字符；x坐标；y坐标；显示1，不显示0
oled.text("hello",40,28,1)
# 显示
oled.show()

```

# 使用方法

出现这种报错的原因是由于 ESP32 单片机不支持使用 high/low 方法，需要把 ssd1306.py 文件中的所有 high/low 替换为 on/off。

把该项目中的 ssd1306.py 文件上传到 ESP32 单片机中，然后运行以下代码：


```python

from machine import Pin,SoftSPI, SPI
from ssd1306 import SSD1306_SPI
 

# 创建 SPI 对象
spi=SoftSPI(baudrate=600000, sck=Pin(18),mosi=Pin(23),miso=Pin(19))

# spi=SPI(2,100000)

oled=SSD1306_SPI(128,64,spi,dc=Pin(2),res=Pin(15),cs=Pin(4))  #创建oled对象
 
# 清屏
oled.fill(0)
# 要显示的字符；x坐标；y坐标；显示1，不显示0
oled.text("hello",40,28,1)
# 显示
oled.show()

```








