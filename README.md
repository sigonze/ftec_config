# Fanatec FFB settings

Python script to configure Fanatec FFB settings under Linux using Sysfs


## Prerequisite
HID Fanatec FF driver has to be installed first.
The driver is available here: [gotzl/hid-fanatecff](https://github.com/gotzl/hid-fanatecff/)


## Usage

```
./ftec_settings <profile>
```

Profile information are stored in the `profiles.ini` file using this format:
```
[<profile>]
SEN = <value>
FF = <value>
NDP = <value>
NFR = <value>
NIN = <value>
INT = <value>
FEI = <value>
FOR = <value>
SPR = <value>
DPR = <value>
BLI = <value>
SHO = <value>
```
Each field correspond to a file in sysfs.


## Example

For instance for Assetto Corsa Evo the profile and the FFB settings are:
```
[acevo]
SEN = 1080
FF = 80
NDP = 15
NFR = 5
NIN = 0
INT = 2
FEI = 100
FOR = 100
SPR = 100
DPR = 100
BLI = 101
SHO = 100
```

The command to configure FFB settings is:
```
./ftec_settings acevo
```

And the output should be something which looks like:
```console
$ ./ftec_settings acevo
DEBUG: Path: /sys/module/hid_fanatec/drivers/hid:fanatec/0003:0EB7:0020.0003/driver/0003:0EB7:0020.0001/ftec_tuning/0003:0EB7:0020.0001
INFO: Device ID: 0003:0EB7:0020.0001
INFO: Device: Fanatec FANATEC Wheel
DEBUG: SEN set to 1080.
DEBUG: FF set to 80.
DEBUG: NDP set to 15.
DEBUG: NFR set to 5.
DEBUG: NIN set to 0.
DEBUG: INT set to 2.
DEBUG: FEI set to 100.
DEBUG: FOR set to 100.
DEBUG: SPR set to 100.
DEBUG: DPR set to 100.
DEBUG: BLI set to 101.
DEBUG: SHO set to 100.
```
