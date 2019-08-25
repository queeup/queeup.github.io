---
layout: blog
title: Thinkpad T430 AMT Firmware güncelleme
---
### *Gereken donanım:*

- usb disk (minimum 8GB, windows PE için)
- [Windows PE:](https://toolslib.net/downloads/finish/322-winpese-x64-14393/298/get/iHVNFiHUVkOEVbXWJ1xVY49rVVgW0x9K)
- [Hiren’s BootCD PE x64:](https://www.hirensbootcd.org/files/HBCD_PE_x64.iso)

### *Gereken programlar:*

- innoextract: exe dosyalarının içinden gerekli dosyaları çıkartmak için gereken linux uygulaması.
  
  ```console
  # apt install innoextract
  ```

- [intel_sa00086.py:](https://downloadcenter.intel.com/downloads/eula/27150/INTEL-SA-00086-Detection-Tool?httpDown=https%3A%2F%2Fdownloadmirror.intel.com%2F27150%2Feng%2FSA00086_Linux.tar.gz) Güvenlik açığını kontrol eden python betiği.
  
  ```console
  $ tar -zxvf SA00086_Linux.tar.gz intel_sa00086.py
  # python2 intel_sa00086.py
  ```

### *Gereken dosyalar:*

- [Intel Management Engine Interface 9.0 and Serial Over LAN (SOL) Driver for Windows XP - ThinkPad: ](https://pcsupport.lenovo.com/tr/tr/products/LAPTOPS-AND-NETBOOKS/THINKPAD-T-SERIES-LAPTOPS/THINKPAD-T430/downloads/DS032434)
  
  - [g1r812ww.exe](https://download.lenovo.com/ibmdl/pub/pc/pccbbs/mobiles/g1r812ww.exe) içindeki HECI.inf dosyasını ayıklamak için:
    
    ```console
    $ innoextract g1r812ww.exe
    ```
  
  - Windows PE altında sürücüyü yüklemek için:
    
    ```console
    C:\Users\Thinkpad> drvload app\Drivers\MEI\HECI.inf
    ```

- [Intel Management Engine Firmware 8.1 for Windows 10 (64-bit), 8.1 (64-bit), 8 (32-bit, 64-bit), 7 (32-bit, 64-bit), XP - ThinkPad: ](https://pcsupport.lenovo.com/tr/tr/products/LAPTOPS-AND-NETBOOKS/THINKPAD-T-SERIES-LAPTOPS/THINKPAD-T430/downloads/DS032435)
  
  - [g1rg24ww.exe](https://download.lenovo.com/pccbbs/mobiles/g1rg24ww.exe) içindeki MEUPDATE.CMD dosyasını ayıklamak için:
    
    ```console
    $ innoextract g1rg24ww.exe
    ```
  
  - Windows PE altında firmware güncellemesini yapmak için:    
    
    ```console
    C:\Users\Thinkpad> app\MEUPDATE.CMD
    ```

*Kaynaklar:* 

- [http://www.thinkwiki.org/wiki/Intel_Active_Management_Technology_(AMT)#Firmware_update](http://www.thinkwiki.org/wiki/Intel_Active_Management_Technology_(AMT)#Firmware_update)

- [https://pcsupport.lenovo.com/tr/tr/products/laptops-and-netbooks/thinkpad-t-series-laptops/thinkpad-t430/downloads](https://pcsupport.lenovo.com/tr/tr/products/laptops-and-netbooks/thinkpad-t-series-laptops/thinkpad-t430/downloads)

- [https://cloudnull.io/2017/07/x1-firmware-without-windows/](https://cloudnull.io/2017/07/x1-firmware-without-windows/)

- [https://www.hirensbootcd.org/](https://www.hirensbootcd.org/)

- [https://www.flamingspork.com/blog/2017/11/22/updating-windows-management-engine-firmware-on-a-lenovo-without-a-windows-install/](https://www.flamingspork.com/blog/2017/11/22/updating-windows-management-engine-firmware-on-a-lenovo-without-a-windows-install/)

- [https://downloadcenter.intel.com/download/27150?v=t](https://downloadcenter.intel.com/download/27150?v=t)

- [https://superuser.com/a/1283343](https://superuser.com/a/1283343)

- [https://www.reddit.com/r/Ubuntu/comments/7ey55d/make_sure_your_computer_is_safe_intel_management/](https://www.reddit.com/r/Ubuntu/comments/7ey55d/make_sure_your_computer_is_safe_intel_management/)
