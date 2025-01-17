# www.open-ats.eu
## 3D printed ground vehicle controlled over mobile internet for observation / transportation / development

<img src="https://www.open-ats.eu/linking/vehicleclear.png">

[Demo video](https://www.youtube.com/watch?v=fuw2pRNdg8U) &nbsp;&nbsp;&nbsp;
[Documentation](https://www.open-ats.eu/documentation.html) &nbsp;&nbsp;&nbsp;
[3D-Model vehicle](https://www.open-ats.eu/3dmodel_main.html) &nbsp;&nbsp;&nbsp;
[3D-Model electronics](https://www.open-ats.eu/3dmodel_elec.html) &nbsp;&nbsp;&nbsp;
[3D-Model print](https://www.open-ats.eu/3dmodel_print.html)

## features:
#### programs
- programs for access the vehicle over movile internet 
  - program for controlling motors
  - program for videostreaming
- open-source software, all programs written in python (focus on easy to understand)
- programs using udp for low latency
- opencv for taking video and displaying them, good for future AI 
- all programs can as well be used for standard rc-cars, airplanes or boats <br /> with PWM input and even for stationary surveillance cameras.

#### 3d printing
- open-source hardware, hole vehicle 3D-printable
  - 3D-printed ball bearing (printable in one piece without any support)
  - 3D-printed flexible tires (airless, filaflex 82A)
- insertable metal springs on all axis
- assembly with only M3-screws and threaded brass inserts
- support structures rarely required, low part count, easy assemply

#### electronics
- two individual servomotors to steer the front wheels
- two individual brushless motors directly integrated into the rear wheels 
  (inwheel, hubmotor)
- raspberry pi
- blheli32 ESC's (will soon change to B-G431B-ESC1)
- 18650 li-ion cells with bms (25.2V)
- low cost

#### disadvantages
- low torque cause of directdrive hub motor (will increase with planetary gear)
- low torque cause of sensorless ESC (will increase with currentsensing ESC)
- video stream consumes too much data
## get started just write the following ([for detailed info see guide](https://github.com/Open-ATS-Github/Newone/blob/main/002_program/readme.txt)):
```
python3 main.py
```

## example code:
#### take and show webcam/rpi-camera image
```
import cv2
cap = cv2.VideoCapture(0)
img = cap.read()[1] #capturing image
cv2.imshow('stream',img) #1st argument = windows name
cv2.waitKey(1)
```
#### control motor with rpi (pin 15, pwm=1500ms)
```
#start GPIO deamon first: sudo pigpiod (preinstalled on RPI)
import pigpio #importing gpio library 
output = pigpio.pi().set_servo_pulsewidth #just shorting that long name
output(15,1500)#gpio 15, pwm=1500ms
```
#### send data to the server
```
import socket
address_server	=('your ip here',3274)
soc = socket.socket(family = socket.AF_INET, type = socket.SOCK_DGRAM) #internet protocol parameters
soc.sendto(b'your message',address_server)
```
<img src="https://www.open-ats.eu/3dfiles/print.jpg">

feel free to contact for any problem: info@open-ats.eu, also consider [donating](https://www.open-ats.eu/donate.html) or get a 
[videocall with devs(20$/hour)](https://www.open-ats.eu/contact.html)
