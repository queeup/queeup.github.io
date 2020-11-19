# Kurulum

### Server için:

* https://github.com/Angristan/OpenVPN-install

### Sadece client için:

```
# pacman -S openvpn
```

# Client

### *.ovpn client dosyasını alarmpi.conf olarak değiştiriyoruz.

```
# nano /etc/openvpn/client/alarmpi.conf
```

### Server'a bağlanmak için.

```
# systemctl start openvpn-client@alarmpi.service
# systemctl enable openvpn-client@alarmpi.service
```

### Hata ayıklamak için:

```
# systemctl status openvpn-client@alarmpi.service
# journalctl -u openvpn-client@alarmpi.service
```

### Gerekmeyen server özelliğini devre dışı bırakmak için:

```
# systemctl stop openvpn-server@server.service
# systemctl disable openvpn-server@server.service
```

### Socks proxy kurup local ağdaki bilgisayarlara proxy desteği vermek için:

* https://stackoverflow.com/a/28222249/11391913

```
# ssh-keygen
# cat ~/.ssh/id_rsa.pub >> ~/.ssh/authorized_keys
# ssh -f -o PasswordAuthentication=no -N -D 0.0.0.0:1080 localhost
```

# Server

### Hata ayıklamaları (log) devre dışı bırakmak için:

* `/etc/openvpn/server.conf`

```
status /dev/null
log /dev/null
verb 0
```
