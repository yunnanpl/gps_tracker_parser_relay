# GPS tracker parser/relay
The idea of this page is to use the cheaper, subscription-free GPS trackers, for variety of solutions and applications.

At the monment the main focus is to use the SinoTrack (https://www.sinotrack.com/) GPS tracker, together with OwnTracks (https://owntracks.org/), with Home Assistant (https://www.home-assistant.io/).
In the future probably the TK Star will be checked (https://www.tk-star.com/) (when I will own one).

Clearly, as usual, the project should be as simple as possible, and have the least dependencies, etc.

IMPORTANT: Depending on a country, one should think about 4G tracker instead of the 2G only... even if the price is higher, battery last shorter and mobile phone range may be shorter... ;)

# Approach
## Idea, steps, coarse plan
 * get a tracker, and working compatible sim card (usually an IoT card)
 * redirect the messages to my own server, instead the official server
 * parse the messages and use those for something else (OwnTracks, MQTT, Traccar, whatever)
   * it seems these trackers use so called h02 format for transmitting messages (see link at the bottom) 
 * (alternative idea, to pass the packets back to SinoTrack servers, in order to use those as backup
 * (alternative idea 2, send the current parking position (or positions of the car overall) to google maps)

## Requirements
 * python
 * a 24h running computer
   * static IP is recommended BUT not necessary, as Dynamic DNS domain does very well too !
 * open port (default 8090, but can be anything)
 * the magic script :)

## Expected issues

# Instructions
Tips and tricks for SinoTrack GPS. It may vary depending on the model you get.

The models with L at the end are usually the 4G models (mine are ST-915L and ST-904L).

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
  * 8030000 ip/domain
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
  * int is a value of activity in minutes, after wakeup !!!
  * that means, for maximal battery/transfer saving, set it to 1
  * setting this 0, disables sleep and forces kind of WORK mode (so no sleep)
  * default is 5
* 8050000 int
  * int is a value in seconds between messages (while key/engine is ON, for car bound devices)
  * some pages recommend not to set it below 10 (even if it should be possible to go to 5)
  * default 20
* 8090000 int
  * int is a value in seconds between messages (while key/engine is OFF, for car bound devices)
  * some pages recommend not to set it below 10 (even if it should be possible to go to 5)
  * default 300
* 6650000xxxx
  * send location at least once a day, on given time
  * xxxx means HHMM (hours and minutes )
  * INFO this does not seem to work on mine ST-915L

Other functions:
* RCONF
  * get the configuration
* RESET
  * reset device 
* 6690000
  * request google maps link
  * INFO this triggers a wakeup too, after ~1 minute
* 8960000xxx
  * xxx is a timezone value, for example E00
  * set time zone, by default E00 (east 00)



# Other links

 * https://github.com/Junker/h02own
 * https://github.com/engemamhosain/Sinotrack-gps-device
 * https://github.com/jonamat/gps-tracker-rebouncer

