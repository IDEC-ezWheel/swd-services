# Interface commonapi.SmcService.Core

Version: 1.0

This section is generated from the Franca IDL file for Interface Core in package commonapi.SmcService

Interface description: 
SWD product services.

## Methods

### Method connect

Connect to the canopen device with the node id specifed.

Input Parameters:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| UInt8 | node_id | The node id of the device : from 1 to 127. |

Output Parameters:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| Int32 | error_code |  |

### Method disconnect

Disconnect from the canopen device.

Output Parameters:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| Int32 | error_code |  |

### Method getConnectionStatus

Retrieve the core status connection.

Output Parameters:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| Boolean | is_connected | The connection status. |
| Boolean | is_PDO_init_succeeded | The PDO status. |
| Int32 | error_code |  |

### Method getConnectedNodeId

Get the connected node id.

Output Parameters:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| UInt8 | node_id | The node id of the connected device : from 1 to 127. |
| Int32 | error_code |  |

### Method getCanDevice

Get the CAN device.

Output Parameters:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| String | can_device | The CAN device. (ie "can0") |
| Int32 | error_code |  |

### Method getCoreVersion

Retrieve the SWD core services version. Ex : 0.2.8

Output Parameters:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| String | core_version | The core version. |
| Int32 | error_code |  |

### Method switchMode

Switch into the specified canopen object dictionary mode.

Input Parameters:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| [Enumeration ModeEnum](#enumeration-modeenum) | mode | The new mode. |

Output Parameters:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| Int32 | error_code |  |

### Method loadSettingsFromDCF

Load settings from DCF file.

Input Parameters:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| String | dcf_file | Indicates the DCF file. |

Output Parameters:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| Int32 | error_code |  |

### Method saveSettingsToDCF

Save settings to DCF file.

Input Parameters:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| String | dcf_file | Indicates the DCF file. |

Output Parameters:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| Int32 | error_code |  |

### Method loadSettingsFromDevice

Load settings from the device.

Output Parameters:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| Int32 | error_code |  |

### Method saveSettingsToDevice

Save settings to the device.

Output Parameters:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| Int32 | error_code |  |

## Enumerations

### Enumeration ModeEnum

Indicates the canopen object dictionary mode type.

|     |     |     |
| --- | --- | --- |
| Enumerator | Value | Description |
| REMOTE | 0 | The canopen object dictionary is synchronize with the device. (default) |
| LOCAL | 1 | The canopen object dictionary is local. Load/SaveSettingsFromDevice shall be used to synchronize it with the device. |

Used in: 
[Method switchMode](#method-switchmode)

# Interface commonapi.SmcService.NMT

Version: 1.0

This section is generated from the Franca IDL file for Interface NMT in package commonapi.SmcService

Interface description: 
[CIA301] Network management (NMT).

## Methods

### Method getNMTState

Retrieve the NMT state of the SWD product.

Output Parameters:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| [Enumeration NMTState](#enumeration-nmtstate) | nmt_state | The NMT state. |
| Int32 | error_code |  |

### Method setNMTState

Modify the NMT state of the SWD product.

Input Parameters:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| [Enumeration NMTCommand](#enumeration-nmtcommand) | nmt_command | The new NMT state. |

Output Parameters:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| Int32 | error_code |  |

### Method broadcastNMTState

Broadcast the NMT state to all CANopen nodes.

Input Parameters:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| [Enumeration NMTCommand](#enumeration-nmtcommand) | nmt_command | The new NMT state. |

Output Parameters:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| Int32 | error_code |  |

## Enumerations

### Enumeration NMTState

Indicates the NMT state of the SWD product. 
NOTA : 
- CANopen devices enter the NMT state Pre-operational directly after finishing the CANopen devices initialization. 
- During this NMT state CANopen device parameterization and CAN-ID-allocation via SDO (e.g. using a configuration tool) is possible. 
  Then the CANopen devices may be switched directly into the NMT state Operational.
- The NMT state machine determines the behavior of the communication function unit. 
NOTA : 
- In the NMT state Pre-operational, communication via SDOs is possible. PDOs do not exist, so PDO/SRDO communication are not allowed.
- In the NMT state Operational, all communication objects are active.
- In the NMT state Stopped, all communication objects are stopped (except node guarding and heartbeat, if active).

|     |     |     |
| --- | --- | --- |
| Enumerator | Value | Description |
| UNKNOWN | 0 | The SWD product is not detected on the can bus. |
| STOPPED | 4 | The SWD product is in the NMT state Stopped. |
| OPER | 5 | The SWD product is in the NMT state Operational. |
| PREOP | 127 | The SWD product is in the NMT state Pre-operational. |

Used in: 
[Method getNMTState](#method-getnmtstate)
### Enumeration NMTCommand

Indicates the NMT state command. 
NOTA : The NMT state initialisation is divided into three NMT sub-states in order to enable a complete or partial reset of the SWD product:
- Initialising : This is the first NMT sub-state the CANopen device enters after power-on or hardware reset. 
  After finishing the basic CANopen device initialisation the CANopen device enters autonomously into the NMT sub-state reset application.
- Reset application : In this NMT sub-state the parameters of the manufacturer-specific profile area and of the standardized device profile area are set to their power-on values. 
  After setting of the power-on values the NMT sub-state reset communication is entered autonomously.
- Reset communication : In this NMT sub-state the parameters of the communication profile area are set to their power-on values. 
  After this the NMT state Initialisation is finished and the CANopen device executes the NMT service boot-up write and enters the NMT state Pre-operational. 
NOTA : Power-on values are the last stored parameters.

|     |     |     |
| --- | --- | --- |
| Enumerator | Value | Description |
| OPER | 1 | Switch into the NMT state Operational. |
| STOP | 2 | Switch into the NMT state Stopped. |
| PREOP | 128 | Switch into the NMT state Pre-operational. |
| RESET_NODE | 129 | Switch into the NMT sub-state Reset application. |
| RESET_COMM | 130 | Switch into the NMT sub-state Reset communication. |

Used in: 
[Method setNMTState](#method-setnmtstate)
, 
[Method broadcastNMTState](#method-broadcastnmtstate)

# Interface commonapi.SmcService.EMCY

Version: 1.0

This section is generated from the Franca IDL file for Interface EMCY in package commonapi.SmcService

Interface description: 
Emergency ( EMCY ) functionalities

## Methods

### Method getErrorBehavior

Retrieve the ErrorBehavior of selected ErrorType.

Input Parameters:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| [Enumeration ErrorType](#enumeration-errortype) | error_type | Selected ErrorType. |

Output Parameters:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| [Enumeration ErrorBehavior](#enumeration-errorbehavior) | error_behavior | ErrorBehavior of selected ErrorType. |
| Int32 | error_code |  |

### Method setErrorBehavior

Set the ErrorBehavior of selected ErrorType.

Input Parameters:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| [Enumeration ErrorType](#enumeration-errortype) | error_type | Selected ErrorType. |
| [Enumeration ErrorBehavior](#enumeration-errorbehavior) | error_behavior | ErrorBehavior of selected ErrorType. |

Output Parameters:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| Int32 | error_code |  |

### Method clearErrorList

Clear all previous error stored in the pre-defined error array.

Output Parameters:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| Int32 | error_code |  |

### Method getErrorCount

Return the number of error present in the pre-defined error array.

Output Parameters:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| Int32 | error_count | Number of errors. |
| Int32 | error_code |  |

### Method getErrorRegister

Return error register. 
Error Register is made of 8 bits indicating the type of error that happend: 
- [0] Generic
- [1] Current
- [2] Voltage
- [3] Temperature
- [4] Communication
- [5] Device profile specific
- [6] 0 (Reserved)
- [7] Manufacturer

Output Parameters:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| UInt8 | error_register | 8 bits error register. |
| Int32 | error_code |  |

### Method getError

Return EMCY_ERROR_CODE (as UInt32) at index in the pre-defined error array.

Input Parameters:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| Int32 | index | Selected index. |

Output Parameters:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| UInt32 | emcy_error_code | cf EMCY_ERROR_CODE. |
| Int32 | error_code |  |

## Enumerations

### Enumeration ErrorBehavior

Indicates the behavior in case of an error. 
NOTA : 
    - Each ErrorType have an ErrorBehavior.
    - ErrorBehavior will affect the NMT state machine.

|     |     |     |
| --- | --- | --- |
| Enumerator | Value | Description |
| NMT_PREOP | 0 | Change NMT to PreOperational ( Only if NMT was in Operational ). |
| NMT_NO_CHANGE | 1 | No change to NMT. |
| NMT_STOP | 2 | NMT state change to Stopped state. |

Used in: 
[Method getErrorBehavior](#method-geterrorbehavior)
, 
[Method setErrorBehavior](#method-seterrorbehavior)
### Enumeration ErrorType

There are 3 different Emergency ErrorType.
    In case of an error, NMT state shall be affected in accordance
    with ErrorBehavior parameter.
NOTA :  
    - COMMUNICATION ErrorBehavior shall be read-only

|     |     |     |
| --- | --- | --- |
| Enumerator | Value | Description |
| COMMUNICATION | 1 | Communication error, handled by stack. |
| EMCY_ERROR | 2 | EMCY Message that are flaged ERROR. |
| EMCY_WARNING | 3 | EMCY Message that are flaged WARNING. |

Used in: 
[Method getErrorBehavior](#method-geterrorbehavior)
, 
[Method setErrorBehavior](#method-seterrorbehavior)
### Enumeration EMCY_ERROR_CODE

Emergency error codes used.

|     |     |     |
| --- | --- | --- |
| Enumerator | Value | Description |
| GENERIC_ERROR | 4096 | Definition for error code generic error |
| ERROR_RESET | 0 | Definition for error code reset error |
| DC_OVER_CURRENT_1 | 8737 | Definition for error code over current type 1 = warning |
| DC_OVER_CURRENT_2 | 8738 | Definition for error code over current type 2 = error |
| BMS_OC | 8753 | Definition for error code over current BMS |
| OVER_VOLTAGE_1 | 12817 | Definition for error code over voltage type 1 = error |
| OVER_VOLTAGE_2 | 12818 | Definition for error code over current type 2 = warning |
| UNDER_VOLTAGE_1 | 12833 | Definition for error code under voltage type 1 = error |
| UNDER_VOLTAGE_2 | 12834 | Definition for error code under voltage type 2 = warning |
| BMS_UV | 12849 | Definition for error code under voltage BMS |
| BMS_OV | 12850 | Definition for error code over voltage BMS |
| BMS_UV_CHA | 12851 | Definition for error code under voltage BMS during CHA |
| TEMPERATURE | 16384 | Definition for error code temperature |
| EXCESS_TEMPERATURE_DEVICE | 16912 | Definition for error code temperature in device |
| OVER_TEMPERATURE_BMS | 16928 | Definition for error code OT in pack |
| UNDER_TEMPERATURE_BMS | 16929 | Definition for error code UT in pack |
| EXCESS_TEMPERATURE_DRIVE | 17168 | Definition for error code temperature in device driver |
| BMS_PACK_TEMP_SENSOR | 20496 | Definition for error code BMS pack temp sensor |
| CANOPEN_DEVICE_SOFT | 24576 | Definition for error code device soft |
| CANOPEN_PARAMETER_ERROR | 24608 | Definition for error code canopen parameter |
| BMS_INTERNAL_ERROR | 24848 | Definition for error code BMS internal error |
| POWER_ADDITIONAL_MODULES | 28928 | Definition for error code powering additional modules |
| MOTOR_BLOCKED | 28961 | Definition for error code motor blocked |
| OSSD_STO_1 | 32769 | Definition for error code OSSD input STO signal 1 |
| OSSD_STO_2 | 32770 | Definition for error code OSSD input STO signal 2 |
| SAFE_IN_1 | 32771 | Definition for error code safe input signal 1 |
| SAFE_IN_2 | 32772 | Definition for error code safe input signal 2 |
| SAFE_OUT_1 | 32773 | Definition for error code safe output signal 1 |
| SAFE_OUT_2 | 32774 | Definition for error code safe output signal 2 |
| HALL_INCONSISTENCY | 32775 | Definition for error code hall effect sensor inconsistency |
| DRVOFF_COHERENCY | 32776 | Definition for error code driver off inconsistency |
| STO_COHERENCY | 32777 | Definition for error code STO inconsistency |
| NBRAKE | 32778 | Definition for error code nbrake |
| NBRAKE_CTRL | 32779 | Definition for error code nbrake control |
| ENDRV | 32780 | Definition for error code endrv state |
| FAULT_ALIM_EXT | 32781 | Definition for error code fault alim ext |
| EMERGENCY | 32782 | Definition for error code nsto state |
| BRAKE_PRESENCE | 32784 | Definition for error code external brake presence |
| BRAKE_OC | 32785 | Definition for error code brake oc |
| SBU_SET | 32786 | Definition for error code sbu activated |
| SBU_ACTIVATION_ERROR | 32787 | Definition for error code sbu wrong activation |
| NCCSTATE | 32788 | Definition for error code N_CC_STATE consistency diag error (SM23) |
| MCU_NBRAKE | 32789 | Definition for error code MCU_NBRAKE diag |
| BLC | 32790 | Definition for error code BRAKE_LOCK_CHECK diag |
| EXT_BRAKE_CMD | 32791 | Definition for error code external brake command error |
| NBRAKE_INT | 32792 | Definition for error code NBRAKE check in interrupt |
| DRIVER_GENERIC | 32848 | Definition for error code driver generic |
| CAN_ERROR_PASSIVE | 33056 | Definition for error code can error passive |
| CAN_RECOVER_BUS_OFF | 33088 | Definition for error code can bus off |
| PROTOCOL_ERROR_SRDO_SCT_TIMEOUT | 33281 | Definition for error code timeout receiving fresh data |
| PROTOCOL_ERROR_SRDO_SRVT_TIMEOUT | 33282 | Definition for error code timeout receiving inverted data |
| PROTOCOL_ERROR_SRDO_DATA_MISMATCH | 33283 | Definition for error code mismatching data and inverted data |
| PROTOCOL_ERROR_SRDO_WRONG_MSG | 33284 | Definition for error code srdo wrong message |
| PROTOCOL_ERROR_SRDO_WRONG_LEN | 33285 | Definition for error code srdo wrong len |
| PROTOCOL_ERROR_EVENT_TIMER | 33286 | Definition for error code event timer timeout |

# Interface commonapi.SmcService.PDS

Version: 1.0

This section is generated from the Franca IDL file for Interface PDS in package commonapi.SmcService

Interface description: 
[CIA402-2] Controlling the Power Drive System (PDS).

## Methods

### Method getPeripheralStatus

Retrieve the actual supported functions according to the PDS FSA state.

Output Parameters:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| [Struct PeripheralStatus](#struct-peripheralstatus) | peripheral_status | The supported functions. |
| Int32 | error_code |  |

### Method getPDSState

Retrieve the PDS FSA state contains into the CIA402 statusword object (6041h).

Output Parameters:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| [Enumeration PDSState](#enumeration-pdsstate) | pds_state | The PDS FSA state. |
| Int32 | error_code |  |

### Method disableVoltage

Send disable voltage command into CIA402 controlword object (6040h).

Output Parameters:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| Int32 | error_code |  |

### Method shutdown

Send shutdown command into CIA402 controlword object (6040h).

Output Parameters:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| Int32 | error_code |  |

### Method quickStop

Send quick stop command into CIA402 controlword object (6040h).

Output Parameters:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| Int32 | error_code |  |

### Method switchOn

Send switch on command into CIA402 controlword object (6040h).

Output Parameters:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| Int32 | error_code |  |

### Method enableOperation

Send enable operation command into CIA402 controlword object (6040h).

Output Parameters:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| Int32 | error_code |  |

### Method disableOperation

Send disable operation command into CIA402 controlword object (6040h).

Output Parameters:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| Int32 | error_code |  |

### Method faultReset

Send fault reset command into CIA402 controlword object (6040h).

Input Parameters:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| Boolean | status | True to set the fault reset bit else False to clear it. |

Output Parameters:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| Int32 | error_code |  |

### Method enterInOperationEnabledState

Send all the commands needed to enter into FSA operation enabled state.

Output Parameters:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| Int32 | error_code |  |

### Method getAbortConnectionOptionCode

Retrieve the abort connection option code.

Output Parameters:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| [Enumeration AbortConnectionOptionCode](#enumeration-abortconnectionoptioncode) | code | The abort connection option code. |
| Int32 | error_code |  |

### Method setAbortConnectionOptionCode

Modify the abort connection option code.

Input Parameters:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| [Enumeration AbortConnectionOptionCode](#enumeration-abortconnectionoptioncode) | code | The abort connection option code. |

Output Parameters:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| Int32 | error_code |  |

### Method getQuickStopOptionCode

Retrieve the quick stop option code.

Output Parameters:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| [Enumeration QuickStopOptionCode](#enumeration-quickstopoptioncode) | code | The quick stop option code. |
| Int32 | error_code |  |

### Method setQuickStopOptionCode

Modify the quick stop option code.

Input Parameters:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| [Enumeration QuickStopOptionCode](#enumeration-quickstopoptioncode) | code | The quick stop option code. |

Output Parameters:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| Int32 | error_code |  |

### Method getShutdownOptionCode

Retrieve the shutdown option code.

Output Parameters:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| [Enumeration ShutdownOptionCode](#enumeration-shutdownoptioncode) | code | The shutdown option code. |
| Int32 | error_code |  |

### Method setShutdownOptionCode

Modify the shutdown option code.

Input Parameters:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| [Enumeration ShutdownOptionCode](#enumeration-shutdownoptioncode) | code | The shutdown option code. |

Output Parameters:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| Int32 | error_code |  |

### Method getDisableOperationOptionCode

Retrieve the disable operation option code.

Output Parameters:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| [Enumeration DisableOperationOptionCode](#enumeration-disableoperationoptioncode) | code | The disable operation option code. |
| Int32 | error_code |  |

### Method setDisableOperationOptionCode

Modify the disable operation option code.

Input Parameters:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| [Enumeration DisableOperationOptionCode](#enumeration-disableoperationoptioncode) | code | The disable operation option code. |

Output Parameters:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| Int32 | error_code |  |

### Method getHaltOptionCode

Retrieve the halt option code.

Output Parameters:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| [Enumeration HaltOptionCode](#enumeration-haltoptioncode) | code | The halt option code. |
| Int32 | error_code |  |

### Method setHaltOptionCode

Modify the halt option code.

Input Parameters:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| [Enumeration HaltOptionCode](#enumeration-haltoptioncode) | code | The halt option code. |

Output Parameters:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| Int32 | error_code |  |

### Method getFaultReactionOptionCode

Retrieve the fault reaction option code.

Output Parameters:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| [Enumeration FaultReactionOptionCode](#enumeration-faultreactionoptioncode) | code | The fault reaction option code. |
| Int32 | error_code |  |

### Method setFaultReactionOptionCode

Modify the fault reaction option code.

Input Parameters:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| [Enumeration FaultReactionOptionCode](#enumeration-faultreactionoptioncode) | code | The fault reaction option code. |

Output Parameters:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| Int32 | error_code |  |

### Method getOperationModes

Retrieve the operation mode.

Output Parameters:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| [Enumeration OperationMode](#enumeration-operationmode) | requested | The requested operation mode. |
| [Enumeration OperationMode](#enumeration-operationmode) | actual | The actual operation mode. |
| Int32 | error_code |  |

### Method isDriveModeSupported

Retrieve the supported state of the specified drive mode.

Input Parameters:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| [Enumeration OperationMode](#enumeration-operationmode) | mode | The drive mode. |

Output Parameters:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| Boolean | supported | True if the specified drive mode is supported. |
| Int32 | error_code |  |

### Method getUnitParameters

Retrieve the unit parameters.

Output Parameters:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| [Struct UnitParameters](#struct-unitparameters) | params | The unit parameters. |
| Int32 | error_code |  |

### Method setUnitParameters

Modify the unit parameters.

Input Parameters:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| [Struct UnitParameters](#struct-unitparameters) | params | The unit parameters. |

Output Parameters:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| Int32 | error_code |  |

### Method getPolarityParameters

Retrieve the polarity factors parameters used by the SWD product.

Output Parameters:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| [Struct PolarityParameters](#struct-polarityparameters) | params | The configured polarity parameters. |
| Int32 | error_code |  |

### Method setPolarityParameters

Modify the polarity factors parameters used by the SWD product.

Input Parameters:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| [Struct PolarityParameters](#struct-polarityparameters) | params | The new polarity parameters. |

Output Parameters:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| Int32 | error_code |  |

## Structs

### Struct PeripheralStatus

Indicates the PDS supported functions.

Struct fields:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| Boolean | brake_applied | Brake applied, if present. |
| Boolean | low_level_power_applied | Low-level power applied. |
| Boolean | high_level_power_applied | High-level power applied. |
| Boolean | driver_enabled | Drive function enabled. |
| Boolean | configuration_allowed | Configuration allowed. |
| Boolean | communication_enabled | Communication enabled. |

Used in: 
[Method getPeripheralStatus](#method-getperipheralstatus)
### Struct UnitParameters

[CIA402-4] Indicates the configured SI units.

Struct fields:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| UInt32 | time_unit | Indicates the configured SI unit used for time parameters. |
| UInt32 | position_unit | Indicates the configured SI unit used for position parameters. (not used). |
| UInt32 | velocity_unit | Indicates the configured SI unit used for velocity parameters. |
| UInt32 | acceleration_unit | Indicates the configured SI unit used for acceleration and deceleration parameters. |

Used in: 
[Method getUnitParameters](#method-getunitparameters)
, 
[Method setUnitParameters](#method-setunitparameters)
### Struct PolarityParameters

Indicates the polarity factors used by the SWD product. 
NOTA : The polarity factors have no impact on the following safety functions : SDIp and SDIn.

Struct fields:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| Boolean | velocity_polarity | Indicates if the velocity demand value shall be multiplied by 1 of by –1. (False = multiply by 1 and True = multiply by –1). |
| Boolean | position_polarity | Indicates if the motor revolution increments shall be multiplied by 1 of by –1. (False = multiply by 1 and True = multiply by –1). |

Used in: 
[Method getPolarityParameters](#method-getpolarityparameters)
, 
[Method setPolarityParameters](#method-setpolarityparameters)

## Enumerations

### Enumeration PDSState

Indicates the PDS finite state automaton (FSA) state of the SWD product. 
The PDS FSA defines the application behavior of the PDS.
The PDS FSA defines the PDS status and the possible control sequence of the PDS. 
The state of the PDS also determines which commands are accepted. For example, it is only possible to start a point-to-point move when the drive is in the operation enabled state. 
NOTA :
- In the not ready to switch on state, the SWD product performs the device self-test and the self initialization and the drive function is disabled. 
- In the switch on disabled state, the communication is activated and the drive function is disabled.
- In the ready to switch on state, the SWD product is ready to switch on and the drive function is disabled.
- In the switch on state, the SWD product is ready to enter into operation enabled and the drive function is disabled.
- In the operation enabled state, the drive function is enabled.
- In the quick stop active state, the quick stop function is started.
- In the fault reaction active state, the configured fault reaction function is executed.
- In the fault state, the drive function is disabled.

|     |     |     |
| --- | --- | --- |
| Enumerator | Value | Description |
| NOT_READY_TO_SWITCH_ON | 0 | The PDS is in FSA state not ready to switch on. |
| SWITCH_ON_DISABLED | 1 | The PDS is in FSA state switch on disabled. |
| READY_TO_SWITCH_ON | 2 | The PDS is in FSA state ready to switch on. |
| SWITCHED_ON | 3 | The PDS is in FSA state switch on. |
| OPERATION_ENABLED | 4 | The PDS is in FSA state operation enabled. |
| QUICK_STOP_ACTIVE | 5 | The PDS is in FSA state quick stop active. |
| FAULT_REACTION_ACTIVE | 6 | The PDS is in FSA state fault reaction active. |
| FAULT | 7 | The PDS is in FSA state fault. |

Used in: 
[Method getPDSState](#method-getpdsstate)
### Enumeration AbortConnectionOptionCode

Indicates what action shall be performed when one of the following events occurres: 
bus-off, NMT stopped state entered, reset application, and reset communication.
NOTA : 
- Modification is not allowed in OPERATION_ENABLED, QUICK_STOP_ACTIVE and FAULT_REACTION_ACTIVE STATE.
- Changes will be applied at the next transition into OPERATION_ENABLED state. 
- Storing is possible into the non-volatile memory (APPLICATION bloc).

|     |     |     |
| --- | --- | --- |
| Enumerator | Value | Description |
| AC_OPTION_0 | 0 | No action. |
| AC_OPTION_1 | 1 | Fault signal. |
| AC_OPTION_2 | 2 | Disable voltage command. |
| AC_OPTION_3 | 3 | Quick stop command. |

Used in: 
[Method getAbortConnectionOptionCode](#method-getabortconnectionoptioncode)
, 
[Method setAbortConnectionOptionCode](#method-setabortconnectionoptioncode)
### Enumeration QuickStopOptionCode

Indicates what action is performed when the quick stop function is executed.
NOTA : 
- Modification is not allowed in OPERATION_ENABLED, QUICK_STOP_ACTIVE and FAULT_REACTION_ACTIVE STATE
- Changes will be applied at the next transition into OPERATION_ENABLED state. 
- Storing is possible into the non-volatile memory (APPLICATION bloc).

|     |     |     |
| --- | --- | --- |
| Enumerator | Value | Description |
| QS_OPTION_1 | 1 | Slow down on slow down ramp and transit into switch on disabled. |
| QS_OPTION_2 | 2 | Slow down on quick stop ramp and transit into switch on disabled. |
| QS_OPTION_5 | 5 | Slow down on slow down ramp and stay in quick stop active. |
| QS_OPTION_6 | 6 | Slow down on quick stop ramp and stay in quick stop active. |

Used in: 
[Method getQuickStopOptionCode](#method-getquickstopoptioncode)
, 
[Method setQuickStopOptionCode](#method-setquickstopoptioncode)
### Enumeration ShutdownOptionCode

Indicates what action is performed if there is a transition from operation enabled state to ready to switch on state. 
The slow down ramp is the deceleration value of the used mode of operations.
NOTA : 
- Modification is not allowed in OPERATION_ENABLED, QUICK_STOP_ACTIVE and FAULT_REACTION_ACTIVE STATE
- Changes will be applied at the next transition into OPERATION_ENABLED state. 
- Storing is possible into the non-volatile memory (APPLICATION bloc).

|     |     |     |
| --- | --- | --- |
| Enumerator | Value | Description |
| SD_OPTION_0 | 0 | Disable drive function (switch-off the drive power stage). |
| SD_OPTION_1 | 1 | Slow down with slow down ramp; disable of the drive function. |

Used in: 
[Method getShutdownOptionCode](#method-getshutdownoptioncode)
, 
[Method setShutdownOptionCode](#method-setshutdownoptioncode)
### Enumeration DisableOperationOptionCode

Indicates what action is performed if there is a transition from operation enabled state to switched on state. 
The slow down ramp is the deceleration value of the used mode of operations. 
NOTA : 
- Modification is not allowed in OPERATION_ENABLED, QUICK_STOP_ACTIVE and FAULT_REACTION_ACTIVE STATE
- Changes will be applied at the next transition into OPERATION_ENABLED state. 
- Storing is possible into the non-volatile memory (APPLICATION bloc).

|     |     |     |
| --- | --- | --- |
| Enumerator | Value | Description |
| DO_OPTION_0 | 0 | Disable drive function (switch-off the drive power stage). |
| DO_OPTION_1 | 1 | Slow down with slow down ramp; disable of the drive function. |

Used in: 
[Method getDisableOperationOptionCode](#method-getdisableoperationoptioncode)
, 
[Method setDisableOperationOptionCode](#method-setdisableoperationoptioncode)
### Enumeration HaltOptionCode

Indicates what action is performed when the halt function is executed.
The slow down ramp is the deceleration value of the used mode of operations. 
NOTA : 
- Modification is not allowed in OPERATION_ENABLED, QUICK_STOP_ACTIVE and FAULT_REACTION_ACTIVE STATE
- Changes will be applied at the next transition into OPERATION_ENABLED state. 
- Storing is possible into the non-volatile memory (APPLICATION bloc).

|     |     |     |
| --- | --- | --- |
| Enumerator | Value | Description |
| HA_OPTION_1 | 1 | Slow down on slow down ramp and stay in operation enabled. |
| HA_OPTION_2 | 2 | Slow down on quick stop ramp and stay in operation enabled. |

Used in: 
[Method getHaltOptionCode](#method-gethaltoptioncode)
, 
[Method setHaltOptionCode](#method-sethaltoptioncode)
### Enumeration FaultReactionOptionCode

Indicates what action is performed when fault is detected in the PDS. 
The slow down ramp is the deceleration value of the used mode of operations. 
NOTA : 
- Modification is not allowed in OPERATION_ENABLED, QUICK_STOP_ACTIVE and FAULT_REACTION_ACTIVE STATE
- Changes will be applied at the next transition into OPERATION_ENABLED state. 
- Storing is possible into the non-volatile memory (APPLICATION bloc).

|     |     |     |
| --- | --- | --- |
| Enumerator | Value | Description |
| FR_OPTION_0 | 0 | Disable drive function, motor is free to rotate. |
| FR_OPTION_1 | 1 | Slow down on slow down ramp. |
| FR_OPTION_2 | 2 | Slow down on quick stop ramp. |

Used in: 
[Method getFaultReactionOptionCode](#method-getfaultreactionoptioncode)
, 
[Method setFaultReactionOptionCode](#method-setfaultreactionoptioncode)
### Enumeration OperationMode

Indicates the operation mode when the SWD product is in the PDS FSA state operation enabled.
NOTA : 
- The default mode is VL and the other modes are not implemented.
- Storing is possible into the non-volatile memory (APPLICATION bloc).

|     |     |     |
| --- | --- | --- |
| Enumerator | Value | Description |
| NO_MODE | 0 | No mode change/no mode assigned. |
| PP_MODE | 1 | Profile Position mode. |
| VL_MODE | 2 | Velocity mode. |
| PV_MODE | 3 | Profile Velocity mode. |
| TQ_MODE | 4 | Torque profile mode. |
| R_MODE | 5 | Reserved. |
| HM_MODE | 6 | Homing mode. |
| IP_MODE | 7 | Interpolated position mode. |
| CSP_MODE | 8 | Cyclic Sync Position mode. |
| CSV_MODE | 9 | Cyclic Sync Velocity mode. |
| CST_MODE | 10 | Cyclic Sync Torque mode. |
| CSTCA_MODE | 11 | Cyclic Sync Torque mode with Commutation Angle. |

Used in: 
[Method getOperationModes](#method-getoperationmodes)
, 
[Method isDriveModeSupported](#method-isdrivemodesupported)

# Interface commonapi.SmcService.SafeMotion

Version: 1.0

This section is generated from the Franca IDL file for Interface SafeMotion in package commonapi.SmcService

Interface description: 
[CIA402-4] Safety motion drive. 
The activation of a security function can come from  :
- the safety inputs
- the CANopen safety control words
- a internal fault reaction
- the violation of a safety function
SCW CAN : 
- to modify the CANopen safety control words in a safety context, it will be done with CANopen SRDO objects.
- each safety control word can command up to 8 safety functions (one function by bit).
- the association of the bit with the safety function is done into the safety control word mapping. 
SSW CAN :
- each safety status words can monitor up to 8 safety functions (one function by bit).
- the association of the bit with the safety function is done into the safety status word mapping. 
SWC SAFE_IN : 
- the safety input control word can command up to 6 safety functions (one function by bit).
- the association of the bit with the safety function is done into the safety input control word mapping. 
SSW SAFE_OUT :
- the safety output status word can monitor up to 4 safety functions (one function by bit).
- the association of the bit with the safety function is done into the safety output status word mapping.

## Methods

### Method getSafetyControlWordMapping

Retrieve the safety control word mapping of the specified safety control word id.

Input Parameters:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| [Enumeration SafetyControlWordId](#enumeration-safetycontrolwordid) | safety_control_word_id | Id of the safety control word. |

Output Parameters:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| [Struct SafetyWordMapping](#struct-safetywordmapping) | safety_control_word_mapping | The safety control word mapping. |
| Int32 | error_code |  |

### Method setSafetyControlWordMapping

Modify the safety control word mapping of the specified safety control word id.

Input Parameters:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| [Enumeration SafetyControlWordId](#enumeration-safetycontrolwordid) | safety_control_word_id | Id of the safety control word. |
| [Struct SafetyWordMapping](#struct-safetywordmapping) | safety_control_word_mapping | The safety control word mapping. |

Output Parameters:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| Int32 | error_code |  |

### Method getSafetyStatusWordMapping

Retrieve the safety status word mapping of the specified safety status word id.

Input Parameters:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| [Enumeration SafetyStatusWordId](#enumeration-safetystatuswordid) | safety_status_word_id | Id of the safety status word. |

Output Parameters:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| [Struct SafetyWordMapping](#struct-safetywordmapping) | safety_status_word_mapping | The safety status word mapping. |
| Int32 | error_code |  |

### Method setSafetyStatusWordMapping

Modify the safety status word mapping of the specified safety status word id.

Input Parameters:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| [Enumeration SafetyStatusWordId](#enumeration-safetystatuswordid) | safety_status_word_id | Id of the safety status word. |
| [Struct SafetyWordMapping](#struct-safetywordmapping) | safety_status_word_mapping | The safety status word mapping. |

Output Parameters:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| Int32 | error_code |  |

### Method getSafetyFunctionCommand

Retrieve the safety function command of the specified safety function id.

Input Parameters:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| [Enumeration SafetyFunctionId](#enumeration-safetyfunctionid) | safety_function_id | Id of the safety function. |

Output Parameters:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| Boolean | status | False if the safety function command is enabled. |
| Int32 | error_code |  |

### Method getSafetyFunctionStatus

Retrieve the safety function status of the specified safety function id.

Input Parameters:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| [Enumeration SafetyFunctionId](#enumeration-safetyfunctionid) | safety_function_id | Id of the safety function. |

Output Parameters:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| Boolean | status | True if the safety function status is enabled. |
| Int32 | error_code |  |

### Method getSafetyControlWord

Retrieve the safety control word of the specified safety control word id.

Input Parameters:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| [Enumeration SafetyControlWordId](#enumeration-safetycontrolwordid) | safety_control_word_id | Id of the safety control word. |

Output Parameters:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| [Struct SafetyWordType](#struct-safetywordtype) | safety_control_word | The safety control word. |
| Int32 | error_code |  |

### Method setSafetyControlWord

Modify the safety control word of the specified safety control word id.

Input Parameters:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| [Enumeration SafetyControlWordId](#enumeration-safetycontrolwordid) | safety_control_word_id | Id of the safety control word. |
| [Struct SafetyWordType](#struct-safetywordtype) | safety_control_word | The safety control word. |

Output Parameters:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| Int32 | error_code |  |

### Method getSafetyStatusWord

Retrieve the safety status word of the specified safety status word id.

Input Parameters:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| [Enumeration SafetyStatusWordId](#enumeration-safetystatuswordid) | safety_status_word_id | Id of the safety status word. |

Output Parameters:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| [Struct SafetyWordType](#struct-safetywordtype) | safety_status_word | The safety status word. |
| Int32 | error_code |  |

### Method getSTOParameters

Retrieve the STO safety application parameters of the specified STO id.

Input Parameters:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| [Enumeration STOId](#enumeration-stoid) | id | Id of the STO. |

Output Parameters:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| [Struct STOParameters](#struct-stoparameters) | parameters | The STO safety application parameters. |
| UInt16 | signature | The STO safety application configuration signature. |
| Int32 | error_code |  |

### Method setSTOParameters

Modify the safety function STO parameters of the specified STO id.
NOTA : Modification is allowed only in NMT state Pre-operational.

Input Parameters:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| [Enumeration STOId](#enumeration-stoid) | id | Id of the STO. |
| [Struct STOParameters](#struct-stoparameters) | parameters | The STO safety application parameters. |

Output Parameters:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| Int32 | error_code |  |

### Method getSLSParameters

Retrieve the SLS safety application parameters of the specified SLS id.

Input Parameters:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| [Enumeration SLSId](#enumeration-slsid) | id | Id of the SLS. |

Output Parameters:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| [Struct SLSParameters](#struct-slsparameters) | parameters | The SLS safety application parameters. |
| UInt16 | signature | The SLS safety application configuration signature. |
| Int32 | error_code |  |

### Method setSLSParameters

Modify the safety function SLS parameters of the specified SLS id.
NOTA : Modification is allowed only in NMT state Pre-operational.

Input Parameters:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| [Enumeration SLSId](#enumeration-slsid) | id | Id of the SLS. |
| [Struct SLSParameters](#struct-slsparameters) | parameters | The SLS safety application parameters. |

Output Parameters:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| Int32 | error_code |  |

### Method getSDIParameters

Retrieve the SDI safety application parameters of the specified SDI id.

Input Parameters:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| [Enumeration SDIId](#enumeration-sdiid) | id | Id of the SDI. |

Output Parameters:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| [Struct SDIParameters](#struct-sdiparameters) | parameters | The SDI safety application parameters. |
| UInt16 | signature | The SDI safety application configuration signature. |
| Int32 | error_code |  |

### Method setSDIParameters

Modify the safety function SDI parameters of the specified SDI id.
NOTA : Modification is allowed only in NMT state Pre-operational.

Input Parameters:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| [Enumeration SDIId](#enumeration-sdiid) | id | Id of the SDI. |
| [Struct SDIParameters](#struct-sdiparameters) | parameters | The SDI safety application parameters. |

Output Parameters:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| Int32 | error_code |  |

### Method getSBCParameters

Retrieve the SBC safety application parameters of the specified SBC id.

Input Parameters:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| [Enumeration SBCId](#enumeration-sbcid) | id | Id of the SBC. |

Output Parameters:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| [Struct SBCParameters](#struct-sbcparameters) | parameters | The SBC safety application parameters. |
| UInt16 | signature | The SBC safety application configuration signature. |
| Int32 | error_code |  |

### Method getSMSParameters

Retrieve the SMS safety application parameters of the specified SMS id.

Input Parameters:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| [Enumeration SMSId](#enumeration-smsid) | id | Id of the SMS. |

Output Parameters:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| [Struct SMSParameters](#struct-smsparameters) | parameters | The SMS safety application parameters. |
| UInt16 | signature | The SMS safety application configuration signature. |
| Int32 | error_code |  |

### Method setSMSParameters

Modify the safety function SMS parameters of the specified SMS id.
NOTA : Modification is allowed only in NMT state Pre-operational.

Input Parameters:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| [Enumeration SMSId](#enumeration-smsid) | id | Id of the SMS. |
| [Struct SMSParameters](#struct-smsparameters) | parameters | The SMS safety application parameters. |

Output Parameters:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| Int32 | error_code |  |

### Method getSLSaParameters

Retrieve the SLSa safety application parameters of the specified SLSa id.

Input Parameters:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| [Enumeration SLSaId](#enumeration-slsaid) | id | Id of the SLSa. |

Output Parameters:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| [Struct SLSaParameters](#struct-slsaparameters) | parameters | The SLSa safety application parameters. |
| UInt16 | signature | The SLSa safety application configuration signature. |
| Int32 | error_code |  |

### Method setSLSaParameters

Modify the safety function SLSa parameters of the specified SLSa id.
NOTA : Modification is allowed only in NMT state Pre-operational.

Input Parameters:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| [Enumeration SLSaId](#enumeration-slsaid) | id | Id of the SLSa. |
| [Struct SLSaParameters](#struct-slsaparameters) | parameters | The SLSa safety application parameters. |

Output Parameters:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| Int32 | error_code |  |

### Method getSafetyFunctionOutput

Retrieve the consolidated safety function status of the specified safety function id.

Input Parameters:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| [Enumeration SafetyFunctionId](#enumeration-safetyfunctionid) | safety_function_id | Id of the safety function. |

Output Parameters:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| Boolean | status | True if the consolidated safety function is enabled. |
| Int32 | error_code |  |

### Method getSafetyFunctionOutputs

Retrieve all the consolidated safety function statuses.

Output Parameters:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| Array of [Struct SafetyFunctionOuputStatus](#struct-safetyfunctionouputstatus) | items | Indicates all the consolidated safety function statuses. |
| Int32 | error_code |  |

## Structs

### Struct SafetyWordMapping

Represents a safety status/control word mapping (up to 8 functions : one function by bit).

Struct fields:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| [Enumeration SafetyFunctionId](#enumeration-safetyfunctionid) | safety_function_0 | The safety function id mapped on the bit 0. |
| [Enumeration SafetyFunctionId](#enumeration-safetyfunctionid) | safety_function_1 | The safety function id mapped on the bit 1. |
| [Enumeration SafetyFunctionId](#enumeration-safetyfunctionid) | safety_function_2 | The safety function id mapped on the bit 2. |
| [Enumeration SafetyFunctionId](#enumeration-safetyfunctionid) | safety_function_3 | The safety function id mapped on the bit 3. |
| [Enumeration SafetyFunctionId](#enumeration-safetyfunctionid) | safety_function_4 | The safety function id mapped on the bit 4. |
| [Enumeration SafetyFunctionId](#enumeration-safetyfunctionid) | safety_function_5 | The safety function id mapped on the bit 5. |
| [Enumeration SafetyFunctionId](#enumeration-safetyfunctionid) | safety_function_6 | The safety function id mapped on the bit 6. |
| [Enumeration SafetyFunctionId](#enumeration-safetyfunctionid) | safety_function_7 | The safety function id mapped on the bit 7. |

Used in: 
[Method getSafetyControlWordMapping](#method-getsafetycontrolwordmapping)
, 
[Method setSafetyControlWordMapping](#method-setsafetycontrolwordmapping)
, 
[Method getSafetyStatusWordMapping](#method-getsafetystatuswordmapping)
, 
[Method setSafetyStatusWordMapping](#method-setsafetystatuswordmapping)
### Struct SafetyWordType

Represents a safety status/control word (up to 8 functions : one function by bit).

Struct fields:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| Boolean | safety_function_0 | The safety function state mapped on the bit 0. |
| Boolean | safety_function_1 | The safety function state mapped on the bit 1. |
| Boolean | safety_function_2 | The safety function state mapped on the bit 2. |
| Boolean | safety_function_3 | The safety function state mapped on the bit 3. |
| Boolean | safety_function_4 | The safety function state mapped on the bit 4. |
| Boolean | safety_function_5 | The safety function state mapped on the bit 5. |
| Boolean | safety_function_6 | The safety function state mapped on the bit 6. |
| Boolean | safety_function_7 | The safety function state mapped on the bit 7. |

Used in: 
[Method getSafetyControlWord](#method-getsafetycontrolword)
, 
[Method setSafetyControlWord](#method-setsafetycontrolword)
, 
[Method getSafetyStatusWord](#method-getsafetystatusword)
### Struct STOParameters

Represents the STO safety application parameters.

Struct fields:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| Boolean | restart_acknowledge_behavior | Indicates the configured STO restart acknowledge behavior. A value of TRUE shall Indicates that the STO restart is manual, and a value of FALSE shall Indicates that the STO restart is automatically performed. Default value : TRUE. |
| UInt32 | activate_sbc | Indicate, which command shall be performed by means of a pointer (index and sub-index) to the command parameter e.g. 6688 0100h. A value of 0000 0000h shall Indicates that no brake shall be used. Default value : 0000 0000h. |

Used in: 
[Method getSTOParameters](#method-getstoparameters)
, 
[Method setSTOParameters](#method-setstoparameters)
### Struct SLSParameters

Represents the SLS safety application parameters.

Struct fields:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| UInt16 | time_to_velocity_monitoring | Indicates the configured delay of activating the SLS function. |
| UInt32 | velocity_limit_u32 | Indicates the configured speed limit. |
| UInt16 | time_for_velocity_in_limits | Indicates the configured time for the velocity within the configured limits. |
| Boolean | sto_error_reaction | Indicates the configured SLS error reaction when the configured velocity or deceleration limits are exceeded. - False means no reaction - True means a STO reaction is required. |

Used in: 
[Method getSLSParameters](#method-getslsparameters)
, 
[Method setSLSParameters](#method-setslsparameters)
### Struct SDIParameters

Represents the SDI safety application parameters.

Struct fields:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| UInt32 | velocity_zero_window_u32 | Indicates the configured velocity within the zero-window. |

Used in: 
[Method getSDIParameters](#method-getsdiparameters)
, 
[Method setSDIParameters](#method-setsdiparameters)
### Struct SBCParameters

Represents the SBC safety application parameters.

Struct fields:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| UInt16 | brake_time_delay | Indicates the configured time to close the brake(s). |

Used in: 
[Method getSBCParameters](#method-getsbcparameters)
### Struct SMSParameters

Represents the SMS safety application parameters.

Struct fields:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| UInt32 | velocity_maximum_positive_u32 | Indicates the configured maximum velocity in positive direction. Default value : 0. |
| UInt32 | velocity_maximum_negative_u32 | Indicates the configured maximum velocity in negative direction. Default value : 0. |
| Boolean | sto_error_reaction | Indicates the configured SMS error reaction when the configured velocity limits are exceeded. - False means no reaction - True means a STO reaction is required. |

Used in: 
[Method getSMSParameters](#method-getsmsparameters)
, 
[Method setSMSParameters](#method-setsmsparameters)
### Struct SLSaParameters

Struct fields:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| UInt16 | time_to_positive_velocity_monitoring | Indicates the configured delay of activating the positive SLSa function. |
| UInt32 | positive_velocity_limit_u32 | Indicates the configured positive speed limit. |
| UInt16 | time_for_positive_velocity_in_limits | Indicates the configured time for the positve velocity within the configured limits. |
| UInt16 | time_to_negative_velocity_monitoring | Indicates the configured delay of activating the negative SLSa function. |
| UInt32 | negative_velocity_limit_u32 | Indicates the configured negative speed limit. |
| UInt16 | time_for_negative_velocity_in_limits | Indicates the configured time for the negative velocity within the configured limits. |
| Boolean | sto_error_reaction | Indicates the configured SLSa error reaction when the configured velocity limits are exceeded. - False means no reaction - True means a STO reaction is required. |

Used in: 
[Method getSLSaParameters](#method-getslsaparameters)
, 
[Method setSLSaParameters](#method-setslsaparameters)
### Struct SafetyFunctionOuputStatus

Indicates the consolidated status of a safety function.

Struct fields:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| [Enumeration SafetyFunctionId](#enumeration-safetyfunctionid) | safety_function_id | Id of the safety function. |
| Boolean | status | True if the consolidated safety function is enabled. |

Used in: 
[Method getSafetyFunctionOutputs](#method-getsafetyfunctionoutputs)

## Enumerations

### Enumeration SafetyControlWordId

Indicates the safety control word id.
NOTA : 
- Only CAN_X and PERMANENT_CAN_X safety control words are writable.
- SAFEIN_1 corresponds to the safety inputs.

|     |     |     |
| --- | --- | --- |
| Enumerator | Value | Description |
| CAN_1 | 0 | Id of the CANopen safety control word CAN 1. |
| CAN_2 | 1 | Id of the CANopen safety control word CAN 2. |
| CAN_3 | 2 | Id of the CANopen safety control word CAN 3. |
| CAN_4 | 3 | Id of the CANopen safety control word CAN 4. |
| CAN_5 | 4 | Id of the CANopen safety control word CAN 5. |
| CAN_6 | 5 | Id of the CANopen safety control word CAN 6. |
| CAN_7 | 6 | Id of the CANopen safety control word CAN 7. |
| CAN_8 | 7 | Id of the CANopen safety control word CAN 8. |
| SAFEIN_1 | 8 | Id of the SafeInputs safety control word SAFEIN 1. |
| PERMANENT_CAN_1 | 9 | Id of the Safety control word PERMANENT CAN 1. |
| PERMANENT_CAN_2 | 10 | Id of the Safety control word PERMANENT CAN 2. |

Used in: 
[Method getSafetyControlWordMapping](#method-getsafetycontrolwordmapping)
, 
[Method setSafetyControlWordMapping](#method-setsafetycontrolwordmapping)
, 
[Method getSafetyControlWord](#method-getsafetycontrolword)
, 
[Method setSafetyControlWord](#method-setsafetycontrolword)
### Enumeration SafetyStatusWordId

Indicates the safety status word id.

|     |     |     |
| --- | --- | --- |
| Enumerator | Value | Description |
| CAN_1 | 0 | Id of the CANopen safety status word CAN 1. |
| CAN_2 | 1 | Id of the CANopen safety status word CAN 2. |
| CAN_3 | 2 | Id of the CANopen safety status word CAN 3. |
| CAN_4 | 3 | Id of the CANopen safety status word CAN 4. |
| CAN_5 | 4 | Id of the CANopen safety status word CAN 5. |
| CAN_6 | 5 | Id of the CANopen safety status word CAN 6. |
| CAN_7 | 6 | Id of the CANopen safety status word CAN 7. |
| CAN_8 | 7 | Id of the CANopen safety status word CAN 8. |
| SAFEOUT | 8 | Id of the SafeOutputs safety status word SAFEOUT. |
| PERMANENT_CAN_1 | 9 | Id of the Safety status word PERMANENT CAN 1. |
| PERMANENT_CAN_2 | 10 | Id of the Safety status word PERMANENT CAN 2. |

Used in: 
[Method getSafetyStatusWordMapping](#method-getsafetystatuswordmapping)
, 
[Method setSafetyStatusWordMapping](#method-setsafetystatuswordmapping)
, 
[Method getSafetyStatusWord](#method-getsafetystatusword)
### Enumeration SafetyFunctionId

Id of the security function mappable into the safety control words.
NOTA :
- The enum shall be aligned with ezw_safety_word_fct_t enum order

|     |     |     |
| --- | --- | --- |
| Enumerator | Value | Description |
| STO | 0 | Id of the safety security function STO (Safe Torque Off). |
| SBC_1 | 1 | Id of the safety security function SBC 1 (Safe Brake Control). |
| SBC_2 | 2 | Id of the safety security function SBC 2. |
| SBC_3 | 3 | Id of the safety security function SBC 3. |
| SLS_1 | 4 | Id of the safety security function SLS 1 (Safe Limit Speed). |
| SLS_2 | 5 | Id of the safety security function SLS 2. |
| SLS_3 | 6 | Id of the safety security function SLS 3. |
| SLS_4 | 7 | Id of the safety security function SLS 4. |
| SLS_5 | 8 | Id of the safety security function SLS 5. |
| SLS_6 | 9 | Id of the safety security function SLS 6. |
| SLS_7 | 10 | Id of the safety security function SLS 7. |
| SLS_8 | 11 | Id of the safety security function SLS 8. |
| SDIP_1 | 12 | Id of the safety security function SDI Positive 1 (Safe Direction Indication). |
| SDIP_2 | 13 | Id of the safety security function SDI Positive 2. |
| SDIN_1 | 14 | Id of the safety security function SDI Negative 1. |
| SDIN_2 | 15 | Id of the safety security function SDI Negative 2. |
| ERROR_ACK | 16 | Id of the safety security function error acknowledge. |
| RST_ACK | 17 | Id of the safety security function restart acknowledge. |
| SBU | 18 | Id of the safety security function SBU (Safe Brake Unlock). |
| SMS_1 | 19 | Id of the safety security function SMS (Safe Maximum Speed). |
| SLSa_1 | 20 | Id of the safety security function SLSa 1 (Safe Limit Speed asymmetric). |
| SLSa_2 | 21 | Id of the safety security function SLSa 2. |
| SLSa_3 | 22 | Id of the safety security function SLSa 3. |
| SLSa_4 | 23 | Id of the safety security function SLSa 4. |
| SLSa_5 | 24 | Id of the safety security function SLSa 5. |
| SLSa_6 | 25 | Id of the safety security function SLSa 6. |
| SLSa_7 | 26 | Id of the safety security function SLSa 7. |
| SLSa_8 | 27 | Id of the safety security function SLSa 8. |
| NONE | -1 | Id of the safety security function NONE. |

Used in: 
[Method getSafetyFunctionCommand](#method-getsafetyfunctioncommand)
, 
[Method getSafetyFunctionStatus](#method-getsafetyfunctionstatus)
, 
[Method getSafetyFunctionOutput](#method-getsafetyfunctionoutput)
, 
[Struct SafetyWordMapping](#struct-safetywordmapping)
, 
[Struct SafetyFunctionOuputStatus](#struct-safetyfunctionouputstatus)
### Enumeration STOId

Id of the STO safety function.

|     |     |     |
| --- | --- | --- |
| Enumerator | Value | Description |
| STO_1 | 1 | Id of the safety security function STO 1. |

Used in: 
[Method getSTOParameters](#method-getstoparameters)
, 
[Method setSTOParameters](#method-setstoparameters)
### Enumeration SLSId

Id of the SLS safety function.

|     |     |     |
| --- | --- | --- |
| Enumerator | Value | Description |
| SLS_1 | 1 | Id of the safety security function SLS 1. |
| SLS_2 | 2 | Id of the safety security function SLS 2. |
| SLS_3 | 3 | Id of the safety security function SLS 3. |
| SLS_4 | 4 | Id of the safety security function SLS 4. |
| SLS_5 | 5 | Id of the safety security function SLS 5. |
| SLS_6 | 6 | Id of the safety security function SLS 6. |
| SLS_7 | 7 | Id of the safety security function SLS 7. |
| SLS_8 | 8 | Id of the safety security function SLS 8. |

Used in: 
[Method getSLSParameters](#method-getslsparameters)
, 
[Method setSLSParameters](#method-setslsparameters)
### Enumeration SDIId

Id of the SDI safety function.

|     |     |     |
| --- | --- | --- |
| Enumerator | Value | Description |
| SDI_1 | 1 | Id of the safety security function SDI 1. |
| SDI_2 | 2 | Id of the safety security function SDI 2. |

Used in: 
[Method getSDIParameters](#method-getsdiparameters)
, 
[Method setSDIParameters](#method-setsdiparameters)
### Enumeration SBCId

Id of the SBC safety function.

|     |     |     |
| --- | --- | --- |
| Enumerator | Value | Description |
| SBC_1 | 1 | Id of the safety security function SBC 1. |
| SBC_2 | 2 | Id of the safety security function SBC 2. |
| SBC_3 | 3 | Id of the safety security function SBC 3. |

Used in: 
[Method getSBCParameters](#method-getsbcparameters)
### Enumeration SMSId

Id of the SMS safety function.

|     |     |     |
| --- | --- | --- |
| Enumerator | Value | Description |
| SMS_1 | 1 | Id of the safety security function SMS 1. |

Used in: 
[Method getSMSParameters](#method-getsmsparameters)
, 
[Method setSMSParameters](#method-setsmsparameters)
### Enumeration SLSaId

Id of the SLSa safety function.

|     |     |     |
| --- | --- | --- |
| Enumerator | Value | Description |
| SLSa_1 | 1 | Id of the safety security function SLSa 1. |
| SLSa_2 | 2 | Id of the safety security function SLSa 2. |
| SLSa_3 | 3 | Id of the safety security function SLSa 3. |
| SLSa_4 | 4 | Id of the safety security function SLSa 4. |
| SLSa_5 | 5 | Id of the safety security function SLSa 5. |
| SLSa_6 | 6 | Id of the safety security function SLSa 6. |
| SLSa_7 | 7 | Id of the safety security function SLSa 7. |
| SLSa_8 | 8 | Id of the safety security function SLSa 8. |

Used in: 
[Method getSLSaParameters](#method-getslsaparameters)
, 
[Method setSLSaParameters](#method-setslsaparameters)

# Interface commonapi.SmcService.Communication

Version: 1.0

This section is generated from the Franca IDL file for Interface Communication in package commonapi.SmcService

Interface description: 
[CIA301] Communication setting.

## Methods

### Method storeParameters

Store the parameters of the specified bloc id into the non-volatile memory.

Input Parameters:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| [Enumeration BlocId](#enumeration-blocid) | bloc_id | The bloc id. |

Output Parameters:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| Int32 | error_code |  |

### Method restoreDefaultParameters

Restore the default parameters of the specified bloc id. Restoring is done by declaring the stored parameters in NVM as invalid. 
 The function does not load the default parameters. 
 The default values shall be set valid after the CANopen device is reset (NMT service reset node for sub-index from 01h to 7Fh, NMT service reset communication for sub-index 02h) or power cycled.
.

Input Parameters:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| [Enumeration BlocId](#enumeration-blocid) | bloc_id | The bloc id. |

Output Parameters:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| Int32 | error_code |  |

### Method getIdentityParameters

Retrieve the device parameters.

Output Parameters:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| [Struct IdentityParameters](#struct-identityparameters) | params | The device parameters. |
| Int32 | error_code |  |

### Method getNetworkParameters

Retrieve the network parameters.

Output Parameters:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| [Struct NetworkParameters](#struct-networkparameters) | params | The network parameters. |
| Int32 | error_code |  |

### Method setNetworkParameters

Modify the network parameters.

Input Parameters:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| [Struct NetworkParameters](#struct-networkparameters) | params | The new network parameters. |

Output Parameters:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| Int32 | error_code |  |

### Method getCommunicationParameters

Retrieve the communication parameters.

Output Parameters:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| [Struct CommunicationParameters](#struct-communicationparameters) | params | The communication parameters. |
| Int32 | error_code |  |

### Method setCommunicationParameters

Modify the communication parameters.

Input Parameters:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| [Struct CommunicationParameters](#struct-communicationparameters) | params | The communication parameters. |

Output Parameters:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| Int32 | error_code |  |

### Method getSDOCommunicationParameters

Retrieve the SDO communication parameters of the specified SDO id.

Input Parameters:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| [Enumeration SDOId](#enumeration-sdoid) | id | The SDO id. |

Output Parameters:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| [Struct SDOCommunicationParameters](#struct-sdocommunicationparameters) | params | The communication parameters. |
| Int32 | error_code |  |

### Method setSDOCommunicationParameters

Modify the SDO communication parameters of the specified SDO id.

Input Parameters:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| [Enumeration SDOId](#enumeration-sdoid) | id | The SDO id. |
| [Struct SDOCommunicationParameters](#struct-sdocommunicationparameters) | params | The new communication parameters. |

Output Parameters:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| Int32 | error_code |  |

### Method getRPDOCommunicationParameters

Retrieve the communication parameters of the specified RPDO id (PDO the CANopen device is able to receive).

Input Parameters:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| [Enumeration PDOId](#enumeration-pdoid) | id | The PDO id. |

Output Parameters:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| [Struct PDOCommunicationParameters](#struct-pdocommunicationparameters) | params | The communication parameters. |
| Int32 | error_code |  |

### Method setRPDOCommunicationParameters

Modify the communication parameters of the specified RPDO id (PDO the CANopen device is able to receive).

Input Parameters:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| [Enumeration PDOId](#enumeration-pdoid) | id | The PDO id. |
| [Struct PDOCommunicationParameters](#struct-pdocommunicationparameters) | params | The new communication parameters. |

Output Parameters:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| Int32 | error_code |  |

### Method getTPDOCommunicationParameters

Retrieve the communication parameters of the specified TPDO id (PDO the CANopen device is able to transmit).

Input Parameters:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| [Enumeration PDOId](#enumeration-pdoid) | id | The PDO id. |

Output Parameters:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| [Struct PDOCommunicationParameters](#struct-pdocommunicationparameters) | params | The communication parameters. |
| Int32 | error_code |  |

### Method setTPDOCommunicationParameters

Modify the communication parameters of the specified TPDO id (PDO the CANopen device is able to transmit).

Input Parameters:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| [Enumeration PDOId](#enumeration-pdoid) | id | The PDO id. |
| [Struct PDOCommunicationParameters](#struct-pdocommunicationparameters) | params | The new communication parameters. |

Output Parameters:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| Int32 | error_code |  |

### Method getRPDOMappingParameters

Retrieve the mapping parameters of the specified RPDO id (PDO the CANopen device is able to receive).

Input Parameters:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| [Enumeration PDOId](#enumeration-pdoid) | id | The PDO id. |

Output Parameters:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| [Struct PDOMappingParameters](#struct-pdomappingparameters) | params | The mapping parameters. |
| Int32 | error_code |  |

### Method setRPDOMappingParameters

Modify the mapping parameters of the specified RPDO id (PDO the CANopen device is able to receive).

Input Parameters:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| [Enumeration PDOId](#enumeration-pdoid) | id | The PDO id. |
| [Struct PDOMappingParameters](#struct-pdomappingparameters) | params | The new mapping parameters. |

Output Parameters:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| Int32 | error_code |  |

### Method getTPDOMappingParameters

Retrieve the mapping parameters of the specified TPDO id (PDO the CANopen device is able to transmit).

Input Parameters:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| [Enumeration PDOId](#enumeration-pdoid) | id | The PDO id. |

Output Parameters:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| [Struct PDOMappingParameters](#struct-pdomappingparameters) | params | The mapping parameters. |
| Int32 | error_code |  |

### Method setTPDOMappingParameters

Modify the Mapping parameters of the specified TPDO id (PDO the CANopen device is able to transmit).

Input Parameters:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| [Enumeration PDOId](#enumeration-pdoid) | id | The PDO id. |
| [Struct PDOMappingParameters](#struct-pdomappingparameters) | params | The new mapping parameters. |

Output Parameters:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| Int32 | error_code |  |

## Structs

### Struct IdentityParameters

Indicates the identity device parameters.

Struct fields:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| UInt32 | vendor_id | Indicates the Vendor-ID. |
| UInt32 | product_code | Indicates the product code. |
| UInt32 | revision_number | Indicates the revision number. |
| UInt32 | serial_number | Indicates the serial number. |

Used in: 
[Method getIdentityParameters](#method-getidentityparameters)
### Struct NetworkParameters

Indicates the configured network parameters.

Struct fields:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| [Enumeration BitTiming](#enumeration-bittiming) | bit_timing | The bit timing index of the device. |
| UInt8 | node_id | The node id of the device : from 1 to 127. |
| Boolean | rt_activated | True means R_termination is activated. |

Used in: 
[Method getNetworkParameters](#method-getnetworkparameters)
, 
[Method setNetworkParameters](#method-setnetworkparameters)
### Struct COBID

Represents a COB-ID. 
A COB-ID allows to specify the CAN-ID of the message on the can bus and its validity. 
NOTA : 
- SWD product allows only CAN-ID in 11 bits format.
- SWD product doesn’t allows TPDO send in RTR mode (bit 30 = 1). 
- SWD product doesn’t allows dynamic SDO connections (bit 30 = 0). 
- The bit valid (bit 31) allows selecting which TPDOs/RPDOs are used in the NMT state Operational.

Struct fields:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| UInt16 | can_id | The CAN-ID. |
| Boolean | valid | True if valid else False. |
| Boolean | flag | Represents the bit 30. SDO : False = value is assigned statically; TPDO : True = no RTR allowed on this PDO; RPDO : not used |

Used in: 
[Struct SDOCommunicationParameters](#struct-sdocommunicationparameters)
, 
[Struct PDOCommunicationParameters](#struct-pdocommunicationparameters)
### Struct CommunicationParameters

Indicates the configured communication parameters.

Struct fields:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| UInt16 | can_id_sync | Indicates the configured CAN-ID of the synchronization object (SYNC). Default : 80h. |
| UInt16 | prod_hb_time | Indicates the configured cycle time of the heartbeat in steps of 1 ms. 0h = heartbeat disabled. Default : 500ms. |

Used in: 
[Method getCommunicationParameters](#method-getcommunicationparameters)
, 
[Method setCommunicationParameters](#method-setcommunicationparameters)
### Struct SDOCommunicationParameters

Indicates the SDO server communication parameters.
NOTA : 
- The SDO server 1 communication parameters are in read only mode.
- COB-ID of the SDO reception of the SDO 1 server is $NODEID+0x600.
- COB-ID of the SDO transmission of the SDO 1 server is $NODEID+0x580. 
- Only static SDO connections are allowed (bit dyn 30 = 0). 
- Static SDO connections are configured non-temporarily and may be saved in non-volatile memory.

Struct fields:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| [Struct COBID](#struct-cobid) | cob_id_client_to_server | Indicates the configured COB-ID of the SDO reception. |
| [Struct COBID](#struct-cobid) | cob_id_server_to_client | Indicates the configured COB-ID of the SDO transmission. |

Used in: 
[Method getSDOCommunicationParameters](#method-getsdocommunicationparameters)
, 
[Method setSDOCommunicationParameters](#method-setsdocommunicationparameters)
### Struct PDOCommunicationParameters

Indicates the communication parameters of a PDO.

Struct fields:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| [Struct COBID](#struct-cobid) | cob_id | Indicates the COB-ID used by the PDO. |
| [Enumeration PDOTransmissionType](#enumeration-pdotransmissiontype) | transmission_type | Indicates the transmission type. Default : PDO_SYNC_1 in TX. |
| UInt16 | event_timer | Independent of the transmission type the RPDO event timer is used recognize the expiration in ms of the RPDO. In mode PDO_ASYNC_FF additionally an event time can be used for TPDO. If an event timer exists for a TPDO (value not equal to 0) the elapsed timer in ms is considered to be an event (not implemented). |

Used in: 
[Method getRPDOCommunicationParameters](#method-getrpdocommunicationparameters)
, 
[Method setRPDOCommunicationParameters](#method-setrpdocommunicationparameters)
, 
[Method getTPDOCommunicationParameters](#method-gettpdocommunicationparameters)
, 
[Method setTPDOCommunicationParameters](#method-settpdocommunicationparameters)
### Struct PDOMappingParameters

Indicates the mapping parameters of a PDO.

Struct fields:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| UInt8 | nb | Indicates the number of mapped application objects in PDO. |
| Array of UInt32 | items | Indicates the mapped application objects in PDO : Index SubIndex Size (0x0 to inactive). |

Used in: 
[Method getRPDOMappingParameters](#method-getrpdomappingparameters)
, 
[Method setRPDOMappingParameters](#method-setrpdomappingparameters)
, 
[Method getTPDOMappingParameters](#method-gettpdomappingparameters)
, 
[Method setTPDOMappingParameters](#method-settpdomappingparameters)

## Enumerations

### Enumeration BlocId

Indicates the parameters to store/restore into the non-volatile memory.

|     |     |     |
| --- | --- | --- |
| Enumerator | Value | Description |
| ALL | 1 | Used to store/restore all parameters. |
| COMMUNICATION | 2 | Used to store/restore communication parameters (index from 1000h to 1FFFh) and LSS parameters (index from 2100h to 2102h) |
| APPLICATION | 3 | Used to store/restore application parameters (index from 6000h to 9FFFh). |
| MANUFACTURER | 4 | Used to store/restore manufacturer parameters. |

Used in: 
[Method storeParameters](#method-storeparameters)
, 
[Method restoreDefaultParameters](#method-restoredefaultparameters)
### Enumeration BitTiming

Indicates the bit timming.

|     |     |     |
| --- | --- | --- |
| Enumerator | Value | Description |
| BT_1000 | 0 | Baud rate of 1 MBit/sec |
| BT_800 | 1 | Baud rate of 800 kBit/sec |
| BT_500 | 2 | Baud rate of 500 kBit/sec |
| BT_250 | 3 | Baud rate of 250 kBit/sec |
| BT_125 | 4 | Baud rate of 125 kBit/sec |
| BT_100 | 5 | Baud rate of 100 kBit/sec |
| BT_50 | 6 | Baud rate of 50 kBit/sec |
| BT_20 | 7 | Baud rate of 20 kBit/sec |
| BT_10 | 8 | Baud rate of 10 kBit/sec |

Used in: 
[Struct NetworkParameters](#struct-networkparameters)
### Enumeration SDOId

Indicates the SDO server id.

|     |     |     |
| --- | --- | --- |
| Enumerator | Value | Description |
| SDO_1 | 1 | Id of the SDO server 1 (default SDO server : read Only). |
| SDO_2 | 2 | Id of the SDO server 2. |
| SDO_3 | 3 | Id of the SDO server 3. |
| SDO_4 | 4 | Id of the SDO server 4. |

Used in: 
[Method getSDOCommunicationParameters](#method-getsdocommunicationparameters)
, 
[Method setSDOCommunicationParameters](#method-setsdocommunicationparameters)
### Enumeration PDOId

Indicates the PDO id.

|     |     |     |
| --- | --- | --- |
| Enumerator | Value | Description |
| PDO_1 | 1 | Id of the PDO 1. |
| PDO_2 | 2 | Id of the PDO 2. |
| PDO_3 | 3 | Id of the PDO 3. |
| PDO_4 | 4 | Id of the PDO 4. |
| PDO_5 | 5 | Id of the PDO 5. |
| PDO_6 | 6 | Id of the PDO 6. |
| PDO_7 | 7 | Id of the PDO 7. |
| PDO_8 | 8 | Id of the PDO 8. |

Used in: 
[Method getRPDOCommunicationParameters](#method-getrpdocommunicationparameters)
, 
[Method setRPDOCommunicationParameters](#method-setrpdocommunicationparameters)
, 
[Method getTPDOCommunicationParameters](#method-gettpdocommunicationparameters)
, 
[Method setTPDOCommunicationParameters](#method-settpdocommunicationparameters)
, 
[Method getRPDOMappingParameters](#method-getrpdomappingparameters)
, 
[Method setRPDOMappingParameters](#method-setrpdomappingparameters)
, 
[Method getTPDOMappingParameters](#method-gettpdomappingparameters)
, 
[Method setTPDOMappingParameters](#method-settpdomappingparameters)
### Enumeration PDOTransmissionType

Indicates the transmission type of a PDO. 
Cyclic Synchronous PDOs are transmitted with the SYNC message. The Cyclic synchronous options 1-240 can be used to divide down when the PDO is transmitted so that a value of 2 is transmitted every other SYNC message etc. 
the device still samples on the SYNC message as before so sample lag is only ever SYNC interval behind, but the update rate can be divided down.
With Acyclic synchronous these only transmit when a Remote request from another device ‘pre-triggers’ the PDO or A device (profile) specific event ‘pre-triggers’ the PDO.

|     |     |     |
| --- | --- | --- |
| Enumerator | Value | Description |
| PDO_SYNC_1 | 1 |  |
| PDO_SYNC_2 | 2 |  |
| PDO_SYNC_3 | 3 |  |
| PDO_SYNC_4 | 4 |  |
| PDO_SYNC_5 | 5 |  |
| PDO_SYNC_6 | 6 |  |
| PDO_SYNC_7 | 7 |  |
| PDO_SYNC_8 | 8 |  |
| PDO_SYNC_9 | 9 |  |
| PDO_SYNC_10 | 10 |  |
| PDO_SYNC_11 | 11 |  |
| PDO_SYNC_12 | 12 |  |
| PDO_SYNC_13 | 13 |  |
| PDO_SYNC_14 | 14 |  |
| PDO_SYNC_15 | 15 |  |
| PDO_SYNC_16 | 16 |  |
| PDO_SYNC_17 | 17 |  |
| PDO_SYNC_18 | 18 |  |
| PDO_SYNC_19 | 19 |  |
| PDO_SYNC_20 | 20 |  |
| PDO_SYNC_21 | 21 |  |
| PDO_SYNC_22 | 22 |  |
| PDO_SYNC_23 | 23 |  |
| PDO_SYNC_24 | 24 |  |
| PDO_SYNC_25 | 25 |  |
| PDO_SYNC_26 | 26 |  |
| PDO_SYNC_27 | 27 |  |
| PDO_SYNC_28 | 28 |  |
| PDO_SYNC_29 | 29 |  |
| PDO_SYNC_30 | 30 |  |
| PDO_SYNC_31 | 31 |  |
| PDO_SYNC_32 | 32 |  |
| PDO_SYNC_33 | 33 |  |
| PDO_SYNC_34 | 34 |  |
| PDO_SYNC_35 | 35 |  |
| PDO_SYNC_36 | 36 |  |
| PDO_SYNC_37 | 37 |  |
| PDO_SYNC_38 | 38 |  |
| PDO_SYNC_39 | 39 |  |
| PDO_SYNC_40 | 40 |  |
| PDO_SYNC_41 | 41 |  |
| PDO_SYNC_42 | 42 |  |
| PDO_SYNC_43 | 43 |  |
| PDO_SYNC_44 | 44 |  |
| PDO_SYNC_45 | 45 |  |
| PDO_SYNC_46 | 46 |  |
| PDO_SYNC_47 | 47 |  |
| PDO_SYNC_48 | 48 |  |
| PDO_SYNC_49 | 49 |  |
| PDO_SYNC_50 | 50 |  |
| PDO_SYNC_51 | 51 |  |
| PDO_SYNC_52 | 52 |  |
| PDO_SYNC_53 | 53 |  |
| PDO_SYNC_54 | 54 |  |
| PDO_SYNC_55 | 55 |  |
| PDO_SYNC_56 | 56 |  |
| PDO_SYNC_57 | 57 |  |
| PDO_SYNC_58 | 58 |  |
| PDO_SYNC_59 | 59 |  |
| PDO_SYNC_60 | 60 |  |
| PDO_SYNC_61 | 61 |  |
| PDO_SYNC_62 | 62 |  |
| PDO_SYNC_63 | 63 |  |
| PDO_SYNC_64 | 64 |  |
| PDO_SYNC_65 | 65 |  |
| PDO_SYNC_66 | 66 |  |
| PDO_SYNC_67 | 67 |  |
| PDO_SYNC_68 | 68 |  |
| PDO_SYNC_69 | 69 |  |
| PDO_SYNC_70 | 70 |  |
| PDO_SYNC_71 | 71 |  |
| PDO_SYNC_72 | 72 |  |
| PDO_SYNC_73 | 73 |  |
| PDO_SYNC_74 | 74 |  |
| PDO_SYNC_75 | 75 |  |
| PDO_SYNC_76 | 76 |  |
| PDO_SYNC_77 | 77 |  |
| PDO_SYNC_78 | 78 |  |
| PDO_SYNC_79 | 79 |  |
| PDO_SYNC_80 | 80 |  |
| PDO_SYNC_81 | 81 |  |
| PDO_SYNC_82 | 82 |  |
| PDO_SYNC_83 | 83 |  |
| PDO_SYNC_84 | 84 |  |
| PDO_SYNC_85 | 85 |  |
| PDO_SYNC_86 | 86 |  |
| PDO_SYNC_87 | 87 |  |
| PDO_SYNC_88 | 88 |  |
| PDO_SYNC_89 | 89 |  |
| PDO_SYNC_90 | 90 |  |
| PDO_SYNC_91 | 91 |  |
| PDO_SYNC_92 | 92 |  |
| PDO_SYNC_93 | 93 |  |
| PDO_SYNC_94 | 94 |  |
| PDO_SYNC_95 | 95 |  |
| PDO_SYNC_96 | 96 |  |
| PDO_SYNC_97 | 97 |  |
| PDO_SYNC_98 | 98 |  |
| PDO_SYNC_99 | 99 |  |
| PDO_SYNC_100 | 100 |  |
| PDO_SYNC_101 | 101 |  |
| PDO_SYNC_102 | 102 |  |
| PDO_SYNC_103 | 103 |  |
| PDO_SYNC_104 | 104 |  |
| PDO_SYNC_105 | 105 |  |
| PDO_SYNC_106 | 106 |  |
| PDO_SYNC_107 | 107 |  |
| PDO_SYNC_108 | 108 |  |
| PDO_SYNC_109 | 109 |  |
| PDO_SYNC_110 | 110 |  |
| PDO_SYNC_111 | 111 |  |
| PDO_SYNC_112 | 112 |  |
| PDO_SYNC_113 | 113 |  |
| PDO_SYNC_114 | 114 |  |
| PDO_SYNC_115 | 115 |  |
| PDO_SYNC_116 | 116 |  |
| PDO_SYNC_117 | 117 |  |
| PDO_SYNC_118 | 118 |  |
| PDO_SYNC_119 | 119 |  |
| PDO_SYNC_120 | 120 |  |
| PDO_SYNC_121 | 121 |  |
| PDO_SYNC_122 | 122 |  |
| PDO_SYNC_123 | 123 |  |
| PDO_SYNC_124 | 124 |  |
| PDO_SYNC_125 | 125 |  |
| PDO_SYNC_126 | 126 |  |
| PDO_SYNC_127 | 127 |  |
| PDO_SYNC_128 | 128 |  |
| PDO_SYNC_129 | 129 |  |
| PDO_SYNC_130 | 130 |  |
| PDO_SYNC_131 | 131 |  |
| PDO_SYNC_132 | 132 |  |
| PDO_SYNC_133 | 133 |  |
| PDO_SYNC_134 | 134 |  |
| PDO_SYNC_135 | 135 |  |
| PDO_SYNC_136 | 136 |  |
| PDO_SYNC_137 | 137 |  |
| PDO_SYNC_138 | 138 |  |
| PDO_SYNC_139 | 139 |  |
| PDO_SYNC_140 | 140 |  |
| PDO_SYNC_141 | 141 |  |
| PDO_SYNC_142 | 142 |  |
| PDO_SYNC_143 | 143 |  |
| PDO_SYNC_144 | 144 |  |
| PDO_SYNC_145 | 145 |  |
| PDO_SYNC_146 | 146 |  |
| PDO_SYNC_147 | 147 |  |
| PDO_SYNC_148 | 148 |  |
| PDO_SYNC_149 | 149 |  |
| PDO_SYNC_150 | 150 |  |
| PDO_SYNC_151 | 151 |  |
| PDO_SYNC_152 | 152 |  |
| PDO_SYNC_153 | 153 |  |
| PDO_SYNC_154 | 154 |  |
| PDO_SYNC_155 | 155 |  |
| PDO_SYNC_156 | 156 |  |
| PDO_SYNC_157 | 157 |  |
| PDO_SYNC_158 | 158 |  |
| PDO_SYNC_159 | 159 |  |
| PDO_SYNC_160 | 160 |  |
| PDO_SYNC_161 | 161 |  |
| PDO_SYNC_162 | 162 |  |
| PDO_SYNC_163 | 163 |  |
| PDO_SYNC_164 | 164 |  |
| PDO_SYNC_165 | 165 |  |
| PDO_SYNC_166 | 166 |  |
| PDO_SYNC_167 | 167 |  |
| PDO_SYNC_168 | 168 |  |
| PDO_SYNC_169 | 169 |  |
| PDO_SYNC_170 | 170 |  |
| PDO_SYNC_171 | 171 |  |
| PDO_SYNC_172 | 172 |  |
| PDO_SYNC_173 | 173 |  |
| PDO_SYNC_174 | 174 |  |
| PDO_SYNC_175 | 175 |  |
| PDO_SYNC_176 | 176 |  |
| PDO_SYNC_177 | 177 |  |
| PDO_SYNC_178 | 178 |  |
| PDO_SYNC_179 | 179 |  |
| PDO_SYNC_180 | 180 |  |
| PDO_SYNC_181 | 181 |  |
| PDO_SYNC_182 | 182 |  |
| PDO_SYNC_183 | 183 |  |
| PDO_SYNC_184 | 184 |  |
| PDO_SYNC_185 | 185 |  |
| PDO_SYNC_186 | 186 |  |
| PDO_SYNC_187 | 187 |  |
| PDO_SYNC_188 | 188 |  |
| PDO_SYNC_189 | 189 |  |
| PDO_SYNC_190 | 190 |  |
| PDO_SYNC_191 | 191 |  |
| PDO_SYNC_192 | 192 |  |
| PDO_SYNC_193 | 193 |  |
| PDO_SYNC_194 | 194 |  |
| PDO_SYNC_195 | 195 |  |
| PDO_SYNC_196 | 196 |  |
| PDO_SYNC_197 | 197 |  |
| PDO_SYNC_198 | 198 |  |
| PDO_SYNC_199 | 199 |  |
| PDO_SYNC_200 | 200 |  |
| PDO_SYNC_201 | 201 |  |
| PDO_SYNC_202 | 202 |  |
| PDO_SYNC_203 | 203 |  |
| PDO_SYNC_204 | 204 |  |
| PDO_SYNC_205 | 205 |  |
| PDO_SYNC_206 | 206 |  |
| PDO_SYNC_207 | 207 |  |
| PDO_SYNC_208 | 208 |  |
| PDO_SYNC_209 | 209 |  |
| PDO_SYNC_210 | 210 |  |
| PDO_SYNC_211 | 211 |  |
| PDO_SYNC_212 | 212 |  |
| PDO_SYNC_213 | 213 |  |
| PDO_SYNC_214 | 214 |  |
| PDO_SYNC_215 | 215 |  |
| PDO_SYNC_216 | 216 |  |
| PDO_SYNC_217 | 217 |  |
| PDO_SYNC_218 | 218 |  |
| PDO_SYNC_219 | 219 |  |
| PDO_SYNC_220 | 220 |  |
| PDO_SYNC_221 | 221 |  |
| PDO_SYNC_222 | 222 |  |
| PDO_SYNC_223 | 223 |  |
| PDO_SYNC_224 | 224 |  |
| PDO_SYNC_225 | 225 |  |
| PDO_SYNC_226 | 226 |  |
| PDO_SYNC_227 | 227 |  |
| PDO_SYNC_228 | 228 |  |
| PDO_SYNC_229 | 229 |  |
| PDO_SYNC_230 | 230 |  |
| PDO_SYNC_231 | 231 |  |
| PDO_SYNC_232 | 232 |  |
| PDO_SYNC_233 | 233 |  |
| PDO_SYNC_234 | 234 |  |
| PDO_SYNC_235 | 235 |  |
| PDO_SYNC_236 | 236 |  |
| PDO_SYNC_237 | 237 |  |
| PDO_SYNC_238 | 238 |  |
| PDO_SYNC_239 | 239 |  |
| PDO_SYNC_240 | 240 |  |
| PDO_ASYNC_FF | 255 | Asynchronous: The data become valid when the PDO message is received and are taken over into the object dictionary. |

Used in: 
[Struct PDOCommunicationParameters](#struct-pdocommunicationparameters)

# Interface commonapi.SmcService.Manufacturer

Version: 1.0

This section is generated from the Franca IDL file for Interface Manufacturer in package commonapi.SmcService

Interface description: 
Manufacturer services.

## Methods

### Method getDeviceParameters

Retrieve the device parameters.

Output Parameters:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| [Struct DeviceParameters](#struct-deviceparameters) | params | The device parameters. |
| Int32 | error_code |  |

### Method getSWDParameters

Retrieve the SWD product parameters.

Output Parameters:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| [Struct SWDParameters](#struct-swdparameters) | params | The SWD product parameters. |
| Int32 | error_code |  |

### Method setSWDParameters

Modify the SWD product parameters. 
NOTA : 
- Changes will be applied at the next transition into OPERATION_ENABLED state. 
- Storing is possible into the non-volatile memory (MANUFACTURER bloc).

Input Parameters:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| [Struct SWDParameters](#struct-swdparameters) | params | The new SWD product parameters. |

Output Parameters:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| Int32 | error_code |  |

### Method getCalibrationValidity

Retrieve the validity of the calibration in non volatile memory.

Output Parameters:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| Boolean | isValid | The calibration validity. |
| Int32 | error_code |  |

### Method getSystemErrorState

Retrieve the system error states.

Output Parameters:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| [Enumeration SystemErrorStatus](#enumeration-systemerrorstatus) | battery_uv | Indicates the state of a battery under voltage. |
| [Enumeration SystemErrorStatus](#enumeration-systemerrorstatus) | battery_ov | Indicates the state of a battery over voltage. |
| [Enumeration SystemErrorStatus](#enumeration-systemerrorstatus) | phase_oc | Indicates the state of a phase over current. |
| [Enumeration SystemErrorStatus](#enumeration-systemerrorstatus) | mos_ot | Indicates the state of a MOS over temperature. |
| [Enumeration SystemErrorStatus](#enumeration-systemerrorstatus) | drv_ot | Indicates the state of a driver over temperature. |
| Int32 | error_code |  |

### Method getSystemErrorProtectState

Retrieve the system error protection state.

Output Parameters:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| [Enumeration SystemErrorProtectState](#enumeration-systemerrorprotectstate) | prev_state | The previous system error protect state. |
| [Enumeration SystemErrorProtectState](#enumeration-systemerrorprotectstate) | current_state | The actual system error protect state. |
| Int32 | error_code |  |

### Method getSWVersion

Retrieve the SWD product software version. Ex : 1.0.1

Output Parameters:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| String | sw_version | The software version. |
| Int32 | error_code |  |

### Method getSWId

Retrieve the SWD product software id. Ex : 2 
NOTA 
[
    FW_UNKNOWN = 0U
    FW_SWD_RECOVERY =1U
    FW_SWD_CORE = 2U
    FW_SWD_150 = 3U
    ...
    Maintenance = 255U
]

Output Parameters:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| UInt8 | sw_id | The software id. |
| Int32 | error_code |  |

### Method getSWRef

Retrieve the SWD product software reference. Ex : FW_SWD_CORE

Output Parameters:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| String | software_ref | The software reference. |
| Int32 | error_code |  |

### Method getHWVersion

Retrieve the SWD product hardware version. Ex : 5
NOTA 
[
    0 = Hardware version init
    1 = A
    2 = B
    3 = C
    4 = D
    5 = E
    6 = F
    7 = G
    8 = H
    9 = I
    10 = J
    ...
]

Output Parameters:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| UInt32 | hw_version | The hardware version. |
| Int32 | error_code |  |

### Method getHWId

Retrieve the SWD product hardware id. Ex : 777 
NOTA 
[
    727 = SWD150
    777 = SWDCore or SWD125
    ...
]

Output Parameters:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| UInt32 | hw_id | The hardware id. |
| Int32 | error_code |  |

### Method getProductId

Retrieve the SWD product id. Ex : 15
NOTA 
[
    NO_PRODUCT_REF = 0U
    ezSWD125IM.14/C = 1U
    ezSWD125IM.14B/C = 2U
    ezSWD125IM.25/C = 3U
    ezSWD125IM.25B/C = 4U
    ezSWD125IM.4/C = 5U
    ezSWD125IM.4B/C = 6U
    ...
    ezSWD150IH.14/C-0 = 7U
    ezSWD150IH.14/C-1 = 8U
    ezSWD150IH.14B/C-0 = 9U
    ezSWD150IH.14B/C-1 = 10U
    ezSWD150IH.25/C-0 = 11U
    ezSWD150IH.25/C-1 = 12U
    ezSWD150IH.25B/C-0 = 13U
    ezSWD150IH.25B/C-1 = 14U
    ...
    ezSWDcore.14/C = 15U
    ezSWDcore.14B/C = 16U
    ezSWDcore.25/C = 17U
    ezSWDcore.25B/C = 18U
    ezSWDcore.4/C = 19U
    ezSWDcore.4B/C = 20U
    ezSWDcore.0/C = 21U
    ...
]

Output Parameters:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| UInt32 | product_id | The product id. |
| Int32 | error_code |  |

### Method getProductRef

Retrieve the SWD product reference. Ex : ezSWD125IM.14/C

Output Parameters:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| String | product_ref | The product reference. |
| Int32 | error_code |  |

### Method getOdometryValue

Retrieve the position distance of the SWD product in mm.
FORMULA : position_value / NbStepRevolutionElec / NbPolePair / Reduction x Diameter x M_PI
NOTA : The previous parameters are defined into the configuration file. 
NOTA : The counter direction depends of the position polarity parameter.
NOTA : The format of the configuration file is JSON
       ie. Nidec motor :
        "nbStepRevolutionElec": 6,
        "nbPolePair": 5,
        "reduction": 14.0,
        "diameter": 125.0

Output Parameters:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| Int32 | odometry_value | The position distance of the SWD Core in mm. |
| Int32 | error_code |  |

### Method getOdometryValueTS

Retrieve the position distance of the SWD product in mm.
FORMULA : position_value / NbStepRevolutionElec / NbPolePair / Reduction x Diameter x M_PI
NOTA : The previous parameters are defined into the configuration file. 
NOTA : The counter direction depends of the position polarity parameter.
NOTA : The format of the configuration file is JSON
       ie. Nidec motor :
        "nbStepRevolutionElec": 6,
        "nbPolePair": 5,
        "reduction": 14.0,
        "diameter": 125.0

Output Parameters:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| Int32 | odometry_value | The position distance of the SWD product in mm. |
| UInt64 | timestamp | The timestamp in microseconds (Unix epoch time from 1 January 1970). |
| Int32 | error_code |  |

### Method getAccurateOdometryValue

Retrieve a more precise position distance of the SWD product in mm at low level speed. (Warning : This position is non-safe. Safety relevant applications should rely with getOdometryValue()).
FORMULA : accurate_position_value / Reduction x Diameter x M_PI
NOTA : The previous parameters are defined into the configuration file. 
NOTA : The counter direction depends of the position polarity parameter.
NOTA : The format of the configuration file is JSON
       ie. Nidec motor :
        "reduction": 14.0,
        "diameter": 125.0

Output Parameters:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| Int32 | accurate_odometry_value | The accurate position distance of the SWD product in mm. |
| Int32 | error_code |  |

### Method getAccurateOdometryValueTS

Retrieve a more precise position distance of the SWD product in mm at low level speed. (Warning : This position is non-safe. Safety relevant applications should rely with getOdometryValue()).
FORMULA : accurate_position_value / Reduction x Diameter x M_PI
NOTA : The previous parameters are defined into the configuration file.
NOTA : The counter direction depends of the position polarity parameter.
NOTA : The format of the configuration file is JSON
       ie. Nidec motor :
        "reduction": 14.0,
        "diameter": 125.0

Output Parameters:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| Int32 | accurate_odometry_value | The accurate position distance of the SWD product in mm. |
| UInt64 | timestamp | The timestamp in microseconds (Unix epoch time from 1 January 1970). |
| Int32 | error_code |  |

### Method getAccuratePositionValue

Retrieve the precise multiturn position value, in units of motor mechanical degrees.
NOTA : The counter direction depends of the position polarity parameter.
NOTA : This position is non-safe and is for information only. Safety relevant applications should rely on safe object "0x6064: position_value".

Output Parameters:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| Int32 | accurate_position_value | The precise multiturn position value, in units of motor mechanical degrees. |
| Int32 | error_code |  |

### Method getAccuratePositionValueTS

Retrieve the precise multiturn position value, in units of motor mechanical degrees.
NOTA : The counter direction depends of the position polarity parameter.
NOTA : This position is non-safe and is for information only. Safety relevant applications should rely on safe object "0x6064: position_value".

Output Parameters:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| Int32 | accurate_position_value | The precise multiturn position value, in units of motor mechanical degrees. |
| UInt64 | timestamp | The timestamp in ms from 1970. |
| Int32 | error_code |  |

### Method getOutputControl

Retrieve the control value for an OutputSource
NOTA : Value of 1 means OutputSource is active
NOTA : Value of 0 means OutputSource is inactive 
NOTA : Value of control can be saved in EEPROM ( MANUFACTURER data )
NOTA : Value of control is applied immediately

Input Parameters:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| [Enumeration OutputSource](#enumeration-outputsource) | output_source | which OutputSource control you want to get. |

Output Parameters:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| Boolean | control | control for the OutputSource : 1 OutputSource is active, 0 OutputSource is inactive |
| Int32 | error_code |  |

### Method setOutputControl

Set the control value for an OutputSource
NOTA : Value of 1 means OutputSource is active
NOTA : Value of 0 means OutputSource is inactive 
NOTA : Value of control can be saved in EEPROM ( MANUFACTURER data )
NOTA : Value of control is applied immediately

Input Parameters:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| [Enumeration OutputSource](#enumeration-outputsource) | output_source | which OutputSource control you want to set. |
| Boolean | control | control for the OutputSource : 1 OutputSource is active, 0 OutputSource is inactive |

Output Parameters:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| Int32 | error_code |  |

### Method getOutputStatus

Retrieve the status of an OutputSource
NOTA : Value of 1 means OutputSource is active
NOTA : Value of 0 means OutputSource is inactive

Input Parameters:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| [Enumeration OutputSource](#enumeration-outputsource) | output_source | which OutputSource status you want to get. |

Output Parameters:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| Boolean | status | The status of OutputSource. |
| Int32 | error_code |  |

### Method setExternalBrakePresence

Modify the external brake presence flag. 
NOTA : Value of 1 means external brake is configured to be present.
NOTA : Value of 0 means external brake is configured to be not present.

Input Parameters:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| Boolean | externalBrakePresence | The external brake presence flag. |

Output Parameters:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| Int32 | error_code |  |

### Method getExternalBrakePresence

Retrieve the external brake presence flag.
NOTA : Value of 1 means external brake is configured to be present.
NOTA : Value of 0 means external brake is configured to be not present.

Output Parameters:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| Boolean | externalBrakePresence | The external brake presence flag. |
| Int32 | error_code |  |

## Structs

### Struct DeviceParameters

Indicates the manufacturer device parameters.

Struct fields:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| String | manufacturer_device_name | The device name. |
| String | hardware_version_description | The hardware version description. |
| String | manufacturer_software_version | The software version description. |

Used in: 
[Method getDeviceParameters](#method-getdeviceparameters)
### Struct SWDParameters

Indicates the configured SWD product parameters.

Struct fields:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| UInt32 | motctrl_speed_pid_p | The proportional parameter (mdeg.s-1) of the speed motor control bloc. Default : 200. |
| UInt32 | motctrl_speed_pid_i | The integral parameter (mdeg.s-1) of the speed motor control bloc. Default : 10. |
| UInt32 | motctrl_speed_pid_d | The derivative parameter (mdeg.s-1) of the speed motor control bloc. Default : 0. |
| UInt32 | motctrl_speed_pid_tw | The integral anti-windup time constant parameter (ms) of the speed motor control bloc. Default : 316. |
| UInt32 | motctrl_speed_pid_tn | The derivative filter time constant parameter (ms) of the speed motor control bloc. Default : 300. |

Used in: 
[Method getSWDParameters](#method-getswdparameters)
, 
[Method setSWDParameters](#method-setswdparameters)

## Enumerations

### Enumeration SystemErrorStatus

Indicates the state of a system error.

|     |     |     |
| --- | --- | --- |
| Enumerator | Value | Description |
| EZW_SAFETY_CHECK_NORMAL | 0 |  |
| EZW_SAFETY_CHECK_WARNING | 1 |  |
| EZW_SAFETY_CHECK_ERROR | 2 |  |

Used in: 
[Method getSystemErrorState](#method-getsystemerrorstate)
### Enumeration SystemErrorProtectState

Indicates the state of a system error protection.

|     |     |     |
| --- | --- | --- |
| Enumerator | Value | Description |
| EZW_PROTECT_NONE | 0 | No error. |
| EZW_PROTECT_ZERO_TORQUE_PROTECT | 1 | This protection reduces to null the current inside the motor. |
| EZW_PROTECT_BRAKE_CC_PROTECT | 2 | This protection try to suppress the curent inside the motor by a short-circuit of the motor phase with the brake CC . |
| EZW_PROTECT_APPLY_SBC_CONFIG | 3 | This protection stop the drive with the SBC. |

Used in: 
[Method getSystemErrorProtectState](#method-getsystemerrorprotectstate)
### Enumeration OutputSource

Output source.

|     |     |     |
| --- | --- | --- |
| Enumerator | Value | Description |
| CAN_ALIM | 0 | CAN alimentation. |
| CAN_IO_ALIM | 1 | CAN IO alimentation. |

Used in: 
[Method getOutputControl](#method-getoutputcontrol)
, 
[Method setOutputControl](#method-setoutputcontrol)
, 
[Method getOutputStatus](#method-getoutputstatus)

# Interface commonapi.SmcService.VelocityMode

Version: 1.0

This section is generated from the Franca IDL file for Interface VelocityMode in package commonapi.SmcService

Interface description: 
[CIA402-2] The velocity mode controls the speed (velocity) of the SWD product but not its position.
The selection of a new target velocity use a acceleration / deceleration ramp. 
The velocity mode is composed of three main functions:
- velocity limit function
- ramp function
- velocity control function
and is composed of the following factor functions:
- factor function
- reverse factor function.

## Methods

### Method setTargetVelocity

Indicate the required velocity of the system. It will be multiplied by the vl dimension factor and the vl set-point factor. 
The value shall be given in user-defined velocity units or in revolutions per minute (r/min), if the vl dimension factor and the vl set-point factor are not implemented or have the value 1. 
Positive values shall indicate forward direction and negative values shall indicate reverse direction.

Input Parameters:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| Int16 | target_velocity | The required velocity (range : -2000 to 2000 r/min). |

Output Parameters:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| Int32 | error_code |  |

### Method getTargetVelocity

Retrieve the actual required velocity of the system.

Output Parameters:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| Int16 | target_velocity | The actual required velocity of the system. |
| Int32 | error_code |  |

### Method getVelocityActualValue

Retrieve the actual velocity of the system. The value shall be given in the very same unit as the vl target velocity.         
Positive values shall indicate forward direction and negative values shall indicate reverse direction.

Output Parameters:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| Int32 | velocity_actual_value | The actual velocity of the system. |
| Int32 | error_code |  |

### Method getVelocityActualValueTS

Retrieve the actual velocity of the system. The value shall be given in the very same unit as the vl target velocity.         
Positive values shall indicate forward direction and negative values shall indicate reverse direction.

Output Parameters:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| Int32 | velocity_actual_value | The actual velocity of the system. |
| UInt64 | timestamp | The timestamp in ms from 1970. |
| Int32 | error_code |  |

### Method getVelocityDemand

Retrieve the instantaneous velocity generated by the ramp function. The value shall be given in the very same unit as the vl target velocity. 
Positive values shall indicate forward direction and negative values shall indicate reverse direction.
NOTA : The velocity demand depends of the velocity polarity parameter.

Output Parameters:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| Int16 | velocity_demand | The instantaneous velocity generated by the ramp function. |
| Int32 | error_code |  |

### Method getPositionValue

Retrieve the position of the SWD product in motor revolution increments. The SWD product resolution is 30 increments par revolution.        
NOTA : The counter direction depends of the position polarity parameter.

Output Parameters:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| Int32 | position_value | The position of the SWD product in motor revolution increments. |
| Int32 | error_code |  |

### Method getPositionValueTS

Retrieve the position of the SWD product in motor revolution increments. The SWD product resolution is 30 increments par revolution.        
NOTA : The counter direction depends of the position polarity parameter.

Output Parameters:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| Int32 | position_value | The position of the SWD product in motor revolution increments. |
| UInt64 | timestamp | The timestamp in ms from 1970. |
| Int32 | error_code |  |

### Method getVelocityModeParameters

Retrieve the velocity mode parameters.

Output Parameters:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| [Struct VelocityModeParameters](#struct-velocitymodeparameters) | params | The velocity mode parameters. |
| Int32 | error_code |  |

### Method setVelocityModeParameters

Modify the velocity mode parameters.

Input Parameters:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| [Struct VelocityModeParameters](#struct-velocitymodeparameters) | params | The new velocity mode parameters. |

Output Parameters:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| Int32 | error_code |  |

### Method getVelocityModeStatusword

Retrieve the velocity mode statusword.

Output Parameters:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| [Struct VelocityModeStatusword](#struct-velocitymodestatusword) | params | The velocity mode statusword. |
| Int32 | error_code |  |

### Method getVelocityModeControlword

Retrieve the velocity mode controlword.

Output Parameters:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| [Struct VelocityModeControlword](#struct-velocitymodecontrolword) | params | The velocity mode controlword. |
| Int32 | error_code |  |

### Method setEnableRamp

Modify the enable ramp flag into the velocity mode controlword.

Input Parameters:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| Boolean | enable_ramp | If False, the velocity demand value shall be controlled in any other (manufacturer-specific) way, for example by a test function generator or manufacturer-specific halt function; else, the velocity demand value shall accord with ramp output value. |

Output Parameters:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| Int32 | error_code |  |

### Method setUnlockRamp

Modify the unlock ramp flag into the velocity mode controlword.

Input Parameters:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| Boolean | unlock_ramp | If False, the ramp output value shall be locked to current output value; else the ramp output value shall follow ramp input value. |

Output Parameters:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| Int32 | error_code |  |

### Method setReferenceRamp

Modify the reference ramp flag into the velocity mode controlword.

Input Parameters:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| Boolean | reference_ramp | If False, the ramp input value shall be set to zero; else the ramp input value shall accord with ramp reference. |

Output Parameters:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| Int32 | error_code |  |

### Method setHalt

Modify the halt flag into the velocity mode controlword.

Input Parameters:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| Boolean | halt | If True, the motor shall be stopped. |

Output Parameters:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| Int32 | error_code |  |

## Structs

### Struct VelocityModeParameters

[CIA402-2] Velocity mode parameters. 
The velocity mode use some parameters to control the velocity control function.

Struct fields:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| UInt32 | vl_velocity_min_amount | The configured minimum amount of velocity. The value shall be given in rotations per minute (r/min) or in user-defined velocity units. Default : 40 r/min |
| UInt32 | vl_velocity_max_amount | The configured maximum amount of velocity. The values shall be given in rotations per minute (r/min) or in user-defined velocity units. Default : 2000 r/min |
| UInt32 | vl_velocity_acceleration_delta_speed | The configured delta speed of the slope of the acceleration ramp. The values shall be given in rotations per minute (r/min) or in user-defined velocity units. Default : 500 r/min. |
| UInt16 | vl_velocity_acceleration_delta_time | The configured delta time of the slope of the acceleration ramp. The values shall be given in second or in user-defined time units. Default : 1s. |
| UInt32 | vl_velocity_deceleration_delta_speed | The configured delta speed of the slope of the deceleration ramp. The values shall be given in rotations per minute (r/min) or in user-defined velocity units. Default : 500 r/min. |
| UInt16 | vl_velocity_deceleration_delta_time | The configured delta time of the slope of the deceleration ramp. The values shall be given in second or in user-defined time units. Default : 1s. |
| UInt32 | vl_velocity_quick_stop_delta_speed | The configured delta speed of the slope of the deceleration ramp for quick stop. The values shall be given in rotations per minute (r/min) or in user-defined velocity units. Default : 1000 r/min. |
| UInt16 | vl_velocity_quick_stop_delta_time | The configured delta time of the slope of the deceleration ramp for quick stop. The values shall be given in second or in user-defined time units. Default : 1s. |
| Int16 | vl_set_point_factor_numerator | The configured numerator of the velocity set-point factor. Default : 1 |
| Int16 | vl_set_point_factor_denominator | The configured denominator of the velocity set-point factor. Default : 1 |
| Int32 | vl_dimension_factor_numerator | The configured numerator of the velocity dimension factor. Default : 1 |
| Int32 | vl_dimension_factor_denominator | The configured denominator of the velocity dimension factor. Default : 1 |

Used in: 
[Method getVelocityModeParameters](#method-getvelocitymodeparameters)
, 
[Method setVelocityModeParameters](#method-setvelocitymodeparameters)
### Struct VelocityModeStatusword

[CIA402-2] Velocity mode statusword. 
The velocity mode use some bits of the CIA402 statusword to report some status.

Struct fields:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| Boolean | internal_limit_active | If True, the velocity demand value is limited to vl_velocity_max_amount / vl_velocity_min_amount. |

Used in: 
[Method getVelocityModeStatusword](#method-getvelocitymodestatusword)
### Struct VelocityModeControlword

[CIA402-2] Velocity mode controlword. 
The velocity mode use some bits of the CIA402 controlword to control the velocity control function.

Struct fields:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| Boolean | enable_ramp | If False, the velocity demand value shall be controlled in any other (manufacturer-specific) way, for example by a test function generator or manufacturer-specific halt function; else, the velocity demand value shall accord with ramp output value. |
| Boolean | unlock_ramp | If False, the ramp output value shall be locked to current output value; else the ramp output value shall follow ramp input value. |
| Boolean | reference_ramp | If False, the ramp input value shall be set to zero; else the ramp input value shall accord with ramp reference. |
| Boolean | halt | If True, the motor shall be stopped. |

Used in: 
[Method getVelocityModeControlword](#method-getvelocitymodecontrolword)

# Interface commonapi.SmcService.SRDO

Version: 1.0

This section is generated from the Franca IDL file for Interface SRDO in package commonapi.SmcService

Interface description: 
CIA304 : SRDO (Safety Related Data Object). 
This is similar to a PDO, but additional properties are defined. These are:
- cyclic data transmission with timeout monitoring
- Double transmission of usage data, one of which is inverted bit by bit
- Check the data consistency
- Check the time interval between the inverted and non-inverted data
- Backup of the configuration through a CRC. 

NOTA : To make an entire SRDO configuration valid, a flag must be set to Index 0x13FE in
the object dictionary. This flag is automatically set to an invalid configuration for every
write access that is done to a safety-related SRDO parameter. After completing the
configuration, this flag must be set to a valid configuration.

## Methods

### Method getSRDOParameters

Retrieve the communication parameters of the specified SRDO id.

Input Parameters:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| [Enumeration SRDOId](#enumeration-srdoid) | id | The SRDO id. |

Output Parameters:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| [Enumeration SRDODirection](#enumeration-srdodirection) | direction | The direction of the SRDO. |
| [Struct SRDOParameters](#struct-srdoparameters) | parameters | The communication parameters of the SRDO. |
| UInt16 | signature | The signature of the SRDO. |
| Int32 | error_code |  |

### Method setSRDOParameters

Modify the communication parameters of the specified SRDO id.

Input Parameters:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| [Enumeration SRDOId](#enumeration-srdoid) | id | The SRDO id. |
| [Struct SRDOParameters](#struct-srdoparameters) | parameters | The new communication parameters. |

Output Parameters:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| Int32 | error_code |  |

### Method getSRDOMapping

Retrieve the mapping parameters of the specified SRDO id.

Input Parameters:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| [Enumeration SRDOId](#enumeration-srdoid) | id | The SRDO id. |

Output Parameters:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| [Struct SRDOMapping](#struct-srdomapping) | mapping | The configured mapping parameters. |
| Int32 | error_code |  |

### Method getSRDOConfigurationValidity

Retrieve the SRDO configuration valid flag (0x13fe => 0xA5 the configuration is valid; other values the configuration is invalid).

Output Parameters:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| Boolean | isValid | The SRDO configuration valid flag. |
| Int32 | error_code |  |

### Method setSRDOConfigurationValidity

Modify the SRDO configuration valid flag (0x13fe => 0xA5 the configuration is valid; other values the configuration is invalid).

Output Parameters:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| Int32 | error_code |  |

## Structs

### Struct SRDOParameters

Indicates the communication parameters of a SRDO. 
NOTA : COB IDs in the range from 0x100 to 0x180 are used so that the transmission in the CANopen network does not interfere with other services and the priority of the CAN IDs is higher than that of PDOs.

Struct fields:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| Boolean | valid | Indicates the validity of the SRDO. True if exists / is valid; False if does not exist / is not valid. SRDO1 and SRDO2 are not modifiable. |
| UInt16 | sct | Indicates the refresh time SCT (Safety Cycle Time) of the SRDO. Default : 25ms. |
| UInt8 | srvt | Indicates the srvt (Safety-related Validation Time) time between the 2 CAN messages of an SRDO. Default : 20ms. |
| [Enumeration SRDOTransmissionType](#enumeration-srdotransmissiontype) | transmission_type | Indicates the transmission type. Fix : PDO_ASYNC_FE. |
| UInt16 | can_id1 | Indicates the CAN identifier (11 bits) for plain data. |
| UInt16 | can_id2 | Indicates the CAN identifier (11 bits) for bitwise inverted data. |

Used in: 
[Method getSRDOParameters](#method-getsrdoparameters)
, 
[Method setSRDOParameters](#method-setsrdoparameters)
### Struct SRDOMapping

Indicates the mapping parameters of a SRDO.

Struct fields:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| UInt8 | mapping_count | Indicates the number of mapped data in SRDO. 2 mapping entry by data object (normal and inverted). |
| Array of UInt32 | data | Indicates the mapped data in SRDO. |

Used in: 
[Method getSRDOMapping](#method-getsrdomapping)

## Enumerations

### Enumeration SRDOId

Indicates the SRDO Id. NOTA : id 3 to 8 doesn’t exist.

|     |     |     |
| --- | --- | --- |
| Enumerator | Value | Description |
| SRDO_1 | 1 | Id of the SRDO 1. |
| SRDO_2 | 2 | Id of the SRDO 2. |
| SRDO_9 | 9 | Id of the SRDO 9. |
| SRDO_10 | 10 | Id of the SRDO 10. |
| SRDO_11 | 11 | Id of the SRDO 11. |
| SRDO_12 | 12 | Id of the SRDO 12. |
| SRDO_13 | 13 | Id of the SRDO 13. |
| SRDO_14 | 14 | Id of the SRDO 14. |
| SRDO_15 | 15 | Id of the SRDO 15. |
| SRDO_16 | 16 | Id of the SRDO 16. |

Used in: 
[Method getSRDOParameters](#method-getsrdoparameters)
, 
[Method setSRDOParameters](#method-setsrdoparameters)
, 
[Method getSRDOMapping](#method-getsrdomapping)
### Enumeration SRDODirection

Indicates the direction of a SRDO.

|     |     |     |
| --- | --- | --- |
| Enumerator | Value | Description |
| SRDO_TX | 1 | The SRDO is switched on as send-SRDO (TSRDO). |
| SRDO_RX | 2 | The SRDO is switched on as receiver-SRDO (RSRDO). |

Used in: 
[Method getSRDOParameters](#method-getsrdoparameters)
### Enumeration SRDOTransmissionType

Indicates the transmission type of a SRDO.

|     |     |     |
| --- | --- | --- |
| Enumerator | Value | Description |
| PDO_ASYNC_FE | 254 | Asynchronous: The data become valid when the PDO message is received and are taken over into the object dictionary. |

Used in: 
[Struct SRDOParameters](#struct-srdoparameters)

# Interface commonapi.SmcService.CANOpen

Version: 1.0

This section is generated from the Franca IDL file for Interface CANOpen in package commonapi.SmcService

Interface description: 
CANopen object dictionary services.

## Methods

### Method getValueString

Retrieve the value of the specified object address for a type string.

Input Parameters:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| UInt32 | address | The object address. |

Output Parameters:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| String | data | The object value. |
| Int32 | error_code |  |

### Method setValueString

Modify the value of the specified object address for a type string.

Input Parameters:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| UInt32 | address | The object address. |
| String | data | The object value. |

Output Parameters:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| Int32 | error_code |  |

### Method getValueInt64

Retrieve the value of the specified object address for a type int64.

Input Parameters:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| UInt32 | address | The object address. |

Output Parameters:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| Int64 | data | The object value. |
| Int32 | error_code |  |

### Method setValueInt64

Modify the value of the specified object address for a type int64.

Input Parameters:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| UInt32 | address | The object address. |
| Int64 | data | The object value. |

Output Parameters:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| Int32 | error_code |  |

### Method getValueInt32

Retrieve the value of the specified object address for a type int32.

Input Parameters:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| UInt32 | address | The object address. |

Output Parameters:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| Int32 | data | The object value. |
| Int32 | error_code |  |

### Method setValueInt32

Modify the value of the specified object address for a type int32.

Input Parameters:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| UInt32 | address | The object address. |
| Int32 | data | The object value. |

Output Parameters:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| Int32 | error_code |  |

### Method getValueInt16

Retrieve the value of the specified object address for a type int16.

Input Parameters:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| UInt32 | address | The object address. |

Output Parameters:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| Int16 | data | The object value. |
| Int32 | error_code |  |

### Method setValueInt16

Modify the value of the specified object address for a type int16.

Input Parameters:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| UInt32 | address | The object address. |
| Int16 | data | The object value. |

Output Parameters:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| Int32 | error_code |  |

### Method getValueInt8

Retrieve the value of the specified object address for a type int8.

Input Parameters:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| UInt32 | address | The object address. |

Output Parameters:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| Int8 | data | The object value. |
| Int32 | error_code |  |

### Method setValueInt8

Modify the value of the specified object address for a type int8.

Input Parameters:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| UInt32 | address | The object address. |
| Int8 | data | The object value. |

Output Parameters:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| Int32 | error_code |  |

### Method getValueUInt64

Retrieve the value of the specified object address for a type uint64.

Input Parameters:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| UInt32 | address | The object address. |

Output Parameters:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| UInt64 | data | The object value. |
| Int32 | error_code |  |

### Method setValueUInt64

Modify the value of the specified object address for a type uint64.

Input Parameters:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| UInt32 | address | The object address. |
| UInt64 | data | The object value. |

Output Parameters:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| Int32 | error_code |  |

### Method getValueUInt32

Retrieve the value of the specified object address for a type uint32.

Input Parameters:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| UInt32 | address | The object address. |

Output Parameters:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| UInt32 | data | The object value. |
| Int32 | error_code |  |

### Method setValueUInt32

Modify the value of the specified object address for a type uint32.

Input Parameters:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| UInt32 | address | The object address. |
| UInt32 | data | The object value. |

Output Parameters:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| Int32 | error_code |  |

### Method getValueUInt16

Retrieve the value of the specified object address for a type uint16.

Input Parameters:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| UInt32 | address | The object address. |

Output Parameters:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| UInt16 | data | The object value. |
| Int32 | error_code |  |

### Method setValueUInt16

Modify the value of the specified object address for a type uint16.

Input Parameters:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| UInt32 | address | The object address. |
| UInt16 | data | The object value. |

Output Parameters:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| Int32 | error_code |  |

### Method getValueUInt8

Retrieve the value of the specified object address for a type uint8.

Input Parameters:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| UInt32 | address | The object address. |

Output Parameters:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| UInt8 | data | The object value. |
| Int32 | error_code |  |

### Method setValueUInt8

Modify the value of the specified object address for a type uint8.

Input Parameters:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| UInt32 | address | The object address. |
| UInt8 | data | The object value. |

Output Parameters:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| Int32 | error_code |  |

### Method getValueFloat

Retrieve the value of the specified object address for a type float.

Input Parameters:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| UInt32 | address | The object address. |

Output Parameters:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| Float | data | The object value. |
| Int32 | error_code |  |

### Method setValueFloat

Modify the value of the specified object address for a type float.

Input Parameters:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| UInt32 | address | The object address. |
| Float | data | The object value. |

Output Parameters:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| Int32 | error_code |  |

### Method getValueDouble

Retrieve the value of the specified object address for a type double.

Input Parameters:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| UInt32 | address | The object address. |

Output Parameters:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| Double | data | The object value. |
| Int32 | error_code |  |

### Method setValueDouble

Modify the value of the specified object address for a type double.

Input Parameters:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| UInt32 | address | The object address. |
| Double | data | The object value. |

Output Parameters:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| Int32 | error_code |  |

### Method getValueBool

Retrieve the value of the specified object address for a type boolean.

Input Parameters:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| UInt32 | address | The object address. |

Output Parameters:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| Boolean | data | The object value. |
| Int32 | error_code |  |

### Method setValueBool

Modify the value of the specified object address for a type boolean.

Input Parameters:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| UInt32 | address | The object address. |
| Boolean | data | The object value. |

Output Parameters:

|     |     |     |
| --- | --- | --- |
| Type | Name | Description |
| Int32 | error_code |  |

# TypeCollection commonapi.SmcService.Types

Version: 1.0

This section is generated from the Franca IDL file for TypeCollection Types in package commonapi.SmcService

## Enumerations

### Enumeration ErrorEnum

Indicates the error type.

|     |     |     |
| --- | --- | --- |
| Enumerator | Value | Description |
| ERROR_NOT_INITIALIZED | 0 | Not initialized error. |
| ERROR_NONE | 1 | No error occurred. |
| ERROR_HARDWARE | 2 | Hardware error. |
| ERROR_CONFIG | 3 | Configuration error. |
| ERROR_ARGUMENT | 4 | Argument error. |
| ERROR_INTERNAL | 5 | Internal error. |
| ERROR_EXTERNAL | 6 | External error. |
