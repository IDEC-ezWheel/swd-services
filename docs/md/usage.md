# swd-services

## Start using swd-services

### Configure CAN bus on Linux socket (Optional if already configured)

```shell
sudo ip link set down can0
sudo ip link set can0 up type can bitrate 1000000 restart-ms 100
sudo ip link set can0 txqueuelen 1000
```

### Configure D-Bus session (Optional if already one exists)

### Start ezw-smc-service

```shell
unset LD_LIBRARY_PATH 
/usr/bin/dbus-launch > /tmp/SYSTEMCTL_dbus.id
export $(cat /tmp/SYS*.id) 
export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:/opt/ezw/usr/lib 
/opt/ezw/usr/bin/ezw-smc-service /opt/ezw/usr/etc/ezw-smc-core/drive_config.ini
```

*Success if you can see those logs:*

- *"Initialize PDO success."*
- *"Initializing dbus service!"*

## Examples

### Code using ezw-smc-core c++ API

The c++ code 'DiffDriveController.cpp' for [ROS](https://github.com/ezWheelSAS/swd_ros_controllers/blob/main/src/diff_drive_controller/DiffDriveController.cpp) and [ROS2](https://github.com/ezWheelSAS/swd_ros2_controllers/blob/main/src/diff_drive_controller/DiffDriveParameters.cpp), can be used to control a pair of SWD® drives, as a diffrential kinematic platform.

### Code using ezw-smc-service python API

The python 'remote' script can be used to control a SWD® drive:

```shell
/opt/ezw/usr/sbin/remote.py smc_drive
```

*Keyboard commands are listed at the end.*

The python 'swd_xxxx_x_commissioning' scripts can be used to [configure a SWD® drive](https://github.com/ezWheelSAS/swd-starter-kit-config):

```shell
swd_left_4_commissioning.py
swd_right_5_commissioning.py
```

*Note that, if you are using SWD® diff_drive_controller you might have to stop it before commissioning SWD® drives.*

## Troubleshooting

#### Install dbus-x11

```shell
sudo apt install dbus-x11
```

#### Check that a can interface is mounted

```shell
ip link show
```

if there is no can interface, mount it.

#### AttributeError: module 'attr' has no attribute 's'

```shell
pip install attr
pip install attrs
```
