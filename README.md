# Mint Handbook

- [Resource Management](#resource-management)
  - [Large file and folder monitor](#large-file-and-folder-monitor)
  - [Find large files](#find-large-files)
  - [journalctl](#journalctl)
- [Packages](#packages)
  - [Cleanup after hou(sekeeping](#cleanup-after-housekeeping)
  - [Remove Bluetooth](#remove-bluetooth)
  - [Remove screen reader + TTS](#remove-screen-reader--tts)
  - [Remove asian fonts (>100 MB)](#remove-asian-fonts-100-mb)
  - [Remove useless fonts](#remove-useless-fonts)
  - [Remove Libreoffice](#remove-libreoffice)
- [SSL Inspection](#ssl-inspection)
  - [Add root CA to java](#add-root-ca-to-java)

---

## Resource Management

### Large file and folder monitor

Use the CLI tool ncdu for a simple overview of the largest files and folders.

```shell
ncdu
```

### Find large files

Find files in current directory with a specified minimum size (in this example 100 MB)

```shell
find . -type f -size +100M
```

### journalctl

See space used by system logs:

```shell
journalctl --disk-usage
```

Set maximum log retention time in `/etc/systemd/journald.conf`

```
MaxRetentionSec=2months
```

## Packages

### Cleanup after housekeeping

After removing many packages do this:

```shell
sudo apt-get autoremove && sudo apt-get autoclean
```

### Remove Bluetooth

```shell
sudo apt-get purge blueman bluez-utils bluez bluetooth
```

### Remove screen reader + TTS

```shell
sudo apt-get purge orca speech-dispatcher
```

### Remove asian fonts (>100 MB)

```shell
sudo apt-get purge "fonts-kacst*" "fonts-khmeros*" fonts-lklug-sinhala fonts-guru-extra "fonts-nanum*" fonts-noto-cjk "fonts-takao*" fonts-tibetan-machine fonts-lao fonts-sil-padauk fonts-sil-abyssinica "fonts-tlwg-*" "fonts-lohit-*" fonts-beng-extra fonts-gargi fonts-gubbi fonts-gujr-extra fonts-kalapi "fonts-samyak*" fonts-navilu fonts-nakula fonts-orya-extra fonts-pagul fonts-sarai "fonts-telu*" "fonts-wqy*" "fonts-smc*" fonts-deva-extra fonts-sahadeva && sudo dpkg-reconfigure fontconfig
```

### Remove useless fonts

```shell
sudo apt-get purge fonts-beng-extra fonts-beng fonts-deva-extra fonts-deva fonts-gargi fonts-gubbi fonts-gujr-extra fonts-gujr fonts-guru-extra fonts-guru fonts-indic fonts-kacst-one fonts-kacst fonts-kalapi fonts-khmeros-core fonts-knda fonts-lao fonts-lklug-sinhala fonts-lohit-beng-assamese fonts-lohit-beng-bengali fonts-lohit-deva fonts-lohit-gujr fonts-lohit-guru fonts-lohit-knda fonts-lohit-mlym fonts-lohit-orya fonts-lohit-taml-classical fonts-lohit-taml fonts-lohit-telu fonts-mlym fonts-nakula fonts-navilu fonts-noto-cjk fonts-orya-extra fonts-orya fonts-pagul fonts-sahadeva fonts-samyak-deva fonts-samyak-gujr fonts-samyak-mlym fonts-samyak-taml fonts-sarai fonts-sil-abyssinica fonts-sil-padauk fonts-smc-anjalioldlipi fonts-smc-chilanka fonts-smc-dyuthi fonts-smc-karumbi fonts-smc-keraleeyam fonts-smc-manjari fonts-smc-meera fonts-smc-rachana fonts-smc-raghumalayalamsans fonts-smc-suruma fonts-smc-uroob fonts-smc fonts-taml fonts-telu-extra fonts-telu fonts-thai-tlwg fonts-tibetan-machine fonts-tlwg-garuda-ttf fonts-tlwg-garuda fonts-tlwg-kinnari-ttf fonts-tlwg-kinnari fonts-tlwg-laksaman-ttf fonts-tlwg-laksaman fonts-tlwg-loma-ttf fonts-tlwg-loma fonts-tlwg-mono-ttf fonts-tlwg-mono fonts-tlwg-norasi-ttf fonts-tlwg-norasi fonts-tlwg-purisa-ttf fonts-tlwg-purisa fonts-tlwg-sawasdee-ttf fonts-tlwg-sawasdee fonts-tlwg-typewriter-ttf fonts-tlwg-typewriter fonts-tlwg-typist-ttf fonts-tlwg-typist fonts-tlwg-typo-ttf fonts-tlwg-typo fonts-tlwg-umpush-ttf fonts-tlwg-umpush fonts-tlwg-waree-ttf fonts-tlwg-waree fonts-yrsa-rasa
```

### Remove Libreoffice

```shell
sudo apt-get purge libreoffice* liblibreoffice-java && sudo rm -r /etc/libreoffice/registry/res
```

## SSL Inspection

### Add root CA to java

Navigate to `*/jbr` or `*/jre` and then `lib/security`.  
Then type the following:

```shell
keytool -import -alias aldi -keystore cacerts -file ~/Dokumente/AlDiRootCA.crt
```
