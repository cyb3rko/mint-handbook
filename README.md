# Mint Handbook

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
### Remove Libreoffice

```shell
sudo apt-get purge libreoffice* liblibreoffice-java && sudo rm -r /etc/libreoffice/registry/res
```
