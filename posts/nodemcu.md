---
layout: blog
title: Linux ve NodeMCU
---
#### Aygıta kullanıcıların erişimini sağlamak için:

* Udev kuralını yaratmak için:
    
    ```console
    $ RULES='SUBSYSTEMS=="usb", ATTRS{idProduct}=="7523", ATTRS{idVendor}=="1a86", MODE:="0666", GROUP="plugdev"'
    $ echo $RULES | sudo tee /etc/udev/rules.d/nodeMCU.rules
    ```
* Udev'i yeniden başlatıp yeni kuralı geçerli kılmak için:

    ```console
    # systemctl restart systemd-udevd
    ```
    veya
    
    ```console
    # udevadm control --reload-rules
    # udevadm trigger
    ```

#### Firmware güncellemek veya değiştirmek için:
* İlk olarak temizliyoruz:
    
    ```console
    $ esptool.py --port /dev/ttyUSB0 erase_flash
    ```
* Firmware'i yüklemek için:
    
    ```console
    $ esptool.py --port=/dev/ttyUSB0  write_flash -fm=dio -fs=32m 0x00000 <firmware_file>.bin
    ```
    veya
    ```console
    $ esptool.py -p /dev/ttyUSB0 write_flash -fm dout 0x0000 <firmware_file>.bin
    ```


#### Hata ayıklama için:
```console
$ screen /dev/ttyUSB0 115200
```
_Not_: screen programından çıkmak için `ctrl+a` ve sonrasında `:quit` yazıp enter tuşuna basın.

_Kaynaklar_:

* https://github.com/honnet/iot_intro
* https://steve.fi/Hardware/esp8266-basics/
* https://blog.ithasu.org/2015/09/flashing-nodemcu-using-ubuntu/
* https://github.com/artynet/arduino-linux-setup/blob/master/arduino-linux-setup-09.sh
* https://docs.platformio.org/en/latest/faq.html#platformio-udev-rules