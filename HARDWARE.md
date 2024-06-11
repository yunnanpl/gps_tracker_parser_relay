# Hardware

Description of hardware used, with its internal settings and other findings.

## ST-915 L
Usually L means it is a 4G device.

This is a response from RCONF SMS command. It is a single line (but usually 2 messages).
```
ST-915/4G,ID:xxxxxxxxxx,PW:0000,U1:,U2:,U3:,MODE:GPRS-MOVE,DAILY:ON,GEO FENCE:OFF,OVER SPEED:OFF,VOICE:OFF,SHAKE ALARM:OFF,SLEEP:ON,APN:my.apn.net,,,IP:my.server.net:8090,GPRS UPLOAD TIME:30s,TIME ZONE:0.0
```

Dividing it into separate pieces, we get the following:
 * ST-915/4G,
 * ID:xxxxxxxxxx,
 * PW:0000,U1:,U2:,U3:,
 * MODE:GPRS-MOVE,
 * DAILY:ON,
 * GEO FENCE:OFF,
 * OVER SPEED:OFF,
 * VOICE:OFF,
 * SHAKE ALARM:OFF,
 * SLEEP:ON,
 * APN:my.apn.net,,,
 * IP:my.server.net:8090,
 * GPRS UPLOAD TIME:30s,
 * TIME ZONE:0.0

This is a response from CXZT SMS command. Strangely, it is an SMS with line breaks.
```
ST915(70SALASCD)_V_1.0 2023/08/23
ID:7028917064
IP:my.server.net 8090
UT:30,600,1800
BAT:92
APN:my.apn.net
GPS:V-20-14
GSM:16
```
This is cleanly divided into pieces already:
 * ST915(70SALASCD)_V_1.0 2023/08/23
 * ID:xxxxxxxxxx
 * IP:my.server.net 8090
 * UT:30,600,1800
 * BAT:92
 * APN:my.apn.net
 * GPS:V-20-14
 * GSM:16

## ST-904L (L means it is the 4G version)

As above, L means it is a 4G device.

The response from RCONF command, is very similar, but slightly different than from the device above.
```
ST-904:V5.42,ID:xxxxxxxxxx,UP:0000,U1:,U2:,U3:,MODE:GPRS-MOVE,GEO FENCE: OFF,OVER SPEED:OFF,VOICE:ON,SHAKE ALARM:OFF,SLEEP:1,APN:my.apn.net,,,IP:my.server.net,8090,GPRS UPLOAD TIME:30,TIME ZONE:E00,BATTYER:80
```

Dividing it into pieces we get (comma-separated):
 * ST-904:V5.42,
 * ID:xxxxxxxxxx,
 * UP:0000,U1:,U2:,U3:,
 * MODE:GPRS-MOVE,
 * GEO FENCE: OFF,
 * OVER SPEED:OFF,
 * VOICE:ON,
 * SHAKE ALARM:OFF,
 * SLEEP:1,
 * APN:my.apn.net,,,
 * IP:my.server.net,8090,
 * GPRS UPLOAD TIME:30,
 * TIME ZONE:E00,
 * BATTYER:80

Some extraordinary english knowledge is visible in the last variable for battery.

The response from CXZT command, is significantly different.
```
W07_ENSMS_10D6J_B39_V5.42-TQ*ID:xxxxxxxxxx*my.server.net:8090*A:my.apn.net*G:V*4G:14*PW:0-0*BT:3578*AC:0*SP:60*F:30*V:5988*SF:0*SD:1*LBS:0|*R:19|260693|3
```

Dividing it into pieces we get (star-separated !):

 * W07_ENSMS_10D6J_B39_V5.42-TQ*
 * ID:xxxxxxxxxx*
 * my.server.net:8090*
 * A:my.apn.net*
 * G:V*
 * 4G:14*
 * PW:0-0*
 * BT:3578*
 * AC:0*
 * SP:60*
 * F:30*
 * V:5988*
 * SF:0*
 * SD:1*
 * LBS:0|*
 * R:19|260693|3


