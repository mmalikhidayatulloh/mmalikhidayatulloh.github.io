# Use upower

```
upower -i `upower -e | grep 'BAT'`
```

result

```
~ >>> upower -i `upower -e | grep 'BAT'`                                                                                                              
  native-path:          BAT1
  vendor:               SANYO
  model:                121500210
  serial:               24517
  power supply:         yes
  updated:              Sat 14 Aug 2021 08:21:47 AM WIB (65 seconds ago)
  has history:          yes
  has statistics:       yes
  battery
    present:             yes
    rechargeable:        yes
    state:               discharging
    warning-level:       none
    energy:              13.4 Wh
    energy-empty:        0 Wh
    energy-full:         27.85 Wh
    energy-full-design:  47.52 Wh
    energy-rate:         8.665 W
    voltage:             10.9 V
    time to empty:       1.5 hours
    percentage:          48%
    capacity:            58.6069%
    technology:          lithium-ion
    icon-name:          'battery-good-symbolic'
  History (rate):
    1628904107	8.665	discharging
```

# Use tlp-stat

```
sudo tlp-stat -b
```

Result

```
~ >>> sudo tlp-stat -b                                                                                                                                
--- TLP 1.3.1 --------------------------------------------

+++ Battery Features: Charge Thresholds and Recalibrate
natacpi    = inactive (laptop not supported)
tpacpi-bat = inactive (laptop not supported)
tp-smapi   = inactive (laptop not supported)

+++ Battery Status: BAT1
/sys/class/power_supply/BAT1/manufacturer                   = SANYO
/sys/class/power_supply/BAT1/model_name                     = 121500210
/sys/class/power_supply/BAT1/cycle_count                    = (not supported)
/sys/class/power_supply/BAT1/energy_full_design             =  47520 [mWh]
/sys/class/power_supply/BAT1/energy_full                    =  27850 [mWh]
/sys/class/power_supply/BAT1/energy_now                     =  13210 [mWh]
/sys/class/power_supply/BAT1/power_now                      =   5538 [mW]
/sys/class/power_supply/BAT1/status                         = Discharging

Charge                                                      =   47.4 [%]
Capacity                                                    =   58.6 [%]
```

# Use acpi

By default, aspi is not installed. so you have to install it first

# Source

[https://bandithijo.github.io/blog/beberapa-command-mengecek-laptop-battery](https://bandithijo.github.io/blog/beberapa-command-mengecek-laptop-battery)