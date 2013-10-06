JAMF-ExtensionAttribute
=======================

An Extension Attribute to display the current Watchman Monitoring status in a JSS


Purpose
=======
This Monitoring Client ships with an ExportStatus tool, for use with third party systems like JAMF's Casper Suite.

Calling 

    /Library/MonitoringClient/Utilities/ExportStatus
    
Will cause the Monitoring Client to output a summary of the current system status to a plist at

    /Library/MonitoringClient/ClientData/UnifiedStatus.plist
    
This plist has a summary of all plugin reports, as well boolean keys which indicate whether a computer requires attention.


Plist Contents
==============

The resulting plist contains 5 keys:

|Key            |Type|Purpose
|----------------|-----|------
|Client URL     |URL|View the full details in the Watchman Monitoring Server
|CurrentError    |BOOL|Is a plugin currently reporting a problem
|CurrentWarning |BOOL|Is a plugin currently sending informational output (aside from "all's well")
|ReportData     |String|A plain-text list of plugins and their status.
|ReportTime      |DateTime| The time the output was generated



Sample Output
=============

```
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
<plist version="1.0">
<dict>
	<key>ClientURL</key>
	<string>https://demo.monitoringclient.com/client/YYYYMMDD-XXXX-YYYYYY</string>
	<key>CurrentError</key>
	<true/>
	<key>CurrentWarning</key>
	<true/>
	<key>ReportData</key>
	<string>Check Laptop Battery	OK
Check LightSpeed Server	Notice
Check Munki	OK
Check Root Capacity	Warning
Check SoftRAID Volumes	OK
Check Specified Applications	OK
Check Specified Volumes	Warning
Check SuperDuper!	OK
Report Backup Minder Errors	OK
Report CCC Errors	OK
Report Client Status	OK
Report Disk I/O Errors	OK
Report Internal IP Address	OK
Report Kernel Panic Count	OK
Report LightSpeed Server Expirations	Notice
Report LightSpeed Server Webstore Log Errors	OK
Report Malware	OK
Report Network Status	OK
Report POST Errors	OK
Report RAM Errors	OK
Report Reboot Events	Warning
Report SMART Errors	OK
Time Machine Exclusions	OK

https://macconsultinggroup-com.watchmanmonitoring.com/client/20130818-N9F4-XCI4JD</string>
	<key>ReportTime</key>
	<date>2013-10-05T13:49:03Z</date>
</dict>
</plist>
```
