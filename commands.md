---
layout: blog
title: Kullanışlı komutlar
---
- Bütün günlük iletileri dosyalarını gerçek zamanlı görmek için:
  Kaynak: http://www.commandlinefu.com/commands/view/13605/view-all-new-log-messages-in-real-time-with-color

    ```bash
    find /var/log -type f -iregex '.*[^\.][^0-9]+$' -not -iregex '.*gz$' 2> /dev/null | xargs tail -n0 -f
    ```
- Klasördeki bütün jpg dosyalarını hedef dizine kopyalar.
    
    ```bash
    find /home/user/foldertosearch -name "*.jpg" -type f -exec cp '{}' /home/user/foldertocopyto/ \;
    find /home/user/foldertosearch -name "*.mpeg" -type f -exec cp '{}' /home/user/foldertocopyto/ \;
    ```
- Klasördeki bütün jpg dosyalarını siler.
    
    ```bash
    find /home/user/foldertosearch -name "*.jpg" -type f -exec rm '{}' \;
    ```
- dosya adlarını özyinelemeli(recursively) olarak değiştir: bütün teaser adları _teaser olarak değişir
    
    ```bash
    find -name "teaser*" -exec rename 's/teaser/_teaser/' {} ";"
    ```
- deb paketlerini dizine çıkartır.
    
    ```bash
    dpkg-deb -x <paket_adı.deb> .
    ```
- Paketleri bağımlılıkları ile birlikte kaldırır.
    
    ```bash
    sudo apt-get remove --purge <paket_adı>
    ```
- NO_PUBKEY 26F4EF8440618B66 hatası alırsan son 8 rakamla birlikte aşşağıdaki komutu ver.
    
    ```bash
    sudo apt-key adv --keyserver keyserver.ubuntu.com --recv <son_8_rakam>
    ```
- Eski kernel paketlerini kaldırır.
    
    ```bash
    sudo apt-get remove --purge 2.6.2x-xx-*
    ```
- how to "unbroken" a package in synaptic / aptitude / apt-get, without uninstalling it. 1. Open status file:
    
    ```bash
    sudo nano /var/lib/dkpg/status
    ```
    - search the file for apples until you find something like:
    
        `Package: apples
        Status: install ok installed
        Priority: optional
        Section: libs
        Installed-Size: 316
        Maintainer: 
        Architecture: i386
        Source: applesauce
        Version: 1.0.10-1
        Depends: packageA, packageB, obsolete
        Description: Apples on your desktop!`
    
    - Remove obsolete from the Depends: row, save the file, and you're done - Software selection menüyü açmak için
    
        ```bash
        sudo tasksel
        ```
- RTMP videoların bilgilerini görmek için:
    
    ```bash
    sudo iptables -t nat -A OUTPUT -p tcp --dport 1935 -m owner \! --uid-owner root -j REDIRECT && sudo rtmpsuck && sudo iptables -t nat -D OUTPUT -p tcp --dport 1935 -m owner \! --uid-owner root -j REDIRECT
    ```
- Yeni baslatici olustur.
    
    ```bash
    gnome-desktop-item-edit ~/Masaüstü --create-new USBDisk.desktop
    ```
- rsync ile kopyala veya yedekle.
    
    ```bash
    rsync -r -a -v --delete -e ssh queeup@192.168.1.5:~/Resimler/ ~/Resimler/
    ```
- 30 karakter uzunluğunda rastgele bir parola oluştur.
  Kaynak: http://www.commandlinefu.com/commands/view/13902/generate-a-random-password-30-characters-long

    ```bash
    strings /dev/urandom | tr -cd '[:alnum:]' | fold -w 30 | head -n 1
    ```
- Bütün hata ayıklama mesajlarını gerçek zamanlı göster.
  Kaynak: http://www.commandlinefu.com/commands/view/13605/view-all-new-log-messages-in-real-time-with-color
    ```bash
    find /var/log -type f -iregex '.*[^\.][^0-9]+$' -not -iregex '.*gz$' 2> /dev/null | xargs tail -n0 -f
    ```
