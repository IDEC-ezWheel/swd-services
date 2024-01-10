# ez-Wheel SWD® services

APIs for managing SWD® (Safety Wheel Drive) drive

## Overview

This repository provides the documentation of the APIs provided in the linux debian package **swd-services**.
These APIs can be used to control and configure the SWD® (Safety Wheel Drive) powered by [ez-Wheel](https://www.ez-wheel.com).

| <img src="https://www.ez-wheel.com/storage/image-product/visuels-swd-core-2-0-0.png" width="45%"></img> | <img src="https://ez-wheel.com/storage/image-product/ezswd125im-31102023-photo-hd-det.png" width="50%"></img> | <img src="https://www.ez-wheel.com/storage/image-product/roue-electrique-swd-150-2-0-0-0.png" width="45%"></img>       |
| ------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------- |
| [SWD® Core](https://www.ez-wheel.com/en/safety-gear-motor) <br />Safety gear motor                      | [SWD® 125](https://ez-wheel.com/en/safety-wheel-drive-swd-125) <br /> Medium duty Safety Wheel Drive |[SWD® 150](https://www.ez-wheel.com/en/swd-150-safety-wheel-drive) <br /> Heavy duty Safety Wheel Drive                      | 

Users should regularly inform themselves about updates of this driver (Activating GitHub notifications with 'Watch', 'All activity' button on top of this page).

## Prerequisites

- SWD® drive
- Ubuntu 22.04 jammy or Ubuntu 20.04 focal
- dbus-x11
- CAN bus communication established bewteen the IPC and the SWD® drive

## Linux debian package

It is available for the following platforms:

- *ARM 32-bits*, i.e. **armhf** debian packages (only for Ubuntu 20.04 focal), for ARM 32 bits machines
- *ARM 64-bits*, i.e. **arm64** debian packages, for ARM 64 bits machines, since version 0.2.6
- *AMD 64-bits*, i.e. **amd64** debian packages, for x86 64 bits machines
