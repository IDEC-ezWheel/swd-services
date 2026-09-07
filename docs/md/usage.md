# Start using swd-services

## 1. Check if a can interface is mounted

```shell
ip link show
```

If there is no can interface, mount it.

## 2. Configure the CAN bus on Linux socket (Optional if already configured)

```shell
sudo ip link set down can0
sudo ip link set can0 up txqueuelen 1000 type can bitrate 1000000 restart-ms 100
```

*Caution* `can0` can differ in your configuration, e.g. `CAN0`, `can1`, ...

### Check in the CAN settings that CAN state is 'UP'

```shell
ip -details -statistics link show can0
```

## 3. Configure D-Bus session (Optional if already one exists)

```shell
unset LD_LIBRARY_PATH 
/usr/bin/dbus-launch > /tmp/SYSTEMCTL_dbus.id
```

## 4. Start ezw-smc-service

```shell
export $(cat /tmp/SYS*.id)
export LD_LIBRARY_PATH=/opt/ezw/usr/lib:$LD_LIBRARY_PATH
/opt/ezw/usr/bin/ezw-smc-service /opt/ezw/usr/etc/ezw-smc-core/drive_config.ini
```

*Success if you can see those logs:*

- *"Initialize PDO success."*
- *"Initializing dbus service!"*

## 5. Examples

### Code using ezw-smc-core C++ API

The C++ code 'DiffDriveController.cpp' for [ROS](https://github.com/IDEC-ezWheel/swd_ros_controllers/blob/main/src/diff_drive_controller/DiffDriveController.cpp) and [ROS2](https://github.com/IDEC-ezWheel/swd_ros2_controllers/blob/main/src/diff_drive_controller/DiffDriveParameters.cpp), can be used to control a pair of SWD® drives, as a diffrential kinematic platform.

### Code using ezw-smc-service python API

The 'remote.py' python script can be used to diagnostic and control a SWD® drive:

```shell
export $(cat /tmp/SYS*.id)
export LD_LIBRARY_PATH=/opt/ezw/usr/lib:$LD_LIBRARY_PATH
/opt/ezw/usr/sbin/remote.py smc_drive
```

*NOTA*: Keyboard commands are listed at the end, e.g. Press 'a' to refresh the 'Diagnostic'.

The 'swd_xxxx_x_commissioning.py' python scripts can be used to [configure a SWD® drive](https://github.com/IDEC-ezWheel/swd-starter-kit-config):

```shell
swd_left_4_commissioning.py
swd_right_5_commissioning.py
```

*Note that, if you are using SWD® diff_drive_controller you might have to stop it before commissioning SWD® drives.*

## Troubleshooting

### Install dbus-x11

```shell
sudo apt install dbus-x11
```

### Check CAN bus communication ongoing

```shell
sudo apt install can-utils
cansend can0 000#0100 `#Broadcast NMT start`
candump can0
```

Or

```shell
pip install Python-CAN-Viewer
python3 -m python_can_viewer
```

If messages are displayed in the terminal, CAN communnicaiton is established. `Ctrl+c` to exit

### AttributeError: module 'attr' has no attribute 's'

```shell
pip uninstall attr
pip install attrs
```

### D-Bus error

If you have the following error:

```shell
SMCS;CAN;ERROR;operator();374;Initialize PDO failed;
SMCS;SMCDS;INFO;main;210;Initializing dbus service !;
process 24396: arguments to dbus_set_error_from_message() were incorrect, assertion "(error) == NULL || !dbus_error_is_set ((error))" failed in file dbus-message.c line 3938.
This is normally a bug in some application using the D-Bus library.
  D-Bus not built with -rdynamic so unable to print a backtrace
Aborted (core dumped)
```

Remove the D-Bus session

```shell
sudo rm /tmp/SYSTEMCTL_dbus.id
```

And (re)[Configure D-Bus session](https://github.com/IDEC-ezWheel/swd-services/blob/main/docs/md/usage.md#configure-d-bus-session-optional-if-already-one-exists).
