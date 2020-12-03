# Lenovo P15V

## Certification

https://certification.ubuntu.com/hardware/202008-28186
 This system was tested with 20.04 LTS, running the 5.6.0-1021-oem kernel.

## BIOS

Set to default
- Secure boot: disabled

## Kernel 5.6.0.1035 + nvidia drivers 455

### Issues

#### Wakes up immediately after suspend
- Plugged or unplugged


### Symptoms

#### dmesg

- jcef_helper[8883]: segfault at 4 ip 00007f6abafab8c7 sp 00007ffc044b93f8 error 6 in libnvidia-glcore.so.455.38[7f6ab9c6c000+15bb000]

#### kern.log

- thermal thermal_zone8: failed to read out thermal zone (-61)

## Links

[Forums](https://forums.lenovo.com/t5/ThinkPad-P-and-W-Series-Mobile-Workstations/bd-p/tp07_en)

