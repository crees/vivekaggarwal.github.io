# Visonic Powerlink 3 Configuration Checklist

The following is my checklist of how to configure the Visonic Powerlink 3 for the Visonic cloud self management service. 

> NOTE: I take no responsibility for anything that may happen to your PowerMaster system.

## Prerequisites

- **Check** PowerMaster is running version 17 or above
- **Check** that the PowerLink 3 module is connected and that a valid IP address is visible
- **Access** to the Master Installer codes

# Process

This process works for Broadband only connections. If you wish to configure phone line or any other means, please have a look at the installation guide.

- INSTALLER MODE
	- 4.COMMUNICATION
		- 3:C.S. REPORTING
			- 01:REPORT EVENTS = **all *backup**
			- 02:1st RPRT CHAN = **Broadband**
			- 03:2nd RRPT CHAN - **Disabled**
			- 04:3rd RRPT CHAN - **Disabled**
			- 11:RCVR1 ACCOUNT - **CLEAR** (Using UNLOCK button)
			- 12:RCVR2 ACCOUNT - **CLEAR** (Using UNLOCK button)
			- 16:PSTN/GSM RCV1 - **CLEAR** (Using UNLOCK button)
			- 17:PSTN/GSM RCV1 - **CLEAR** (Using UNLOCK button)
			- 21:IP RCVR 1 - **052.058.105.181**
			- 22:IP RCVR 2 - **000.000.000.000**
			- 53:COM.FAIL RPRT
				- PSTN FAIL = **do not report**

# Mobile App
- Download Visonic-GO ([Apple](https://itunes.apple.com/gb/app/visonic-go/id989778273?mt=8), [Android](https://play.google.com/store/apps/details?id=com.visonic.VisonicAlert&hl=en_GB))
- Host Server: **visonic.tycomonitor.com**
- Panel ID: _Panel ID from Serial Number_
- User Code: _Valid user code_
