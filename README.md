# pizero-tflite
It isn't easy to get the Tensorflow Lite distribution compiled and installed onto a Raspberry Pi Zero. Here are some helpful notes.

The rpi_tools are years out of date. The recommended g++ compiler doesn't like c++ 11 and fails loudly. Not sure why this isn't caught.

I used Ubuntu to get this working but I suspect any linux would suffice if you can find the requisite libs. OS X does not seem happy about this toolchain. Avoid.

I was able to apt install arm-linux-gnueabi-g++, compile a hello world, and run it on the pi. I recommend you do this to prove that this is the correct compiler and it can produce runnable programs for the pi.

TensorFlow says:
### Step 4b. To build ARMv6 binary for Raspberry Pi Zero:
`PATH=../rpi_tools/arm-bcm2708/arm-rpi-4.9.3-linux-gnueabihf/bin:$PATH \
  ./tensorflow/lite/tools/make/build_rpi_lib.sh TARGET_ARCH=armv6`

This is incorrect. Here is what worked for me:


`./tensorflow/lite/tools/make/build_rpi_lib.sh TARGET_ARCH=armv6 TARGET_TOOLCHAIN_PREFIX=arm-linux-gnueabi-`

Hope this helps.
