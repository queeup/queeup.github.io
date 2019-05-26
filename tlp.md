---
layout: blog
title: Ubuntu/Linuxmint TLP(Linux Advanced Power Management)
---
#### Dağıtımın varsayılan "İşlemci Frekans Ölçekleme" ayarlarını iptal etmek için: 
```console
# update-rc.d -f ondemand remove 
```

#### Dağıtımın varsayılan "İşlemci Frekans Ölçekleme" ayarına geri dönmek için:
```console
# update-rc.d ondemand defaults 
```

#### Ayarlarım:
```
+++ Configured Settings: /etc/default/tlp
TLP_ENABLE=1
DISK_IDLE_SECS_ON_AC=0
DISK_IDLE_SECS_ON_BAT=2
MAX_LOST_WORK_SECS_ON_AC=15
MAX_LOST_WORK_SECS_ON_BAT=60
CPU_SCALING_GOVERNOR_ON_AC=ondemand
CPU_SCALING_GOVERNOR_ON_BAT=powersave
CPU_BOOST_ON_AC=1
CPU_BOOST_ON_BAT=0
SCHED_POWERSAVE_ON_AC=0
SCHED_POWERSAVE_ON_BAT=1
NMI_WATCHDOG=0
DISK_DEVICES="sda sdb"
DISK_APM_LEVEL_ON_AC="254 254"
DISK_APM_LEVEL_ON_BAT="128 128"
SATA_LINKPWR_ON_AC=max_performance
SATA_LINKPWR_ON_BAT=min_power
PCIE_ASPM_ON_AC=performance
PCIE_ASPM_ON_BAT=powersave
RADEON_POWER_PROFILE_ON_AC=high
RADEON_POWER_PROFILE_ON_BAT=low
RADEON_DPM_STATE_ON_AC=performance
RADEON_DPM_STATE_ON_BAT=battery
RADEON_DPM_PERF_LEVEL_ON_AC=auto
RADEON_DPM_PERF_LEVEL_ON_BAT=auto
WIFI_PWR_ON_AC=1
WIFI_PWR_ON_BAT=5
WOL_DISABLE=Y
SOUND_POWER_SAVE_ON_AC=0
SOUND_POWER_SAVE_ON_BAT=1
SOUND_POWER_SAVE_CONTROLLER=Y
BAY_POWEROFF_ON_BAT=1
BAY_DEVICE="sr0"
RUNTIME_PM_ON_AC=on
RUNTIME_PM_ON_BAT=auto
RUNTIME_PM_ALL=1
USB_AUTOSUSPEND=1
USB_BLACKLIST_WWAN=1
RESTORE_DEVICE_STATE_ON_STARTUP=0
```

#### Hemen başlatmak veya değişen ayarları uygulamak için:
```console
# tlp start
```

#### Kontrol etmek için:
```console
# tlp-stat
```

_Kaynak_:
 
 * http://linrunner.de/en/tlp/docs/tlp-faq.html
 * http://linrunner.de/en/tlp/docs/tlp-configuration.html
 * http://linrunner.de/en/tlp/docs/tlp-linux-advanced-power-management.html