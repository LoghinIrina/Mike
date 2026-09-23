Mike is a small robotic car that can be controlled in several ways.
### First method
Mike incorporates an ESP32 that hosts a web interface on the router's local network, serving as a remote control (the car moves based on the buttons pressed on the interface). This is the first method for controlling Mike.
#### Architecture for first method
``` text
Phone / Computer
        |
      Wi-Fi
        |
      Router
        |
      Wi-Fi
        |
ESP32: web interface, motor control, OLED
         |
Motor drivers -> motors
```
### Second method
The second control method involves hand detection using the computer's webcam. This method requires the use of localhost or HTTPS, as a computer's camera cannot be accessed via standard HTTP; consequently, the web server cannot be hosted on the car's ESP32 as it is in the first method. I chose the localhost approach: the laptop's browser detects the hand, converts the hand's position or finger configuration into a command—such as FORWARD, LEFT, or STOP—and sends that command via Wi-Fi to the ESP32. The ESP32 simply executes the commands on the motors.
``` text
Laptop
  |
Laptop Camera
  |
Hand Detection
(MediaPipe / JavaScript in browser)
  |
Gesture Recognition
(forward / back / left / right / stop)
  |
Web Interface
running in browser
  |
Wi-Fi
  |
Router
  |
Wi-Fi
  |
ESP32: web server, command receiver, motor control
  |
Motor drivers
  |
Motors
```

### Third method
The third method is still a work in progress, and I’ll post an update as soon as I finish it.
### Main Components:
- 4WD Smart Car Chassis Kit <https://sigmanortec.ro/Kit-sasiu-Smart-Car-4WD-p136281803> 
- Step-Down Converter <https://sigmanortec.ro/Modul-coborator-tensiune-XL4015-5-36VDC-5A-75W-cu-display-p158469512>
- Motor Driver ×2 <https://ardushop.ro/ro/motoare-si-drivere/1753-modul-driver-dual-de-motoare-25-a-6427854026408.html>
- Red Breadboard <https://www.emag.ro/breadboard-170-puncte-ai188-s461/pd/D7M90YMBM/>
- ESP32 <https://sigmanortec.ro/placa-dezvoltare-esp32-ch340c-30p-usb-c-wifi-si-bluetooth>
- 2S LiPo Battery XT60 <https://www.aliexpress.com/item/1005007883555706.html>
#### Other items needed:
- dupont wires
- soldering iron
- 18AWG wire
- XT60 connector
- 5A or 7.5A fuse
- fuse holder
- double-sided tape
