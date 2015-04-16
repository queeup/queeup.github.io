---
layout: blog
title: Bluetooth aygıtının adını değiştirmek
---
####Aygıt adlarının saklandığı dosyayı açmak için:

_Not_: `<BDADDR>` = Bilgisayarınızdaki Bluetooth aygıtının adresi (XX:XX:XX:XX:XX:XX)
 
  * Bluetooth aygıtının adresini bulmak için: 
 
    ```
    $ hciconfig -a | grep BD | awk '{print $3}'
    ```

```
# nano /var/lib/bluetooth/<BDADDR>/names`
```

  * _Aygıt adını tanımlama şekli_:

    ```
    <nn:nn:nn:nn:nn:nn>=device name a
    <mm:mm:mm:mm:mm:mm>=device name b
    ```

####Dosyada gerekli düzenlemeleri yaptıktan sonra bluetooth hizmetini yeniden başlatın:
```
# service bluetooth restart
```

####Bilgisayarınızdaki Bluetooth aygıtına bağlı olan aygıtların temizlenmesi veya sıfırlanması için:

  * _Not_: Bu dizin bluetooth servisi yeniden başlatıldıktan sonra otomatik olarak yeniden oluşur.

```
# rm -rf /var/lib/bluetooth/<BDADDR>`
# service bluetooth restart
```

_Kaynak_:

 * http://www.spinics.net/lists/linux-bluetooth/msg30560.html
