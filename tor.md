---
layout: blog
title: Tor proxy
---
_Anlatım Archlinux için yapılmıştır. Yükleme ve bazı komutlar diğer işletim sistemlerinde faklıdır._

#### Tor'u yüklemek için:
```bash
# pacman -Sy tor
```

#### Tor ayarlarım:
_Not_: Ayarlardaki IP adreslerini kendi ağınıza göre değiştirin.

```bash
# nano /etc/tor/torrc
```

```
SocksPort 192.168.1.5:9100 # Bind to this adddress:port too.

SocksPolicy accept 192.168.1.0/24
SocksPolicy reject *

Log notice syslog

DataDirectory /var/lib/tor

ExitPolicy reject *:* # no exits allowed

User tor # Return to tor user after service started as root to listen on privileged ports
DNSPort 53
```

#### Özel izin gerektiren portlar için tor'u root yetkileriyle başlatmak:
```bash
# mkdir /etc/systemd/system/tor.service.d`
# touch /etc/systemd/system/tor.service.d/start-as-root.conf`
```

  * Yaratılan dosyaya aşağıdaki metni yapıştırın:
    ```
    [Service]
    User=root
    ```

#### Tor'u başlat
```bash
# systemctl start tor.service
```

#### Hata ayıklamak ve tor'un mesajlarına bakmak için:
```bash
# systemctl status -l tor.service
```

#### Tüm tor çıktıları için:
```bash
journalctl -u tor
```

#### Sistem başlarken tor'u otomatik olarak başlatmak için:
```bash
# systemctl enable tor.service
```

#### Tarayıcı veya programların tor'u kullanmasını sağlayan ayarlar:
 * Socks5 ve Uzak DNS
 * IP: 192.168.1.5
 * Port: 9100

_Kaynaklar_:
 
 * https://wiki.archlinux.org/index.php/tor
 * https://www.torproject.org/docs/tor-manual.html.en
 * Raspberry Pi 21 Brilliant Projects - Project 5 / Sayfa 35-39
