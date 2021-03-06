---
layout: post
title: Raspberry PI 3 one wire fix!
published: true
---

## Fixing Raspberry Pi dead usb ports:
![_config.yml](https://pbs.twimg.com/media/DApSHfzXgAQ65M6.jpg:large)
This week, i decided to power  an old Raspberry Pi and use it for monitoring a new webservice that i  built only to find out keyboard/mouse connected to PI are not working.


#### i found out that Raspberry pi boards have testpoints that can be used for troubleshooting:
According to Wikipedia, a test point is a "location within an electronic circuit that is used to either monitor the state of the circuitry or to inject test signals"  so basicly testpoint's will help me find out what is actually preventing usb ports to work!

#### bellow is a list of Raspberry Pi board test points:


| TestPoint ID | TestPoint Description |
|:--------------|:----------------------|
| PP1  | 5V  |
| PP4  | GND |
| PP5  | GND |
| PP6  | GND |
| PP7  | 5V after polyfuse |
| PP8  | 3V3 |
| PP9  | 1V8 |
| PP10  | Goes from 3V3 to 2V on brownout |
| PP11  | DAC_2V5 (for composite video DAC) |
| PP12  | AUD_2V5 (for PWM audio drivers) |
| PP13  | Goes from 3V3 to 2V on ACT activity |
| PP14  | SD_CLK |
| PP15  | SD_CMD |
| PP16  | SD_DAT0 |
| PP17  | SD_DAT1 |
| PP18 | SD_DAT2 |
| PP19  | SD_DAT13 |
| PP20  | H5V |
| PP21  | RUN signal (reset) |
| PP22 | Goes from 3V3 to 2V on activity of green (link) ethernet jack LED |
| PP23 | Goes from 3V3 to 2V on activity of yellow (speed) ethernet jack LED |
| PP24 | COMPVID |
| PP25 | AUDIO_L |
| PP26 | AUDI_R |
| PP27 | VBUS (USB 5V power) |
| PP28 | ETH_CLK (25.000 MHz) |
| PP29 | VC_TMS |
| PP30 | VC_TRST_N |
| PP31 | VC_CLK |
| PP32 | VC_TDI |
| PP33 | VC_TDO |
| PP34 | GND |
| PP35 | GPIO6 of LAN9514 |
| PP36 | GPIO7 of LAN9514 |
| PP37 | CAM_GPIO0 |
| PP38 | CAM_GPIO1 |
| PP39 | SCL0 |
| PP40 | SDA0 |



#### as from the testpoint table, testpoint PP27 is used to test USB 5V power 
 I grabbed my voltmeter and tested testpoint PP27 since it's responsible of usb power (5v).Turns out usb ports are not getting any power !

#### I wanted a qucik fix !:
 Unfortunatly i could'nt know the cause of the problem, i'm not an engineer, but first idea came up to me was to find another source of 5v to feed the usb ports. Since PP1 testpoint output a 5V i decided to solder a wire between PP1 and PP27 and see what happens ( i already lost hope and don't care if i burt the entire board !)
#### soldering:
![soldered.jpg](https://i.imgur.com/wh01rRC.jpg)


##### After the worst solderinge ever, i connected the PI and powered it on and everything was working like a charm !! 


Note: this is'nt a tutorial and it could make your PI even worst, it worked for me but i can't gurantee !!
