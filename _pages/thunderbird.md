---
layout: page
title: thunderbird ayarları
---
### Varsayılan Posta Görünümü Ayarı

Kaynak: http://superuser.com/a/13551

_Düzen > Tercihler > Gelişmiş > Genel > Yapılandırma Düzenleyicisi_

```
mailnews.default_sort_order:         default      integer     18
mailnews.default_view_flags:         default      integer     1
```

Özetle Görünüm Sıralama Koşulu: Tarih | Azalarak | Dizili

### IMAP Ayarları

Kaynak: http://superuser.com/a/57899

- Bütün IMAP klasörlerini yeni postalar için kontrol et:

_Düzen > Tercihler > Gelişmiş > Genel > Yapılandırma Düzenleyicisi_
    
```
mail.server.default.check_all_folders_for_new:  default  boolean  true
```

- Sadece istediğim klasörleri kontrol et

_Klasör'e sağ tıkla > Özellikler > Bu hesap için yeni ileti alırken her zaman bu dizini denetle_


- IMAP klasörleri çok yer tutuyorsa

_Düzen > Hesap Ayarları > Eşitleme ve Depolama > Hesaba ait iletileri bu bilgisayarda tut_ seçimini kaldır.
