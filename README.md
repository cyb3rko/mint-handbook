# Mint Handbook

## Resource Management

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

### Remove Bluetooth

```shell
sudo apt-get purge blueman bluez-utils bluez bluetooth && sudo apt-get autoremove && sudo apt-get autoclean
```

### Remove screen reader + TTS

```shell
sudo apt-get remove orca speech-dispatcher
```

### Remove asian fonts (>100 MB)

```shell
sudo apt-get remove "fonts-kacst*" "fonts-khmeros*" fonts-lklug-sinhala fonts-guru-extra "fonts-nanum*" fonts-noto-cjk "fonts-takao*" fonts-tibetan-machine fonts-lao fonts-sil-padauk fonts-sil-abyssinica "fonts-tlwg-*" "fonts-lohit-*" fonts-beng-extra fonts-gargi fonts-gubbi fonts-gujr-extra fonts-kalapi "fonts-samyak*" fonts-navilu fonts-nakula fonts-orya-extra fonts-pagul fonts-sarai "fonts-telu*" "fonts-wqy*" "fonts-smc*" fonts-deva-extra fonts-sahadeva && sudo dpkg-reconfigure fontconfig
```
