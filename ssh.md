---
layout: blog
title: SSH Proxy Tüneli
---
#### Gereken paketleri yüklemek için:
```bash
# apt-get install ssh openssh-server openssh-client
```

#### Proxy sunucusunu çalıştırmak için:
```bash
$ ssh -N -D 0.0.0.0:1080 localhost
```

#### Arkaplanda ve parola girişi olmadan çalıştırmak için:
```bash
$ ssh -f -o PasswordAuthentication=no -N -D 0.0.0.0:1080 localhost
```

#### Tarayıcı veya programların ssh proxy tünelini kullanmasını sağlayan ayarlar:
_Not_: Sistem ayarlarında bu ssh proxy tünelini ayarlayıp uygulamaların sistem proxy ayarlarını kullanmasını sağlayabilirsiziniz.

 * Socks
 * IP: localhost
 * Port: 1080

_Kaynak_:

 * http://www.sofogeek.com/hatched-news/general/browse-internet-as-nobody-knows-what-you-are-doing-simple-socks-proxy-setup-under-linux/
 * http://www.catonmat.net/blog/linux-socks5-proxy/
 * http://straightedgelinux.com/blog/howto/socks.html
 * https://calomel.org/firefox_ssh_proxy.html