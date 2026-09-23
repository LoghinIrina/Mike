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
