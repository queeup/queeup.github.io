---
layout: blog
title: Firefox Ayarları
---
### Kısayollar
* İstenilen sekme numarasına gitmek için `Alt+<Numara>`
* Sağa veya sola doğru sekmeleri gezmek için `Ctrl+PgUp` ve `Ctrl+PgDn`


#### Donanım ivmelenmesini devre dışı bırakmak için:
`Tercihler > Gelişmiş > Genel > Mümkün olduğunda donanım ivmelenmesini kullan`: Devre dışı bırak

#### Sayfa yükleme hızını arttırmak için:
```
network.http.pipelining                  true
network.http.pipelining.maxrequests      8
network.http.pipelining.ssl              true
network.http.proxy.pipelining            true
```

#### Animasyonları devre dışı bırakmak için:
```
browser.tabs.animate                         false
browser.panorama.animate_zoom                false
browser.display.show_image_placeholders      false
```

#### Varsayılan kaynak kodu göstericisi için:
```
view_source.editor.external     true
view_source.editor.path         Enter your editor path
```

#### Gizlilik ayarları:
`Tercihler > Gizlilik > Geçmiş > Geçmiş için özel ayarları kullan > Üçüncü taraf çerezlerini kabul et`: Asla

_Kaynak_:
 
 * http://www.reeachme.com/how-to-do/firefox-tweaks-better-browsing-experience/