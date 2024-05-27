# Testing and Automation for STM32 Projects

## Ellis chagnes May 2024

Run as a gitpod https://gitpod.io/#github.com/hpssjellis/stm32-testing-automation

## Commands to try

Here are some other common options you might use with STM32_Programmer_CLI:

-c: Connect to a device.  
-r: Read memory from a device.  
-w: Write memory to a device.  
-e: Erase memory of a device.  
-u: Unprotect memory.  


```

STM32_Programmer_CLI -l

STM32_Programmer_CLI -c port=SWD

STM32_Programmer_CLI -c port=SWD -r8 0x08000000 1024

STM32_Programmer_CLI -c port=SWD -w your_firmware.hex 0x08000000

STM32_Programmer_CLI -c port=SWD -u



```

## The big issue: online

This gitpod is an online version of stm32_programer_cli so connecting to a device is going to be tricky. Not sure if it is worth the effort but I will try a few methods.

possibly the arduino connect agent, websockets, webSerial or an app called socat

install socrat on both client and online server

on client

```
sudo apt-get install socat

socat TCP-LISTEN:54321,reuseaddr,fork /dev/ttyUSB0

ssh -R 54321:localhost:54321 user@remote_server

```

on server
```
sudo apt-get install socat

socat PTY,link=/dev/virtualcom0,raw TCP:localhost:54321

STM32_Programmer_CLI -c port=/dev/virtualcom0



```




[![Language](https://img.shields.io/badge/Made%20with-C-blue.svg)](https://shields.io/)
[![Language](https://img.shields.io/badge/Made%20with-C++-blue.svg)](https://shields.io/)
[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](https://opensource.org/licenses/MIT)


## LinkedIn Articles

- [Part 0 - Creating a minimal build environment with Docker.](https://www.linkedin.com/pulse/part-0-creating-minimal-build-environment-docker-dias-m-sc--pg72e)
