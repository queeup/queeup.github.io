---
layout: page
title: ubuntu'da wireshark'ı yönetici hakları olmadan çalıştırmak
---
#### İlk olarak net trafiğini yönetici hakları olmadan görebilmek için aşağıdaki komutu verip evet'i(yes) seçin:

```console
# dpkg-reconfigure wireshark-common
```

#### dumpcap komutunu çalıştırılabilir yapın:
```console
# chmod +x /usr/bin/dumpcap
```

#### Daha sonra kullanıcıyı wireshark grubuna ekleyin:

```console
# adduser `whoami` wireshark
```

Masaüstünden çıkış yapıp tekrar girdikten sonra wireshark'ı yönetici hakları olmadan çalıştırıp kullanabilirsiniz. 
