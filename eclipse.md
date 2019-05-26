---
layout: blog
title: Eclipse notlarım
---
#### Eclipse ayarlarımı kaydetmek için:

_Kaynak_: http://stackoverflow.com/a/4214604 , http://help.eclipse.org/luna/index.jsp?topic=%2Forg.eclipse.platform.doc.user%2Ftasks%2Ftimpandexp.htm

`File -> Export -> Preferences` menüsünden ayarları dışa aktar.

#### Eski eklentileri temizlemek için:

_Kaynak_: https://github.com/azachar/eclipse-plugin-cleaner

_Not: Aşşağıdaki komutta -t parametresini güvenlik amaçlı koydum. Hiç bir şeyi değiştirmeden komutun ne yapacağını simüle eder._

```console
java -jar plugin-cleaner-0.4-jar-with-dependencies.jar -t -m unlimited
```

#### Python Gtk+ geliştirirken Gtk modulünün bulunamaması:

_Kaynak_: http://stackoverflow.com/a/21482193

`Window->Preferences->PyDev->Interpreters->Python Interpreter->Forced Builtins`: `gi` modülünü buraya ekle ve Eclipse'i yeniden başlat.