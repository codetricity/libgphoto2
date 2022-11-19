# libgphoto2 for RICOH THETA USB API

## modifications for RICOH THETA

* shutterspeed works thanks to patch from [hugues](https://community.theta360.guide/u/Hugues)

## more information on libgphoto2

Refer to the original [libgphoto2 README](https://github.com/gphoto/libgphoto2/blob/master/README.md) for more information



## modification overview

`config.c (libgphoto2-2.5.30\camlibs\ptp2)`

```c
	{ N_("Shutter Speed"), 					"shutterspeed", 			PTP_DPC_RICOH_ShutterSpeed, 			PTP_VENDOR_MICROSOFT, 		PTP_DTC_UINT64, _get_Ricoh_ShutterSpeed, _put_Ricoh_ShutterSpeed },	
```

Line was added after this line:

```c
{ N_("Shutter Speed"), "shutterspeed", PTP_DPC_RICOH_ShutterSpeed, PTP_VENDOR_PENTAX, PTP_DTC_UINT64, _get_Ricoh_ShutterSpeed, _put_Ricoh_ShutterSpeed },
```

## gphoto2 examples

### get current shutter speed

```text
gphoto2 --get-config shutterspeed
Label: Shutter Speed                                                           
Readonly: 0
Type: RADIO
Current: Auto
Choice: 0 Auto
END
```

### set exposure program to shutter priority

```
gphoto2 --set-config=/main/other/500e=4
```

### get shutterspeed when camera set to shutter priority

```
 gphoto2 --get-config shutterspeed
Label: Shutter Speed                                                           
Readonly: 0
Type: RADIO
Current: 1/250
Choice: 0 1/16000
Choice: 1 1/12800
Choice: 2 1/10000
Choice: 3 1/8000
Choice: 4 1/6400
Choice: 5 1/5000
Choice: 6 1/4000
Choice: 7 1/3200
Choice: 8 1/2500
Choice: 9 1/2000
Choice: 10 1/1600
Choice: 11 1/1250
Choice: 12 1/1000
Choice: 13 1/800
Choice: 14 1/640
Choice: 15 1/500
Choice: 16 1/400
Choice: 17 1/320
Choice: 18 1/250
Choice: 19 1/200
Choice: 20 1/160
Choice: 21 1/125
Choice: 22 1/100
Choice: 23 1/80
Choice: 24 1/60
Choice: 25 1/50
Choice: 26 1/40
Choice: 27 1/30
Choice: 28 1/25
Choice: 29 1/20
Choice: 30 1/15
Choice: 31 1/13
Choice: 32 1/10
Choice: 33 1/8
Choice: 34 1/6
Choice: 35 1/5
Choice: 36 1/4
Choice: 37 1/3
Choice: 38 10/25
Choice: 39 1/2
Choice: 40 10/16
Choice: 41 10/13
Choice: 42 1/1
Choice: 43 13/10
Choice: 44 16/10
Choice: 45 2/1
Choice: 46 25/10
Choice: 47 32/10
Choice: 48 4/1
Choice: 49 5/1
Choice: 50 6/1
Choice: 51 8/1
Choice: 52 10/1
Choice: 53 13/1
Choice: 54 15/1
END
```

### set shutterspeed to 1/1600

```
gphoto2 --set-config-index shutterspeed=10
```

### get shutterspeed to verify setting

Current is 1/1600, which is choice 10.

```
gphoto2 --get-config shutterspeed
Label: Shutter Speed                                                           
Readonly: 0
Type: RADIO
Current: 1/1600

```

### Set Back to Mode 2, Auto

```
gphoto2 --set-config=/main/other/500e=2

```

### Reconfirm Auto

```
gphoto2 --get-config shutterspeed
Label: Shutter Speed                                                           
Readonly: 0
Type: RADIO
Current: Auto
Choice: 0 Auto
```
