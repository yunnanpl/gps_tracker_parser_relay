# sinotrack_gps_tracking
Tips and tricks for SinoTrack GPS, to use with OwnTracks and Homeassistant

## How to setup SinoTrack
Most important settings are
* APN
  * to access internet
* mode
  * to set in what mode should the GPS work (usually WORK mode)
* server
  * to what server the messages should be sent

## Settings
There are more settings than your manual says !!!
You can find it in multiple sources in internet (and here https://forocoches.com/foro/showthread.php?t=5926074).

By tweaking the settings you can get much better battery life with the same functionality.

Basic settings:
* APN
  * 8040000 ip/domain
* mode
  * WORK0000
    * active mode, always send with fixed delay even if not active
    * most battery consuming
  * MOVE0000
    * normal mode, usually sleeping and more active while moving
  * STANDBY0000
    * standby mode, do nothing until a request (SMS) is received
* 8040000 ip/domain port
  * where the data should be sent
  * NEW DEVICES - device is doing DNS resolving, so it is possible to put a domain name there (also Dynamic DNS !)
  * port can be anything, and default port for sinotrack is 8090

Important advanced settings:
* SLEEP0000 int
  * int is a value in minutes, between sleep modes
  * setting this 0, disables sleep and forces kind of WORK mode
* 8050000 int
  * int is a value in seconds between messages (while key/engine is ON, for car bound devices)
  * some pages recommend not to set it below 10 (even if it should be possible to go to 5)
* 8090000 int
  * int is a value in seconds between messages (while key/engine is OFF, for car bound devices)
  * some pages recommend not to set it below 10 (even if it should be possible to go to 5)

Other functions:
* RCONF
  * get the configuration
* RESET
  * reset device 
* 6690000
  * request google maps link
* 8960000E00
  * set time zone, by default E00 (east 00)

