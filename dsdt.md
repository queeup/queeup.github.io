---
layout: blog
title: DSDT Onarımı
---
- Gereken paketler: iasl
 - `# apt-get install iasl`
- Yanlış birşey yaparsanız işletim sisteminiz hiç açılmayabilir. Veri kaybı olmaz.

1. DSDT'yi çıkarıyoruz:

    ```bash
    # cat /sys/firmware/acpi/tables/DSDT > ~/dsdt.dat
    ```

2. Decompile:
 
    ```bash
    $ iasl -d dsdt.dat
    ```

3. Recompile:
 
    ```bash
    $ iasl -tc dsdt.dsl
    ```

4. Hataları incele ve onar:
 Bu aşamada dsdt.dsl dosyasını text editör ile açıp hataları onarıyoruz.

5. Tekrar Recompile ediyoruz:
 
    ```bash
    $ iasl -tc dsdt.dsl
    ```

### Açılışta kendi onardığımız DSDT ile başlatma:
1. dsdt.aml dosyasını /boot dizinine kopyalıyoruz:
  
    ```bash
    # cp ~/dsdt.aml /boot/
    ```
2. DSDT'yi grub önyükleyicide yüklemek için grub.d içine acpi betiğini koyuyoruz.
  
    ```bash
    # nano /etc/grub.d/01_acpi
    ```
  
    ```sh
    #! /bin/sh -e
    
    # Uncomment to load custom ACPI table
    GRUB_CUSTOM_ACPI="/boot/dsdt.aml"
    
    # DON'T MODIFY ANYTHING BELOW THIS LINE!
    
    prefix=/usr
    exec_prefix=${prefix}
    libdir=${exec_prefix}/lib
    
    . ${libdir}/grub/grub-mkconfig_lib
    
    # Load custom ACPI table
    if [ x${GRUB_CUSTOM_ACPI} != x ] && [ -f ${GRUB_CUSTOM_ACPI} ] \
            && is_path_readable_by_grub ${GRUB_CUSTOM_ACPI}; then
        echo "Found custom ACPI table: ${GRUB_CUSTOM_ACPI}" >&2
        prepare_grub_to_access_device `${grub_probe} --target=device ${GRUB_CUSTOM_ACPI}` | sed -e "s/^/ /"
        cat << EOF
    acpi (\$root)`make_system_path_relative_to_its_root ${GRUB_CUSTOM_ACPI}`
    EOF
    fi
    ```

    ```bash
    # chmod +x /etc/grub.d/01_acpi
    ```
3. Grub menüsünü güncelle:

    ```bash
    # update-grub
    ```
4. Yeni DSDT ile yeni initrd'yi yarat:

    ```bash
    # update-initramfs -c -k `uname -r`
    ```
5. Tekrar grub'u güncelle:

    ```bash
    # update-grub
    ```