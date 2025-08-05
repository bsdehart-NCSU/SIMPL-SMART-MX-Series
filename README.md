\# \*\*Crestron SIMPL+ Module: SMART Display MX (V5) RS-232 Control\*\*



\*\*VERSION:\*\* 3.1



\## \*\*GENERAL DESCRIPTION\*\*



This module provides comprehensive RS-232 control for specific SMART Technologies interactive flat panel displays. It allows for management of various display functions including:



\* Power (On, Off, Standby, Toggle)  

\* Input Source Selection (HDMI, VGA, OPS, USB-C, Android)  

\* Brightness Level Control (Set, Up, Down)  

\* Volume Level Control (Set, Up, Down)  

\* Speaker Mute Control (On, Off)  

\* Microphone Mute Control (On, Off)  

\* Video Freeze (On, Off)  

\* Screen Shade (On, Off)  

\* Information Queries (Firmware Version, Model Number, Serial Number, Part Number)  

\* Status Polling for continuous feedback updates.



The module handles sending commands to the display and parsing responses to provide feedback on its current state. It features a robust power transition lock, configurable and granular polling, an optional emulation mode for instant feedback, and debug information.



\## \*\*COMPATIBILITY\*\*



This module is specifically designed and tested for the following SMART display series:



\* SMART Board MX (V5) series (including MX (V5) Pro models)  

\* SMART Board MX (V5) Plus series



\*\*Potential Partial Compatibility:\*\*



\* \*\*SMART Board QX Pro series:\*\* This series utilizes a similar RS-232 command structure for many common functions (power, input, volume, etc.). While basic operations are likely to be compatible, full functionality across all module features is not guaranteed and should be verified through testing. There may be differences in specific parameter values or advanced commands.



\*\*Not Compatible:\*\*



\* Other SMART Board series, such as the GX series, use different RS-232 command protocols and are not compatible with this module.



Always verify functionality with the specific display model in use if it is not listed as a primary compatible model.



\## \*\*FEATURES\*\*



\* Direct RS-232 control of compatible SMART displays.  

\* Discrete and toggle power commands with feedback.  

\* Robust power transition lock with a 20-second timeout to prevent the module from getting stuck.  

\* \*\*Emulation Mode:\*\* Optional feature provides instant feedback for a more responsive user experience, which is then verified by live feedback from the display.  

\* Multiple input source selection with feedback.  

\* Analog and incremental control for brightness and volume with feedback.  

\* Discrete mute controls for speakers and microphone with feedback.  

\* Video freeze and screen shade controls with feedback.  

\* Ability to query display information such as firmware version and serial number.  

\* \*\*Intelligent Polling:\*\* Configurable status polling is automatically deferred during power transitions and only queries relevant commands when the display is confirmed to be on.  

\* \*\*Granular Polling Control:\*\* Individual digital inputs allow the programmer to enable or disable polling for specific functions (e.g., only poll for volume and input status).  

\* Initialization sequence to query current display status on startup.  

\* Debug output for troubleshooting.  

\* Exception handling for a known display anomaly where conflicting power states are reported.



\## \*\*INPUTS\*\*



\### \*\*Power Control\*\*



| Signal Name | Type | Description |

| :---- | :---- | :---- |

| Power\\\_On\\\_trig | DIGITAL | Momentary high pulse sends the "Power On" command to the display. |

| Power\\\_Off\\\_trig | DIGITAL | Momentary high pulse sends the "Power Off" command to the display. |

| Power\\\_Standby\\\_trig | DIGITAL | Momentary high pulse sends the "Power Standby" command to the display. |

| Power\\\_Toggle\\\_trig | DIGITAL | Momentary high pulse toggles the power state. If the display is on, it sends a "Standby" command. If it is off or in standby, it sends an "On" command. |



\### \*\*Input Selection\*\*



| Signal Name | Type | Description |

| :---- | :---- | :---- |

| Input\\\_Select\\\_HDMI1\\\_trig | DIGITAL | Momentary high pulse selects HDMI1 as the active input source. |

| Input\\\_Select\\\_HDMI2\\\_trig | DIGITAL | Momentary high pulse selects HDMI2 as the active input source. |

| Input\\\_Select\\\_HDMI3\\\_trig | DIGITAL | Momentary high pulse selects HDMI3 as the active input source. |

| Input\\\_Select\\\_HDMI4\\\_trig | DIGITAL | Momentary high pulse selects HDMI4 as the active input source. |

| Input\\\_Select\\\_VGA1\\\_trig | DIGITAL | Momentary high pulse selects VGA1 as the active input source. |

| Input\\\_Select\\\_OPS1\\\_trig | DIGITAL | Momentary high pulse selects OPS1 as the active input source. |

| Input\\\_Select\\\_USBC1\\\_trig | DIGITAL | Momentary high pulse selects USB-C 1 as the active input source. |

| Input\\\_Select\\\_USBC2\\\_trig | DIGITAL | Momentary high pulse selects USB-C 2 as the active input source. |

| Input\\\_Select\\\_Android\\\_trig | DIGITAL | Momentary high pulse selects the built-in Android system as the active source. |



\### \*\*Brightness Control\*\*



| Signal Name | Type | Description |

| :---- | :---- | :---- |

| Brightness\\\_Level\\\_ain | ANALOG | Sets the desired brightness level (0-100). Use with Set\\\_Brightness\\\_Level\\\_trig. |

| Set\\\_Brightness\\\_Level\\\_trig | DIGITAL | Momentary high pulse sends the brightness level from Brightness\\\_Level\\\_ain. |

| Brightness\\\_Up\\\_trig | DIGITAL | Momentary high pulse increases the brightness level by a predefined step (e.g., 5%). |

| Brightness\\\_Down\\\_trig | DIGITAL | Momentary high pulse decreases the brightness level by a predefined step (e.g., 5%). |



\### \*\*Volume Control\*\*



| Signal Name | Type | Description |

| :---- | :---- | :---- |

| Volume\\\_Level\\\_ain | ANALOG | Sets the desired volume level (0-100). Use with Set\\\_Volume\\\_Level\\\_trig. |

| Set\\\_Volume\\\_Level\\\_trig | DIGITAL | Momentary high pulse sends the volume level from Volume\\\_Level\\\_ain. |

| Volume\\\_Up\\\_trig | DIGITAL | Momentary high pulse increases the volume level by a predefined step (e.g., 5%). |

| Volume\\\_Down\\\_trig | DIGITAL | Momentary high pulse decreases the volume level by a predefined step (e.g., 5%). |



\### \*\*Speaker Mute Control\*\*



| Signal Name | Type | Description |

| :---- | :---- | :---- |

| Mute\\\_Speakers\\\_On\\\_trig | DIGITAL | Momentary high pulse mutes the display's speakers. |

| Mute\\\_Speakers\\\_Off\\\_trig | DIGITAL | Momentary high pulse un-mutes the display's speakers. |



\### \*\*Microphone Mute Control\*\*



| Signal Name | Type | Description |

| :---- | :---- | :---- |

| Mute\\\_Mic\\\_On\\\_trig | DIGITAL | Momentary high pulse mutes the display's microphone array. |

| Mute\\\_Mic\\\_Off\\\_trig | DIGITAL | Momentary high pulse un-mutes the display's microphone array. |



\### \*\*Video Freeze Control\*\*



| Signal Name | Type | Description |

| :---- | :---- | :---- |

| Video\\\_Freeze\\\_On\\\_trig | DIGITAL | Momentary high pulse freezes the current video image on the display. |

| Video\\\_Freeze\\\_Off\\\_trig | DIGITAL | Momentary high pulse un-freezes the video image. |



\### \*\*Screen Shade Control\*\*



| Signal Name | Type | Description |

| :---- | :---- | :---- |

| Screen\\\_Shade\\\_On\\\_trig | DIGITAL | Momentary high pulse activates the screen shade (blanks the screen). |

| Screen\\\_Shade\\\_Off\\\_trig | DIGITAL | Momentary high pulse deactivates the screen shade. |



\### \*\*Information Queries\*\*



| Signal Name | Type | Description |

| :---- | :---- | :---- |

| Query\\\_Firmware\\\_Version\\\_trig | DIGITAL | Momentary high pulse requests the display's firmware version. |

| Query\\\_Model\\\_Number\\\_trig | DIGITAL | Momentary high pulse requests the display's model number. |

| Query\\\_Serial\\\_Number\\\_trig | DIGITAL | Momentary high pulse requests the display's serial number. |

| Query\\\_Part\\\_Number\\\_trig | DIGITAL | Momentary high pulse requests the display's part number. |



\### \*\*Polling \& General Query\*\*



| Signal Name | Type | Description |

| :---- | :---- | :---- |

| Enable\\\_Polling | DIGITAL | When HIGH, enables periodic polling of all display statuses. When LOW, disables polling. |

| Poll\\\_Rate\\\_seconds | ANALOG | Sets the interval for status polling in whole seconds. (e.g., 60 \\= 60 seconds). Default: 15s. Min: 5s. Max: 300s. If 0 is input, the default rate is used. Changes take effect on the next poll cycle. |

| Enable\\\_Emulation | DIGITAL | When HIGH, feedback outputs will update instantly when a command is sent, providing a more responsive feel. This emulated state is superseded by any live feedback from the device. Default is LOW. |

| Query\\\_All\\\_Status\\\_trig | DIGITAL | Momentary high pulse manually queries all supported display statuses once. |

| Poll\\\_Input\\\_Source | DIGITAL | When HIGH, the active input source will be included in the polling cycle. Defaults to HIGH. |

| Poll\\\_Brightness | DIGITAL | When HIGH, the brightness level will be included in the polling cycle. Defaults to HIGH. |

| Poll\\\_Volume | DIGITAL | When HIGH, the volume level will be included in the polling cycle. Defaults to HIGH. |

| Poll\\\_Speaker\\\_Mute | DIGITAL | When HIGH, the speaker mute status will be included in the polling cycle. Defaults to HIGH. |

| Poll\\\_Mic\\\_Mute | DIGITAL | When HIGH, the microphone mute status will be included in the polling cycle. Defaults to HIGH. |

| Poll\\\_Video\\\_Freeze | DIGITAL | When HIGH, the video freeze status will be included in the polling cycle. Defaults to HIGH. |

| Poll\\\_Screen\\\_Shade | DIGITAL | When HIGH, the screen shade status will be included in the polling cycle. Defaults to HIGH. |



\### \*\*Serial Communication\*\*



| Signal Name | Type | Description |

| :---- | :---- | :---- |

| RS232\\\_rx$ | BUFFER | Connect to the RX$ input of a serial communication symbol (e.g., COM Port, Cresnet COM, etc.). Receives data from the SMART display. Max buffer size: 255 characters. |



\## \*\*OUTPUTS\*\*



\### \*\*Power Feedback\*\*



| Signal Name | Type | Description |

| :---- | :---- | :---- |

| Power\\\_Is\\\_On\\\_fb | DIGITAL | HIGH when the display is confirmed to be ON. LOW otherwise. |

| Power\\\_Is\\\_Off\\\_fb | DIGITAL | HIGH when the display is confirmed to be OFF. LOW otherwise. |

| Power\\\_Is\\\_Standby\\\_fb | DIGITAL | HIGH when the display is confirmed to be in STANDBY. LOW otherwise. |



\### \*\*Input Selection Feedback\*\*



| Signal Name | Type | Description |

| :---- | :---- | :---- |

| Is\\\_HDMI1\\\_fb | DIGITAL | HIGH when HDMI1 is the confirmed active input source. LOW otherwise. |

| Is\\\_HDMI2\\\_fb | DIGITAL | HIGH when HDMI2 is the confirmed active input source. LOW otherwise. |

| Is\\\_HDMI3\\\_fb | DIGITAL | HIGH when HDMI3 is the confirmed active input source. LOW otherwise. |

| Is\\\_HDMI4\\\_fb | DIGITAL | HIGH when HDMI4 is the confirmed active input source. LOW otherwise. |

| Is\\\_VGA1\\\_fb | DIGITAL | HIGH when VGA1 is the confirmed active input source. LOW otherwise. |

| Is\\\_OPS1\\\_fb | DIGITAL | HIGH when OPS1 is the confirmed active input source. LOW otherwise. |

| Is\\\_USBC1\\\_fb | DIGITAL | HIGH when USB-C 1 is the confirmed active input source. LOW otherwise. |

| Is\\\_USBC2\\\_fb | DIGITAL | HIGH when USB-C 2 is the confirmed active input source. LOW otherwise. |

| Is\\\_Android\\\_fb | DIGITAL | HIGH when the built-in Android system is the confirmed active source. LOW otherwise. |



\### \*\*Brightness Feedback\*\*



| Signal Name | Type | Description |

| :---- | :---- | :---- |

| Brightness\\\_Level\\\_fb | ANALOG | Reflects the current brightness level of the display (0-100). |



\### \*\*Volume Feedback\*\*



| Signal Name | Type | Description |

| :---- | :---- | :---- |

| Volume\\\_Level\\\_fb | ANALOG | Reflects the current volume level of the display (0-100). |



\### \*\*Speaker Mute Feedback\*\*



| Signal Name | Type | Description |

| :---- | :---- | :---- |

| Speakers\\\_Are\\\_Muted\\\_fb | DIGITAL | HIGH when the display's speakers are confirmed to be muted. LOW otherwise. |



\### \*\*Microphone Mute Feedback\*\*



| Signal Name | Type | Description |

| :---- | :---- | :---- |

| Mic\\\_Is\\\_Muted\\\_fb | DIGITAL | HIGH when the display's microphone array is confirmed to be muted. LOW otherwise. |



\### \*\*Video Freeze Feedback\*\*



| Signal Name | Type | Description |

| :---- | :---- | :---- |

| Video\\\_Is\\\_Frozen\\\_fb | DIGITAL | HIGH when the display's video image is confirmed to be frozen. LOW otherwise. |



\### \*\*Screen Shade Feedback\*\*



| Signal Name | Type | Description |

| :---- | :---- | :---- |

| Screen\\\_Shade\\\_Is\\\_On\\\_fb | DIGITAL | HIGH when the display's screen shade is confirmed to be active. LOW otherwise. |



\### \*\*Information Feedback\*\*



| Signal Name | Type | Description |

| :---- | :---- | :---- |

| Firmware\\\_Version\\\_fb$ | STRING | Reports the firmware version of the display. Max length: 60 characters. |

| Model\\\_Number\\\_fb$ | STRING | Reports the model number of the display. Max length: 60 characters. |

| Serial\\\_Number\\\_fb$ | STRING | Reports the serial number of the display. Max length: 60 characters. |

| Part\\\_Number\\\_fb$ | STRING | Reports the part number of the display. Max length: 60 characters. |



\### \*\*Polling Feedback\*\*



| Signal Name | Type | Description |

| :---- | :---- | :---- |

| Polling\\\_Active\\\_fb | DIGITAL | HIGH when status polling is currently active. LOW otherwise. |



\### \*\*Serial Communication \& Debug\*\*



| Signal Name | Type | Description |

| :---- | :---- | :---- |

| RS232\\\_tx$ | STRING | Connect to the TX$ output of a serial communication symbol. Transmits commands to the SMART display. Commands are terminated with a Carriage Return (CR \\- \\\\x0D). |

| Debug\\\_fb$ | STRING | Provides status messages, received responses, and error information from the module for troubleshooting purposes. Can be connected to a "Serial/ASCII Send" symbol. |



\## \*\*PARAMETERS\*\*



\* \*\*Enable\\\_Polling (Digital Input)\*\*  

&nbsp; \* \*\*Function:\*\* Controls the automatic status polling feature.  

&nbsp; \* \*\*HIGH:\*\* Polling is active. The module will periodically send query commands to the display to update all feedback signals.  

&nbsp; \* \*\*LOW:\*\* Polling is inactive. Feedback signals will only update when a command is sent, an explicit query is triggered, or an asynchronous message is received.  

&nbsp; \* \*\*Default State:\*\* Polling is disabled on module startup until Enable\\\_Polling is set high.  

\* \*\*Poll\\\_Rate\\\_seconds (Analog Input)\*\*  

&nbsp; \* \*\*Function:\*\* Sets the time interval between polling cycles when Enable\\\_Polling is high.  

&nbsp; \* \*\*Units:\*\* Value is in whole seconds.  

&nbsp; \* \*\*Example:\*\* An input value of 60 corresponds to a poll rate of 60 seconds.  

&nbsp; \* \*\*Default Value:\*\* 15 (15 seconds). This is used if Poll\\\_Rate\\\_seconds is 0 or not connected.  

&nbsp; \* \*\*Minimum Value:\*\* 5 (5 seconds). Values below this will be clamped to 5 seconds.  

&nbsp; \* \*\*Maximum Value:\*\* 300 (300 seconds / 5 minutes). Values above this will be clamped to 300 seconds.  

&nbsp; \* \*\*Behavior:\*\* Changes to this input are applied before the next scheduled poll. If polling is active and the rate is changed, the current poll cycle will complete, and the next poll will use the new interval.  

\* \*\*Enable\\\_Emulation (Digital Input)\*\*  

&nbsp; \* \*\*Function:\*\* Controls the instant feedback feature.  

&nbsp; \* \*\*HIGH:\*\* When a command is sent, the corresponding feedback output will update immediately to the \*intended\* state. This provides a more responsive user experience. This emulated state will be automatically corrected if/when a different live status is received from the display.  

&nbsp; \* \*\*LOW:\*\* Feedback outputs will only update when a response is received from the device.  

&nbsp; \* \*\*Default State:\*\* Emulation is disabled (LOW) by default.



\## \*\*OPERATIONS\*\*



\### \*\*Initialization\*\*



Upon program start or module reset, the module performs an initial sequence of queries to determine the current state of the display for:



\* Power Status  

\* Current Input Source  

\* Brightness Level  

\* Volume Level  

\* Speaker Mute Status  

\* Microphone Mute Status  

\* Video Freeze Status  

\* Screen Shade Status



This ensures that feedback signals are populated with the display's actual state shortly after startup, provided the display is responsive.



\### \*\*Power Control \& Transition Lock\*\*



The module features a robust locking mechanism to ensure stability during power state changes.



\* \*\*Initiating a Change:\*\* When a power command (Power\\\_On\\\_trig, Power\\\_Off\\\_trig, etc.) is triggered, the module enters a "power transition" state.  

\* \*\*Command Lock:\*\* While in this state, all other commands (including other power commands) are ignored to prevent conflicts while the display is warming up or shutting down.  

\* \*\*Confirmation:\*\* The lock is only released when the module receives a specific asynchronous response (e.g., \\#powerstate=on) from the display, confirming the transition is complete.  

\* \*\*Timeout:\*\* A 20-second timeout acts as a fail-safe. If the expected confirmation is not received within this time, the lock is automatically released to prevent the module from getting stuck.



\### \*\*Sending Commands\*\*



To control the display, pulse the corresponding digital trigger input (e.g., Power\\\_On\\\_trig, Input\\\_Select\\\_HDMI1\\\_trig). For analog settings like brightness or volume, set the desired value on the analog input (e.g., Volume\\\_Level\\\_ain) and then pulse the associated trigger (e.g., Set\\\_Volume\\\_Level\\\_trig).



\### \*\*Querying Status\*\*



\* \*\*Intelligent Polling:\*\* If Enable\\\_Polling is high, the module will query the power state at the defined interval. If the display is on, it will then proceed to query any other statuses that have their individual polling inputs (Poll\\\_Volume, etc.) set high. This prevents sending unnecessary commands to a display that is off. Polling is automatically paused during power transitions.  

\* \*\*Manual Query:\*\*  

&nbsp; \* To query a specific status (e.g., Firmware Version), pulse the corresponding query trigger (e.g., Query\\\_Firmware\\\_Version\\\_trig).  

&nbsp; \* To query all statuses at once, pulse Query\\\_All\\\_Status\\\_trig.



\### \*\*Response Handling\*\*



The module listens for responses from the display on the RS232\\\_rx$ input.



\* \*\*Solicited Responses:\*\* Responses to get commands or set commands will update the relevant feedback signals and internal state.  

\* \*\*Asynchronous Responses:\*\* The display sends unsolicited status updates (prefixed with \\#) when a setting is changed locally or a state change is complete. The module uses these for real-time feedback, especially for confirming power state transitions.



\## \*\*TROUBLESHOOTING \& NOTES\*\*



\* \*\*Communication Settings:\*\* Ensure the serial port connected to the SMART display is configured with the correct baud rate (typically 19200 for MX/QX series), parity (None), data bits (8), and stop bits (1) as specified by SMART for RS-232 control. (This module does not set COM port parameters; they must be configured in the Crestron program.)  

\* \*\*Wiring:\*\* Verify RS-232 wiring (TX, RX, GND) between the Crestron processor and the display. Ensure a straight-through serial cable is used, not a null-modem cable.  

\* \*\*Debug\\\_fb$ Output:\*\* This string output is crucial for troubleshooting. It provides information on:  

&nbsp; \* Module initialization.  

&nbsp; \* Commands being sent (implicitly).  

&nbsp; \* Raw or processed responses received.  

&nbsp; \* Polling activity.  

&nbsp; \* Timeout errors.  

&nbsp; \* Invalid or unknown commands reported by the display.  

\* \*\*Response Timeouts:\*\* If frequent timeouts occur, check physical connections, display responsiveness, COM port settings, and potential for excessive RS-232 bus traffic. The power transition timeout is set to 20 seconds.  

\* \*\*CR Terminator:\*\* All commands sent by this module are terminated with a Carriage Return (\\\\x0D). The module expects responses to also be CR-terminated and may strip Line Feeds (\\\\x0A).  

\* \*\*Polling and Performance:\*\* While polling provides up-to-date feedback, excessively fast polling rates (e.g., every 5-10 seconds) on a busy system or with a slow-responding device might impact performance. Adjust Poll\\\_Rate\\\_seconds as needed. The default of 15 seconds is generally a good balance.  

\* \*\*Power Saving Modes:\*\* Some displays have power-saving modes that might prevent them from responding to RS-232 commands when in a deep sleep state. It may be necessary to disable or adjust these modes on the display for reliable control.  

\* \*\*Standby Anomaly:\*\* This module contains specific logic to handle a known quirk where the display may respond with conflicting powerstate=standby and powerstate=on messages in the same data packet. If this occurs, the module will automatically retry the set powerstate=standby command after a 2-second delay.

