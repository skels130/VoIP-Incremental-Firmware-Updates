# VoIP-Incremental-Firmware-Updates
Apache configuration files to to incremental stepped upgrades for phones

YEALINK:
Phones will pull the hardware common config file (ie y000000000066.cfg), which points them to download the hardware id number.rom (ie 66.rom).

The apache config will rewrite the request based on the current firmware version, to incrementally upgrade to the latest firmware. 
