# Star-Track
Arduino powered GoTo-mount inspired star tracking system.

more info: http://www.instructables.com/id/Star-Track-Arduino-Powered-Star-Pointer-and-Tracke/

There are two Arduino's working in order. Arduino Uno being master and nano being the slave.

Master module

The master(Uno) module has two inputs,

1-Gyro data

2-RTC(Real Time Clock) data

and 6 outputs,

1-cw(base motor clockwise)

2-ccw(base motor counter clockwise)

3-stahp(base motor stop)

4-cw2(DEC motor clockwise)

5-ccw2(DEC motor counter clockwise)

6-stahp2(DEC motor stop)

The RTC is set to UTC time, a function calculates local sidereal time in degrees and rotates the mount to 0h RA position. The loop constantly checks if the gyro data is equal to the user input & sidereal time data. The default is 0,0. If there is a change and the equality breaks the master module send a command to the slave module.

If the user value is higher than the gyro value a signal is sent through cw the motor turns clockwise.

If the user value is less than the gyro value a signal is sent through ccw the motor turns counter clockwise

If the user value is equal to the gyro value a signal is sent through stahp and the motor stops
same for cw2,ccw2,stahp2.

This way the mount will turn to the user-specified coordinates. And update with sidereal time thus it will track the sky.

Note: I could use serial communication between the two Arduino's but since the analog pins are used by the inputs I had to use digital pins.
