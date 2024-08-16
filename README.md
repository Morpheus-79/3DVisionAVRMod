# 3DVisionAVRMod
Partial NVIDIA 3D Vision Emitter emulation using AVR microcontrollers  

This is a fork of [3DVisionAVR](https://github.com/lukis101/3DVisionAVR) by 'lukis101' (Dj Lukis.LT). The original project uses an Arduino Micro Pro for emulating NVIDIAs 3D Vision Emitter with a couple of additional features NVIDIAs hardware doesn't provide (like: support for lots of different IR 3D glasses and driving all supported glasses via VESA 3-pin header sync signal).

This modified code enhances the 3D-Vision IR protocol settings inside the *IRProtocols.h* with some more optimal values and includes the protocol for the ancient ELSA Revelator 3D glasses. I've also implemented a (very crude and amateurish) refresh rate detection. It measures the time between the sent out tokens multiple times and then uses an average of all measurements to calculate the refresh rate.

The result isn't very accurate... but it's good enough to output a rough estimation within a (freely definable) range, which is then utilized to use different *FRAME_DURATION* and *FRAME_PAN* values, dependent of the set refresh rate. If no valid refresh rate is detected, it uses some default *FRAME_DURATION* and *FRAME_PAN* settings.

By default there are 3 refresh rates defined in the *IREmitter.h*:
* **85Hz:** FRAME_DURATION (2   ⃰400); FRAME_PAN (2   ⃰10500)
* **100Hz:** FRAME_DURATION (2   ⃰400); FRAME_PAN (2   ⃰9100)
* **120Hz:** FRAME_DURATION (2   ⃰400); FRAME_PAN (2   ⃰7500)

You can add more (and change the default detection range) inside the *IREmitter.c* under:
> // Set FRAME_DURATION and FRAME_PAN according to refresh rate

The default values for unrecognized refresh rates are in there too.

Todo list (maybe... one day):
* add possibility to switch between protocols on the fly via an additional tactile button
* add RGB LEDs to give a visual cue for what protocol and/or what mode is in use

Please refer to the [original repository](https://github.com/lukis101/3DVisionAVR) for further information about different settings. I also recommend reading the [README by 'b3nn'](https://github.com/b3nn/3DVisionAVR-Hardware/blob/main/README-FLASH-FIRMWARE.md) about flashing the firmware onto the Arduino Micro Pro. If you get a build error like:
> Error can't create obj/Emitter.o: No such file or directory

... please try to create a sub directory called ***obj*** inside the ***3DVisionAVR*** directory and run the build solution again.
