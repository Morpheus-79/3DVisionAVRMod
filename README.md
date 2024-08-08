# 3DVisionAVRMod
Partial NVIDIA 3D Vision Emitter emulation using AVR microcontrollers  

This is a fork of [3DVisionAVR](https://github.com/lukis101/3DVisionAVR) by 'lukis101'. I've modified the 3D-Vision IR protocol settings inside the *IRProtocols.h* with some more optimal values and added the protocol for the ancient ELSA Revelator glasses. I've also implemented a (very crude and amateurish) refresh rate detection. It measures the time between the sent out tokens multiple times and then uses the average time of all measurements to calculate the refresh rate.

The result isn't very accurate... but it's good enough to output a rough estimation within a range, which is then utilized to use different *FRAME_DURATION* and *FRAME_PAN* values, dependent of the set refresh rate. If no valid refresh rate is detected, it uses the default *FRAME_DURATION* and *FRAME_PAN* settings.
