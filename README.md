# ftec_config

Python script to configure Fanatec Wheel under Linux using Sysfs

## Usage

Configure Wheel for F1 23
```
./ftec_config f1_23
```

Test configuration
```
./ftec_config default -w test
```

## Ideas for improvement

- support string arguments (such as `AUTO`, `OFF`, `MIN`, `MAX`)
- range check? (or let the driver fail?)
- support multiple files
- display current values: `./ftec_config --show`
- save current values?: `./ftec_config --save "myfile.json"`
- configure some parameters without any file: `./ftec_config --set "SEN=360"`
- possibility to select SLOT from CLI: `./ftec_config --slot "S2" --profile acc`
- list available devices (`name` available in `input` directory): `./ftec_config --list-devices`
- possiblity to configure multiple slot at the same time
- gui?
- detect launched game and autoapply?


## Notes

Wheel Parameters  
advanced_mode=1 (to be forced?)  
SLOT=(AS=1, S1=2 ... S5=6)  

advanced_mode=0 (should not be used => less pararemeters available)  
SLOT=(AS=1, AC=2)  

SEN=AUTO (2530)  
FF=100  
FFS=PEAK  
NDP=50 (OFF=0,100)  
NFR=0 (OFF=0,100)  
NIN=0 (OFF=0,100)  
INT=11 (OFF=0,20)  
BLI=OFF (1,OFF=101)
FEI=100 (0,100)  
FOR=100 (OFF=0,120)  
SPR=100 (OFF=0,120)  
DPR=100 (OFF=0,120)  
BRF=50 (MIN=0,MAX=100)  
  

```
$ tree /sys/module/hid_fanatec/drivers/hid:fanatec/0003:0EB7:0020.0008/
/sys/module/hid_fanatec/drivers/hid:fanatec/0003:0EB7:0020.0008/
├── country
├── display
├── driver -> ../../../../../../../../bus/hid/drivers/fanatec
├── ftec_tuning
│   └── 0003:0EB7:0020.0008
│       ├── advanced_mode
│       ├── BLI
│       ├── device -> ../../../0003:0EB7:0020.0008
│       ├── DPR
│       ├── FEI
│       ├── FF
│       ├── FOR
│       ├── FUL
│       ├── INT
│       ├── NDP
│       ├── NFR
│       ├── NIN
│       ├── power
│       │   ├── async
│       │   ├── autosuspend_delay_ms
│       │   ├── control
│       │   ├── runtime_active_kids
│       │   ├── runtime_active_time
│       │   ├── runtime_enabled
│       │   ├── runtime_status
│       │   ├── runtime_suspended_time
│       │   └── runtime_usage
│       ├── RESET
│       ├── SEN
│       ├── SHO
│       ├── SLOT
│       ├── SPR
│       ├── subsystem -> ../../../../../../../../../../class/ftec_tuning
│       └── uevent
├── hidraw
│   └── hidraw5
│       ├── dev
│       ├── device -> ../../../0003:0EB7:0020.0008
│       ├── power
│       │   ├── async
│       │   ├── autosuspend_delay_ms
│       │   ├── control
│       │   ├── runtime_active_kids
│       │   ├── runtime_active_time
│       │   ├── runtime_enabled
│       │   ├── runtime_status
│       │   ├── runtime_suspended_time
│       │   └── runtime_usage
│       ├── subsystem -> ../../../../../../../../../../class/hidraw
│       └── uevent
├── input
│   └── input33
│       ├── capabilities
│       │   ├── abs
│       │   ├── ev
│       │   ├── ff
│       │   ├── key
│       │   ├── led
│       │   ├── msc
│       │   ├── rel
│       │   ├── snd
│       │   └── sw
│       ├── device -> ../../../0003:0EB7:0020.0008
│       ├── event20
│       │   ├── dev
│       │   ├── device -> ../../input33
│       │   ├── power
│       │   │   ├── async
│       │   │   ├── autosuspend_delay_ms
│       │   │   ├── control
│       │   │   ├── runtime_active_kids
│       │   │   ├── runtime_active_time
│       │   │   ├── runtime_enabled
│       │   │   ├── runtime_status
│       │   │   ├── runtime_suspended_time
│       │   │   └── runtime_usage
│       │   ├── subsystem -> ../../../../../../../../../../../class/input
│       │   └── uevent
│       ├── id
│       │   ├── bustype
│       │   ├── product
│       │   ├── vendor
│       │   └── version
│       ├── inhibited
│       ├── js0
│       │   ├── dev
│       │   ├── device -> ../../input33
│       │   ├── power
│       │   │   ├── async
│       │   │   ├── autosuspend_delay_ms
│       │   │   ├── control
│       │   │   ├── runtime_active_kids
│       │   │   ├── runtime_active_time
│       │   │   ├── runtime_enabled
│       │   │   ├── runtime_status
│       │   │   ├── runtime_suspended_time
│       │   │   └── runtime_usage
│       │   ├── subsystem -> ../../../../../../../../../../../class/input
│       │   └── uevent
│       ├── modalias
│       ├── name
│       ├── phys
│       ├── power
│       │   ├── async
│       │   ├── autosuspend_delay_ms
│       │   ├── control
│       │   ├── runtime_active_kids
│       │   ├── runtime_active_time
│       │   ├── runtime_enabled
│       │   ├── runtime_status
│       │   ├── runtime_suspended_time
│       │   └── runtime_usage
│       ├── properties
│       ├── subsystem -> ../../../../../../../../../../class/input
│       ├── uevent
│       └── uniq
├── modalias
├── power
│   ├── async
│   ├── autosuspend_delay_ms
│   ├── control
│   ├── runtime_active_kids
│   ├── runtime_active_time
│   ├── runtime_enabled
│   ├── runtime_status
│   ├── runtime_suspended_time
│   └── runtime_usage
├── range
├── report_descriptor
├── subsystem -> ../../../../../../../../bus/hid
├── uevent
└── wheel_id
```