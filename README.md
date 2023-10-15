# Mint Handbook

## Packages

### Remove Bluetooth

```shell
sudo apt-get purge blueman bluez-utils bluez bluetooth && sudo apt-get autoremove && sudo apt-get autoclean
```

### Remove screen reader + TTS

```shell
sudo apt-get remove orca speech-dispatcher
```
