# VoIP-Incremental-Firmware-Updates
Apache configuration files to to incremental stepped upgrades for phones
## Using config files
Add .conf file for applicable phones into a configuration directory in Apache. I would recomend storing in the conf-available folder in /etc/apache2/, and hardlinking to conf-enabled. 
## Phones:
### YEALINK:
Phones will pull the hardware common config file (ie y000000000066.cfg), which points them to download the {hardware id number}.rom (ie 66.rom):
```
#!version:1.0.0.1

##File header "#!version:1.0.0.1" can not be edited or deleted, and must be placed in the first line.##
##This template file is applicable to SIP-T28P/T26P/T22P/T20P/T21P/T19P/T46G/T42G/T41P IP phones running firmware version 72 or later.##
##For more information on configuration parameters, refer to Yealink_SIP-T2_Series_T19P_T4_Series_IP_Phones_Auto_Provisioning_Guide.##

#######################################################################################
##                                   Configure the access URL of firmware            ##       
#######################################################################################
###It configures the access URL of the firmware file.
###The default value is blank.It takes effect after a reboot.
static.firmware.url = https://yourfirmwareserver.com/yealink/66.rom
```

The apache config will rewrite the request based on the current firmware version, to incrementally upgrade to the latest firmware. 
The configuration file assumes that you're storing firmware files at /var/www/html/yealink, and that all firmwares are named in only version format (66.86.0.160.rom, etc)
