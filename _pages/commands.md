---
layout: page
title: kullanışlı komutlar
---

- Bütün günlük iletileri dosyalarını gerçek zamanlı görmek için:
  
  _Kaynak_: [http://www.commandlinefu.com/commands/view/13605/view-all-new-log-messages-in-real-time-with-color]()
  
  ```console
  $ find /var/log -type f -iregex '.*[^\.][^0-9]+$' -not -iregex '.*gz$' 2> /dev/null | xargs tail -n0 -f
  ```

- Klasördeki bütün jpg dosyalarını hedef dizine kopyalar.
  
  ```console
  $ find /home/user/foldertosearch -name "*.jpg" -type f -exec cp '{}' /home/user/foldertocopyto/ \;
  $ find /home/user/foldertosearch -name "*.mpeg" -type f -exec cp '{}' /home/user/foldertocopyto/ \;
  ```

- Klasördeki bütün jpg dosyalarını siler.
  
  ```console
  $ find /home/user/foldertosearch -name "*.jpg" -type f -exec rm '{}' \;
  ```

- dosya adlarını özyinelemeli(recursively) olarak değiştir: bütün teaser adları _teaser olarak değişir
  
  ```console
  $ find -name "teaser*" -exec rename 's/teaser/_teaser/' {} ";"
  ```

- deb paketlerini dizine çıkartır.
  
  ```console
  $ dpkg-deb -x <paket_adı.deb> .
  ```

- Paketleri bağımlılıkları ile birlikte kaldırır.
  
  ```console
  # apt-get remove --purge <paket_adı>
  ```

- NO_PUBKEY 26F4EF8440618B66 hatası alırsan son 8 rakamla birlikte aşşağıdaki komutu ver.
  
  ```console
  # apt-key adv --keyserver keyserver.ubuntu.com --recv <son_8_rakam>
  ```

- Eski kernel paketlerini kaldırır.
  
  ```console
  # apt-get remove --purge 2.6.2x-xx-*
  ```

- how to "unbroken" a package in synaptic / aptitude / apt-get, without uninstalling it. 1. Open status file:
  
  ```console
  # nano /var/lib/dkpg/status
  ```
  
  - search the file for apples until you find something like:
    
    ```Package:
      Status: install ok installed
      Priority: optional
      Section: libs
      Installed-Size: 316
      Maintainer: 
      Architecture: i386
      Source: applesauce
      Version: 1.0.10-1
      Depends: packageA, packageB, obsolete
      Description: Apples on your desktop!```
    ```
  
  - Remove obsolete from the Depends: row, save the file, and you're done - Software selection menüyü açmak için
    
    ```console
    # tasksel
    ```

- RTMP videoların bilgilerini görmek için:
  
  ```console
  # iptables -t nat -A OUTPUT -p tcp --dport 1935 -m owner \! --uid-owner root -j REDIRECT && sudo rtmpsuck && sudo iptables -t nat -D OUTPUT -p tcp --dport 1935 -m owner \! --uid-owner root -j REDIRECT
  ```

- Yeni baslatici olustur.
  
  ```console
  $ gnome-desktop-item-edit ~/Masaüstü --create-new USBDisk.desktop
  ```

- rsync ile kopyala veya yedekle.
  
  ```console
  $ rsync -r -a -v --delete -e ssh queeup@192.168.1.5:~/Resimler/ ~/Resimler/
  ```

- 30 karakter uzunluğunda rastgele bir parola oluştur.
  
  _Kaynak_: [http://www.commandlinefu.com/commands/view/13902/generate-a-random-password-30-characters-long]()
  
  ```console
  $ strings /dev/urandom | tr -cd '[:alnum:]' | fold -w 30 | head -n 1
  ```

- Bütün hata ayıklama mesajlarını gerçek zamanlı göster.
  
  _Kaynak_: [http://www.commandlinefu.com/commands/view/13605/view-all-new-log-messages-in-real-time-with-color]()
  
  ```console
  $ find /var/log -type f -iregex '.*[^\.][^0-9]+$' -not -iregex '.*gz$' 2> /dev/null | xargs tail -n0 -f
  ```

- Resim dosyasını %50 küçült.
  
  ```console
  $ mogrify -resize 50% resim/dosya.jpg
  ```

- Klasördeki bütün dosyaların içeriğini yazdır.
  
  ```console
  $ find /etc/xdg/autostart/ -type f -exec printf '### START OF FILE ###\n### File: %s ###\n' {} \; -exec cat {} \; -exec printf '### END OF FILE ###\n\n' \;
  ```

- Komuta verilen değişkenleri yazdır.
  
  _Kaynak_: [https://stackoverflow.com/q/821837]()
  
  ```console
  $ tr \\0 ' ' < /proc/<pid>/cmdline
  ```
  
    veya
  
  ```console
  $ xargs -0 < /proc/<pid>/cmdline
  ```
  
    veya
  
  ```console
  $ ps -ww -fp <pid>
  ```

- dd komutu ile usb flash belleğe iso kalıbı yazdırma:
  
  ```console
  # dd bs=4M if=path/to/archlinux.iso of=/dev/sdx status=progress oflag=sync
  ```

- Çalıştırılan komut bittikten sonra bilgisayarı kapatmak:
  
    _Kaynak_: [https://askubuntu.com/a/207267]()
  
  ```console
  $ <çalıştırmak istenilen kod>; history -d $((HISTCMD-1)) && echo '[PASSWORD]' | sudo -S shutdown now
  ```

- Sistemdeki ramler hakkında bilgi almak için:
  
  ```console
  # dmidecode -t 17
  ```

- Sistemin BIOS bilgilerini görmek için:

  ```console
  # dmidecode -t 0
  ```

- Dizüstü bilgisayarın pili hakkında bilgi almak için:
  
  ```console
  $ upower -i `upower -e | grep 'BAT'`
  ```
  
    veya
  
  ```console
  $ find /sys/class/power_supply/BAT0/ -type f | xargs -tn1 cat
  ```
- Sistem sıcaklığını ve fanlarını kontrol etmek içi:
  
  ```console
  $ watch -n 1 -d 'sensors; cat /proc/acpi/ibm/fan'
  ```

