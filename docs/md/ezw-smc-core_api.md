# namespace `smccore`



## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`class `[``ICommunicationService``](#classezw_1_1smccore_1_1_i_communication_service)    | [CIA301] Communication setting.
`class `[``IManufacturerService``](#classezw_1_1smccore_1_1_i_manufacturer_service)    | Manufacturer services.
`class `[``ICANOpenService``](#classezw_1_1smccore_1_1_i_c_a_n_open_service)    | CANopen object dictionary services.
`class `[``ICoreService``](#classezw_1_1smccore_1_1_i_core_service)    | SWD product services.
`class `[``IEMCYService``](#classezw_1_1smccore_1_1_i_e_m_c_y_service)    | Emergency ( EMCY ) functionalities.
`class `[``INMTService``](#classezw_1_1smccore_1_1_i_n_m_t_service)    | [CIA301] Network management (NMT).
`class `[``IPDSService``](#classezw_1_1smccore_1_1_i_p_d_s_service)    | [CIA402-2] Controlling the Power Drive System (PDS).
`class `[``ISafeMotionService``](#classezw_1_1smccore_1_1_i_safe_motion_service)    | [CIA402-4] Safety motion drive. The activation of a security function can come from :
`class `[``IService``](#classezw_1_1smccore_1_1_i_service)    | 
`class `[``ISRDOService``](#classezw_1_1smccore_1_1_i_s_r_d_o_service)    | CIA304 : SRDO (Safety Related Data Object). This is similar to a PDO, but additional properties are defined. These are:
`class `[``IVelocityModeService``](#classezw_1_1smccore_1_1_i_velocity_mode_service)    | [CIA402-2] The velocity mode controls the speed (velocity) of the SWD product but not its position. The selection of a new target velocity use a acceleration / deceleration ramp. The velocity mode is composed of three main functions:
# class `ICommunicationService` {#classezw_1_1smccore_1_1_i_communication_service}


[CIA301] Communication setting.



## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`struct `[``COBID``](#structezw_1_1smccore_1_1_i_communication_service_1_1_c_o_b_i_d)        | 
`struct `[``CommunicationParameters``](#structezw_1_1smccore_1_1_i_communication_service_1_1_communication_parameters)        | 
`struct `[``IdentityParameters``](#structezw_1_1smccore_1_1_i_communication_service_1_1_identity_parameters)        | 
`struct `[``NetworkParameters``](#structezw_1_1smccore_1_1_i_communication_service_1_1_network_parameters)        | 
`struct `[``PDOCommunicationParameters``](#structezw_1_1smccore_1_1_i_communication_service_1_1_p_d_o_communication_parameters)        | 
`struct `[``PDOMappingParameters``](#structezw_1_1smccore_1_1_i_communication_service_1_1_p_d_o_mapping_parameters)        | 
`struct `[``SDOCommunicationParameters``](#structezw_1_1smccore_1_1_i_communication_service_1_1_s_d_o_communication_parameters)        | 
`public virtual  ~ICommunicationService() = default` | 
`public ezw_error_t storeParameters(const `[`BlocId`](#classezw_1_1smccore_1_1_i_communication_service_1a0dcd44777037c7e6a03a37a7dbfc31b9)` & pBlocId)` | Store the parameters of the specified bloc id into the non-volatile memory.
`public ezw_error_t restoreDefaultParameters(const `[`BlocId`](#classezw_1_1smccore_1_1_i_communication_service_1a0dcd44777037c7e6a03a37a7dbfc31b9)` & pBlocId)` | Restore the default parameters of the specified bloc id. Restoring is done by declaring the stored parameters in NVM as invalid. The function does not load the default parameters. The default values shall be set valid after the CANopen device is reset (NMT service reset node for sub-index from 01h to 7Fh, NMT service reset communication for sub-index 02h) or power cycled.
`public ezw_error_t getIdentityParameters(`[`IdentityParameters`](#structezw_1_1smccore_1_1_i_communication_service_1_1_identity_parameters)` & pParams) const` | Retrieve the device parameters.
`public ezw_error_t getNetworkParameters(`[`NetworkParameters`](#structezw_1_1smccore_1_1_i_communication_service_1_1_network_parameters)` & pParams) const` | Retrieve the network parameters.
`public ezw_error_t setNetworkParameters(const `[`NetworkParameters`](#structezw_1_1smccore_1_1_i_communication_service_1_1_network_parameters)` & pParams)` | Modify the network parameters.
`public ezw_error_t getCommunicationParameters(`[`CommunicationParameters`](#structezw_1_1smccore_1_1_i_communication_service_1_1_communication_parameters)` & pParams) const` | Retrieve the communication parameters.
`public ezw_error_t setCommunicationParameters(const `[`CommunicationParameters`](#structezw_1_1smccore_1_1_i_communication_service_1_1_communication_parameters)` & pParams)` | Modify the communication parameters.
`public ezw_error_t getSDOCommunicationParameters(const `[`SDOId`](#classezw_1_1smccore_1_1_i_communication_service_1a764ac2fa1a7afff3a0fd2892ff06bfc6)` & pId,`[`SDOCommunicationParameters`](#structezw_1_1smccore_1_1_i_communication_service_1_1_s_d_o_communication_parameters)` & pParams) const` | Retrieve the SDO communication parameters of the specified SDO id.
`public ezw_error_t setSDOCommunicationParameters(const `[`SDOId`](#classezw_1_1smccore_1_1_i_communication_service_1a764ac2fa1a7afff3a0fd2892ff06bfc6)` & pId,const `[`SDOCommunicationParameters`](#structezw_1_1smccore_1_1_i_communication_service_1_1_s_d_o_communication_parameters)` & pParams)` | Modify the SDO communication parameters of the specified SDO id.
`public ezw_error_t getRPDOCommunicationParameters(const `[`PDOId`](#classezw_1_1smccore_1_1_i_communication_service_1a0f9c4168a723b6beb9dd875dcf0ef07b)` & pId,`[`PDOCommunicationParameters`](#structezw_1_1smccore_1_1_i_communication_service_1_1_p_d_o_communication_parameters)` & pParams) const` | Retrieve the communication parameters of the specified RPDO id (PDO the CANopen device is able to receive).
`public ezw_error_t setRPDOCommunicationParameters(const `[`PDOId`](#classezw_1_1smccore_1_1_i_communication_service_1a0f9c4168a723b6beb9dd875dcf0ef07b)` & pId,const `[`PDOCommunicationParameters`](#structezw_1_1smccore_1_1_i_communication_service_1_1_p_d_o_communication_parameters)` & pParams)` | Modify the communication parameters of the specified RPDO id (PDO the CANopen device is able to receive).
`public ezw_error_t getTPDOCommunicationParameters(const `[`PDOId`](#classezw_1_1smccore_1_1_i_communication_service_1a0f9c4168a723b6beb9dd875dcf0ef07b)` & pId,`[`PDOCommunicationParameters`](#structezw_1_1smccore_1_1_i_communication_service_1_1_p_d_o_communication_parameters)` & pParams) const` | Retrieve the communication parameters of the specified TPDO id (PDO the CANopen device is able to transmit).
`public ezw_error_t setTPDOCommunicationParameters(const `[`PDOId`](#classezw_1_1smccore_1_1_i_communication_service_1a0f9c4168a723b6beb9dd875dcf0ef07b)` & pId,const `[`PDOCommunicationParameters`](#structezw_1_1smccore_1_1_i_communication_service_1_1_p_d_o_communication_parameters)` & pParams)` | Modify the communication parameters of the specified TPDO id (PDO the CANopen device is able to transmit).
`public ezw_error_t getRPDOMappingParameters(const `[`PDOId`](#classezw_1_1smccore_1_1_i_communication_service_1a0f9c4168a723b6beb9dd875dcf0ef07b)` & pId,`[`PDOMappingParameters`](#structezw_1_1smccore_1_1_i_communication_service_1_1_p_d_o_mapping_parameters)` & pParams) const` | Retrieve the mapping parameters of the specified RPDO id (PDO the CANopen device is able to receive).
`public ezw_error_t setRPDOMappingParameters(const `[`PDOId`](#classezw_1_1smccore_1_1_i_communication_service_1a0f9c4168a723b6beb9dd875dcf0ef07b)` & pId,const `[`PDOMappingParameters`](#structezw_1_1smccore_1_1_i_communication_service_1_1_p_d_o_mapping_parameters)` & pParams)` | Modify the mapping parameters of the specified RPDO id (PDO the CANopen device is able to receive).
`public ezw_error_t getTPDOMappingParameters(const `[`PDOId`](#classezw_1_1smccore_1_1_i_communication_service_1a0f9c4168a723b6beb9dd875dcf0ef07b)` & pId,`[`PDOMappingParameters`](#structezw_1_1smccore_1_1_i_communication_service_1_1_p_d_o_mapping_parameters)` & pParams) const` | Retrieve the mapping parameters of the specified TPDO id (PDO the CANopen device is able to transmit).
`public ezw_error_t setTPDOMappingParameters(const `[`PDOId`](#classezw_1_1smccore_1_1_i_communication_service_1a0f9c4168a723b6beb9dd875dcf0ef07b)` & pId,const `[`PDOMappingParameters`](#structezw_1_1smccore_1_1_i_communication_service_1_1_p_d_o_mapping_parameters)` & pParams)` | Modify the Mapping parameters of the specified TPDO id (PDO the CANopen device is able to transmit).

## Members

### `struct `[``COBID``](#structezw_1_1smccore_1_1_i_communication_service_1_1_c_o_b_i_d) {#structezw_1_1smccore_1_1_i_communication_service_1_1_c_o_b_i_d}



Represents a COB-ID. A COB-ID allows to specify the CAN-ID of the message on the can bus and its validity. NOTA :

* SWD product allows only CAN-ID in 11 bits format.


* SWD product doesn't allows TPDO send in RTR mode (bit 30 = 1).


* SWD product doesn't allows dynamic SDO connections (bit 30 = 0).


* The bit valid (bit 31) allows selecting which TPDOs/RPDOs are used in the NMT state Operational.
### `struct `[``CommunicationParameters``](#structezw_1_1smccore_1_1_i_communication_service_1_1_communication_parameters) {#structezw_1_1smccore_1_1_i_communication_service_1_1_communication_parameters}



Indicates the configured communication parameters.
### `struct `[``IdentityParameters``](#structezw_1_1smccore_1_1_i_communication_service_1_1_identity_parameters) {#structezw_1_1smccore_1_1_i_communication_service_1_1_identity_parameters}



Indicates the identity device parameters.
### `struct `[``NetworkParameters``](#structezw_1_1smccore_1_1_i_communication_service_1_1_network_parameters) {#structezw_1_1smccore_1_1_i_communication_service_1_1_network_parameters}



Indicates the configured network parameters.
### `struct `[``PDOCommunicationParameters``](#structezw_1_1smccore_1_1_i_communication_service_1_1_p_d_o_communication_parameters) {#structezw_1_1smccore_1_1_i_communication_service_1_1_p_d_o_communication_parameters}



Indicates the communication parameters of a PDO.
### `struct `[``PDOMappingParameters``](#structezw_1_1smccore_1_1_i_communication_service_1_1_p_d_o_mapping_parameters) {#structezw_1_1smccore_1_1_i_communication_service_1_1_p_d_o_mapping_parameters}



Indicates the mapping parameters of a PDO.
### `struct `[``SDOCommunicationParameters``](#structezw_1_1smccore_1_1_i_communication_service_1_1_s_d_o_communication_parameters) {#structezw_1_1smccore_1_1_i_communication_service_1_1_s_d_o_communication_parameters}



Indicates the SDO server communication parameters. NOTA :

* The SDO server 1 communication parameters are in read only mode.


* COB-ID of the SDO reception of the SDO 1 server is $NODEID+0x600.


* COB-ID of the SDO transmission of the SDO 1 server is $NODEID+0x580.


* Only static SDO connections are allowed (bit dyn 30 = 0).


* Static SDO connections are configured non-temporarily and may be saved in non-volatile memory.
### `public virtual  ~ICommunicationService() = default` {#classezw_1_1smccore_1_1_i_communication_service_1a1a552f2dd2cee265a25a51a312c64163}





### `public ezw_error_t storeParameters(const `[`BlocId`](#classezw_1_1smccore_1_1_i_communication_service_1a0dcd44777037c7e6a03a37a7dbfc31b9)` & pBlocId)` {#classezw_1_1smccore_1_1_i_communication_service_1a50f97318d4277e6d90288b1719c4a654}

Store the parameters of the specified bloc id into the non-volatile memory.

#### Parameters
* `pBlocId` The bloc id. 





#### Returns
ERROR_NONE if no error occurred

### `public ezw_error_t restoreDefaultParameters(const `[`BlocId`](#classezw_1_1smccore_1_1_i_communication_service_1a0dcd44777037c7e6a03a37a7dbfc31b9)` & pBlocId)` {#classezw_1_1smccore_1_1_i_communication_service_1a203ebc4d0afc5cec5ddbcb2587ecca17}

Restore the default parameters of the specified bloc id. Restoring is done by declaring the stored parameters in NVM as invalid. The function does not load the default parameters. The default values shall be set valid after the CANopen device is reset (NMT service reset node for sub-index from 01h to 7Fh, NMT service reset communication for sub-index 02h) or power cycled.

#### Parameters
* `pBlocId` The bloc id. 





#### Returns
ERROR_NONE if no error occurred

### `public ezw_error_t getIdentityParameters(`[`IdentityParameters`](#structezw_1_1smccore_1_1_i_communication_service_1_1_identity_parameters)` & pParams) const` {#classezw_1_1smccore_1_1_i_communication_service_1af9b91f44835d40791ff72d19831bffec}

Retrieve the device parameters.

#### Parameters
* `pParams` The device parameters. 





#### Returns
ERROR_NONE if no error occurred

### `public ezw_error_t getNetworkParameters(`[`NetworkParameters`](#structezw_1_1smccore_1_1_i_communication_service_1_1_network_parameters)` & pParams) const` {#classezw_1_1smccore_1_1_i_communication_service_1a83cd8cdb9b0648d6eb6fa1595b9d217c}

Retrieve the network parameters.

#### Parameters
* `pParams` The network parameters. 





#### Returns
ERROR_NONE if no error occurred

### `public ezw_error_t setNetworkParameters(const `[`NetworkParameters`](#structezw_1_1smccore_1_1_i_communication_service_1_1_network_parameters)` & pParams)` {#classezw_1_1smccore_1_1_i_communication_service_1ad35ea89ca973bfeb90a9f2962cfeef9f}

Modify the network parameters.

#### Parameters
* `pParams` The new network parameters. 





#### Returns
ERROR_NONE if no error occurred

### `public ezw_error_t getCommunicationParameters(`[`CommunicationParameters`](#structezw_1_1smccore_1_1_i_communication_service_1_1_communication_parameters)` & pParams) const` {#classezw_1_1smccore_1_1_i_communication_service_1abec1ec392acb82a73b9753c2d6201772}

Retrieve the communication parameters.

#### Parameters
* `pParams` The communication parameters. 





#### Returns
ERROR_NONE if no error occurred

### `public ezw_error_t setCommunicationParameters(const `[`CommunicationParameters`](#structezw_1_1smccore_1_1_i_communication_service_1_1_communication_parameters)` & pParams)` {#classezw_1_1smccore_1_1_i_communication_service_1a22fbf57200bd50cb426eb989f99b0fd0}

Modify the communication parameters.

#### Parameters
* `pParams` The communication parameters. 





#### Returns
ERROR_NONE if no error occurred

### `public ezw_error_t getSDOCommunicationParameters(const `[`SDOId`](#classezw_1_1smccore_1_1_i_communication_service_1a764ac2fa1a7afff3a0fd2892ff06bfc6)` & pId,`[`SDOCommunicationParameters`](#structezw_1_1smccore_1_1_i_communication_service_1_1_s_d_o_communication_parameters)` & pParams) const` {#classezw_1_1smccore_1_1_i_communication_service_1af11fb660eb54a568c2047b9a13ee4176}

Retrieve the SDO communication parameters of the specified SDO id.

#### Parameters
* `pId` The SDO id. 


* `pParams` The communication parameters. 





#### Returns
ERROR_NONE if no error occurred

### `public ezw_error_t setSDOCommunicationParameters(const `[`SDOId`](#classezw_1_1smccore_1_1_i_communication_service_1a764ac2fa1a7afff3a0fd2892ff06bfc6)` & pId,const `[`SDOCommunicationParameters`](#structezw_1_1smccore_1_1_i_communication_service_1_1_s_d_o_communication_parameters)` & pParams)` {#classezw_1_1smccore_1_1_i_communication_service_1a75441100d35c59eaacde498d5d40281f}

Modify the SDO communication parameters of the specified SDO id.

#### Parameters
* `pId` The SDO id. 


* `pParams` The new communication parameters. 





#### Returns
ERROR_NONE if no error occurred

### `public ezw_error_t getRPDOCommunicationParameters(const `[`PDOId`](#classezw_1_1smccore_1_1_i_communication_service_1a0f9c4168a723b6beb9dd875dcf0ef07b)` & pId,`[`PDOCommunicationParameters`](#structezw_1_1smccore_1_1_i_communication_service_1_1_p_d_o_communication_parameters)` & pParams) const` {#classezw_1_1smccore_1_1_i_communication_service_1aa128e9a0dd05d99084d2ba16f1df7e32}

Retrieve the communication parameters of the specified RPDO id (PDO the CANopen device is able to receive).

#### Parameters
* `pId` The PDO id. 


* `pParams` The communication parameters. 





#### Returns
ERROR_NONE if no error occurred

### `public ezw_error_t setRPDOCommunicationParameters(const `[`PDOId`](#classezw_1_1smccore_1_1_i_communication_service_1a0f9c4168a723b6beb9dd875dcf0ef07b)` & pId,const `[`PDOCommunicationParameters`](#structezw_1_1smccore_1_1_i_communication_service_1_1_p_d_o_communication_parameters)` & pParams)` {#classezw_1_1smccore_1_1_i_communication_service_1a6ef9096bc5424b269666a29761cbec37}

Modify the communication parameters of the specified RPDO id (PDO the CANopen device is able to receive).

#### Parameters
* `pId` The PDO id. 


* `pParams` The new communication parameters. 





#### Returns
ERROR_NONE if no error occurred

### `public ezw_error_t getTPDOCommunicationParameters(const `[`PDOId`](#classezw_1_1smccore_1_1_i_communication_service_1a0f9c4168a723b6beb9dd875dcf0ef07b)` & pId,`[`PDOCommunicationParameters`](#structezw_1_1smccore_1_1_i_communication_service_1_1_p_d_o_communication_parameters)` & pParams) const` {#classezw_1_1smccore_1_1_i_communication_service_1a2a32c0a7f0392c955c697797c157c627}

Retrieve the communication parameters of the specified TPDO id (PDO the CANopen device is able to transmit).

#### Parameters
* `pId` The PDO id. 


* `pParams` The communication parameters. 





#### Returns
ERROR_NONE if no error occurred

### `public ezw_error_t setTPDOCommunicationParameters(const `[`PDOId`](#classezw_1_1smccore_1_1_i_communication_service_1a0f9c4168a723b6beb9dd875dcf0ef07b)` & pId,const `[`PDOCommunicationParameters`](#structezw_1_1smccore_1_1_i_communication_service_1_1_p_d_o_communication_parameters)` & pParams)` {#classezw_1_1smccore_1_1_i_communication_service_1ad35d5b7382d64805ce02315d3832d98b}

Modify the communication parameters of the specified TPDO id (PDO the CANopen device is able to transmit).

#### Parameters
* `pId` The PDO id. 


* `pParams` The new communication parameters. 





#### Returns
ERROR_NONE if no error occurred

### `public ezw_error_t getRPDOMappingParameters(const `[`PDOId`](#classezw_1_1smccore_1_1_i_communication_service_1a0f9c4168a723b6beb9dd875dcf0ef07b)` & pId,`[`PDOMappingParameters`](#structezw_1_1smccore_1_1_i_communication_service_1_1_p_d_o_mapping_parameters)` & pParams) const` {#classezw_1_1smccore_1_1_i_communication_service_1abc67a7378477cb182637c7c949e7984d}

Retrieve the mapping parameters of the specified RPDO id (PDO the CANopen device is able to receive).

#### Parameters
* `pId` The PDO id. 


* `pParams` The mapping parameters. 





#### Returns
ERROR_NONE if no error occurred

### `public ezw_error_t setRPDOMappingParameters(const `[`PDOId`](#classezw_1_1smccore_1_1_i_communication_service_1a0f9c4168a723b6beb9dd875dcf0ef07b)` & pId,const `[`PDOMappingParameters`](#structezw_1_1smccore_1_1_i_communication_service_1_1_p_d_o_mapping_parameters)` & pParams)` {#classezw_1_1smccore_1_1_i_communication_service_1a5810b64199e40445c04a402f58727726}

Modify the mapping parameters of the specified RPDO id (PDO the CANopen device is able to receive).

#### Parameters
* `pId` The PDO id. 


* `pParams` The new mapping parameters. 





#### Returns
ERROR_NONE if no error occurred

### `public ezw_error_t getTPDOMappingParameters(const `[`PDOId`](#classezw_1_1smccore_1_1_i_communication_service_1a0f9c4168a723b6beb9dd875dcf0ef07b)` & pId,`[`PDOMappingParameters`](#structezw_1_1smccore_1_1_i_communication_service_1_1_p_d_o_mapping_parameters)` & pParams) const` {#classezw_1_1smccore_1_1_i_communication_service_1a43a94e0f38368b7a1d7eac3f85491c43}

Retrieve the mapping parameters of the specified TPDO id (PDO the CANopen device is able to transmit).

#### Parameters
* `pId` The PDO id. 


* `pParams` The mapping parameters. 





#### Returns
ERROR_NONE if no error occurred

### `public ezw_error_t setTPDOMappingParameters(const `[`PDOId`](#classezw_1_1smccore_1_1_i_communication_service_1a0f9c4168a723b6beb9dd875dcf0ef07b)` & pId,const `[`PDOMappingParameters`](#structezw_1_1smccore_1_1_i_communication_service_1_1_p_d_o_mapping_parameters)` & pParams)` {#classezw_1_1smccore_1_1_i_communication_service_1ace7948f4f85f331deabb68e16d05971f}

Modify the Mapping parameters of the specified TPDO id (PDO the CANopen device is able to transmit).

#### Parameters
* `pId` The PDO id. 


* `pParams` The new mapping parameters. 





#### Returns
ERROR_NONE if no error occurred

# struct `COBID` {#structezw_1_1smccore_1_1_i_communication_service_1_1_c_o_b_i_d}




Represents a COB-ID. A COB-ID allows to specify the CAN-ID of the message on the can bus and its validity. NOTA :

* SWD product allows only CAN-ID in 11 bits format.


* SWD product doesn't allows TPDO send in RTR mode (bit 30 = 1).


* SWD product doesn't allows dynamic SDO connections (bit 30 = 0).


* The bit valid (bit 31) allows selecting which TPDOs/RPDOs are used in the NMT state Operational.

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`public uint16_t can_id` | 
`public bool valid` | 
`public bool flag` | 

## Members

### `public uint16_t can_id` {#structezw_1_1smccore_1_1_i_communication_service_1_1_c_o_b_i_d_1a2aba17567e9ef3439abdfc2a32fee816}



The CAN-ID.

### `public bool valid` {#structezw_1_1smccore_1_1_i_communication_service_1_1_c_o_b_i_d_1a28e3c179a86f337095088b3ca02a2b2a}



True if valid else False.

### `public bool flag` {#structezw_1_1smccore_1_1_i_communication_service_1_1_c_o_b_i_d_1a8b3ab54ed3e81c69863d65e4e6c424a0}



Represents the bit 30. SDO : False = value is assigned statically; TPDO : True = no RTR allowed on this PDO; RPDO : not used

# struct `CommunicationParameters` {#structezw_1_1smccore_1_1_i_communication_service_1_1_communication_parameters}




Indicates the configured communication parameters.

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`public uint16_t can_id_sync` | 
`public uint16_t prod_hb_time` | 

## Members

### `public uint16_t can_id_sync` {#structezw_1_1smccore_1_1_i_communication_service_1_1_communication_parameters_1a65566e1c4cf9437f06adbed7d203a1a9}



Indicates the configured CAN-ID of the synchronization object (SYNC). Default : 80h.

### `public uint16_t prod_hb_time` {#structezw_1_1smccore_1_1_i_communication_service_1_1_communication_parameters_1a79449feb8b33a7d18cc5f2aef4c8994b}



Indicates the configured cycle time of the heartbeat in steps of 1 ms. 0h = heartbeat disabled. Default : 500ms.

# struct `IdentityParameters` {#structezw_1_1smccore_1_1_i_communication_service_1_1_identity_parameters}




Indicates the identity device parameters.

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`public uint32_t vendor_id` | 
`public uint32_t product_code` | 
`public uint32_t revision_number` | 
`public uint32_t serial_number` | 

## Members

### `public uint32_t vendor_id` {#structezw_1_1smccore_1_1_i_communication_service_1_1_identity_parameters_1a3590925789f63df8258823a2d62649b0}



Indicates the Vendor-ID.

### `public uint32_t product_code` {#structezw_1_1smccore_1_1_i_communication_service_1_1_identity_parameters_1ad388e3e5ec3b3be0cd885afae1505483}



Indicates the product code.

### `public uint32_t revision_number` {#structezw_1_1smccore_1_1_i_communication_service_1_1_identity_parameters_1a202d643cd5a07dd50598c61b3d9eeae6}



Indicates the revision number.

### `public uint32_t serial_number` {#structezw_1_1smccore_1_1_i_communication_service_1_1_identity_parameters_1a6e8bbfd1742ed72ee05410d125c27790}



Indicates the serial number.

# struct `NetworkParameters` {#structezw_1_1smccore_1_1_i_communication_service_1_1_network_parameters}




Indicates the configured network parameters.

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`public `[`BitTiming`](#classezw_1_1smccore_1_1_i_communication_service_1ad4446b8710beab2e9a35ff0db3aecb7c)` bit_timing` | 
`public uint8_t node_id` | 
`public bool rt_activated` | 

## Members

### `public `[`BitTiming`](#classezw_1_1smccore_1_1_i_communication_service_1ad4446b8710beab2e9a35ff0db3aecb7c)` bit_timing` {#structezw_1_1smccore_1_1_i_communication_service_1_1_network_parameters_1a205abe6e5da355822e5e50e9ae01768f}



The bit timing index of the device.

### `public uint8_t node_id` {#structezw_1_1smccore_1_1_i_communication_service_1_1_network_parameters_1a85ddb7b34cd98fc48dc986c615e4d0f2}



The node id of the device : from 1 to 127.

### `public bool rt_activated` {#structezw_1_1smccore_1_1_i_communication_service_1_1_network_parameters_1ae0b9e535642ec6a8c50986f47c17a6ae}



True means R_termination is activated.

# struct `PDOCommunicationParameters` {#structezw_1_1smccore_1_1_i_communication_service_1_1_p_d_o_communication_parameters}




Indicates the communication parameters of a PDO.

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`public `[`COBID`](#structezw_1_1smccore_1_1_i_communication_service_1_1_c_o_b_i_d)` cob_id` | 
`public `[`PDOTransmissionType`](#classezw_1_1smccore_1_1_i_communication_service_1ade99b625dac48ed94e3fc1b00d9cc179)` transmission_type` | 
`public uint16_t event_timer` | 

## Members

### `public `[`COBID`](#structezw_1_1smccore_1_1_i_communication_service_1_1_c_o_b_i_d)` cob_id` {#structezw_1_1smccore_1_1_i_communication_service_1_1_p_d_o_communication_parameters_1ad2cde6c10c504cf317d7bac8072263cf}



Indicates the COB-ID used by the PDO.

### `public `[`PDOTransmissionType`](#classezw_1_1smccore_1_1_i_communication_service_1ade99b625dac48ed94e3fc1b00d9cc179)` transmission_type` {#structezw_1_1smccore_1_1_i_communication_service_1_1_p_d_o_communication_parameters_1a29b455042215417ba29eaeb87b08995a}



Indicates the transmission type. Default : PDO_SYNC_1 in TX.

### `public uint16_t event_timer` {#structezw_1_1smccore_1_1_i_communication_service_1_1_p_d_o_communication_parameters_1a537c584c1825af2ddb0a6d97e20fe494}



Independent of the transmission type the RPDO event timer is used recognize the expiration in ms of the RPDO. In mode PDO_ASYNC_FF additionally an event time can be used for TPDO. If an event timer exists for a TPDO (value not equal to 0) the elapsed timer in ms is considered to be an event (not implemented).

# struct `PDOMappingParameters` {#structezw_1_1smccore_1_1_i_communication_service_1_1_p_d_o_mapping_parameters}




Indicates the mapping parameters of a PDO.

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`public uint8_t nb` | 
`public std::vector< uint32_t > items` | 

## Members

### `public uint8_t nb` {#structezw_1_1smccore_1_1_i_communication_service_1_1_p_d_o_mapping_parameters_1a7a66630f9a38648d5556ced26065f809}



Indicates the number of mapped application objects in PDO.

### `public std::vector< uint32_t > items` {#structezw_1_1smccore_1_1_i_communication_service_1_1_p_d_o_mapping_parameters_1a02c6d99aba7220f86b5287412200cea9}



Indicates the mapped application objects in PDO : Index SubIndex Size (0x0 to inactive).

# struct `SDOCommunicationParameters` {#structezw_1_1smccore_1_1_i_communication_service_1_1_s_d_o_communication_parameters}




Indicates the SDO server communication parameters. NOTA :

* The SDO server 1 communication parameters are in read only mode.


* COB-ID of the SDO reception of the SDO 1 server is $NODEID+0x600.


* COB-ID of the SDO transmission of the SDO 1 server is $NODEID+0x580.


* Only static SDO connections are allowed (bit dyn 30 = 0).


* Static SDO connections are configured non-temporarily and may be saved in non-volatile memory.

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`public `[`COBID`](#structezw_1_1smccore_1_1_i_communication_service_1_1_c_o_b_i_d)` cob_id_client_to_server` | 
`public `[`COBID`](#structezw_1_1smccore_1_1_i_communication_service_1_1_c_o_b_i_d)` cob_id_server_to_client` | 

## Members

### `public `[`COBID`](#structezw_1_1smccore_1_1_i_communication_service_1_1_c_o_b_i_d)` cob_id_client_to_server` {#structezw_1_1smccore_1_1_i_communication_service_1_1_s_d_o_communication_parameters_1ae526e1e5012763eaa2343ece07026d86}



Indicates the configured COB-ID of the SDO reception.

### `public `[`COBID`](#structezw_1_1smccore_1_1_i_communication_service_1_1_c_o_b_i_d)` cob_id_server_to_client` {#structezw_1_1smccore_1_1_i_communication_service_1_1_s_d_o_communication_parameters_1ac596d8094110e7eb6ba69f7ef5a7047f}



Indicates the configured COB-ID of the SDO transmission.

# class `IManufacturerService` {#classezw_1_1smccore_1_1_i_manufacturer_service}


Manufacturer services.



## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`struct `[``DeviceParameters``](#structezw_1_1smccore_1_1_i_manufacturer_service_1_1_device_parameters)        | 
`struct `[``SWDParameters``](#structezw_1_1smccore_1_1_i_manufacturer_service_1_1_s_w_d_parameters)        | 
`public virtual  ~IManufacturerService() = default` | 
`public ezw_error_t getDeviceParameters(`[`DeviceParameters`](#structezw_1_1smccore_1_1_i_manufacturer_service_1_1_device_parameters)` & pParams) const` | Retrieve the device parameters.
`public ezw_error_t getSWDParameters(`[`SWDParameters`](#structezw_1_1smccore_1_1_i_manufacturer_service_1_1_s_w_d_parameters)` & pParams) const` | Retrieve the SWD product parameters.
`public ezw_error_t setSWDParameters(const `[`SWDParameters`](#structezw_1_1smccore_1_1_i_manufacturer_service_1_1_s_w_d_parameters)` & pParams)` | Modify the SWD product parameters. NOTA :
`public ezw_error_t getCalibrationValidity(bool & pIsvalid) const` | Retrieve the validity of the calibration in non volatile memory.
`public ezw_error_t getSystemErrorState(`[`SystemErrorStatus`](#classezw_1_1smccore_1_1_i_manufacturer_service_1a13173511214e6c9da5f9b35a3a32d942)` & pBatteryUv,`[`SystemErrorStatus`](#classezw_1_1smccore_1_1_i_manufacturer_service_1a13173511214e6c9da5f9b35a3a32d942)` & pBatteryOv,`[`SystemErrorStatus`](#classezw_1_1smccore_1_1_i_manufacturer_service_1a13173511214e6c9da5f9b35a3a32d942)` & pPhaseOc,`[`SystemErrorStatus`](#classezw_1_1smccore_1_1_i_manufacturer_service_1a13173511214e6c9da5f9b35a3a32d942)` & pMosOt,`[`SystemErrorStatus`](#classezw_1_1smccore_1_1_i_manufacturer_service_1a13173511214e6c9da5f9b35a3a32d942)` & pDrvOt) const` | Retrieve the system error states.
`public ezw_error_t getSystemErrorProtectState(`[`SystemErrorProtectState`](#classezw_1_1smccore_1_1_i_manufacturer_service_1aabb80375e9aecb3c95ca28144e82773b)` & pPrevState,`[`SystemErrorProtectState`](#classezw_1_1smccore_1_1_i_manufacturer_service_1aabb80375e9aecb3c95ca28144e82773b)` & pCurrentState) const` | Retrieve the system error protection state.
`public ezw_error_t getSWVersion(std::string & pSwVersion) const` | Retrieve the SWD product software version. Ex : 1.0.1.
`public ezw_error_t getSWId(uint8_t & pSwId) const` | Retrieve the SWD product software id. Ex : 2 NOTA [ FW_UNKNOWN = 0U FW_SWD_RECOVERY =1U FW_SWD_CORE = 2U FW_SWD_150 = 3U ... Maintenance = 255U ].
`public ezw_error_t getSWRef(std::string & pSoftwareRef) const` | Retrieve the SWD product software reference. Ex : FW_SWD_CORE.
`public ezw_error_t getHWVersion(uint32_t & pHwVersion) const` | Retrieve the SWD product hardware version. Ex : 5 NOTA [ 0 = Hardware version init 1 = A 2 = B 3 = C 4 = D 5 = E 6 = F 7 = G 8 = H 9 = I 10 = J ... ].
`public ezw_error_t getHWId(uint32_t & pHwId) const` | Retrieve the SWD product hardware id. Ex : 777 NOTA [ 727 = SWD150 777 = SWDCore or SWD125 ... ].
`public ezw_error_t getProductId(uint32_t & pProductId) const` | Retrieve the SWD product id. Ex : 15 NOTA [ NO_PRODUCT_REF = 0U ezSWD125IM.14/C = 1U ezSWD125IM.14B/C = 2U ezSWD125IM.25/C = 3U ezSWD125IM.25B/C = 4U ezSWD125IM.4/C = 5U ezSWD125IM.4B/C = 6U ... ezSWD150IH.14/C-0 = 7U ezSWD150IH.14/C-1 = 8U ezSWD150IH.14B/C-0 = 9U ezSWD150IH.14B/C-1 = 10U ezSWD150IH.25/C-0 = 11U ezSWD150IH.25/C-1 = 12U ezSWD150IH.25B/C-0 = 13U ezSWD150IH.25B/C-1 = 14U ... ezSWDcore.14/C = 15U ezSWDcore.14B/C = 16U ezSWDcore.25/C = 17U ezSWDcore.25B/C = 18U ezSWDcore.4/C = 19U ezSWDcore.4B/C = 20U ezSWDcore.0/C = 21U ... ].
`public ezw_error_t getProductRef(std::string & pProductRef) const` | Retrieve the SWD product reference. Ex : ezSWD125IM.14/C.
`public ezw_error_t getOdometryValue(int32_t & pOdometryValue) const` | Retrieve the position distance of the SWD product in mm. FORMULA : position_value / NbStepRevolutionElec / NbPolePair / Reduction x Diameter x M_PI NOTA : The previous parameters are defined into the configuration file. NOTA : The counter direction depends of the position polarity parameter. NOTA : The format of the configuration file is JSON ie. Nidec motor : "nbStepRevolutionElec": 6, "nbPolePair": 5, "reduction": 14.0, "diameter": 125.0.
`public ezw_error_t getOdometryValueTS(int32_t & pOdometryValue,uint64_t & pTimestamp) const` | Retrieve the position distance of the SWD product in mm. FORMULA : position_value / NbStepRevolutionElec / NbPolePair / Reduction x Diameter x M_PI NOTA : The previous parameters are defined into the configuration file. NOTA : The counter direction depends of the position polarity parameter. NOTA : The format of the configuration file is JSON ie. Nidec motor : "nbStepRevolutionElec": 6, "nbPolePair": 5, "reduction": 14.0, "diameter": 125.0.
`public ezw_error_t getAccurateOdometryValue(int32_t & pAccurateOdometryValue) const` | Retrieve a more precise position distance of the SWD product in mm at low level speed. (Warning : This position is non-safe. Safety relevant applications should rely with [getOdometryValue()](#classezw_1_1smccore_1_1_i_manufacturer_service_1ab9d669d77f99244bd66858844366a0c2)). FORMULA : accurate_position_value / Reduction x Diameter x M_PI NOTA : The previous parameters are defined into the configuration file. NOTA : The counter direction depends of the position polarity parameter. NOTA : The format of the configuration file is JSON ie. Nidec motor : "reduction": 14.0, "diameter": 125.0.
`public ezw_error_t getAccurateOdometryValueTS(int32_t & pAccurateOdometryValue,uint64_t & pTimestamp) const` | Retrieve a more precise position distance of the SWD product in mm at low level speed. (Warning : This position is non-safe. Safety relevant applications should rely with [getOdometryValue()](#classezw_1_1smccore_1_1_i_manufacturer_service_1ab9d669d77f99244bd66858844366a0c2)). FORMULA : accurate_position_value / Reduction x Diameter x M_PI NOTA : The previous parameters are defined into the configuration file. NOTA : The counter direction depends of the position polarity parameter. NOTA : The format of the configuration file is JSON ie. Nidec motor : "reduction": 14.0, "diameter": 125.0.
`public ezw_error_t getAccuratePositionValue(int32_t & pAccuratePositionValue) const` | Retrieve the precise multiturn position value, in units of motor mechanical degrees. NOTA : The counter direction depends of the position polarity parameter. NOTA : This position is non-safe and is for information only. Safety relevant applications should rely on safe object "0x6064: position_value".
`public ezw_error_t getAccuratePositionValueTS(int32_t & pAccuratePositionValue,uint64_t & pTimestamp) const` | Retrieve the precise multiturn position value, in units of motor mechanical degrees. NOTA : The counter direction depends of the position polarity parameter. NOTA : This position is non-safe and is for information only. Safety relevant applications should rely on safe object "0x6064: position_value".
`public ezw_error_t getOutputControl(const `[`OutputSource`](#classezw_1_1smccore_1_1_i_manufacturer_service_1a1dadc7a6f8e7fa1b8f3804185af6c854)` & pOutputSource,bool & pControl) const` | Retrieve the control value for an OutputSource NOTA : Value of 1 means OutputSource is active NOTA : Value of 0 means OutputSource is inactive NOTA : Value of control can be saved in EEPROM ( MANUFACTURER data ) NOTA : Value of control is applied immediately.
`public ezw_error_t setOutputControl(const `[`OutputSource`](#classezw_1_1smccore_1_1_i_manufacturer_service_1a1dadc7a6f8e7fa1b8f3804185af6c854)` & pOutputSource,const bool & pControl)` | Set the control value for an OutputSource NOTA : Value of 1 means OutputSource is active NOTA : Value of 0 means OutputSource is inactive NOTA : Value of control can be saved in EEPROM ( MANUFACTURER data ) NOTA : Value of control is applied immediately.
`public ezw_error_t getOutputStatus(const `[`OutputSource`](#classezw_1_1smccore_1_1_i_manufacturer_service_1a1dadc7a6f8e7fa1b8f3804185af6c854)` & pOutputSource,bool & pStatus) const` | Retrieve the status of an OutputSource NOTA : Value of 1 means OutputSource is active NOTA : Value of 0 means OutputSource is inactive.
`public ezw_error_t setExternalBrakePresence(const bool & pExternalbrakepresence)` | Modify the external brake presence flag. NOTA : Value of 1 means external brake is configured to be present. NOTA : Value of 0 means external brake is configured to be not present.
`public ezw_error_t getExternalBrakePresence(bool & pExternalbrakepresence) const` | Retrieve the external brake presence flag. NOTA : Value of 1 means external brake is configured to be present. NOTA : Value of 0 means external brake is configured to be not present.

## Members

### `struct `[``DeviceParameters``](#structezw_1_1smccore_1_1_i_manufacturer_service_1_1_device_parameters) {#structezw_1_1smccore_1_1_i_manufacturer_service_1_1_device_parameters}



Indicates the manufacturer device parameters.
### `struct `[``SWDParameters``](#structezw_1_1smccore_1_1_i_manufacturer_service_1_1_s_w_d_parameters) {#structezw_1_1smccore_1_1_i_manufacturer_service_1_1_s_w_d_parameters}



Indicates the configured SWD product parameters.
### `public virtual  ~IManufacturerService() = default` {#classezw_1_1smccore_1_1_i_manufacturer_service_1a1cf1ce3fc7d71a2aba528a981a0d3e9d}





### `public ezw_error_t getDeviceParameters(`[`DeviceParameters`](#structezw_1_1smccore_1_1_i_manufacturer_service_1_1_device_parameters)` & pParams) const` {#classezw_1_1smccore_1_1_i_manufacturer_service_1ab2a75eaeb56b3a18033bdb53328f233c}

Retrieve the device parameters.

#### Parameters
* `pParams` The device parameters. 





#### Returns
ERROR_NONE if no error occurred

### `public ezw_error_t getSWDParameters(`[`SWDParameters`](#structezw_1_1smccore_1_1_i_manufacturer_service_1_1_s_w_d_parameters)` & pParams) const` {#classezw_1_1smccore_1_1_i_manufacturer_service_1aba42eeb3d290cb81f9a6ec741850c9cc}

Retrieve the SWD product parameters.

#### Parameters
* `pParams` The SWD product parameters. 





#### Returns
ERROR_NONE if no error occurred

### `public ezw_error_t setSWDParameters(const `[`SWDParameters`](#structezw_1_1smccore_1_1_i_manufacturer_service_1_1_s_w_d_parameters)` & pParams)` {#classezw_1_1smccore_1_1_i_manufacturer_service_1a098bbfbfea8dfb8fa1c6208e6d501080}

Modify the SWD product parameters. NOTA :

* Changes will be applied at the next transition into OPERATION_ENABLED state.


* Storing is possible into the non-volatile memory (MANUFACTURER bloc).






#### Parameters
* `pParams` The new SWD product parameters. 





#### Returns
ERROR_NONE if no error occurred

### `public ezw_error_t getCalibrationValidity(bool & pIsvalid) const` {#classezw_1_1smccore_1_1_i_manufacturer_service_1ab282dadf30a7dcbe3daeb0bae6910072}

Retrieve the validity of the calibration in non volatile memory.

#### Parameters
* `pIsvalid` The calibration validity. 





#### Returns
ERROR_NONE if no error occurred

### `public ezw_error_t getSystemErrorState(`[`SystemErrorStatus`](#classezw_1_1smccore_1_1_i_manufacturer_service_1a13173511214e6c9da5f9b35a3a32d942)` & pBatteryUv,`[`SystemErrorStatus`](#classezw_1_1smccore_1_1_i_manufacturer_service_1a13173511214e6c9da5f9b35a3a32d942)` & pBatteryOv,`[`SystemErrorStatus`](#classezw_1_1smccore_1_1_i_manufacturer_service_1a13173511214e6c9da5f9b35a3a32d942)` & pPhaseOc,`[`SystemErrorStatus`](#classezw_1_1smccore_1_1_i_manufacturer_service_1a13173511214e6c9da5f9b35a3a32d942)` & pMosOt,`[`SystemErrorStatus`](#classezw_1_1smccore_1_1_i_manufacturer_service_1a13173511214e6c9da5f9b35a3a32d942)` & pDrvOt) const` {#classezw_1_1smccore_1_1_i_manufacturer_service_1aed9c47ddec77a1dff169894af16a4ef8}

Retrieve the system error states.

#### Parameters
* `pBatteryUv` Indicates the state of a battery under voltage. 


* `pBatteryOv` Indicates the state of a battery over voltage. 


* `pPhaseOc` Indicates the state of a phase over current. 


* `pMosOt` Indicates the state of a MOS over temperature. 


* `pDrvOt` Indicates the state of a driver over temperature. 





#### Returns
ERROR_NONE if no error occurred

### `public ezw_error_t getSystemErrorProtectState(`[`SystemErrorProtectState`](#classezw_1_1smccore_1_1_i_manufacturer_service_1aabb80375e9aecb3c95ca28144e82773b)` & pPrevState,`[`SystemErrorProtectState`](#classezw_1_1smccore_1_1_i_manufacturer_service_1aabb80375e9aecb3c95ca28144e82773b)` & pCurrentState) const` {#classezw_1_1smccore_1_1_i_manufacturer_service_1a6105445fdfd94883532d48ff00acd41d}

Retrieve the system error protection state.

#### Parameters
* `pPrevState` The previous system error protect state. 


* `pCurrentState` The actual system error protect state. 





#### Returns
ERROR_NONE if no error occurred

### `public ezw_error_t getSWVersion(std::string & pSwVersion) const` {#classezw_1_1smccore_1_1_i_manufacturer_service_1a317853ddf12b5d99bbabf442cb8733f7}

Retrieve the SWD product software version. Ex : 1.0.1.

#### Parameters
* `pSwVersion` The software version. 





#### Returns
ERROR_NONE if no error occurred

### `public ezw_error_t getSWId(uint8_t & pSwId) const` {#classezw_1_1smccore_1_1_i_manufacturer_service_1af4f092510a4414624751c7aa8d0cadeb}

Retrieve the SWD product software id. Ex : 2 NOTA [ FW_UNKNOWN = 0U FW_SWD_RECOVERY =1U FW_SWD_CORE = 2U FW_SWD_150 = 3U ... Maintenance = 255U ].

#### Parameters
* `pSwId` The software id. 





#### Returns
ERROR_NONE if no error occurred

### `public ezw_error_t getSWRef(std::string & pSoftwareRef) const` {#classezw_1_1smccore_1_1_i_manufacturer_service_1a5edda607b4a65c051c6908beb815d091}

Retrieve the SWD product software reference. Ex : FW_SWD_CORE.

#### Parameters
* `pSoftwareRef` The software reference. 





#### Returns
ERROR_NONE if no error occurred

### `public ezw_error_t getHWVersion(uint32_t & pHwVersion) const` {#classezw_1_1smccore_1_1_i_manufacturer_service_1a93b78465257313d984db06cd5c50360d}

Retrieve the SWD product hardware version. Ex : 5 NOTA [ 0 = Hardware version init 1 = A 2 = B 3 = C 4 = D 5 = E 6 = F 7 = G 8 = H 9 = I 10 = J ... ].

#### Parameters
* `pHwVersion` The hardware version. 





#### Returns
ERROR_NONE if no error occurred

### `public ezw_error_t getHWId(uint32_t & pHwId) const` {#classezw_1_1smccore_1_1_i_manufacturer_service_1ac05c02aaa2f82b1999b80945730c3312}

Retrieve the SWD product hardware id. Ex : 777 NOTA [ 727 = SWD150 777 = SWDCore or SWD125 ... ].

#### Parameters
* `pHwId` The hardware id. 





#### Returns
ERROR_NONE if no error occurred

### `public ezw_error_t getProductId(uint32_t & pProductId) const` {#classezw_1_1smccore_1_1_i_manufacturer_service_1a3c7ec6b2cacb190b11f9d09c5650c145}

Retrieve the SWD product id. Ex : 15 NOTA [ NO_PRODUCT_REF = 0U ezSWD125IM.14/C = 1U ezSWD125IM.14B/C = 2U ezSWD125IM.25/C = 3U ezSWD125IM.25B/C = 4U ezSWD125IM.4/C = 5U ezSWD125IM.4B/C = 6U ... ezSWD150IH.14/C-0 = 7U ezSWD150IH.14/C-1 = 8U ezSWD150IH.14B/C-0 = 9U ezSWD150IH.14B/C-1 = 10U ezSWD150IH.25/C-0 = 11U ezSWD150IH.25/C-1 = 12U ezSWD150IH.25B/C-0 = 13U ezSWD150IH.25B/C-1 = 14U ... ezSWDcore.14/C = 15U ezSWDcore.14B/C = 16U ezSWDcore.25/C = 17U ezSWDcore.25B/C = 18U ezSWDcore.4/C = 19U ezSWDcore.4B/C = 20U ezSWDcore.0/C = 21U ... ].

#### Parameters
* `pProductId` The product id. 





#### Returns
ERROR_NONE if no error occurred

### `public ezw_error_t getProductRef(std::string & pProductRef) const` {#classezw_1_1smccore_1_1_i_manufacturer_service_1af0cfa86a4dac73674f6653a63b0cae1e}

Retrieve the SWD product reference. Ex : ezSWD125IM.14/C.

#### Parameters
* `pProductRef` The product reference. 





#### Returns
ERROR_NONE if no error occurred

### `public ezw_error_t getOdometryValue(int32_t & pOdometryValue) const` {#classezw_1_1smccore_1_1_i_manufacturer_service_1ab9d669d77f99244bd66858844366a0c2}

Retrieve the position distance of the SWD product in mm. FORMULA : position_value / NbStepRevolutionElec / NbPolePair / Reduction x Diameter x M_PI NOTA : The previous parameters are defined into the configuration file. NOTA : The counter direction depends of the position polarity parameter. NOTA : The format of the configuration file is JSON ie. Nidec motor : "nbStepRevolutionElec": 6, "nbPolePair": 5, "reduction": 14.0, "diameter": 125.0.

#### Parameters
* `pOdometryValue` The position distance of the SWD Core in mm. 





#### Returns
ERROR_NONE if no error occurred

### `public ezw_error_t getOdometryValueTS(int32_t & pOdometryValue,uint64_t & pTimestamp) const` {#classezw_1_1smccore_1_1_i_manufacturer_service_1a6baffc87d4e491a78a1a2af0767f01a0}

Retrieve the position distance of the SWD product in mm. FORMULA : position_value / NbStepRevolutionElec / NbPolePair / Reduction x Diameter x M_PI NOTA : The previous parameters are defined into the configuration file. NOTA : The counter direction depends of the position polarity parameter. NOTA : The format of the configuration file is JSON ie. Nidec motor : "nbStepRevolutionElec": 6, "nbPolePair": 5, "reduction": 14.0, "diameter": 125.0.

#### Parameters
* `pOdometryValue` The position distance of the SWD product in mm. 


* `pTimestamp` The timestamp in microseconds (Unix epoch time from 1 January 1970). 





#### Returns
ERROR_NONE if no error occurred

### `public ezw_error_t getAccurateOdometryValue(int32_t & pAccurateOdometryValue) const` {#classezw_1_1smccore_1_1_i_manufacturer_service_1ae9b3bd1ace7020147fa610568be026c4}

Retrieve a more precise position distance of the SWD product in mm at low level speed. (Warning : This position is non-safe. Safety relevant applications should rely with [getOdometryValue()](#classezw_1_1smccore_1_1_i_manufacturer_service_1ab9d669d77f99244bd66858844366a0c2)). FORMULA : accurate_position_value / Reduction x Diameter x M_PI NOTA : The previous parameters are defined into the configuration file. NOTA : The counter direction depends of the position polarity parameter. NOTA : The format of the configuration file is JSON ie. Nidec motor : "reduction": 14.0, "diameter": 125.0.

#### Parameters
* `pAccurateOdometryValue` The accurate position distance of the SWD product in mm. 





#### Returns
ERROR_NONE if no error occurred

### `public ezw_error_t getAccurateOdometryValueTS(int32_t & pAccurateOdometryValue,uint64_t & pTimestamp) const` {#classezw_1_1smccore_1_1_i_manufacturer_service_1a518c080c0fba333f27c7dcf181095c02}

Retrieve a more precise position distance of the SWD product in mm at low level speed. (Warning : This position is non-safe. Safety relevant applications should rely with [getOdometryValue()](#classezw_1_1smccore_1_1_i_manufacturer_service_1ab9d669d77f99244bd66858844366a0c2)). FORMULA : accurate_position_value / Reduction x Diameter x M_PI NOTA : The previous parameters are defined into the configuration file. NOTA : The counter direction depends of the position polarity parameter. NOTA : The format of the configuration file is JSON ie. Nidec motor : "reduction": 14.0, "diameter": 125.0.

#### Parameters
* `pAccurateOdometryValue` The accurate position distance of the SWD product in mm. 


* `pTimestamp` The timestamp in microseconds (Unix epoch time from 1 January 1970). 





#### Returns
ERROR_NONE if no error occurred

### `public ezw_error_t getAccuratePositionValue(int32_t & pAccuratePositionValue) const` {#classezw_1_1smccore_1_1_i_manufacturer_service_1a272516d52491828fce73065405b05e27}

Retrieve the precise multiturn position value, in units of motor mechanical degrees. NOTA : The counter direction depends of the position polarity parameter. NOTA : This position is non-safe and is for information only. Safety relevant applications should rely on safe object "0x6064: position_value".

#### Parameters
* `pAccuratePositionValue` The precise multiturn position value, in units of motor mechanical degrees. 





#### Returns
ERROR_NONE if no error occurred

### `public ezw_error_t getAccuratePositionValueTS(int32_t & pAccuratePositionValue,uint64_t & pTimestamp) const` {#classezw_1_1smccore_1_1_i_manufacturer_service_1a99a84aa9a7d37c602274255ddaec6d58}

Retrieve the precise multiturn position value, in units of motor mechanical degrees. NOTA : The counter direction depends of the position polarity parameter. NOTA : This position is non-safe and is for information only. Safety relevant applications should rely on safe object "0x6064: position_value".

#### Parameters
* `pAccuratePositionValue` The precise multiturn position value, in units of motor mechanical degrees. 


* `pTimestamp` The timestamp in ms from 1970. 





#### Returns
ERROR_NONE if no error occurred

### `public ezw_error_t getOutputControl(const `[`OutputSource`](#classezw_1_1smccore_1_1_i_manufacturer_service_1a1dadc7a6f8e7fa1b8f3804185af6c854)` & pOutputSource,bool & pControl) const` {#classezw_1_1smccore_1_1_i_manufacturer_service_1a77d860d35d429dfd6a7624aa62465362}

Retrieve the control value for an OutputSource NOTA : Value of 1 means OutputSource is active NOTA : Value of 0 means OutputSource is inactive NOTA : Value of control can be saved in EEPROM ( MANUFACTURER data ) NOTA : Value of control is applied immediately.

#### Parameters
* `pOutputSource` which OutputSource control you want to get. 


* `pControl` control for the OutputSource : 1 OutputSource is active, 0 OutputSource is inactive 





#### Returns
ERROR_NONE if no error occurred

### `public ezw_error_t setOutputControl(const `[`OutputSource`](#classezw_1_1smccore_1_1_i_manufacturer_service_1a1dadc7a6f8e7fa1b8f3804185af6c854)` & pOutputSource,const bool & pControl)` {#classezw_1_1smccore_1_1_i_manufacturer_service_1ae857e19dd2d8955d07be8f81c42a2ee0}

Set the control value for an OutputSource NOTA : Value of 1 means OutputSource is active NOTA : Value of 0 means OutputSource is inactive NOTA : Value of control can be saved in EEPROM ( MANUFACTURER data ) NOTA : Value of control is applied immediately.

#### Parameters
* `pOutputSource` which OutputSource control you want to set. 


* `pControl` control for the OutputSource : 1 OutputSource is active, 0 OutputSource is inactive 





#### Returns
ERROR_NONE if no error occurred

### `public ezw_error_t getOutputStatus(const `[`OutputSource`](#classezw_1_1smccore_1_1_i_manufacturer_service_1a1dadc7a6f8e7fa1b8f3804185af6c854)` & pOutputSource,bool & pStatus) const` {#classezw_1_1smccore_1_1_i_manufacturer_service_1a0c745138782577158a40e84b7d3f9501}

Retrieve the status of an OutputSource NOTA : Value of 1 means OutputSource is active NOTA : Value of 0 means OutputSource is inactive.

#### Parameters
* `pOutputSource` which OutputSource status you want to get. 


* `pStatus` The status of OutputSource. 





#### Returns
ERROR_NONE if no error occurred

### `public ezw_error_t setExternalBrakePresence(const bool & pExternalbrakepresence)` {#classezw_1_1smccore_1_1_i_manufacturer_service_1a0ae9e5f29758b69d977e8396fb9534c2}

Modify the external brake presence flag. NOTA : Value of 1 means external brake is configured to be present. NOTA : Value of 0 means external brake is configured to be not present.

#### Parameters
* `pExternalbrakepresence` The external brake presence flag. 





#### Returns
ERROR_NONE if no error occurred

### `public ezw_error_t getExternalBrakePresence(bool & pExternalbrakepresence) const` {#classezw_1_1smccore_1_1_i_manufacturer_service_1acf5b9d40ad30956fd98e04336130424d}

Retrieve the external brake presence flag. NOTA : Value of 1 means external brake is configured to be present. NOTA : Value of 0 means external brake is configured to be not present.

#### Parameters
* `pExternalbrakepresence` The external brake presence flag. 





#### Returns
ERROR_NONE if no error occurred

# struct `DeviceParameters` {#structezw_1_1smccore_1_1_i_manufacturer_service_1_1_device_parameters}




Indicates the manufacturer device parameters.

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`public std::string manufacturer_device_name` | 
`public std::string hardware_version_description` | 
`public std::string manufacturer_software_version` | 

## Members

### `public std::string manufacturer_device_name` {#structezw_1_1smccore_1_1_i_manufacturer_service_1_1_device_parameters_1a9f7f53665c0172fa5f6bdeeed25cdcb3}



The device name.

### `public std::string hardware_version_description` {#structezw_1_1smccore_1_1_i_manufacturer_service_1_1_device_parameters_1ad75087273e5a9c0e319385cf7bfc805a}



The hardware version description.

### `public std::string manufacturer_software_version` {#structezw_1_1smccore_1_1_i_manufacturer_service_1_1_device_parameters_1a31449c5ed1bda7179ac89b19e4b3dc8f}



The software version description.

# struct `SWDParameters` {#structezw_1_1smccore_1_1_i_manufacturer_service_1_1_s_w_d_parameters}




Indicates the configured SWD product parameters.

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`public uint32_t motctrl_speed_pid_p` | 
`public uint32_t motctrl_speed_pid_i` | 
`public uint32_t motctrl_speed_pid_d` | 
`public uint32_t motctrl_speed_pid_tw` | 
`public uint32_t motctrl_speed_pid_tn` | 

## Members

### `public uint32_t motctrl_speed_pid_p` {#structezw_1_1smccore_1_1_i_manufacturer_service_1_1_s_w_d_parameters_1a4e01c287186848b980cdcfd57d1b8d6d}



The proportional parameter (mdeg.s-1) of the speed motor control bloc. Default : 200.

### `public uint32_t motctrl_speed_pid_i` {#structezw_1_1smccore_1_1_i_manufacturer_service_1_1_s_w_d_parameters_1ac0f0c27a3b8007e6500e1ae905842e4a}



The integral parameter (mdeg.s-1) of the speed motor control bloc. Default : 10.

### `public uint32_t motctrl_speed_pid_d` {#structezw_1_1smccore_1_1_i_manufacturer_service_1_1_s_w_d_parameters_1ab3396f6d067efc1c51f9b0a9ac5b2720}



The derivative parameter (mdeg.s-1) of the speed motor control bloc. Default : 0.

### `public uint32_t motctrl_speed_pid_tw` {#structezw_1_1smccore_1_1_i_manufacturer_service_1_1_s_w_d_parameters_1a80e06795f382a0db7d70da0d4e1e3672}



The integral anti-windup time constant parameter (ms) of the speed motor control bloc. Default : 316.

### `public uint32_t motctrl_speed_pid_tn` {#structezw_1_1smccore_1_1_i_manufacturer_service_1_1_s_w_d_parameters_1a8cf8f17cebb04ffa38990b5c8f39dbe3}



The derivative filter time constant parameter (ms) of the speed motor control bloc. Default : 300.

# class `ICANOpenService` {#classezw_1_1smccore_1_1_i_c_a_n_open_service}


CANopen object dictionary services.



## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`public virtual  ~ICANOpenService() = default` | 
`public ezw_error_t getValueString(const uint32_t & pAddress,std::string & pData) const` | Retrieve the value of the specified object address for a type string.
`public ezw_error_t setValueString(const uint32_t & pAddress,const std::string & pData)` | Modify the value of the specified object address for a type string.
`public ezw_error_t getValueInt64(const uint32_t & pAddress,int64_t & pData) const` | Retrieve the value of the specified object address for a type int64.
`public ezw_error_t setValueInt64(const uint32_t & pAddress,const int64_t & pData)` | Modify the value of the specified object address for a type int64.
`public ezw_error_t getValueInt32(const uint32_t & pAddress,int32_t & pData) const` | Retrieve the value of the specified object address for a type int32.
`public ezw_error_t setValueInt32(const uint32_t & pAddress,const int32_t & pData)` | Modify the value of the specified object address for a type int32.
`public ezw_error_t getValueInt16(const uint32_t & pAddress,int16_t & pData) const` | Retrieve the value of the specified object address for a type int16.
`public ezw_error_t setValueInt16(const uint32_t & pAddress,const int16_t & pData)` | Modify the value of the specified object address for a type int16.
`public ezw_error_t getValueInt8(const uint32_t & pAddress,int8_t & pData) const` | Retrieve the value of the specified object address for a type int8.
`public ezw_error_t setValueInt8(const uint32_t & pAddress,const int8_t & pData)` | Modify the value of the specified object address for a type int8.
`public ezw_error_t getValueUInt64(const uint32_t & pAddress,uint64_t & pData) const` | Retrieve the value of the specified object address for a type uint64.
`public ezw_error_t setValueUInt64(const uint32_t & pAddress,const uint64_t & pData)` | Modify the value of the specified object address for a type uint64.
`public ezw_error_t getValueUInt32(const uint32_t & pAddress,uint32_t & pData) const` | Retrieve the value of the specified object address for a type uint32.
`public ezw_error_t setValueUInt32(const uint32_t & pAddress,const uint32_t & pData)` | Modify the value of the specified object address for a type uint32.
`public ezw_error_t getValueUInt16(const uint32_t & pAddress,uint16_t & pData) const` | Retrieve the value of the specified object address for a type uint16.
`public ezw_error_t setValueUInt16(const uint32_t & pAddress,const uint16_t & pData)` | Modify the value of the specified object address for a type uint16.
`public ezw_error_t getValueUInt8(const uint32_t & pAddress,uint8_t & pData) const` | Retrieve the value of the specified object address for a type uint8.
`public ezw_error_t setValueUInt8(const uint32_t & pAddress,const uint8_t & pData)` | Modify the value of the specified object address for a type uint8.
`public ezw_error_t getValueFloat(const uint32_t & pAddress,float & pData) const` | Retrieve the value of the specified object address for a type float.
`public ezw_error_t setValueFloat(const uint32_t & pAddress,const float & pData)` | Modify the value of the specified object address for a type float.
`public ezw_error_t getValueDouble(const uint32_t & pAddress,double & pData) const` | Retrieve the value of the specified object address for a type double.
`public ezw_error_t setValueDouble(const uint32_t & pAddress,const double & pData)` | Modify the value of the specified object address for a type double.
`public ezw_error_t getValueBool(const uint32_t & pAddress,bool & pData) const` | Retrieve the value of the specified object address for a type boolean.
`public ezw_error_t setValueBool(const uint32_t & pAddress,const bool & pData)` | Modify the value of the specified object address for a type boolean.

## Members

### `public virtual  ~ICANOpenService() = default` {#classezw_1_1smccore_1_1_i_c_a_n_open_service_1a86600da0233b548acee37ceda92ad66b}





### `public ezw_error_t getValueString(const uint32_t & pAddress,std::string & pData) const` {#classezw_1_1smccore_1_1_i_c_a_n_open_service_1ac0571f86b858ca053d5cf55566fc1616}

Retrieve the value of the specified object address for a type string.

#### Parameters
* `pAddress` The object address. 


* `pData` The object value. 





#### Returns
ERROR_NONE if no error occurred

### `public ezw_error_t setValueString(const uint32_t & pAddress,const std::string & pData)` {#classezw_1_1smccore_1_1_i_c_a_n_open_service_1a9bc60e06912e0da6957ec6521aa49d03}

Modify the value of the specified object address for a type string.

#### Parameters
* `pAddress` The object address. 


* `pData` The object value. 





#### Returns
ERROR_NONE if no error occurred

### `public ezw_error_t getValueInt64(const uint32_t & pAddress,int64_t & pData) const` {#classezw_1_1smccore_1_1_i_c_a_n_open_service_1a41e7ad6a8355e7553e8a937291bf1bf4}

Retrieve the value of the specified object address for a type int64.

#### Parameters
* `pAddress` The object address. 


* `pData` The object value. 





#### Returns
ERROR_NONE if no error occurred

### `public ezw_error_t setValueInt64(const uint32_t & pAddress,const int64_t & pData)` {#classezw_1_1smccore_1_1_i_c_a_n_open_service_1a3fed01f830377c0cd510d567ceae568a}

Modify the value of the specified object address for a type int64.

#### Parameters
* `pAddress` The object address. 


* `pData` The object value. 





#### Returns
ERROR_NONE if no error occurred

### `public ezw_error_t getValueInt32(const uint32_t & pAddress,int32_t & pData) const` {#classezw_1_1smccore_1_1_i_c_a_n_open_service_1a6f62aa3538771d476e4aee79c541155d}

Retrieve the value of the specified object address for a type int32.

#### Parameters
* `pAddress` The object address. 


* `pData` The object value. 





#### Returns
ERROR_NONE if no error occurred

### `public ezw_error_t setValueInt32(const uint32_t & pAddress,const int32_t & pData)` {#classezw_1_1smccore_1_1_i_c_a_n_open_service_1ae8137cf316002a82c090689e189953c6}

Modify the value of the specified object address for a type int32.

#### Parameters
* `pAddress` The object address. 


* `pData` The object value. 





#### Returns
ERROR_NONE if no error occurred

### `public ezw_error_t getValueInt16(const uint32_t & pAddress,int16_t & pData) const` {#classezw_1_1smccore_1_1_i_c_a_n_open_service_1a07435e102ec1acde341dfa6f0f603f68}

Retrieve the value of the specified object address for a type int16.

#### Parameters
* `pAddress` The object address. 


* `pData` The object value. 





#### Returns
ERROR_NONE if no error occurred

### `public ezw_error_t setValueInt16(const uint32_t & pAddress,const int16_t & pData)` {#classezw_1_1smccore_1_1_i_c_a_n_open_service_1a645088c230a1f487561ca089c14da1e9}

Modify the value of the specified object address for a type int16.

#### Parameters
* `pAddress` The object address. 


* `pData` The object value. 





#### Returns
ERROR_NONE if no error occurred

### `public ezw_error_t getValueInt8(const uint32_t & pAddress,int8_t & pData) const` {#classezw_1_1smccore_1_1_i_c_a_n_open_service_1a8ec2af47b51477805249fe1f898474d7}

Retrieve the value of the specified object address for a type int8.

#### Parameters
* `pAddress` The object address. 


* `pData` The object value. 





#### Returns
ERROR_NONE if no error occurred

### `public ezw_error_t setValueInt8(const uint32_t & pAddress,const int8_t & pData)` {#classezw_1_1smccore_1_1_i_c_a_n_open_service_1aa7a8b012f4ec01e55edf35803b152f9d}

Modify the value of the specified object address for a type int8.

#### Parameters
* `pAddress` The object address. 


* `pData` The object value. 





#### Returns
ERROR_NONE if no error occurred

### `public ezw_error_t getValueUInt64(const uint32_t & pAddress,uint64_t & pData) const` {#classezw_1_1smccore_1_1_i_c_a_n_open_service_1a4eb73d51f66660d5554bbe0acc530cc3}

Retrieve the value of the specified object address for a type uint64.

#### Parameters
* `pAddress` The object address. 


* `pData` The object value. 





#### Returns
ERROR_NONE if no error occurred

### `public ezw_error_t setValueUInt64(const uint32_t & pAddress,const uint64_t & pData)` {#classezw_1_1smccore_1_1_i_c_a_n_open_service_1a566e774fed86cc8fa903998ef6250a27}

Modify the value of the specified object address for a type uint64.

#### Parameters
* `pAddress` The object address. 


* `pData` The object value. 





#### Returns
ERROR_NONE if no error occurred

### `public ezw_error_t getValueUInt32(const uint32_t & pAddress,uint32_t & pData) const` {#classezw_1_1smccore_1_1_i_c_a_n_open_service_1af9d0ce931c58e8a7902480e5720f5aa0}

Retrieve the value of the specified object address for a type uint32.

#### Parameters
* `pAddress` The object address. 


* `pData` The object value. 





#### Returns
ERROR_NONE if no error occurred

### `public ezw_error_t setValueUInt32(const uint32_t & pAddress,const uint32_t & pData)` {#classezw_1_1smccore_1_1_i_c_a_n_open_service_1a170559c65d5d3f6bf88a34e5b157bb83}

Modify the value of the specified object address for a type uint32.

#### Parameters
* `pAddress` The object address. 


* `pData` The object value. 





#### Returns
ERROR_NONE if no error occurred

### `public ezw_error_t getValueUInt16(const uint32_t & pAddress,uint16_t & pData) const` {#classezw_1_1smccore_1_1_i_c_a_n_open_service_1abbd10f4c18a1e3ca1207998bcd713adb}

Retrieve the value of the specified object address for a type uint16.

#### Parameters
* `pAddress` The object address. 


* `pData` The object value. 





#### Returns
ERROR_NONE if no error occurred

### `public ezw_error_t setValueUInt16(const uint32_t & pAddress,const uint16_t & pData)` {#classezw_1_1smccore_1_1_i_c_a_n_open_service_1a9f8579f6b0bee8ba8867a38f1a1187d2}

Modify the value of the specified object address for a type uint16.

#### Parameters
* `pAddress` The object address. 


* `pData` The object value. 





#### Returns
ERROR_NONE if no error occurred

### `public ezw_error_t getValueUInt8(const uint32_t & pAddress,uint8_t & pData) const` {#classezw_1_1smccore_1_1_i_c_a_n_open_service_1a676593b9f8f5fff6038d22b68322fee7}

Retrieve the value of the specified object address for a type uint8.

#### Parameters
* `pAddress` The object address. 


* `pData` The object value. 





#### Returns
ERROR_NONE if no error occurred

### `public ezw_error_t setValueUInt8(const uint32_t & pAddress,const uint8_t & pData)` {#classezw_1_1smccore_1_1_i_c_a_n_open_service_1a9e910e72dd9c5661ac506c004733710e}

Modify the value of the specified object address for a type uint8.

#### Parameters
* `pAddress` The object address. 


* `pData` The object value. 





#### Returns
ERROR_NONE if no error occurred

### `public ezw_error_t getValueFloat(const uint32_t & pAddress,float & pData) const` {#classezw_1_1smccore_1_1_i_c_a_n_open_service_1a6a5aa7313ef8a7e057c1bf0ff9dfa89e}

Retrieve the value of the specified object address for a type float.

#### Parameters
* `pAddress` The object address. 


* `pData` The object value. 





#### Returns
ERROR_NONE if no error occurred

### `public ezw_error_t setValueFloat(const uint32_t & pAddress,const float & pData)` {#classezw_1_1smccore_1_1_i_c_a_n_open_service_1acf9cd4f1839b652758ad31124cd03751}

Modify the value of the specified object address for a type float.

#### Parameters
* `pAddress` The object address. 


* `pData` The object value. 





#### Returns
ERROR_NONE if no error occurred

### `public ezw_error_t getValueDouble(const uint32_t & pAddress,double & pData) const` {#classezw_1_1smccore_1_1_i_c_a_n_open_service_1a631c6f66cdfe5f23c7b1870164fe15dd}

Retrieve the value of the specified object address for a type double.

#### Parameters
* `pAddress` The object address. 


* `pData` The object value. 





#### Returns
ERROR_NONE if no error occurred

### `public ezw_error_t setValueDouble(const uint32_t & pAddress,const double & pData)` {#classezw_1_1smccore_1_1_i_c_a_n_open_service_1acc3d155af073235a46199b41b6c9b73e}

Modify the value of the specified object address for a type double.

#### Parameters
* `pAddress` The object address. 


* `pData` The object value. 





#### Returns
ERROR_NONE if no error occurred

### `public ezw_error_t getValueBool(const uint32_t & pAddress,bool & pData) const` {#classezw_1_1smccore_1_1_i_c_a_n_open_service_1ad5711063de179b846a5671fec795ea82}

Retrieve the value of the specified object address for a type boolean.

#### Parameters
* `pAddress` The object address. 


* `pData` The object value. 





#### Returns
ERROR_NONE if no error occurred

### `public ezw_error_t setValueBool(const uint32_t & pAddress,const bool & pData)` {#classezw_1_1smccore_1_1_i_c_a_n_open_service_1a2ce5d0e2bec07948e0e788cf38e7f9b9}

Modify the value of the specified object address for a type boolean.

#### Parameters
* `pAddress` The object address. 


* `pData` The object value. 





#### Returns
ERROR_NONE if no error occurred

# class `ICoreService` {#classezw_1_1smccore_1_1_i_core_service}


SWD product services.



## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`public virtual  ~ICoreService() = default` | 
`public ezw_error_t connect(const uint8_t & pNodeId)` | Connect to the canopen device with the node id specifed.
`public ezw_error_t disconnect()` | Disconnect from the canopen device.
`public ezw_error_t getConnectionStatus(bool & pIsConnected,bool & pIsPdoInitSucceeded)` | Retrieve the core status connection.
`public ezw_error_t getConnectedNodeId(uint8_t & pNodeId)` | Get the connected node id.
`public ezw_error_t getCanDevice(std::string & pCanDevice)` | Get the CAN device.
`public ezw_error_t getCoreVersion(std::string & pCoreVersion)` | Retrieve the SWD core services version. Ex : 0.2.8.
`public ezw_error_t switchMode(const `[`ModeEnum`](#classezw_1_1smccore_1_1_i_core_service_1a2dd9abb99fbe514c13af3ab5993e173f)` & pMode)` | Switch into the specified canopen object dictionary mode.
`public ezw_error_t loadSettingsFromDCF(const std::string & pDcfFile)` | Load settings from DCF file.
`public ezw_error_t saveSettingsToDCF(const std::string & pDcfFile)` | Save settings to DCF file.
`public ezw_error_t loadSettingsFromDevice()` | Load settings from the device.
`public ezw_error_t saveSettingsToDevice()` | Save settings to the device.

## Members

### `public virtual  ~ICoreService() = default` {#classezw_1_1smccore_1_1_i_core_service_1a9f9459eaa81ea165b613ed94c9a52eb9}





### `public ezw_error_t connect(const uint8_t & pNodeId)` {#classezw_1_1smccore_1_1_i_core_service_1a69d1380055c56c8871424767d424b15a}

Connect to the canopen device with the node id specifed.

#### Parameters
* `pNodeId` The node id of the device : from 1 to 127. 





#### Returns
ERROR_NONE if no error occurred

### `public ezw_error_t disconnect()` {#classezw_1_1smccore_1_1_i_core_service_1a9def19a4f5917c864992421eda49380d}

Disconnect from the canopen device.

#### Returns
ERROR_NONE if no error occurred

### `public ezw_error_t getConnectionStatus(bool & pIsConnected,bool & pIsPdoInitSucceeded)` {#classezw_1_1smccore_1_1_i_core_service_1a098dc40295e851d108ee0870903deca1}

Retrieve the core status connection.

#### Parameters
* `pIsConnected` The connection status. 


* `pIsPdoInitSucceeded` The PDO status. 





#### Returns
ERROR_NONE if no error occurred

### `public ezw_error_t getConnectedNodeId(uint8_t & pNodeId)` {#classezw_1_1smccore_1_1_i_core_service_1a0097425817a441da52a9b5037ba705ea}

Get the connected node id.

#### Parameters
* `pNodeId` The node id of the connected device : from 1 to 127. 





#### Returns
ERROR_NONE if no error occurred

### `public ezw_error_t getCanDevice(std::string & pCanDevice)` {#classezw_1_1smccore_1_1_i_core_service_1a8b77050645f3eb552ea21241d979d1a2}

Get the CAN device.

#### Parameters
* `pCanDevice` The CAN device. (ie "can0") 





#### Returns
ERROR_NONE if no error occurred

### `public ezw_error_t getCoreVersion(std::string & pCoreVersion)` {#classezw_1_1smccore_1_1_i_core_service_1a5ce7796af51ca1c5414f7e73a245f76f}

Retrieve the SWD core services version. Ex : 0.2.8.

#### Parameters
* `pCoreVersion` The core version. 





#### Returns
ERROR_NONE if no error occurred

### `public ezw_error_t switchMode(const `[`ModeEnum`](#classezw_1_1smccore_1_1_i_core_service_1a2dd9abb99fbe514c13af3ab5993e173f)` & pMode)` {#classezw_1_1smccore_1_1_i_core_service_1a1bcddb8e11fcd02e1a2f1b72bccb573b}

Switch into the specified canopen object dictionary mode.

#### Parameters
* `pMode` The new mode. 





#### Returns
ERROR_NONE if no error occurred

### `public ezw_error_t loadSettingsFromDCF(const std::string & pDcfFile)` {#classezw_1_1smccore_1_1_i_core_service_1a720813154fbad2e21d4ee1a57986b071}

Load settings from DCF file.

#### Parameters
* `pDcfFile` Indicates the DCF file. 





#### Returns
ERROR_NONE if no error occurred

### `public ezw_error_t saveSettingsToDCF(const std::string & pDcfFile)` {#classezw_1_1smccore_1_1_i_core_service_1a84b06cab732cd87de969a2e68e1ed909}

Save settings to DCF file.

#### Parameters
* `pDcfFile` Indicates the DCF file. 





#### Returns
ERROR_NONE if no error occurred

### `public ezw_error_t loadSettingsFromDevice()` {#classezw_1_1smccore_1_1_i_core_service_1a330f08b61590726caab545478e6ef9c9}

Load settings from the device.

#### Returns
ERROR_NONE if no error occurred

### `public ezw_error_t saveSettingsToDevice()` {#classezw_1_1smccore_1_1_i_core_service_1a0e7ee9a7155cf39dfdb0227315f745ad}

Save settings to the device.

#### Returns
ERROR_NONE if no error occurred

# class `IEMCYService` {#classezw_1_1smccore_1_1_i_e_m_c_y_service}


Emergency ( EMCY ) functionalities.



## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`public virtual  ~IEMCYService() = default` | 
`public ezw_error_t getErrorBehavior(const `[`ErrorType`](#classezw_1_1smccore_1_1_i_e_m_c_y_service_1ab0df38968e4f03a3f1f6d6df0f31f45a)` & pErrorType,`[`ErrorBehavior`](#classezw_1_1smccore_1_1_i_e_m_c_y_service_1a54c3d982e7be3c196e8a0907b69ac57e)` & pErrorBehavior) const` | Retrieve the ErrorBehavior of selected ErrorType.
`public ezw_error_t setErrorBehavior(const `[`ErrorType`](#classezw_1_1smccore_1_1_i_e_m_c_y_service_1ab0df38968e4f03a3f1f6d6df0f31f45a)` & pErrorType,const `[`ErrorBehavior`](#classezw_1_1smccore_1_1_i_e_m_c_y_service_1a54c3d982e7be3c196e8a0907b69ac57e)` & pErrorBehavior)` | Set the ErrorBehavior of selected ErrorType.
`public ezw_error_t clearErrorList()` | Clear all previous error stored in the pre-defined error array.
`public ezw_error_t getErrorCount(int32_t & pErrorCount) const` | Return the number of error present in the pre-defined error array.
`public ezw_error_t getErrorRegister(uint8_t & pErrorRegister) const` | Return error register. Error Register is made of 8 bits indicating the type of error that happend:
`public ezw_error_t getError(const int32_t & pIndex,uint32_t & pEmcyErrorCode) const` | Return EMCY_ERROR_CODE (as UInt32) at index in the pre-defined error array.

## Members

### `public virtual  ~IEMCYService() = default` {#classezw_1_1smccore_1_1_i_e_m_c_y_service_1a5fcaa045b653bd79c692cf52739cd847}





### `public ezw_error_t getErrorBehavior(const `[`ErrorType`](#classezw_1_1smccore_1_1_i_e_m_c_y_service_1ab0df38968e4f03a3f1f6d6df0f31f45a)` & pErrorType,`[`ErrorBehavior`](#classezw_1_1smccore_1_1_i_e_m_c_y_service_1a54c3d982e7be3c196e8a0907b69ac57e)` & pErrorBehavior) const` {#classezw_1_1smccore_1_1_i_e_m_c_y_service_1aabe1282bf5c87e3ce9100271d3cbfd5c}

Retrieve the ErrorBehavior of selected ErrorType.

#### Parameters
* `pErrorType` Selected ErrorType. 


* `pErrorBehavior` ErrorBehavior of selected ErrorType. 





#### Returns
ERROR_NONE if no error occurred

### `public ezw_error_t setErrorBehavior(const `[`ErrorType`](#classezw_1_1smccore_1_1_i_e_m_c_y_service_1ab0df38968e4f03a3f1f6d6df0f31f45a)` & pErrorType,const `[`ErrorBehavior`](#classezw_1_1smccore_1_1_i_e_m_c_y_service_1a54c3d982e7be3c196e8a0907b69ac57e)` & pErrorBehavior)` {#classezw_1_1smccore_1_1_i_e_m_c_y_service_1aeac4828727d2855ab4a5d462987cf7b4}

Set the ErrorBehavior of selected ErrorType.

#### Parameters
* `pErrorType` Selected ErrorType. 


* `pErrorBehavior` ErrorBehavior of selected ErrorType. 





#### Returns
ERROR_NONE if no error occurred

### `public ezw_error_t clearErrorList()` {#classezw_1_1smccore_1_1_i_e_m_c_y_service_1a4a17933c87f309e083d1d750d31498fb}

Clear all previous error stored in the pre-defined error array.

#### Returns
ERROR_NONE if no error occurred

### `public ezw_error_t getErrorCount(int32_t & pErrorCount) const` {#classezw_1_1smccore_1_1_i_e_m_c_y_service_1a9dc6b7a6b09e8e2f939475887d2bcb7e}

Return the number of error present in the pre-defined error array.

#### Parameters
* `pErrorCount` Number of errors. 





#### Returns
ERROR_NONE if no error occurred

### `public ezw_error_t getErrorRegister(uint8_t & pErrorRegister) const` {#classezw_1_1smccore_1_1_i_e_m_c_y_service_1aa9286f55c3ca4485272262d63a140097}

Return error register. Error Register is made of 8 bits indicating the type of error that happend:

* [0] Generic


* [1] Current


* [2] Voltage


* [3] Temperature


* [4] Communication


* [5] Device profile specific


* [6] 0 (Reserved)


* [7] Manufacturer






#### Parameters
* `pErrorRegister` 8 bits error register. 





#### Returns
ERROR_NONE if no error occurred

### `public ezw_error_t getError(const int32_t & pIndex,uint32_t & pEmcyErrorCode) const` {#classezw_1_1smccore_1_1_i_e_m_c_y_service_1acac06f9ef98c3c80b22cef139d119c73}

Return EMCY_ERROR_CODE (as UInt32) at index in the pre-defined error array.

#### Parameters
* `pIndex` Selected index. 


* `pEmcyErrorCode` cf EMCY_ERROR_CODE. 





#### Returns
ERROR_NONE if no error occurred

# class `INMTService` {#classezw_1_1smccore_1_1_i_n_m_t_service}


[CIA301] Network management (NMT).



## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`public virtual  ~INMTService() = default` | 
`public ezw_error_t getNMTState(`[`NMTState`](#classezw_1_1smccore_1_1_i_n_m_t_service_1aad57b3ce89e210d941133c671627c9ea)` & pNmtState) const` | Retrieve the NMT state of the SWD product.
`public ezw_error_t setNMTState(const `[`NMTCommand`](#classezw_1_1smccore_1_1_i_n_m_t_service_1a510d814938ebc6c52369437caedd43b3)` & pNmtCommand)` | Modify the NMT state of the SWD product.
`public ezw_error_t broadcastNMTState(const `[`NMTCommand`](#classezw_1_1smccore_1_1_i_n_m_t_service_1a510d814938ebc6c52369437caedd43b3)` & pNmtCommand)` | Broadcast the NMT state to all CANopen nodes.

## Members

### `public virtual  ~INMTService() = default` {#classezw_1_1smccore_1_1_i_n_m_t_service_1a84016e760b6c8c891663f764cbdcd269}





### `public ezw_error_t getNMTState(`[`NMTState`](#classezw_1_1smccore_1_1_i_n_m_t_service_1aad57b3ce89e210d941133c671627c9ea)` & pNmtState) const` {#classezw_1_1smccore_1_1_i_n_m_t_service_1ade49f7d78de2d64cdd17854c22031055}

Retrieve the NMT state of the SWD product.

#### Parameters
* `pNmtState` The NMT state. 





#### Returns
ERROR_NONE if no error occurred

### `public ezw_error_t setNMTState(const `[`NMTCommand`](#classezw_1_1smccore_1_1_i_n_m_t_service_1a510d814938ebc6c52369437caedd43b3)` & pNmtCommand)` {#classezw_1_1smccore_1_1_i_n_m_t_service_1ae2526d073ed285f7b832c84e0de75ed7}

Modify the NMT state of the SWD product.

#### Parameters
* `pNmtCommand` The new NMT state. 





#### Returns
ERROR_NONE if no error occurred

### `public ezw_error_t broadcastNMTState(const `[`NMTCommand`](#classezw_1_1smccore_1_1_i_n_m_t_service_1a510d814938ebc6c52369437caedd43b3)` & pNmtCommand)` {#classezw_1_1smccore_1_1_i_n_m_t_service_1a5c715a444261c3675296a41a0f185fca}

Broadcast the NMT state to all CANopen nodes.

#### Parameters
* `pNmtCommand` The new NMT state. 





#### Returns
ERROR_NONE if no error occurred

# class `IPDSService` {#classezw_1_1smccore_1_1_i_p_d_s_service}


[CIA402-2] Controlling the Power Drive System (PDS).



## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`struct `[``PeripheralStatus``](#structezw_1_1smccore_1_1_i_p_d_s_service_1_1_peripheral_status)        | 
`struct `[``PolarityParameters``](#structezw_1_1smccore_1_1_i_p_d_s_service_1_1_polarity_parameters)        | 
`struct `[``UnitParameters``](#structezw_1_1smccore_1_1_i_p_d_s_service_1_1_unit_parameters)        | 
`public virtual  ~IPDSService() = default` | 
`public ezw_error_t getPeripheralStatus(`[`PeripheralStatus`](#structezw_1_1smccore_1_1_i_p_d_s_service_1_1_peripheral_status)` & pPeripheralStatus) const` | Retrieve the actual supported functions according to the PDS FSA state.
`public ezw_error_t getPDSState(`[`PDSState`](#classezw_1_1smccore_1_1_i_p_d_s_service_1a03d2d253d0952d4c8a1b078efdc2922b)` & pPdsState) const` | Retrieve the PDS FSA state contains into the CIA402 statusword object (6041h).
`public ezw_error_t disableVoltage() const` | Send disable voltage command into CIA402 controlword object (6040h).
`public ezw_error_t shutdown() const` | Send shutdown command into CIA402 controlword object (6040h).
`public ezw_error_t quickStop() const` | Send quick stop command into CIA402 controlword object (6040h).
`public ezw_error_t switchOn() const` | Send switch on command into CIA402 controlword object (6040h).
`public ezw_error_t enableOperation() const` | Send enable operation command into CIA402 controlword object (6040h).
`public ezw_error_t disableOperation() const` | Send disable operation command into CIA402 controlword object (6040h).
`public ezw_error_t faultReset(const bool & pStatus) const` | Send fault reset command into CIA402 controlword object (6040h).
`public ezw_error_t enterInOperationEnabledState()` | Send all the commands needed to enter into FSA operation enabled state.
`public ezw_error_t getAbortConnectionOptionCode(`[`AbortConnectionOptionCode`](#classezw_1_1smccore_1_1_i_p_d_s_service_1aec8315fa6c08016f314f817d45f75cb6)` & pCode) const` | Retrieve the abort connection option code.
`public ezw_error_t setAbortConnectionOptionCode(const `[`AbortConnectionOptionCode`](#classezw_1_1smccore_1_1_i_p_d_s_service_1aec8315fa6c08016f314f817d45f75cb6)` & pCode) const` | Modify the abort connection option code.
`public ezw_error_t getQuickStopOptionCode(`[`QuickStopOptionCode`](#classezw_1_1smccore_1_1_i_p_d_s_service_1a7c18091dbcf61978e72b6cd0448a956b)` & pCode) const` | Retrieve the quick stop option code.
`public ezw_error_t setQuickStopOptionCode(const `[`QuickStopOptionCode`](#classezw_1_1smccore_1_1_i_p_d_s_service_1a7c18091dbcf61978e72b6cd0448a956b)` & pCode) const` | Modify the quick stop option code.
`public ezw_error_t getShutdownOptionCode(`[`ShutdownOptionCode`](#classezw_1_1smccore_1_1_i_p_d_s_service_1ab09f56f2e031f6248890e1fe67195866)` & pCode) const` | Retrieve the shutdown option code.
`public ezw_error_t setShutdownOptionCode(const `[`ShutdownOptionCode`](#classezw_1_1smccore_1_1_i_p_d_s_service_1ab09f56f2e031f6248890e1fe67195866)` & pCode) const` | Modify the shutdown option code.
`public ezw_error_t getDisableOperationOptionCode(`[`DisableOperationOptionCode`](#classezw_1_1smccore_1_1_i_p_d_s_service_1a7192a9b761a76c255e0eaa96ffaf54bb)` & pCode) const` | Retrieve the disable operation option code.
`public ezw_error_t setDisableOperationOptionCode(const `[`DisableOperationOptionCode`](#classezw_1_1smccore_1_1_i_p_d_s_service_1a7192a9b761a76c255e0eaa96ffaf54bb)` & pCode) const` | Modify the disable operation option code.
`public ezw_error_t getHaltOptionCode(`[`HaltOptionCode`](#classezw_1_1smccore_1_1_i_p_d_s_service_1abeaee0ab27dd05d40b85e8d0ecdf5d5a)` & pCode) const` | Retrieve the halt option code.
`public ezw_error_t setHaltOptionCode(const `[`HaltOptionCode`](#classezw_1_1smccore_1_1_i_p_d_s_service_1abeaee0ab27dd05d40b85e8d0ecdf5d5a)` & pCode) const` | Modify the halt option code.
`public ezw_error_t getFaultReactionOptionCode(`[`FaultReactionOptionCode`](#classezw_1_1smccore_1_1_i_p_d_s_service_1a4b216f90dc92b6026c07937cadd40d21)` & pCode) const` | Retrieve the fault reaction option code.
`public ezw_error_t setFaultReactionOptionCode(const `[`FaultReactionOptionCode`](#classezw_1_1smccore_1_1_i_p_d_s_service_1a4b216f90dc92b6026c07937cadd40d21)` & pCode) const` | Modify the fault reaction option code.
`public ezw_error_t getOperationModes(`[`OperationMode`](#classezw_1_1smccore_1_1_i_p_d_s_service_1a25bbfb7442459b8d546e1f1551835479)` & pRequested,`[`OperationMode`](#classezw_1_1smccore_1_1_i_p_d_s_service_1a25bbfb7442459b8d546e1f1551835479)` & pActual) const` | Retrieve the operation mode.
`public ezw_error_t isDriveModeSupported(const `[`OperationMode`](#classezw_1_1smccore_1_1_i_p_d_s_service_1a25bbfb7442459b8d546e1f1551835479)` & pMode,bool & pSupported) const` | Retrieve the supported state of the specified drive mode.
`public ezw_error_t getUnitParameters(`[`UnitParameters`](#structezw_1_1smccore_1_1_i_p_d_s_service_1_1_unit_parameters)` & pParams) const` | Retrieve the unit parameters.
`public ezw_error_t setUnitParameters(const `[`UnitParameters`](#structezw_1_1smccore_1_1_i_p_d_s_service_1_1_unit_parameters)` & pParams)` | Modify the unit parameters.
`public ezw_error_t getPolarityParameters(`[`PolarityParameters`](#structezw_1_1smccore_1_1_i_p_d_s_service_1_1_polarity_parameters)` & pParams) const` | Retrieve the polarity factors parameters used by the SWD product.
`public ezw_error_t setPolarityParameters(const `[`PolarityParameters`](#structezw_1_1smccore_1_1_i_p_d_s_service_1_1_polarity_parameters)` & pParams)` | Modify the polarity factors parameters used by the SWD product.

## Members

### `struct `[``PeripheralStatus``](#structezw_1_1smccore_1_1_i_p_d_s_service_1_1_peripheral_status) {#structezw_1_1smccore_1_1_i_p_d_s_service_1_1_peripheral_status}



Indicates the PDS supported functions.
### `struct `[``PolarityParameters``](#structezw_1_1smccore_1_1_i_p_d_s_service_1_1_polarity_parameters) {#structezw_1_1smccore_1_1_i_p_d_s_service_1_1_polarity_parameters}



Indicates the polarity factors used by the SWD product. NOTA : The polarity factors have no impact on the following safety functions : SDIp and SDIn.
### `struct `[``UnitParameters``](#structezw_1_1smccore_1_1_i_p_d_s_service_1_1_unit_parameters) {#structezw_1_1smccore_1_1_i_p_d_s_service_1_1_unit_parameters}



[CIA402-4] Indicates the configured SI units.
### `public virtual  ~IPDSService() = default` {#classezw_1_1smccore_1_1_i_p_d_s_service_1ae56177220abc3f12f6bfc3fc46d714f7}





### `public ezw_error_t getPeripheralStatus(`[`PeripheralStatus`](#structezw_1_1smccore_1_1_i_p_d_s_service_1_1_peripheral_status)` & pPeripheralStatus) const` {#classezw_1_1smccore_1_1_i_p_d_s_service_1a8fdce989f6cef9bab5cd7882ceebbb7a}

Retrieve the actual supported functions according to the PDS FSA state.

#### Parameters
* `pPeripheralStatus` The supported functions. 





#### Returns
ERROR_NONE if no error occurred

### `public ezw_error_t getPDSState(`[`PDSState`](#classezw_1_1smccore_1_1_i_p_d_s_service_1a03d2d253d0952d4c8a1b078efdc2922b)` & pPdsState) const` {#classezw_1_1smccore_1_1_i_p_d_s_service_1a900d8ee68b5acb7d817b3d4ab40d54bd}

Retrieve the PDS FSA state contains into the CIA402 statusword object (6041h).

#### Parameters
* `pPdsState` The PDS FSA state. 





#### Returns
ERROR_NONE if no error occurred

### `public ezw_error_t disableVoltage() const` {#classezw_1_1smccore_1_1_i_p_d_s_service_1a049589456fea9e693f94459f5ee02ce6}

Send disable voltage command into CIA402 controlword object (6040h).

#### Returns
ERROR_NONE if no error occurred

### `public ezw_error_t shutdown() const` {#classezw_1_1smccore_1_1_i_p_d_s_service_1a9d075aafa6f7fb58132c69640cb5c0b9}

Send shutdown command into CIA402 controlword object (6040h).

#### Returns
ERROR_NONE if no error occurred

### `public ezw_error_t quickStop() const` {#classezw_1_1smccore_1_1_i_p_d_s_service_1a8234166501cd326ee16300c8f066970f}

Send quick stop command into CIA402 controlword object (6040h).

#### Returns
ERROR_NONE if no error occurred

### `public ezw_error_t switchOn() const` {#classezw_1_1smccore_1_1_i_p_d_s_service_1abef179f8566bb56bafbe1462a5d115ef}

Send switch on command into CIA402 controlword object (6040h).

#### Returns
ERROR_NONE if no error occurred

### `public ezw_error_t enableOperation() const` {#classezw_1_1smccore_1_1_i_p_d_s_service_1a91938f2d342a7deabf56b33096b08416}

Send enable operation command into CIA402 controlword object (6040h).

#### Returns
ERROR_NONE if no error occurred

### `public ezw_error_t disableOperation() const` {#classezw_1_1smccore_1_1_i_p_d_s_service_1adfda599e9c2a4e46a7198f9a7500b6ce}

Send disable operation command into CIA402 controlword object (6040h).

#### Returns
ERROR_NONE if no error occurred

### `public ezw_error_t faultReset(const bool & pStatus) const` {#classezw_1_1smccore_1_1_i_p_d_s_service_1a546ae6ead8b3e7811449fb690c1b677c}

Send fault reset command into CIA402 controlword object (6040h).

#### Parameters
* `pStatus` True to set the fault reset bit else False to clear it. 





#### Returns
ERROR_NONE if no error occurred

### `public ezw_error_t enterInOperationEnabledState()` {#classezw_1_1smccore_1_1_i_p_d_s_service_1adf59c2072921ecb27e460a56b9fd9656}

Send all the commands needed to enter into FSA operation enabled state.

#### Returns
ERROR_NONE if no error occurred

### `public ezw_error_t getAbortConnectionOptionCode(`[`AbortConnectionOptionCode`](#classezw_1_1smccore_1_1_i_p_d_s_service_1aec8315fa6c08016f314f817d45f75cb6)` & pCode) const` {#classezw_1_1smccore_1_1_i_p_d_s_service_1a7c1fed84cde3351fa767e9ddb8dc5862}

Retrieve the abort connection option code.

#### Parameters
* `pCode` The abort connection option code. 





#### Returns
ERROR_NONE if no error occurred

### `public ezw_error_t setAbortConnectionOptionCode(const `[`AbortConnectionOptionCode`](#classezw_1_1smccore_1_1_i_p_d_s_service_1aec8315fa6c08016f314f817d45f75cb6)` & pCode) const` {#classezw_1_1smccore_1_1_i_p_d_s_service_1af066bcd43e91e28d89707ceb7a780193}

Modify the abort connection option code.

#### Parameters
* `pCode` The abort connection option code. 





#### Returns
ERROR_NONE if no error occurred

### `public ezw_error_t getQuickStopOptionCode(`[`QuickStopOptionCode`](#classezw_1_1smccore_1_1_i_p_d_s_service_1a7c18091dbcf61978e72b6cd0448a956b)` & pCode) const` {#classezw_1_1smccore_1_1_i_p_d_s_service_1a4aeef53cf8a8d1de7ababa0c1f8ea214}

Retrieve the quick stop option code.

#### Parameters
* `pCode` The quick stop option code. 





#### Returns
ERROR_NONE if no error occurred

### `public ezw_error_t setQuickStopOptionCode(const `[`QuickStopOptionCode`](#classezw_1_1smccore_1_1_i_p_d_s_service_1a7c18091dbcf61978e72b6cd0448a956b)` & pCode) const` {#classezw_1_1smccore_1_1_i_p_d_s_service_1a17b4e2cefd1a8425d23aef96bff1afd9}

Modify the quick stop option code.

#### Parameters
* `pCode` The quick stop option code. 





#### Returns
ERROR_NONE if no error occurred

### `public ezw_error_t getShutdownOptionCode(`[`ShutdownOptionCode`](#classezw_1_1smccore_1_1_i_p_d_s_service_1ab09f56f2e031f6248890e1fe67195866)` & pCode) const` {#classezw_1_1smccore_1_1_i_p_d_s_service_1ac6d189f44741ffd2023b7832149abf2d}

Retrieve the shutdown option code.

#### Parameters
* `pCode` The shutdown option code. 





#### Returns
ERROR_NONE if no error occurred

### `public ezw_error_t setShutdownOptionCode(const `[`ShutdownOptionCode`](#classezw_1_1smccore_1_1_i_p_d_s_service_1ab09f56f2e031f6248890e1fe67195866)` & pCode) const` {#classezw_1_1smccore_1_1_i_p_d_s_service_1a0d71b334a4794c867a6aa3952b4ba08e}

Modify the shutdown option code.

#### Parameters
* `pCode` The shutdown option code. 





#### Returns
ERROR_NONE if no error occurred

### `public ezw_error_t getDisableOperationOptionCode(`[`DisableOperationOptionCode`](#classezw_1_1smccore_1_1_i_p_d_s_service_1a7192a9b761a76c255e0eaa96ffaf54bb)` & pCode) const` {#classezw_1_1smccore_1_1_i_p_d_s_service_1a54ad712eeaa7ec97af1a7ffbff59742c}

Retrieve the disable operation option code.

#### Parameters
* `pCode` The disable operation option code. 





#### Returns
ERROR_NONE if no error occurred

### `public ezw_error_t setDisableOperationOptionCode(const `[`DisableOperationOptionCode`](#classezw_1_1smccore_1_1_i_p_d_s_service_1a7192a9b761a76c255e0eaa96ffaf54bb)` & pCode) const` {#classezw_1_1smccore_1_1_i_p_d_s_service_1a60482c8d3adff2184ad110a74fd3b6dc}

Modify the disable operation option code.

#### Parameters
* `pCode` The disable operation option code. 





#### Returns
ERROR_NONE if no error occurred

### `public ezw_error_t getHaltOptionCode(`[`HaltOptionCode`](#classezw_1_1smccore_1_1_i_p_d_s_service_1abeaee0ab27dd05d40b85e8d0ecdf5d5a)` & pCode) const` {#classezw_1_1smccore_1_1_i_p_d_s_service_1aca7a9661c53226859a0e9708d7dd7f68}

Retrieve the halt option code.

#### Parameters
* `pCode` The halt option code. 





#### Returns
ERROR_NONE if no error occurred

### `public ezw_error_t setHaltOptionCode(const `[`HaltOptionCode`](#classezw_1_1smccore_1_1_i_p_d_s_service_1abeaee0ab27dd05d40b85e8d0ecdf5d5a)` & pCode) const` {#classezw_1_1smccore_1_1_i_p_d_s_service_1ab6bfc4ce4912ba92e29054d9425c0e39}

Modify the halt option code.

#### Parameters
* `pCode` The halt option code. 





#### Returns
ERROR_NONE if no error occurred

### `public ezw_error_t getFaultReactionOptionCode(`[`FaultReactionOptionCode`](#classezw_1_1smccore_1_1_i_p_d_s_service_1a4b216f90dc92b6026c07937cadd40d21)` & pCode) const` {#classezw_1_1smccore_1_1_i_p_d_s_service_1a0fdf9f68053a05aac33aa88f892a0219}

Retrieve the fault reaction option code.

#### Parameters
* `pCode` The fault reaction option code. 





#### Returns
ERROR_NONE if no error occurred

### `public ezw_error_t setFaultReactionOptionCode(const `[`FaultReactionOptionCode`](#classezw_1_1smccore_1_1_i_p_d_s_service_1a4b216f90dc92b6026c07937cadd40d21)` & pCode) const` {#classezw_1_1smccore_1_1_i_p_d_s_service_1aaf9c51b2b1fb662d5c0db9de812523f0}

Modify the fault reaction option code.

#### Parameters
* `pCode` The fault reaction option code. 





#### Returns
ERROR_NONE if no error occurred

### `public ezw_error_t getOperationModes(`[`OperationMode`](#classezw_1_1smccore_1_1_i_p_d_s_service_1a25bbfb7442459b8d546e1f1551835479)` & pRequested,`[`OperationMode`](#classezw_1_1smccore_1_1_i_p_d_s_service_1a25bbfb7442459b8d546e1f1551835479)` & pActual) const` {#classezw_1_1smccore_1_1_i_p_d_s_service_1ae8d03984816287296b2224c56babd5d3}

Retrieve the operation mode.

#### Parameters
* `pRequested` The requested operation mode. 


* `pActual` The actual operation mode. 





#### Returns
ERROR_NONE if no error occurred

### `public ezw_error_t isDriveModeSupported(const `[`OperationMode`](#classezw_1_1smccore_1_1_i_p_d_s_service_1a25bbfb7442459b8d546e1f1551835479)` & pMode,bool & pSupported) const` {#classezw_1_1smccore_1_1_i_p_d_s_service_1a19fc2ad1214c314d64b6b0234ad344e6}

Retrieve the supported state of the specified drive mode.

#### Parameters
* `pMode` The drive mode. 


* `pSupported` True if the specified drive mode is supported. 





#### Returns
ERROR_NONE if no error occurred

### `public ezw_error_t getUnitParameters(`[`UnitParameters`](#structezw_1_1smccore_1_1_i_p_d_s_service_1_1_unit_parameters)` & pParams) const` {#classezw_1_1smccore_1_1_i_p_d_s_service_1abc3f744d438d7399b8ef500ba2d67ec7}

Retrieve the unit parameters.

#### Parameters
* `pParams` The unit parameters. 





#### Returns
ERROR_NONE if no error occurred

### `public ezw_error_t setUnitParameters(const `[`UnitParameters`](#structezw_1_1smccore_1_1_i_p_d_s_service_1_1_unit_parameters)` & pParams)` {#classezw_1_1smccore_1_1_i_p_d_s_service_1a73f03c50470179e851a9df06a96784b5}

Modify the unit parameters.

#### Parameters
* `pParams` The unit parameters. 





#### Returns
ERROR_NONE if no error occurred

### `public ezw_error_t getPolarityParameters(`[`PolarityParameters`](#structezw_1_1smccore_1_1_i_p_d_s_service_1_1_polarity_parameters)` & pParams) const` {#classezw_1_1smccore_1_1_i_p_d_s_service_1a9038c029b48f9b17bd71b5f152c31a57}

Retrieve the polarity factors parameters used by the SWD product.

#### Parameters
* `pParams` The configured polarity parameters. 





#### Returns
ERROR_NONE if no error occurred

### `public ezw_error_t setPolarityParameters(const `[`PolarityParameters`](#structezw_1_1smccore_1_1_i_p_d_s_service_1_1_polarity_parameters)` & pParams)` {#classezw_1_1smccore_1_1_i_p_d_s_service_1a28fdcbfdf566a18ca854845abf30ffc4}

Modify the polarity factors parameters used by the SWD product.

#### Parameters
* `pParams` The new polarity parameters. 





#### Returns
ERROR_NONE if no error occurred

# struct `PeripheralStatus` {#structezw_1_1smccore_1_1_i_p_d_s_service_1_1_peripheral_status}




Indicates the PDS supported functions.

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`public bool brake_applied` | 
`public bool low_level_power_applied` | 
`public bool high_level_power_applied` | 
`public bool driver_enabled` | 
`public bool configuration_allowed` | 
`public bool communication_enabled` | 

## Members

### `public bool brake_applied` {#structezw_1_1smccore_1_1_i_p_d_s_service_1_1_peripheral_status_1a7b6572ead5bf5f0d9f08c101f50303ec}



Brake applied, if present.

### `public bool low_level_power_applied` {#structezw_1_1smccore_1_1_i_p_d_s_service_1_1_peripheral_status_1ad1638d50b6ceff494de50b3a2e1698ba}



Low-level power applied.

### `public bool high_level_power_applied` {#structezw_1_1smccore_1_1_i_p_d_s_service_1_1_peripheral_status_1a7797f10210d16673e252060d7d17fed0}



High-level power applied.

### `public bool driver_enabled` {#structezw_1_1smccore_1_1_i_p_d_s_service_1_1_peripheral_status_1a9f94d602a62e9e2cd23d7bff69a0186c}



Drive function enabled.

### `public bool configuration_allowed` {#structezw_1_1smccore_1_1_i_p_d_s_service_1_1_peripheral_status_1a561e94f432414bc9a900872dd0bfe510}



Configuration allowed.

### `public bool communication_enabled` {#structezw_1_1smccore_1_1_i_p_d_s_service_1_1_peripheral_status_1aef3ae019d683dc0341f2e3c49d2eae3e}



Communication enabled.

# struct `PolarityParameters` {#structezw_1_1smccore_1_1_i_p_d_s_service_1_1_polarity_parameters}




Indicates the polarity factors used by the SWD product. NOTA : The polarity factors have no impact on the following safety functions : SDIp and SDIn.

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`public bool velocity_polarity` | 
`public bool position_polarity` | 

## Members

### `public bool velocity_polarity` {#structezw_1_1smccore_1_1_i_p_d_s_service_1_1_polarity_parameters_1a895fd562e12a77e0b4e2f69f611b3fac}



Indicates if the velocity demand value shall be multiplied by 1 of by –1. (False = multiply by 1 and True = multiply by –1).

### `public bool position_polarity` {#structezw_1_1smccore_1_1_i_p_d_s_service_1_1_polarity_parameters_1ac13023493d83fe191c6d55a6b44cf710}



Indicates if the motor revolution increments shall be multiplied by 1 of by –1. (False = multiply by 1 and True = multiply by –1).

# struct `UnitParameters` {#structezw_1_1smccore_1_1_i_p_d_s_service_1_1_unit_parameters}




[CIA402-4] Indicates the configured SI units.

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`public uint32_t time_unit` | 
`public uint32_t position_unit` | 
`public uint32_t velocity_unit` | 
`public uint32_t acceleration_unit` | 

## Members

### `public uint32_t time_unit` {#structezw_1_1smccore_1_1_i_p_d_s_service_1_1_unit_parameters_1a758fffcda15af6987fae3702219165ed}



Indicates the configured SI unit used for time parameters.

### `public uint32_t position_unit` {#structezw_1_1smccore_1_1_i_p_d_s_service_1_1_unit_parameters_1a9f8459b1dff856214615ce7fd5a5984f}



Indicates the configured SI unit used for position parameters. (not used).

### `public uint32_t velocity_unit` {#structezw_1_1smccore_1_1_i_p_d_s_service_1_1_unit_parameters_1a5f6bad47f79ee88309b9a3c29884a0f3}



Indicates the configured SI unit used for velocity parameters.

### `public uint32_t acceleration_unit` {#structezw_1_1smccore_1_1_i_p_d_s_service_1_1_unit_parameters_1a159e0e1bff5cf5e2fd342135843395eb}



Indicates the configured SI unit used for acceleration and deceleration parameters.

# class `ISafeMotionService` {#classezw_1_1smccore_1_1_i_safe_motion_service}


[CIA402-4] Safety motion drive. The activation of a security function can come from :

* the safety inputs


* the CANopen safety control words


* a internal fault reaction


* the violation of a safety function SCW CAN :


* to modify the CANopen safety control words in a safety context, it will be done with CANopen SRDO objects.


* each safety control word can command up to 8 safety functions (one function by bit).


* the association of the bit with the safety function is done into the safety control word mapping. SSW CAN :


* each safety status words can monitor up to 8 safety functions (one function by bit).


* the association of the bit with the safety function is done into the safety status word mapping. SWC SAFE_IN :


* the safety input control word can command up to 6 safety functions (one function by bit).


* the association of the bit with the safety function is done into the safety input control word mapping. SSW SAFE_OUT :


* the safety output status word can monitor up to 4 safety functions (one function by bit).


* the association of the bit with the safety function is done into the safety output status word mapping.

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`struct `[``SafetyFunctionOuputStatus``](#structezw_1_1smccore_1_1_i_safe_motion_service_1_1_safety_function_ouput_status)        | 
`struct `[``SafetyWordMapping``](#structezw_1_1smccore_1_1_i_safe_motion_service_1_1_safety_word_mapping)        | 
`struct `[``SafetyWordType``](#structezw_1_1smccore_1_1_i_safe_motion_service_1_1_safety_word_type)        | 
`struct `[``SBCParameters``](#structezw_1_1smccore_1_1_i_safe_motion_service_1_1_s_b_c_parameters)        | 
`struct `[``SDIParameters``](#structezw_1_1smccore_1_1_i_safe_motion_service_1_1_s_d_i_parameters)        | 
`struct `[``SLSaParameters``](#structezw_1_1smccore_1_1_i_safe_motion_service_1_1_s_l_sa_parameters)        | 
`struct `[``SLSParameters``](#structezw_1_1smccore_1_1_i_safe_motion_service_1_1_s_l_s_parameters)        | 
`struct `[``SMSParameters``](#structezw_1_1smccore_1_1_i_safe_motion_service_1_1_s_m_s_parameters)        | 
`struct `[``STOParameters``](#structezw_1_1smccore_1_1_i_safe_motion_service_1_1_s_t_o_parameters)        | 
`public virtual  ~ISafeMotionService() = default` | 
`public ezw_error_t getSafetyControlWordMapping(const `[`SafetyControlWordId`](#classezw_1_1smccore_1_1_i_safe_motion_service_1a2da3e945f1e59696b6d28d75e22e5b8d)` & pSafetyControlWordId,`[`SafetyWordMapping`](#structezw_1_1smccore_1_1_i_safe_motion_service_1_1_safety_word_mapping)` & pSafetyControlWordMapping) const` | Retrieve the safety control word mapping of the specified safety control word id.
`public ezw_error_t setSafetyControlWordMapping(const `[`SafetyControlWordId`](#classezw_1_1smccore_1_1_i_safe_motion_service_1a2da3e945f1e59696b6d28d75e22e5b8d)` & pSafetyControlWordId,const `[`SafetyWordMapping`](#structezw_1_1smccore_1_1_i_safe_motion_service_1_1_safety_word_mapping)` & pSafetyControlWordMapping)` | Modify the safety control word mapping of the specified safety control word id.
`public ezw_error_t getSafetyStatusWordMapping(const `[`SafetyStatusWordId`](#classezw_1_1smccore_1_1_i_safe_motion_service_1a79a03b44c531b0a136e602c8ba1dc052)` & pSafetyStatusWordId,`[`SafetyWordMapping`](#structezw_1_1smccore_1_1_i_safe_motion_service_1_1_safety_word_mapping)` & pSafetyStatusWordMapping) const` | Retrieve the safety status word mapping of the specified safety status word id.
`public ezw_error_t setSafetyStatusWordMapping(const `[`SafetyStatusWordId`](#classezw_1_1smccore_1_1_i_safe_motion_service_1a79a03b44c531b0a136e602c8ba1dc052)` & pSafetyStatusWordId,const `[`SafetyWordMapping`](#structezw_1_1smccore_1_1_i_safe_motion_service_1_1_safety_word_mapping)` & pSafetyStatusWordMapping)` | Modify the safety status word mapping of the specified safety status word id.
`public ezw_error_t getSafetyFunctionCommand(const `[`SafetyFunctionId`](#classezw_1_1smccore_1_1_i_safe_motion_service_1aa185e2d74ea19870933a1e1c7598f367)` & pSafetyFunctionId,bool & pStatus) const` | Retrieve the safety function command of the specified safety function id.
`public ezw_error_t getSafetyFunctionStatus(const `[`SafetyFunctionId`](#classezw_1_1smccore_1_1_i_safe_motion_service_1aa185e2d74ea19870933a1e1c7598f367)` & pSafetyFunctionId,bool & pStatus) const` | Retrieve the safety function status of the specified safety function id.
`public ezw_error_t getSafetyControlWord(const `[`SafetyControlWordId`](#classezw_1_1smccore_1_1_i_safe_motion_service_1a2da3e945f1e59696b6d28d75e22e5b8d)` & pSafetyControlWordId,`[`SafetyWordType`](#structezw_1_1smccore_1_1_i_safe_motion_service_1_1_safety_word_type)` & pSafetyControlWord) const` | Retrieve the safety control word of the specified safety control word id.
`public ezw_error_t setSafetyControlWord(const `[`SafetyControlWordId`](#classezw_1_1smccore_1_1_i_safe_motion_service_1a2da3e945f1e59696b6d28d75e22e5b8d)` & pSafetyControlWordId,const `[`SafetyWordType`](#structezw_1_1smccore_1_1_i_safe_motion_service_1_1_safety_word_type)` & pSafetyControlWord)` | Modify the safety control word of the specified safety control word id.
`public ezw_error_t getSafetyStatusWord(const `[`SafetyStatusWordId`](#classezw_1_1smccore_1_1_i_safe_motion_service_1a79a03b44c531b0a136e602c8ba1dc052)` & pSafetyStatusWordId,`[`SafetyWordType`](#structezw_1_1smccore_1_1_i_safe_motion_service_1_1_safety_word_type)` & pSafetyStatusWord) const` | Retrieve the safety status word of the specified safety status word id.
`public ezw_error_t getSTOParameters(const `[`STOId`](#classezw_1_1smccore_1_1_i_safe_motion_service_1a62f9880d8a52df487676d47c3698a864)` & pId,`[`STOParameters`](#structezw_1_1smccore_1_1_i_safe_motion_service_1_1_s_t_o_parameters)` & pParameters,uint16_t & pSignature) const` | Retrieve the STO safety application parameters of the specified STO id.
`public ezw_error_t setSTOParameters(const `[`STOId`](#classezw_1_1smccore_1_1_i_safe_motion_service_1a62f9880d8a52df487676d47c3698a864)` & pId,const `[`STOParameters`](#structezw_1_1smccore_1_1_i_safe_motion_service_1_1_s_t_o_parameters)` & pParameters)` | Modify the safety function STO parameters of the specified STO id. NOTA : Modification is allowed only in NMT state Pre-operational.
`public ezw_error_t getSLSParameters(const `[`SLSId`](#classezw_1_1smccore_1_1_i_safe_motion_service_1af9a3e7557f9976350f7dcd8ec9002181)` & pId,`[`SLSParameters`](#structezw_1_1smccore_1_1_i_safe_motion_service_1_1_s_l_s_parameters)` & pParameters,uint16_t & pSignature) const` | Retrieve the SLS safety application parameters of the specified SLS id.
`public ezw_error_t setSLSParameters(const `[`SLSId`](#classezw_1_1smccore_1_1_i_safe_motion_service_1af9a3e7557f9976350f7dcd8ec9002181)` & pId,const `[`SLSParameters`](#structezw_1_1smccore_1_1_i_safe_motion_service_1_1_s_l_s_parameters)` & pParameters)` | Modify the safety function SLS parameters of the specified SLS id. NOTA : Modification is allowed only in NMT state Pre-operational.
`public ezw_error_t getSDIParameters(const `[`SDIId`](#classezw_1_1smccore_1_1_i_safe_motion_service_1af3aa910a001660cb96060ab0b05ce52c)` & pId,`[`SDIParameters`](#structezw_1_1smccore_1_1_i_safe_motion_service_1_1_s_d_i_parameters)` & pParameters,uint16_t & pSignature) const` | Retrieve the SDI safety application parameters of the specified SDI id.
`public ezw_error_t setSDIParameters(const `[`SDIId`](#classezw_1_1smccore_1_1_i_safe_motion_service_1af3aa910a001660cb96060ab0b05ce52c)` & pId,const `[`SDIParameters`](#structezw_1_1smccore_1_1_i_safe_motion_service_1_1_s_d_i_parameters)` & pParameters)` | Modify the safety function SDI parameters of the specified SDI id. NOTA : Modification is allowed only in NMT state Pre-operational.
`public ezw_error_t getSBCParameters(const `[`SBCId`](#classezw_1_1smccore_1_1_i_safe_motion_service_1a77246d628a91bf387edddaee3defb618)` & pId,`[`SBCParameters`](#structezw_1_1smccore_1_1_i_safe_motion_service_1_1_s_b_c_parameters)` & pParameters,uint16_t & pSignature) const` | Retrieve the SBC safety application parameters of the specified SBC id.
`public ezw_error_t getSMSParameters(const `[`SMSId`](#classezw_1_1smccore_1_1_i_safe_motion_service_1aea8dd47c0bd8cfd893c4bd24e70921a2)` & pId,`[`SMSParameters`](#structezw_1_1smccore_1_1_i_safe_motion_service_1_1_s_m_s_parameters)` & pParameters,uint16_t & pSignature) const` | Retrieve the SMS safety application parameters of the specified SMS id.
`public ezw_error_t setSMSParameters(const `[`SMSId`](#classezw_1_1smccore_1_1_i_safe_motion_service_1aea8dd47c0bd8cfd893c4bd24e70921a2)` & pId,const `[`SMSParameters`](#structezw_1_1smccore_1_1_i_safe_motion_service_1_1_s_m_s_parameters)` & pParameters)` | Modify the safety function SMS parameters of the specified SMS id. NOTA : Modification is allowed only in NMT state Pre-operational.
`public ezw_error_t getSLSaParameters(const `[`SLSaId`](#classezw_1_1smccore_1_1_i_safe_motion_service_1a805acb16d70d8a04d5b2d9ae25e2a831)` & pId,SLSaParameters & pParameters,uint16_t & pSignature) const` | Retrieve the SLSa safety application parameters of the specified SLSa id.
`public ezw_error_t setSLSaParameters(const `[`SLSaId`](#classezw_1_1smccore_1_1_i_safe_motion_service_1a805acb16d70d8a04d5b2d9ae25e2a831)` & pId,const SLSaParameters & pParameters)` | Modify the safety function SLSa parameters of the specified SLSa id. NOTA : Modification is allowed only in NMT state Pre-operational.
`public ezw_error_t getSafetyFunctionOutput(const `[`SafetyFunctionId`](#classezw_1_1smccore_1_1_i_safe_motion_service_1aa185e2d74ea19870933a1e1c7598f367)` & pSafetyFunctionId,bool & pStatus) const` | Retrieve the consolidated safety function status of the specified safety function id.
`public ezw_error_t getSafetyFunctionOutputs(std::vector< `[`SafetyFunctionOuputStatus`](#structezw_1_1smccore_1_1_i_safe_motion_service_1_1_safety_function_ouput_status)` > & pItems) const` | Retrieve all the consolidated safety function statuses.

## Members

### `struct `[``SafetyFunctionOuputStatus``](#structezw_1_1smccore_1_1_i_safe_motion_service_1_1_safety_function_ouput_status) {#structezw_1_1smccore_1_1_i_safe_motion_service_1_1_safety_function_ouput_status}



Indicates the consolidated status of a safety function.
### `struct `[``SafetyWordMapping``](#structezw_1_1smccore_1_1_i_safe_motion_service_1_1_safety_word_mapping) {#structezw_1_1smccore_1_1_i_safe_motion_service_1_1_safety_word_mapping}



Represents a safety status/control word mapping (up to 8 functions : one function by bit).
### `struct `[``SafetyWordType``](#structezw_1_1smccore_1_1_i_safe_motion_service_1_1_safety_word_type) {#structezw_1_1smccore_1_1_i_safe_motion_service_1_1_safety_word_type}



Represents a safety status/control word (up to 8 functions : one function by bit).
### `struct `[``SBCParameters``](#structezw_1_1smccore_1_1_i_safe_motion_service_1_1_s_b_c_parameters) {#structezw_1_1smccore_1_1_i_safe_motion_service_1_1_s_b_c_parameters}



Represents the SBC safety application parameters.
### `struct `[``SDIParameters``](#structezw_1_1smccore_1_1_i_safe_motion_service_1_1_s_d_i_parameters) {#structezw_1_1smccore_1_1_i_safe_motion_service_1_1_s_d_i_parameters}



Represents the SDI safety application parameters.
### `struct `[``SLSaParameters``](#structezw_1_1smccore_1_1_i_safe_motion_service_1_1_s_l_sa_parameters) {#structezw_1_1smccore_1_1_i_safe_motion_service_1_1_s_l_sa_parameters}




### `struct `[``SLSParameters``](#structezw_1_1smccore_1_1_i_safe_motion_service_1_1_s_l_s_parameters) {#structezw_1_1smccore_1_1_i_safe_motion_service_1_1_s_l_s_parameters}



Represents the SLS safety application parameters.
### `struct `[``SMSParameters``](#structezw_1_1smccore_1_1_i_safe_motion_service_1_1_s_m_s_parameters) {#structezw_1_1smccore_1_1_i_safe_motion_service_1_1_s_m_s_parameters}



Represents the SMS safety application parameters.
### `struct `[``STOParameters``](#structezw_1_1smccore_1_1_i_safe_motion_service_1_1_s_t_o_parameters) {#structezw_1_1smccore_1_1_i_safe_motion_service_1_1_s_t_o_parameters}



Represents the STO safety application parameters.
### `public virtual  ~ISafeMotionService() = default` {#classezw_1_1smccore_1_1_i_safe_motion_service_1a63c35d803c10b459cf83f2a00e9c3706}





### `public ezw_error_t getSafetyControlWordMapping(const `[`SafetyControlWordId`](#classezw_1_1smccore_1_1_i_safe_motion_service_1a2da3e945f1e59696b6d28d75e22e5b8d)` & pSafetyControlWordId,`[`SafetyWordMapping`](#structezw_1_1smccore_1_1_i_safe_motion_service_1_1_safety_word_mapping)` & pSafetyControlWordMapping) const` {#classezw_1_1smccore_1_1_i_safe_motion_service_1ac756f7868ca414d082476b54987a1122}

Retrieve the safety control word mapping of the specified safety control word id.

#### Parameters
* `pSafetyControlWordId` Id of the safety control word. 


* `pSafetyControlWordMapping` The safety control word mapping. 





#### Returns
ERROR_NONE if no error occurred

### `public ezw_error_t setSafetyControlWordMapping(const `[`SafetyControlWordId`](#classezw_1_1smccore_1_1_i_safe_motion_service_1a2da3e945f1e59696b6d28d75e22e5b8d)` & pSafetyControlWordId,const `[`SafetyWordMapping`](#structezw_1_1smccore_1_1_i_safe_motion_service_1_1_safety_word_mapping)` & pSafetyControlWordMapping)` {#classezw_1_1smccore_1_1_i_safe_motion_service_1a48cd62bc4f2865689a40cb1940f46253}

Modify the safety control word mapping of the specified safety control word id.

#### Parameters
* `pSafetyControlWordId` Id of the safety control word. 


* `pSafetyControlWordMapping` The safety control word mapping. 





#### Returns
ERROR_NONE if no error occurred

### `public ezw_error_t getSafetyStatusWordMapping(const `[`SafetyStatusWordId`](#classezw_1_1smccore_1_1_i_safe_motion_service_1a79a03b44c531b0a136e602c8ba1dc052)` & pSafetyStatusWordId,`[`SafetyWordMapping`](#structezw_1_1smccore_1_1_i_safe_motion_service_1_1_safety_word_mapping)` & pSafetyStatusWordMapping) const` {#classezw_1_1smccore_1_1_i_safe_motion_service_1ab1fb1cab5ebe32ca8955f1351f566597}

Retrieve the safety status word mapping of the specified safety status word id.

#### Parameters
* `pSafetyStatusWordId` Id of the safety status word. 


* `pSafetyStatusWordMapping` The safety status word mapping. 





#### Returns
ERROR_NONE if no error occurred

### `public ezw_error_t setSafetyStatusWordMapping(const `[`SafetyStatusWordId`](#classezw_1_1smccore_1_1_i_safe_motion_service_1a79a03b44c531b0a136e602c8ba1dc052)` & pSafetyStatusWordId,const `[`SafetyWordMapping`](#structezw_1_1smccore_1_1_i_safe_motion_service_1_1_safety_word_mapping)` & pSafetyStatusWordMapping)` {#classezw_1_1smccore_1_1_i_safe_motion_service_1aa961b88f510e9a7e3ce0241758ae9d79}

Modify the safety status word mapping of the specified safety status word id.

#### Parameters
* `pSafetyStatusWordId` Id of the safety status word. 


* `pSafetyStatusWordMapping` The safety status word mapping. 





#### Returns
ERROR_NONE if no error occurred

### `public ezw_error_t getSafetyFunctionCommand(const `[`SafetyFunctionId`](#classezw_1_1smccore_1_1_i_safe_motion_service_1aa185e2d74ea19870933a1e1c7598f367)` & pSafetyFunctionId,bool & pStatus) const` {#classezw_1_1smccore_1_1_i_safe_motion_service_1acb356d00334aab8bb2c5927458846648}

Retrieve the safety function command of the specified safety function id.

#### Parameters
* `pSafetyFunctionId` Id of the safety function. 


* `pStatus` False if the safety function command is enabled. 





#### Returns
ERROR_NONE if no error occurred

### `public ezw_error_t getSafetyFunctionStatus(const `[`SafetyFunctionId`](#classezw_1_1smccore_1_1_i_safe_motion_service_1aa185e2d74ea19870933a1e1c7598f367)` & pSafetyFunctionId,bool & pStatus) const` {#classezw_1_1smccore_1_1_i_safe_motion_service_1a3c8fee7718461feeed2b667afeb9f65f}

Retrieve the safety function status of the specified safety function id.

#### Parameters
* `pSafetyFunctionId` Id of the safety function. 


* `pStatus` True if the safety function status is enabled. 





#### Returns
ERROR_NONE if no error occurred

### `public ezw_error_t getSafetyControlWord(const `[`SafetyControlWordId`](#classezw_1_1smccore_1_1_i_safe_motion_service_1a2da3e945f1e59696b6d28d75e22e5b8d)` & pSafetyControlWordId,`[`SafetyWordType`](#structezw_1_1smccore_1_1_i_safe_motion_service_1_1_safety_word_type)` & pSafetyControlWord) const` {#classezw_1_1smccore_1_1_i_safe_motion_service_1a2ad5e2bcb88de8d8c79a9c33d11336c8}

Retrieve the safety control word of the specified safety control word id.

#### Parameters
* `pSafetyControlWordId` Id of the safety control word. 


* `pSafetyControlWord` The safety control word. 





#### Returns
ERROR_NONE if no error occurred

### `public ezw_error_t setSafetyControlWord(const `[`SafetyControlWordId`](#classezw_1_1smccore_1_1_i_safe_motion_service_1a2da3e945f1e59696b6d28d75e22e5b8d)` & pSafetyControlWordId,const `[`SafetyWordType`](#structezw_1_1smccore_1_1_i_safe_motion_service_1_1_safety_word_type)` & pSafetyControlWord)` {#classezw_1_1smccore_1_1_i_safe_motion_service_1ab31753e65d77045f4c324e4e7cf84a9a}

Modify the safety control word of the specified safety control word id.

#### Parameters
* `pSafetyControlWordId` Id of the safety control word. 


* `pSafetyControlWord` The safety control word. 





#### Returns
ERROR_NONE if no error occurred

### `public ezw_error_t getSafetyStatusWord(const `[`SafetyStatusWordId`](#classezw_1_1smccore_1_1_i_safe_motion_service_1a79a03b44c531b0a136e602c8ba1dc052)` & pSafetyStatusWordId,`[`SafetyWordType`](#structezw_1_1smccore_1_1_i_safe_motion_service_1_1_safety_word_type)` & pSafetyStatusWord) const` {#classezw_1_1smccore_1_1_i_safe_motion_service_1aca3611f5d452b0017a6bd65c41d33984}

Retrieve the safety status word of the specified safety status word id.

#### Parameters
* `pSafetyStatusWordId` Id of the safety status word. 


* `pSafetyStatusWord` The safety status word. 





#### Returns
ERROR_NONE if no error occurred

### `public ezw_error_t getSTOParameters(const `[`STOId`](#classezw_1_1smccore_1_1_i_safe_motion_service_1a62f9880d8a52df487676d47c3698a864)` & pId,`[`STOParameters`](#structezw_1_1smccore_1_1_i_safe_motion_service_1_1_s_t_o_parameters)` & pParameters,uint16_t & pSignature) const` {#classezw_1_1smccore_1_1_i_safe_motion_service_1a7cf41f6d464a5b4afa779b1e9443f1ac}

Retrieve the STO safety application parameters of the specified STO id.

#### Parameters
* `pId` Id of the STO. 


* `pParameters` The STO safety application parameters. 


* `pSignature` The STO safety application configuration signature. 





#### Returns
ERROR_NONE if no error occurred

### `public ezw_error_t setSTOParameters(const `[`STOId`](#classezw_1_1smccore_1_1_i_safe_motion_service_1a62f9880d8a52df487676d47c3698a864)` & pId,const `[`STOParameters`](#structezw_1_1smccore_1_1_i_safe_motion_service_1_1_s_t_o_parameters)` & pParameters)` {#classezw_1_1smccore_1_1_i_safe_motion_service_1a1c942e93481a5bc1842cc157b71d167c}

Modify the safety function STO parameters of the specified STO id. NOTA : Modification is allowed only in NMT state Pre-operational.

#### Parameters
* `pId` Id of the STO. 


* `pParameters` The STO safety application parameters. 





#### Returns
ERROR_NONE if no error occurred

### `public ezw_error_t getSLSParameters(const `[`SLSId`](#classezw_1_1smccore_1_1_i_safe_motion_service_1af9a3e7557f9976350f7dcd8ec9002181)` & pId,`[`SLSParameters`](#structezw_1_1smccore_1_1_i_safe_motion_service_1_1_s_l_s_parameters)` & pParameters,uint16_t & pSignature) const` {#classezw_1_1smccore_1_1_i_safe_motion_service_1afae923d927e6fcd69058a7ac1d55ef9c}

Retrieve the SLS safety application parameters of the specified SLS id.

#### Parameters
* `pId` Id of the SLS. 


* `pParameters` The SLS safety application parameters. 


* `pSignature` The SLS safety application configuration signature. 





#### Returns
ERROR_NONE if no error occurred

### `public ezw_error_t setSLSParameters(const `[`SLSId`](#classezw_1_1smccore_1_1_i_safe_motion_service_1af9a3e7557f9976350f7dcd8ec9002181)` & pId,const `[`SLSParameters`](#structezw_1_1smccore_1_1_i_safe_motion_service_1_1_s_l_s_parameters)` & pParameters)` {#classezw_1_1smccore_1_1_i_safe_motion_service_1aa59c9a8ad0c07b57cf84dc96c267e438}

Modify the safety function SLS parameters of the specified SLS id. NOTA : Modification is allowed only in NMT state Pre-operational.

#### Parameters
* `pId` Id of the SLS. 


* `pParameters` The SLS safety application parameters. 





#### Returns
ERROR_NONE if no error occurred

### `public ezw_error_t getSDIParameters(const `[`SDIId`](#classezw_1_1smccore_1_1_i_safe_motion_service_1af3aa910a001660cb96060ab0b05ce52c)` & pId,`[`SDIParameters`](#structezw_1_1smccore_1_1_i_safe_motion_service_1_1_s_d_i_parameters)` & pParameters,uint16_t & pSignature) const` {#classezw_1_1smccore_1_1_i_safe_motion_service_1a620817262cd40f7629b8688d09624529}

Retrieve the SDI safety application parameters of the specified SDI id.

#### Parameters
* `pId` Id of the SDI. 


* `pParameters` The SDI safety application parameters. 


* `pSignature` The SDI safety application configuration signature. 





#### Returns
ERROR_NONE if no error occurred

### `public ezw_error_t setSDIParameters(const `[`SDIId`](#classezw_1_1smccore_1_1_i_safe_motion_service_1af3aa910a001660cb96060ab0b05ce52c)` & pId,const `[`SDIParameters`](#structezw_1_1smccore_1_1_i_safe_motion_service_1_1_s_d_i_parameters)` & pParameters)` {#classezw_1_1smccore_1_1_i_safe_motion_service_1a31379d33edefc3d64354918bcd76ec7a}

Modify the safety function SDI parameters of the specified SDI id. NOTA : Modification is allowed only in NMT state Pre-operational.

#### Parameters
* `pId` Id of the SDI. 


* `pParameters` The SDI safety application parameters. 





#### Returns
ERROR_NONE if no error occurred

### `public ezw_error_t getSBCParameters(const `[`SBCId`](#classezw_1_1smccore_1_1_i_safe_motion_service_1a77246d628a91bf387edddaee3defb618)` & pId,`[`SBCParameters`](#structezw_1_1smccore_1_1_i_safe_motion_service_1_1_s_b_c_parameters)` & pParameters,uint16_t & pSignature) const` {#classezw_1_1smccore_1_1_i_safe_motion_service_1a77b6eafd770b987b4316bc00387f3e68}

Retrieve the SBC safety application parameters of the specified SBC id.

#### Parameters
* `pId` Id of the SBC. 


* `pParameters` The SBC safety application parameters. 


* `pSignature` The SBC safety application configuration signature. 





#### Returns
ERROR_NONE if no error occurred

### `public ezw_error_t getSMSParameters(const `[`SMSId`](#classezw_1_1smccore_1_1_i_safe_motion_service_1aea8dd47c0bd8cfd893c4bd24e70921a2)` & pId,`[`SMSParameters`](#structezw_1_1smccore_1_1_i_safe_motion_service_1_1_s_m_s_parameters)` & pParameters,uint16_t & pSignature) const` {#classezw_1_1smccore_1_1_i_safe_motion_service_1a90346fda3363d015a5c50d9e8585daac}

Retrieve the SMS safety application parameters of the specified SMS id.

#### Parameters
* `pId` Id of the SMS. 


* `pParameters` The SMS safety application parameters. 


* `pSignature` The SMS safety application configuration signature. 





#### Returns
ERROR_NONE if no error occurred

### `public ezw_error_t setSMSParameters(const `[`SMSId`](#classezw_1_1smccore_1_1_i_safe_motion_service_1aea8dd47c0bd8cfd893c4bd24e70921a2)` & pId,const `[`SMSParameters`](#structezw_1_1smccore_1_1_i_safe_motion_service_1_1_s_m_s_parameters)` & pParameters)` {#classezw_1_1smccore_1_1_i_safe_motion_service_1a208c12f1735ec098f08e9fa46e089a5d}

Modify the safety function SMS parameters of the specified SMS id. NOTA : Modification is allowed only in NMT state Pre-operational.

#### Parameters
* `pId` Id of the SMS. 


* `pParameters` The SMS safety application parameters. 





#### Returns
ERROR_NONE if no error occurred

### `public ezw_error_t getSLSaParameters(const `[`SLSaId`](#classezw_1_1smccore_1_1_i_safe_motion_service_1a805acb16d70d8a04d5b2d9ae25e2a831)` & pId,SLSaParameters & pParameters,uint16_t & pSignature) const` {#classezw_1_1smccore_1_1_i_safe_motion_service_1ac1e678111ae913b18d8b3ed11155b413}

Retrieve the SLSa safety application parameters of the specified SLSa id.

#### Parameters
* `pId` Id of the SLSa. 


* `pParameters` The SLSa safety application parameters. 


* `pSignature` The SLSa safety application configuration signature. 





#### Returns
ERROR_NONE if no error occurred

### `public ezw_error_t setSLSaParameters(const `[`SLSaId`](#classezw_1_1smccore_1_1_i_safe_motion_service_1a805acb16d70d8a04d5b2d9ae25e2a831)` & pId,const SLSaParameters & pParameters)` {#classezw_1_1smccore_1_1_i_safe_motion_service_1a6c217ebd9a65e75ea193987ac6deea5b}

Modify the safety function SLSa parameters of the specified SLSa id. NOTA : Modification is allowed only in NMT state Pre-operational.

#### Parameters
* `pId` Id of the SLSa. 


* `pParameters` The SLSa safety application parameters. 





#### Returns
ERROR_NONE if no error occurred

### `public ezw_error_t getSafetyFunctionOutput(const `[`SafetyFunctionId`](#classezw_1_1smccore_1_1_i_safe_motion_service_1aa185e2d74ea19870933a1e1c7598f367)` & pSafetyFunctionId,bool & pStatus) const` {#classezw_1_1smccore_1_1_i_safe_motion_service_1a6e5830412132456a23880c1a8800d2d0}

Retrieve the consolidated safety function status of the specified safety function id.

#### Parameters
* `pSafetyFunctionId` Id of the safety function. 


* `pStatus` True if the consolidated safety function is enabled. 





#### Returns
ERROR_NONE if no error occurred

### `public ezw_error_t getSafetyFunctionOutputs(std::vector< `[`SafetyFunctionOuputStatus`](#structezw_1_1smccore_1_1_i_safe_motion_service_1_1_safety_function_ouput_status)` > & pItems) const` {#classezw_1_1smccore_1_1_i_safe_motion_service_1ad0d7d9da31daeb8aaf202c0e518cff98}

Retrieve all the consolidated safety function statuses.

#### Parameters
* `pItems` Indicates all the consolidated safety function statuses. 





#### Returns
ERROR_NONE if no error occurred

# struct `SafetyFunctionOuputStatus` {#structezw_1_1smccore_1_1_i_safe_motion_service_1_1_safety_function_ouput_status}




Indicates the consolidated status of a safety function.

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`public `[`SafetyFunctionId`](#classezw_1_1smccore_1_1_i_safe_motion_service_1aa185e2d74ea19870933a1e1c7598f367)` safety_function_id` | 
`public bool status` | 

## Members

### `public `[`SafetyFunctionId`](#classezw_1_1smccore_1_1_i_safe_motion_service_1aa185e2d74ea19870933a1e1c7598f367)` safety_function_id` {#structezw_1_1smccore_1_1_i_safe_motion_service_1_1_safety_function_ouput_status_1a2091b06fe99ba957ad29157845cd6424}



Id of the safety function.

### `public bool status` {#structezw_1_1smccore_1_1_i_safe_motion_service_1_1_safety_function_ouput_status_1ad1f0bff7112206922c9d5a87adad6f2b}



True if the consolidated safety function is enabled.

# struct `SafetyWordMapping` {#structezw_1_1smccore_1_1_i_safe_motion_service_1_1_safety_word_mapping}




Represents a safety status/control word mapping (up to 8 functions : one function by bit).

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`public `[`SafetyFunctionId`](#classezw_1_1smccore_1_1_i_safe_motion_service_1aa185e2d74ea19870933a1e1c7598f367)` safety_function_0` | 
`public `[`SafetyFunctionId`](#classezw_1_1smccore_1_1_i_safe_motion_service_1aa185e2d74ea19870933a1e1c7598f367)` safety_function_1` | 
`public `[`SafetyFunctionId`](#classezw_1_1smccore_1_1_i_safe_motion_service_1aa185e2d74ea19870933a1e1c7598f367)` safety_function_2` | 
`public `[`SafetyFunctionId`](#classezw_1_1smccore_1_1_i_safe_motion_service_1aa185e2d74ea19870933a1e1c7598f367)` safety_function_3` | 
`public `[`SafetyFunctionId`](#classezw_1_1smccore_1_1_i_safe_motion_service_1aa185e2d74ea19870933a1e1c7598f367)` safety_function_4` | 
`public `[`SafetyFunctionId`](#classezw_1_1smccore_1_1_i_safe_motion_service_1aa185e2d74ea19870933a1e1c7598f367)` safety_function_5` | 
`public `[`SafetyFunctionId`](#classezw_1_1smccore_1_1_i_safe_motion_service_1aa185e2d74ea19870933a1e1c7598f367)` safety_function_6` | 
`public `[`SafetyFunctionId`](#classezw_1_1smccore_1_1_i_safe_motion_service_1aa185e2d74ea19870933a1e1c7598f367)` safety_function_7` | 

## Members

### `public `[`SafetyFunctionId`](#classezw_1_1smccore_1_1_i_safe_motion_service_1aa185e2d74ea19870933a1e1c7598f367)` safety_function_0` {#structezw_1_1smccore_1_1_i_safe_motion_service_1_1_safety_word_mapping_1a783bbf3ede09f970f5953da6a5193d4f}



The safety function id mapped on the bit 0.

### `public `[`SafetyFunctionId`](#classezw_1_1smccore_1_1_i_safe_motion_service_1aa185e2d74ea19870933a1e1c7598f367)` safety_function_1` {#structezw_1_1smccore_1_1_i_safe_motion_service_1_1_safety_word_mapping_1ad1dcde2a8748bcd4b9082f3d0920038c}



The safety function id mapped on the bit 1.

### `public `[`SafetyFunctionId`](#classezw_1_1smccore_1_1_i_safe_motion_service_1aa185e2d74ea19870933a1e1c7598f367)` safety_function_2` {#structezw_1_1smccore_1_1_i_safe_motion_service_1_1_safety_word_mapping_1a3f175b8a71e9a01bb65311af577cf464}



The safety function id mapped on the bit 2.

### `public `[`SafetyFunctionId`](#classezw_1_1smccore_1_1_i_safe_motion_service_1aa185e2d74ea19870933a1e1c7598f367)` safety_function_3` {#structezw_1_1smccore_1_1_i_safe_motion_service_1_1_safety_word_mapping_1ae82ca79e68a07ca70750112a75fe500f}



The safety function id mapped on the bit 3.

### `public `[`SafetyFunctionId`](#classezw_1_1smccore_1_1_i_safe_motion_service_1aa185e2d74ea19870933a1e1c7598f367)` safety_function_4` {#structezw_1_1smccore_1_1_i_safe_motion_service_1_1_safety_word_mapping_1a70700d5a9e857b93454038f12b75cc5e}



The safety function id mapped on the bit 4.

### `public `[`SafetyFunctionId`](#classezw_1_1smccore_1_1_i_safe_motion_service_1aa185e2d74ea19870933a1e1c7598f367)` safety_function_5` {#structezw_1_1smccore_1_1_i_safe_motion_service_1_1_safety_word_mapping_1a7bcc79e84b01641258c01bd26973718a}



The safety function id mapped on the bit 5.

### `public `[`SafetyFunctionId`](#classezw_1_1smccore_1_1_i_safe_motion_service_1aa185e2d74ea19870933a1e1c7598f367)` safety_function_6` {#structezw_1_1smccore_1_1_i_safe_motion_service_1_1_safety_word_mapping_1a10b78a5e387685f967c0ac3c51d844fe}



The safety function id mapped on the bit 6.

### `public `[`SafetyFunctionId`](#classezw_1_1smccore_1_1_i_safe_motion_service_1aa185e2d74ea19870933a1e1c7598f367)` safety_function_7` {#structezw_1_1smccore_1_1_i_safe_motion_service_1_1_safety_word_mapping_1acb07182b19114e4bf89fabb64d409f91}



The safety function id mapped on the bit 7.

# struct `SafetyWordType` {#structezw_1_1smccore_1_1_i_safe_motion_service_1_1_safety_word_type}




Represents a safety status/control word (up to 8 functions : one function by bit).

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`public bool safety_function_0` | 
`public bool safety_function_1` | 
`public bool safety_function_2` | 
`public bool safety_function_3` | 
`public bool safety_function_4` | 
`public bool safety_function_5` | 
`public bool safety_function_6` | 
`public bool safety_function_7` | 

## Members

### `public bool safety_function_0` {#structezw_1_1smccore_1_1_i_safe_motion_service_1_1_safety_word_type_1a9912cf583a6b3036ed3dcfda8278de31}



The safety function state mapped on the bit 0.

### `public bool safety_function_1` {#structezw_1_1smccore_1_1_i_safe_motion_service_1_1_safety_word_type_1abed35fb1db4aa1fc678c9bbf3d5851f3}



The safety function state mapped on the bit 1.

### `public bool safety_function_2` {#structezw_1_1smccore_1_1_i_safe_motion_service_1_1_safety_word_type_1ac962ec81959777b00840bbdc2209fdb4}



The safety function state mapped on the bit 2.

### `public bool safety_function_3` {#structezw_1_1smccore_1_1_i_safe_motion_service_1_1_safety_word_type_1a0268a839943ddbb2f47b173b8cc2da05}



The safety function state mapped on the bit 3.

### `public bool safety_function_4` {#structezw_1_1smccore_1_1_i_safe_motion_service_1_1_safety_word_type_1a411a27edd50ea81a836cb7384c71bd8a}



The safety function state mapped on the bit 4.

### `public bool safety_function_5` {#structezw_1_1smccore_1_1_i_safe_motion_service_1_1_safety_word_type_1a39b779975f05428f16a3b52b6a32ae6e}



The safety function state mapped on the bit 5.

### `public bool safety_function_6` {#structezw_1_1smccore_1_1_i_safe_motion_service_1_1_safety_word_type_1a31b68f431cf59018f1819ea94b963802}



The safety function state mapped on the bit 6.

### `public bool safety_function_7` {#structezw_1_1smccore_1_1_i_safe_motion_service_1_1_safety_word_type_1a566be576c146de4cd46f17157fa4e2f3}



The safety function state mapped on the bit 7.

# struct `SBCParameters` {#structezw_1_1smccore_1_1_i_safe_motion_service_1_1_s_b_c_parameters}




Represents the SBC safety application parameters.

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`public uint16_t brake_time_delay` | 

## Members

### `public uint16_t brake_time_delay` {#structezw_1_1smccore_1_1_i_safe_motion_service_1_1_s_b_c_parameters_1af20979aabfe35da6660d48d6327518d3}



Indicates the configured time to close the brake(s).

# struct `SDIParameters` {#structezw_1_1smccore_1_1_i_safe_motion_service_1_1_s_d_i_parameters}




Represents the SDI safety application parameters.

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`public uint32_t velocity_zero_window_u32` | 

## Members

### `public uint32_t velocity_zero_window_u32` {#structezw_1_1smccore_1_1_i_safe_motion_service_1_1_s_d_i_parameters_1a5d7ed00a3e4349395ff08d94ce60ccc9}



Indicates the configured velocity within the zero-window.

# struct `SLSaParameters` {#structezw_1_1smccore_1_1_i_safe_motion_service_1_1_s_l_sa_parameters}






## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`public uint16_t time_to_positive_velocity_monitoring` | 
`public uint32_t positive_velocity_limit_u32` | 
`public uint16_t time_for_positive_velocity_in_limits` | 
`public uint16_t time_to_negative_velocity_monitoring` | 
`public uint32_t negative_velocity_limit_u32` | 
`public uint16_t time_for_negative_velocity_in_limits` | 
`public bool sto_error_reaction` | 

## Members

### `public uint16_t time_to_positive_velocity_monitoring` {#structezw_1_1smccore_1_1_i_safe_motion_service_1_1_s_l_sa_parameters_1a8d44e4e00e1885440e71ef066ed24ff2}



Indicates the configured delay of activating the positive SLSa function.

### `public uint32_t positive_velocity_limit_u32` {#structezw_1_1smccore_1_1_i_safe_motion_service_1_1_s_l_sa_parameters_1a0ecc22ad981d9d0838afa9084363e7fe}



Indicates the configured positive speed limit.

### `public uint16_t time_for_positive_velocity_in_limits` {#structezw_1_1smccore_1_1_i_safe_motion_service_1_1_s_l_sa_parameters_1ae6d780f9383b5cff5e4d0fcbd4c04f71}



Indicates the configured time for the positve velocity within the configured limits.

### `public uint16_t time_to_negative_velocity_monitoring` {#structezw_1_1smccore_1_1_i_safe_motion_service_1_1_s_l_sa_parameters_1a31feb01dbec6b73b44895eea667fe8e4}



Indicates the configured delay of activating the negative SLSa function.

### `public uint32_t negative_velocity_limit_u32` {#structezw_1_1smccore_1_1_i_safe_motion_service_1_1_s_l_sa_parameters_1a1cef364a4a83a6cf9d193020120f79f2}



Indicates the configured negative speed limit.

### `public uint16_t time_for_negative_velocity_in_limits` {#structezw_1_1smccore_1_1_i_safe_motion_service_1_1_s_l_sa_parameters_1a70a24b29fea8d69b014c16d8e874d486}



Indicates the configured time for the negative velocity within the configured limits.

### `public bool sto_error_reaction` {#structezw_1_1smccore_1_1_i_safe_motion_service_1_1_s_l_sa_parameters_1a41d47f8accd8ee7f5ca4fca7022fb1c9}



Indicates the configured SLSa error reaction when the configured velocity limits are exceeded.

* False means no reaction


* True means a STO reaction is required.

# struct `SLSParameters` {#structezw_1_1smccore_1_1_i_safe_motion_service_1_1_s_l_s_parameters}




Represents the SLS safety application parameters.

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`public uint16_t time_to_velocity_monitoring` | 
`public uint32_t velocity_limit_u32` | 
`public uint16_t time_for_velocity_in_limits` | 
`public bool sto_error_reaction` | 

## Members

### `public uint16_t time_to_velocity_monitoring` {#structezw_1_1smccore_1_1_i_safe_motion_service_1_1_s_l_s_parameters_1a13a02a5f13faa422f8ef20bfe562c15a}



Indicates the configured delay of activating the SLS function.

### `public uint32_t velocity_limit_u32` {#structezw_1_1smccore_1_1_i_safe_motion_service_1_1_s_l_s_parameters_1ab38e1e0ef684f592e08c34bfc0051ad9}



Indicates the configured speed limit.

### `public uint16_t time_for_velocity_in_limits` {#structezw_1_1smccore_1_1_i_safe_motion_service_1_1_s_l_s_parameters_1ab487cd709fd4a96d1eac8d368335e96d}



Indicates the configured time for the velocity within the configured limits.

### `public bool sto_error_reaction` {#structezw_1_1smccore_1_1_i_safe_motion_service_1_1_s_l_s_parameters_1a41d47f8accd8ee7f5ca4fca7022fb1c9}



Indicates the configured SLS error reaction when the configured velocity or deceleration limits are exceeded.

* False means no reaction


* True means a STO reaction is required.

# struct `SMSParameters` {#structezw_1_1smccore_1_1_i_safe_motion_service_1_1_s_m_s_parameters}




Represents the SMS safety application parameters.

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`public uint32_t velocity_maximum_positive_u32` | 
`public uint32_t velocity_maximum_negative_u32` | 
`public bool sto_error_reaction` | 

## Members

### `public uint32_t velocity_maximum_positive_u32` {#structezw_1_1smccore_1_1_i_safe_motion_service_1_1_s_m_s_parameters_1ab38bae635592b96bbf3616b9440957d8}



Indicates the configured maximum velocity in positive direction. Default value : 0.

### `public uint32_t velocity_maximum_negative_u32` {#structezw_1_1smccore_1_1_i_safe_motion_service_1_1_s_m_s_parameters_1a7fc2999a8de9494101d28dcb8acd6f02}



Indicates the configured maximum velocity in negative direction. Default value : 0.

### `public bool sto_error_reaction` {#structezw_1_1smccore_1_1_i_safe_motion_service_1_1_s_m_s_parameters_1a41d47f8accd8ee7f5ca4fca7022fb1c9}



Indicates the configured SMS error reaction when the configured velocity limits are exceeded.

* False means no reaction


* True means a STO reaction is required.

# struct `STOParameters` {#structezw_1_1smccore_1_1_i_safe_motion_service_1_1_s_t_o_parameters}




Represents the STO safety application parameters.

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`public bool restart_acknowledge_behavior` | 
`public uint32_t activate_sbc` | 

## Members

### `public bool restart_acknowledge_behavior` {#structezw_1_1smccore_1_1_i_safe_motion_service_1_1_s_t_o_parameters_1aac8bda3f2819d4e8f761cd2d08ac4e6a}



Indicates the configured STO restart acknowledge behavior. A value of TRUE shall Indicates that the STO restart is manual, and a value of FALSE shall Indicates that the STO restart is automatically performed. Default value : TRUE.

### `public uint32_t activate_sbc` {#structezw_1_1smccore_1_1_i_safe_motion_service_1_1_s_t_o_parameters_1af4415b57d7cf9ef2392888664e340d60}



Indicate, which command shall be performed by means of a pointer (index and sub-index) to the command parameter e.g. 6688 0100h. A value of 0000 0000h shall Indicates that no brake shall be used. Default value : 0000 0000h.

# class `IService` {#classezw_1_1smccore_1_1_i_service}

```
class IService
  : public ICoreService
  : public IInternalService
  : public INMTService
  : public IEMCYService
  : public IPDSService
  : public ISafeMotionService
  : public ICommunicationService
  : public IManufacturerService
  : public IVelocityModeService
  : public ISRDOService
  : public ICANOpenService
```  





## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`public virtual  ~IService() = default` | 

## Members

### `public virtual  ~IService() = default` {#classezw_1_1smccore_1_1_i_service_1a8d120acbc856223c1c67c1ef07942074}





# class `ISRDOService` {#classezw_1_1smccore_1_1_i_s_r_d_o_service}


CIA304 : SRDO (Safety Related Data Object). This is similar to a PDO, but additional properties are defined. These are:

* cyclic data transmission with timeout monitoring


* Double transmission of usage data, one of which is inverted bit by bit


* Check the data consistency


* Check the time interval between the inverted and non-inverted data


* Backup of the configuration through a CRC.





NOTA : To make an entire SRDO configuration valid, a flag must be set to Index 0x13FE in the object dictionary. This flag is automatically set to an invalid configuration for every write access that is done to a safety-related SRDO parameter. After completing the configuration, this flag must be set to a valid configuration.

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`struct `[``SRDOMapping``](#structezw_1_1smccore_1_1_i_s_r_d_o_service_1_1_s_r_d_o_mapping)        | 
`struct `[``SRDOParameters``](#structezw_1_1smccore_1_1_i_s_r_d_o_service_1_1_s_r_d_o_parameters)        | 
`public virtual  ~ISRDOService() = default` | 
`public ezw_error_t getSRDOParameters(const `[`SRDOId`](#classezw_1_1smccore_1_1_i_s_r_d_o_service_1ada13879d88402c6df07a0cb76901e613)` & pId,`[`SRDODirection`](#classezw_1_1smccore_1_1_i_s_r_d_o_service_1aae1dfab76a67a9ee6cc355f4d19541be)` & pDirection,`[`SRDOParameters`](#structezw_1_1smccore_1_1_i_s_r_d_o_service_1_1_s_r_d_o_parameters)` & pParameters,uint16_t & pSignature) const` | Retrieve the communication parameters of the specified SRDO id.
`public ezw_error_t setSRDOParameters(const `[`SRDOId`](#classezw_1_1smccore_1_1_i_s_r_d_o_service_1ada13879d88402c6df07a0cb76901e613)` & pId,const `[`SRDOParameters`](#structezw_1_1smccore_1_1_i_s_r_d_o_service_1_1_s_r_d_o_parameters)` & pParameters)` | Modify the communication parameters of the specified SRDO id.
`public ezw_error_t getSRDOMapping(const `[`SRDOId`](#classezw_1_1smccore_1_1_i_s_r_d_o_service_1ada13879d88402c6df07a0cb76901e613)` & pId,`[`SRDOMapping`](#structezw_1_1smccore_1_1_i_s_r_d_o_service_1_1_s_r_d_o_mapping)` & pMapping) const` | Retrieve the mapping parameters of the specified SRDO id.
`public ezw_error_t getSRDOConfigurationValidity(bool & pIsvalid) const` | Retrieve the SRDO configuration valid flag (0x13fe => 0xA5 the configuration is valid; other values the configuration is invalid).
`public ezw_error_t setSRDOConfigurationValidity()` | Modify the SRDO configuration valid flag (0x13fe => 0xA5 the configuration is valid; other values the configuration is invalid).

## Members

### `struct `[``SRDOMapping``](#structezw_1_1smccore_1_1_i_s_r_d_o_service_1_1_s_r_d_o_mapping) {#structezw_1_1smccore_1_1_i_s_r_d_o_service_1_1_s_r_d_o_mapping}



Indicates the mapping parameters of a SRDO.
### `struct `[``SRDOParameters``](#structezw_1_1smccore_1_1_i_s_r_d_o_service_1_1_s_r_d_o_parameters) {#structezw_1_1smccore_1_1_i_s_r_d_o_service_1_1_s_r_d_o_parameters}



Indicates the communication parameters of a SRDO. NOTA : COB IDs in the range from 0x100 to 0x180 are used so that the transmission in the CANopen network does not interfere with other services and the priority of the CAN IDs is higher than that of PDOs.
### `public virtual  ~ISRDOService() = default` {#classezw_1_1smccore_1_1_i_s_r_d_o_service_1a4c03ef04eaf63a37a8ea1613c810fb45}





### `public ezw_error_t getSRDOParameters(const `[`SRDOId`](#classezw_1_1smccore_1_1_i_s_r_d_o_service_1ada13879d88402c6df07a0cb76901e613)` & pId,`[`SRDODirection`](#classezw_1_1smccore_1_1_i_s_r_d_o_service_1aae1dfab76a67a9ee6cc355f4d19541be)` & pDirection,`[`SRDOParameters`](#structezw_1_1smccore_1_1_i_s_r_d_o_service_1_1_s_r_d_o_parameters)` & pParameters,uint16_t & pSignature) const` {#classezw_1_1smccore_1_1_i_s_r_d_o_service_1a790f6bbece905ddce3a3f28714e9c4c4}

Retrieve the communication parameters of the specified SRDO id.

#### Parameters
* `pId` The SRDO id. 


* `pDirection` The direction of the SRDO. 


* `pParameters` The communication parameters of the SRDO. 


* `pSignature` The signature of the SRDO. 





#### Returns
ERROR_NONE if no error occurred

### `public ezw_error_t setSRDOParameters(const `[`SRDOId`](#classezw_1_1smccore_1_1_i_s_r_d_o_service_1ada13879d88402c6df07a0cb76901e613)` & pId,const `[`SRDOParameters`](#structezw_1_1smccore_1_1_i_s_r_d_o_service_1_1_s_r_d_o_parameters)` & pParameters)` {#classezw_1_1smccore_1_1_i_s_r_d_o_service_1a1975e23114b78124b3d41b927a616673}

Modify the communication parameters of the specified SRDO id.

#### Parameters
* `pId` The SRDO id. 


* `pParameters` The new communication parameters. 





#### Returns
ERROR_NONE if no error occurred

### `public ezw_error_t getSRDOMapping(const `[`SRDOId`](#classezw_1_1smccore_1_1_i_s_r_d_o_service_1ada13879d88402c6df07a0cb76901e613)` & pId,`[`SRDOMapping`](#structezw_1_1smccore_1_1_i_s_r_d_o_service_1_1_s_r_d_o_mapping)` & pMapping) const` {#classezw_1_1smccore_1_1_i_s_r_d_o_service_1a750e067ed5762650e76bc1dc12cd9449}

Retrieve the mapping parameters of the specified SRDO id.

#### Parameters
* `pId` The SRDO id. 


* `pMapping` The configured mapping parameters. 





#### Returns
ERROR_NONE if no error occurred

### `public ezw_error_t getSRDOConfigurationValidity(bool & pIsvalid) const` {#classezw_1_1smccore_1_1_i_s_r_d_o_service_1ac799397bc988b608915e750f6c3ba6d1}

Retrieve the SRDO configuration valid flag (0x13fe => 0xA5 the configuration is valid; other values the configuration is invalid).

#### Parameters
* `pIsvalid` The SRDO configuration valid flag. 





#### Returns
ERROR_NONE if no error occurred

### `public ezw_error_t setSRDOConfigurationValidity()` {#classezw_1_1smccore_1_1_i_s_r_d_o_service_1a4c68ad0fb7c332f1274ff28d4ffb0407}

Modify the SRDO configuration valid flag (0x13fe => 0xA5 the configuration is valid; other values the configuration is invalid).

#### Returns
ERROR_NONE if no error occurred

# struct `SRDOMapping` {#structezw_1_1smccore_1_1_i_s_r_d_o_service_1_1_s_r_d_o_mapping}




Indicates the mapping parameters of a SRDO.

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`public uint8_t mapping_count` | 
`public std::vector< uint32_t > data` | 

## Members

### `public uint8_t mapping_count` {#structezw_1_1smccore_1_1_i_s_r_d_o_service_1_1_s_r_d_o_mapping_1a25cd67df406833199e0ac58dbec0b6e2}



Indicates the number of mapped data in SRDO. 2 mapping entry by data object (normal and inverted).

### `public std::vector< uint32_t > data` {#structezw_1_1smccore_1_1_i_s_r_d_o_service_1_1_s_r_d_o_mapping_1a8eb11bd6f7b149a072f0fd2385739034}



Indicates the mapped data in SRDO.

# struct `SRDOParameters` {#structezw_1_1smccore_1_1_i_s_r_d_o_service_1_1_s_r_d_o_parameters}




Indicates the communication parameters of a SRDO. NOTA : COB IDs in the range from 0x100 to 0x180 are used so that the transmission in the CANopen network does not interfere with other services and the priority of the CAN IDs is higher than that of PDOs.

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`public bool valid` | 
`public uint16_t sct` | 
`public uint8_t srvt` | 
`public `[`SRDOTransmissionType`](#classezw_1_1smccore_1_1_i_s_r_d_o_service_1a19cf7dd7893704cd0d0dba7e26a1ba7d)` transmission_type` | 
`public uint16_t can_id1` | 
`public uint16_t can_id2` | 

## Members

### `public bool valid` {#structezw_1_1smccore_1_1_i_s_r_d_o_service_1_1_s_r_d_o_parameters_1a28e3c179a86f337095088b3ca02a2b2a}



Indicates the validity of the SRDO. True if exists / is valid; False if does not exist / is not valid. SRDO1 and SRDO2 are not modifiable.

### `public uint16_t sct` {#structezw_1_1smccore_1_1_i_s_r_d_o_service_1_1_s_r_d_o_parameters_1a34b7142a02f2576f8da62e66b3b4b906}



Indicates the refresh time SCT (Safety Cycle Time) of the SRDO. Default : 25ms.

### `public uint8_t srvt` {#structezw_1_1smccore_1_1_i_s_r_d_o_service_1_1_s_r_d_o_parameters_1a73a1b8ad0e44c442c1c1f3d430160f71}



Indicates the srvt (Safety-related Validation Time) time between the 2 CAN messages of an SRDO. Default : 20ms.

### `public `[`SRDOTransmissionType`](#classezw_1_1smccore_1_1_i_s_r_d_o_service_1a19cf7dd7893704cd0d0dba7e26a1ba7d)` transmission_type` {#structezw_1_1smccore_1_1_i_s_r_d_o_service_1_1_s_r_d_o_parameters_1a58ec68894f671da61fdd24cbfdef0ad8}



Indicates the transmission type. Fix : PDO_ASYNC_FE.

### `public uint16_t can_id1` {#structezw_1_1smccore_1_1_i_s_r_d_o_service_1_1_s_r_d_o_parameters_1a42247c09e1aa67c8d7c691e3dc626c66}



Indicates the CAN identifier (11 bits) for plain data.

### `public uint16_t can_id2` {#structezw_1_1smccore_1_1_i_s_r_d_o_service_1_1_s_r_d_o_parameters_1a85b2e4cb7582e8ad35a7fb5ad1e18733}



Indicates the CAN identifier (11 bits) for bitwise inverted data.

# class `IVelocityModeService` {#classezw_1_1smccore_1_1_i_velocity_mode_service}


[CIA402-2] The velocity mode controls the speed (velocity) of the SWD product but not its position. The selection of a new target velocity use a acceleration / deceleration ramp. The velocity mode is composed of three main functions:

* velocity limit function


* ramp function


* velocity control function and is composed of the following factor functions:


* factor function


* reverse factor function.

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`struct `[``VelocityModeControlword``](#structezw_1_1smccore_1_1_i_velocity_mode_service_1_1_velocity_mode_controlword)        | 
`struct `[``VelocityModeParameters``](#structezw_1_1smccore_1_1_i_velocity_mode_service_1_1_velocity_mode_parameters)        | 
`struct `[``VelocityModeStatusword``](#structezw_1_1smccore_1_1_i_velocity_mode_service_1_1_velocity_mode_statusword)        | 
`public virtual  ~IVelocityModeService() = default` | 
`public ezw_error_t setTargetVelocity(const int16_t & pTargetVelocity)` | Indicate the required velocity of the system. It will be multiplied by the vl dimension factor and the vl set-point factor. The value shall be given in user-defined velocity units or in revolutions per minute (r/min), if the vl dimension factor and the vl set-point factor are not implemented or have the value 1. Positive values shall indicate forward direction and negative values shall indicate reverse direction.
`public ezw_error_t getTargetVelocity(int16_t & pTargetVelocity) const` | Retrieve the actual required velocity of the system.
`public ezw_error_t getVelocityActualValue(int32_t & pVelocityActualValue) const` | Retrieve the actual velocity of the system. The value shall be given in the very same unit as the vl target velocity. Positive values shall indicate forward direction and negative values shall indicate reverse direction.
`public ezw_error_t getVelocityActualValueTS(int32_t & pVelocityActualValue,uint64_t & pTimestamp) const` | Retrieve the actual velocity of the system. The value shall be given in the very same unit as the vl target velocity. Positive values shall indicate forward direction and negative values shall indicate reverse direction.
`public ezw_error_t getVelocityDemand(int16_t & pVelocityDemand) const` | Retrieve the instantaneous velocity generated by the ramp function. The value shall be given in the very same unit as the vl target velocity. Positive values shall indicate forward direction and negative values shall indicate reverse direction. NOTA : The velocity demand depends of the velocity polarity parameter.
`public ezw_error_t getPositionValue(int32_t & pPositionValue) const` | Retrieve the position of the SWD product in motor revolution increments. The SWD product resolution is 30 increments par revolution. NOTA : The counter direction depends of the position polarity parameter.
`public ezw_error_t getPositionValueTS(int32_t & pPositionValue,uint64_t & pTimestamp) const` | Retrieve the position of the SWD product in motor revolution increments. The SWD product resolution is 30 increments par revolution. NOTA : The counter direction depends of the position polarity parameter.
`public ezw_error_t getVelocityModeParameters(`[`VelocityModeParameters`](#structezw_1_1smccore_1_1_i_velocity_mode_service_1_1_velocity_mode_parameters)` & pParams) const` | Retrieve the velocity mode parameters.
`public ezw_error_t setVelocityModeParameters(const `[`VelocityModeParameters`](#structezw_1_1smccore_1_1_i_velocity_mode_service_1_1_velocity_mode_parameters)` & pParams)` | Modify the velocity mode parameters.
`public ezw_error_t getVelocityModeStatusword(`[`VelocityModeStatusword`](#structezw_1_1smccore_1_1_i_velocity_mode_service_1_1_velocity_mode_statusword)` & pParams) const` | Retrieve the velocity mode statusword.
`public ezw_error_t getVelocityModeControlword(`[`VelocityModeControlword`](#structezw_1_1smccore_1_1_i_velocity_mode_service_1_1_velocity_mode_controlword)` & pParams) const` | Retrieve the velocity mode controlword.
`public ezw_error_t setEnableRamp(const bool & pEnableRamp)` | Modify the enable ramp flag into the velocity mode controlword.
`public ezw_error_t setUnlockRamp(const bool & pUnlockRamp)` | Modify the unlock ramp flag into the velocity mode controlword.
`public ezw_error_t setReferenceRamp(const bool & pReferenceRamp)` | Modify the reference ramp flag into the velocity mode controlword.
`public ezw_error_t setHalt(const bool & pHalt)` | Modify the halt flag into the velocity mode controlword.

## Members

### `struct `[``VelocityModeControlword``](#structezw_1_1smccore_1_1_i_velocity_mode_service_1_1_velocity_mode_controlword) {#structezw_1_1smccore_1_1_i_velocity_mode_service_1_1_velocity_mode_controlword}



[CIA402-2] Velocity mode controlword. The velocity mode use some bits of the CIA402 controlword to control the velocity control function.
### `struct `[``VelocityModeParameters``](#structezw_1_1smccore_1_1_i_velocity_mode_service_1_1_velocity_mode_parameters) {#structezw_1_1smccore_1_1_i_velocity_mode_service_1_1_velocity_mode_parameters}



[CIA402-2] Velocity mode parameters. The velocity mode use some parameters to control the velocity control function.
### `struct `[``VelocityModeStatusword``](#structezw_1_1smccore_1_1_i_velocity_mode_service_1_1_velocity_mode_statusword) {#structezw_1_1smccore_1_1_i_velocity_mode_service_1_1_velocity_mode_statusword}



[CIA402-2] Velocity mode statusword. The velocity mode use some bits of the CIA402 statusword to report some status.
### `public virtual  ~IVelocityModeService() = default` {#classezw_1_1smccore_1_1_i_velocity_mode_service_1adddd60bcf4a7198ab3c3e6492ab4281a}





### `public ezw_error_t setTargetVelocity(const int16_t & pTargetVelocity)` {#classezw_1_1smccore_1_1_i_velocity_mode_service_1a28c22c1b445697bb9155f27302fbf0e2}

Indicate the required velocity of the system. It will be multiplied by the vl dimension factor and the vl set-point factor. The value shall be given in user-defined velocity units or in revolutions per minute (r/min), if the vl dimension factor and the vl set-point factor are not implemented or have the value 1. Positive values shall indicate forward direction and negative values shall indicate reverse direction.

#### Parameters
* `pTargetVelocity` The required velocity (range : -2000 to 2000 r/min). 





#### Returns
ERROR_NONE if no error occurred

### `public ezw_error_t getTargetVelocity(int16_t & pTargetVelocity) const` {#classezw_1_1smccore_1_1_i_velocity_mode_service_1a54f3c733f820cc631d9d5a3d1d9f35a3}

Retrieve the actual required velocity of the system.

#### Parameters
* `pTargetVelocity` The actual required velocity of the system. 





#### Returns
ERROR_NONE if no error occurred

### `public ezw_error_t getVelocityActualValue(int32_t & pVelocityActualValue) const` {#classezw_1_1smccore_1_1_i_velocity_mode_service_1a913505eb9e2a73602c957867c87ef112}

Retrieve the actual velocity of the system. The value shall be given in the very same unit as the vl target velocity. Positive values shall indicate forward direction and negative values shall indicate reverse direction.

#### Parameters
* `pVelocityActualValue` The actual velocity of the system. 





#### Returns
ERROR_NONE if no error occurred

### `public ezw_error_t getVelocityActualValueTS(int32_t & pVelocityActualValue,uint64_t & pTimestamp) const` {#classezw_1_1smccore_1_1_i_velocity_mode_service_1afa502af1d055b0d10385472e1424aaf9}

Retrieve the actual velocity of the system. The value shall be given in the very same unit as the vl target velocity. Positive values shall indicate forward direction and negative values shall indicate reverse direction.

#### Parameters
* `pVelocityActualValue` The actual velocity of the system. 


* `pTimestamp` The timestamp in ms from 1970. 





#### Returns
ERROR_NONE if no error occurred

### `public ezw_error_t getVelocityDemand(int16_t & pVelocityDemand) const` {#classezw_1_1smccore_1_1_i_velocity_mode_service_1aa4eece74cf79faced193aa5595ca4d60}

Retrieve the instantaneous velocity generated by the ramp function. The value shall be given in the very same unit as the vl target velocity. Positive values shall indicate forward direction and negative values shall indicate reverse direction. NOTA : The velocity demand depends of the velocity polarity parameter.

#### Parameters
* `pVelocityDemand` The instantaneous velocity generated by the ramp function. 





#### Returns
ERROR_NONE if no error occurred

### `public ezw_error_t getPositionValue(int32_t & pPositionValue) const` {#classezw_1_1smccore_1_1_i_velocity_mode_service_1a64309e786f9725c9accfd0537df4e432}

Retrieve the position of the SWD product in motor revolution increments. The SWD product resolution is 30 increments par revolution. NOTA : The counter direction depends of the position polarity parameter.

#### Parameters
* `pPositionValue` The position of the SWD product in motor revolution increments. 





#### Returns
ERROR_NONE if no error occurred

### `public ezw_error_t getPositionValueTS(int32_t & pPositionValue,uint64_t & pTimestamp) const` {#classezw_1_1smccore_1_1_i_velocity_mode_service_1ad11c60817dca3dbdbcc5a9029115e498}

Retrieve the position of the SWD product in motor revolution increments. The SWD product resolution is 30 increments par revolution. NOTA : The counter direction depends of the position polarity parameter.

#### Parameters
* `pPositionValue` The position of the SWD product in motor revolution increments. 


* `pTimestamp` The timestamp in ms from 1970. 





#### Returns
ERROR_NONE if no error occurred

### `public ezw_error_t getVelocityModeParameters(`[`VelocityModeParameters`](#structezw_1_1smccore_1_1_i_velocity_mode_service_1_1_velocity_mode_parameters)` & pParams) const` {#classezw_1_1smccore_1_1_i_velocity_mode_service_1a79b680fe17b27ec7579d8a27f145cc24}

Retrieve the velocity mode parameters.

#### Parameters
* `pParams` The velocity mode parameters. 





#### Returns
ERROR_NONE if no error occurred

### `public ezw_error_t setVelocityModeParameters(const `[`VelocityModeParameters`](#structezw_1_1smccore_1_1_i_velocity_mode_service_1_1_velocity_mode_parameters)` & pParams)` {#classezw_1_1smccore_1_1_i_velocity_mode_service_1a12e2eb961195156722a4187712867d9d}

Modify the velocity mode parameters.

#### Parameters
* `pParams` The new velocity mode parameters. 





#### Returns
ERROR_NONE if no error occurred

### `public ezw_error_t getVelocityModeStatusword(`[`VelocityModeStatusword`](#structezw_1_1smccore_1_1_i_velocity_mode_service_1_1_velocity_mode_statusword)` & pParams) const` {#classezw_1_1smccore_1_1_i_velocity_mode_service_1ac44b8724e0a4911b8f7825090fdaea13}

Retrieve the velocity mode statusword.

#### Parameters
* `pParams` The velocity mode statusword. 





#### Returns
ERROR_NONE if no error occurred

### `public ezw_error_t getVelocityModeControlword(`[`VelocityModeControlword`](#structezw_1_1smccore_1_1_i_velocity_mode_service_1_1_velocity_mode_controlword)` & pParams) const` {#classezw_1_1smccore_1_1_i_velocity_mode_service_1ab77fd3358147b6a8385d731c5a451f89}

Retrieve the velocity mode controlword.

#### Parameters
* `pParams` The velocity mode controlword. 





#### Returns
ERROR_NONE if no error occurred

### `public ezw_error_t setEnableRamp(const bool & pEnableRamp)` {#classezw_1_1smccore_1_1_i_velocity_mode_service_1a5500e3cbe7521a860914f4b461973f64}

Modify the enable ramp flag into the velocity mode controlword.

#### Parameters
* `pEnableRamp` If False, the velocity demand value shall be controlled in any other (manufacturer-specific) way, for example by a test function generator or manufacturer-specific halt function; else, the velocity demand value shall accord with ramp output value. 





#### Returns
ERROR_NONE if no error occurred

### `public ezw_error_t setUnlockRamp(const bool & pUnlockRamp)` {#classezw_1_1smccore_1_1_i_velocity_mode_service_1acedaec601418e8422a1d59e1ed95e0a7}

Modify the unlock ramp flag into the velocity mode controlword.

#### Parameters
* `pUnlockRamp` If False, the ramp output value shall be locked to current output value; else the ramp output value shall follow ramp input value. 





#### Returns
ERROR_NONE if no error occurred

### `public ezw_error_t setReferenceRamp(const bool & pReferenceRamp)` {#classezw_1_1smccore_1_1_i_velocity_mode_service_1a053710ebf822bbdcd117dc767eb3ce54}

Modify the reference ramp flag into the velocity mode controlword.

#### Parameters
* `pReferenceRamp` If False, the ramp input value shall be set to zero; else the ramp input value shall accord with ramp reference. 





#### Returns
ERROR_NONE if no error occurred

### `public ezw_error_t setHalt(const bool & pHalt)` {#classezw_1_1smccore_1_1_i_velocity_mode_service_1a5ffe6b598193da7544c9b795da039062}

Modify the halt flag into the velocity mode controlword.

#### Parameters
* `pHalt` If True, the motor shall be stopped. 





#### Returns
ERROR_NONE if no error occurred

# struct `VelocityModeControlword` {#structezw_1_1smccore_1_1_i_velocity_mode_service_1_1_velocity_mode_controlword}




[CIA402-2] Velocity mode controlword. The velocity mode use some bits of the CIA402 controlword to control the velocity control function.

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`public bool enable_ramp` | 
`public bool unlock_ramp` | 
`public bool reference_ramp` | 
`public bool halt` | 

## Members

### `public bool enable_ramp` {#structezw_1_1smccore_1_1_i_velocity_mode_service_1_1_velocity_mode_controlword_1a552179de8b6b69dd6f41b29fa5c175aa}



If False, the velocity demand value shall be controlled in any other (manufacturer-specific) way, for example by a test function generator or manufacturer-specific halt function; else, the velocity demand value shall accord with ramp output value.

### `public bool unlock_ramp` {#structezw_1_1smccore_1_1_i_velocity_mode_service_1_1_velocity_mode_controlword_1af112508884f747cbe9d1ea436e3dda5e}



If False, the ramp output value shall be locked to current output value; else the ramp output value shall follow ramp input value.

### `public bool reference_ramp` {#structezw_1_1smccore_1_1_i_velocity_mode_service_1_1_velocity_mode_controlword_1a6f1324e8fe58520773fda09b2b14c0f7}



If False, the ramp input value shall be set to zero; else the ramp input value shall accord with ramp reference.

### `public bool halt` {#structezw_1_1smccore_1_1_i_velocity_mode_service_1_1_velocity_mode_controlword_1a709a225534eea96ed808a3a80d9cf5e4}



If True, the motor shall be stopped.

# struct `VelocityModeParameters` {#structezw_1_1smccore_1_1_i_velocity_mode_service_1_1_velocity_mode_parameters}




[CIA402-2] Velocity mode parameters. The velocity mode use some parameters to control the velocity control function.

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`public uint32_t vl_velocity_min_amount` | 
`public uint32_t vl_velocity_max_amount` | 
`public uint32_t vl_velocity_acceleration_delta_speed` | 
`public uint16_t vl_velocity_acceleration_delta_time` | 
`public uint32_t vl_velocity_deceleration_delta_speed` | 
`public uint16_t vl_velocity_deceleration_delta_time` | 
`public uint32_t vl_velocity_quick_stop_delta_speed` | 
`public uint16_t vl_velocity_quick_stop_delta_time` | 
`public int16_t vl_set_point_factor_numerator` | 
`public int16_t vl_set_point_factor_denominator` | 
`public int32_t vl_dimension_factor_numerator` | 
`public int32_t vl_dimension_factor_denominator` | 

## Members

### `public uint32_t vl_velocity_min_amount` {#structezw_1_1smccore_1_1_i_velocity_mode_service_1_1_velocity_mode_parameters_1aaa102af59eea50fc2e1e319762a4a64b}



The configured minimum amount of velocity. The value shall be given in rotations per minute (r/min) or in user-defined velocity units. Default : 40 r/min

### `public uint32_t vl_velocity_max_amount` {#structezw_1_1smccore_1_1_i_velocity_mode_service_1_1_velocity_mode_parameters_1a64461be7b15ab96654daf7ac6de88a12}



The configured maximum amount of velocity. The values shall be given in rotations per minute (r/min) or in user-defined velocity units. Default : 2000 r/min

### `public uint32_t vl_velocity_acceleration_delta_speed` {#structezw_1_1smccore_1_1_i_velocity_mode_service_1_1_velocity_mode_parameters_1a51ff361ffce2692069653d3233654787}



The configured delta speed of the slope of the acceleration ramp. The values shall be given in rotations per minute (r/min) or in user-defined velocity units. Default : 500 r/min.

### `public uint16_t vl_velocity_acceleration_delta_time` {#structezw_1_1smccore_1_1_i_velocity_mode_service_1_1_velocity_mode_parameters_1a48e197f14c05a0d3228223998abbf265}



The configured delta time of the slope of the acceleration ramp. The values shall be given in second or in user-defined time units. Default : 1s.

### `public uint32_t vl_velocity_deceleration_delta_speed` {#structezw_1_1smccore_1_1_i_velocity_mode_service_1_1_velocity_mode_parameters_1a52f1c69a04006a5cd88343afbcb2da55}



The configured delta speed of the slope of the deceleration ramp. The values shall be given in rotations per minute (r/min) or in user-defined velocity units. Default : 500 r/min.

### `public uint16_t vl_velocity_deceleration_delta_time` {#structezw_1_1smccore_1_1_i_velocity_mode_service_1_1_velocity_mode_parameters_1a489069075f7cd9598e455d1111a8ec94}



The configured delta time of the slope of the deceleration ramp. The values shall be given in second or in user-defined time units. Default : 1s.

### `public uint32_t vl_velocity_quick_stop_delta_speed` {#structezw_1_1smccore_1_1_i_velocity_mode_service_1_1_velocity_mode_parameters_1a74320fdcdb8bacfd1784dc3f65ca5aae}



The configured delta speed of the slope of the deceleration ramp for quick stop. The values shall be given in rotations per minute (r/min) or in user-defined velocity units. Default : 1000 r/min.

### `public uint16_t vl_velocity_quick_stop_delta_time` {#structezw_1_1smccore_1_1_i_velocity_mode_service_1_1_velocity_mode_parameters_1af74de5c7e5b53467f52463352ef2a1df}



The configured delta time of the slope of the deceleration ramp for quick stop. The values shall be given in second or in user-defined time units. Default : 1s.

### `public int16_t vl_set_point_factor_numerator` {#structezw_1_1smccore_1_1_i_velocity_mode_service_1_1_velocity_mode_parameters_1a32f87062ce1f5376f2ee63f4e2a8c635}



The configured numerator of the velocity set-point factor. Default : 1

### `public int16_t vl_set_point_factor_denominator` {#structezw_1_1smccore_1_1_i_velocity_mode_service_1_1_velocity_mode_parameters_1a08272572c5d4fd6d6cf62e7c8677e741}



The configured denominator of the velocity set-point factor. Default : 1

### `public int32_t vl_dimension_factor_numerator` {#structezw_1_1smccore_1_1_i_velocity_mode_service_1_1_velocity_mode_parameters_1a4c22d7a082304e2de09a383ae841f669}



The configured numerator of the velocity dimension factor. Default : 1

### `public int32_t vl_dimension_factor_denominator` {#structezw_1_1smccore_1_1_i_velocity_mode_service_1_1_velocity_mode_parameters_1a13bebb56e2b39c345ad744c47d79b6d9}



The configured denominator of the velocity dimension factor. Default : 1

# struct `VelocityModeStatusword` {#structezw_1_1smccore_1_1_i_velocity_mode_service_1_1_velocity_mode_statusword}




[CIA402-2] Velocity mode statusword. The velocity mode use some bits of the CIA402 statusword to report some status.

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`public bool internal_limit_active` | 

## Members

### `public bool internal_limit_active` {#structezw_1_1smccore_1_1_i_velocity_mode_service_1_1_velocity_mode_statusword_1ad6a999af07601087d46ed24e776751b5}



If True, the velocity demand value is limited to vl_velocity_max_amount / vl_velocity_min_amount.

