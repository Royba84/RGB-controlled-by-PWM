# RGB-controlled-by-PWM

In this project we will learn how to control RGB using PWM and a Joystick.

To make it a little bit "complex" we won't use an RGB moudle or Joystick moudle BUT - 3 diffrent LEDS as an RGB and 2 potentiometers (one for each axis) as a joystick.

You can implement is as you wish :)

Lets start:

Color of the R G and B LED is controlled by an XY Joystick (two potentiometers and button).

Position of the XY-Joysticks is evaluated every 250ms by using a timer

The system can work at two modes:

Mode A:

X-axis of the joystick controlled G color intensity by using PWM

Y-axis of the joystick controlled R color intensity by using PWM

B color intensity is not changed

Intensity of the R, G, B are graphically shown on the serial Plotter

Mode B:

X-axis of the joystick controlled color intensity of all LEDs by using PWM

Y- axis of the joystick CHANGED R color intensity by using PWM G and B color

intensities are not changed Intensities of the R, G, B are

graphically shown on the serial Plotter.

ModeA:

In this plot we can see the graphs of LEDs intensity. The Red graph represent the blue LED, the yellow graphrepresent the red LED, and the blue graph represent the green LED.

![image](https://user-images.githubusercontent.com/105777016/169201716-a49e934a-15cf-4ef5-ba75-08228b4852e6.png)

ModeB:

In this plot we can see the graphs ofLEDs intensity.We switched from mode A to mode B by pushing the button in the beginning of themeasurement. TheRed graph represent the blue LED, the yellow graph represent the red LED, andthe blue graph represent the green LED.

![image](https://user-images.githubusercontent.com/105777016/169201742-b049c3ad-0fc0-464a-844f-9359bae4f0e4.png)

Block diagram:

![image](https://user-images.githubusercontent.com/105777016/169201767-6265b31f-021d-4b4d-b264-ca68600215cb.png)

Electric circuit:

![image](https://user-images.githubusercontent.com/105777016/169201789-f4dc7175-a9ab-4bdb-a96a-4cba17eb61d0.png)

System layout:

![image](https://user-images.githubusercontent.com/105777016/169201806-32d98763-45fe-4fe3-88ab-78a2a8b3f135.png)

