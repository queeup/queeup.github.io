---
layout: page
title: alarmpi komutları
---
#### Sistemi güncellemek için:
```console
# pacman -Syu
```

#### Güncelledikten sonra yeniden başlatmak için:
```console
# sync && sync && sync && reboot
```

#### Önbellek klasöründe duran paketleri silmek için:
```console
# pacman -Scc
```

#### SD kartı yedeklemek için:
```console
# dd bs=4M if=/dev/mmcblk<X> | gzip > backup-file_`date +%F`.img.gz
```

#### Yedeği SD kartına geri yüklemek için:
```console
$ gunzip --stdout backup-file.img.gz | sudo dd bs=4M of=/dev/mmcblk<X>
```

_Kaynaklar_:
* [https://www.raspberrypi.org/documentation/linux/filesystem/backup.md]()
* [https://www.linux.com/learn/full-metal-backup-using-dd-command]()
