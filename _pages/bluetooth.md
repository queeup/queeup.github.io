---
layout: page
title: bluetooth aygıtının adını değiştirmek
---
#### Aygıt adlarının saklandığı dosyayı açmak için:

`<BDADDR1>` = Bilgisayarınızdaki Bluetooth aygıtının adresi (XX:XX:XX:XX:XX:XX)
`<BDADDR2>` = Bilgisayarınıza bağlı olan, adını değiştirmek istediğiniz \
              Bluetooth aygıtının adresi (YY:YY:YY:YY:YY:YY)
 
* Bluetooth aygıtının adresini bulmak için: 

  ```console
  $ hciconfig -a | grep BD | awk '{print $3}'
  ```

#### Root terminaline giriş yapmak için:

```console
$ sudo -i
```

```console
# nano /var/lib/bluetooth/<BDADDR1>/<BDADDR2>info
```

  * _Aygıt adını tanımlama şekli_:

    `Name=<device name>`

#### Dosyada gerekli düzenlemeleri yaptıktan sonra bluetooth hizmetini yeniden başlatın:
```console
# service bluetooth restart
```

#### Bilgisayarınızdaki Bluetooth aygıtına bağlı olan aygıtların temizlenmesi veya sıfırlanması için:

  * _Not_: Bu dizin bluetooth servisi yeniden başlatıldıktan sonra otomatik olarak yeniden oluşur.

```console
# rm -rf /var/lib/bluetooth/<BDADDR1>/<BDADDR2>
# service bluetooth restart
```

_Kaynak_:

 * [http://www.spinics.net/lists/linux-bluetooth/msg30560.html]()
