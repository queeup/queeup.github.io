---
layout: blog
title: Ubuntu'da Wireshark'ı yönetici hakları olmadan çalıştırmak
---
#### İlk olarak net trafiğini yönetici hakları olmadan görebilmek için aşağıdaki komutu verip evet'i(yes) seçin.

```bash
# dpkg-reconfigure wireshark-common
```
#### Daha sonra kullanıcıyı wireshark grubuna ekle:

```bash
# adduser `whoami` wireshark
```
Masaüstünden çıkış yapıp tekrar girdikten sonra wireshark'ı yönetici hakları olmadan çalıştırıp kullanabilirsiniz. 
