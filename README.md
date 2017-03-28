# ADMP441 MEMS I2S driver for Raspberry Pi.

## Breakout Board

Purchased from [OSHPark](https://oshpark.com/shared_projects/ypqAU3CH) via https://github.com/SamEA/ADMP441_Microphone.git

### BOM
![OSHPark](https://raw.githubusercontent.com/SamEA/ADMP441_Microphone/master/ADMP441%20Breakout%20Board%20Top.png)

1. R1 - 100kOhm
2. C1 - 100nF
3. U1 - ADMP441 MEMS desoldered from Amazon Dash

## Raspberry Pi

|ADMP441|RPi|
|-------|---|
|WS     |19 |
|SD     |20 |
|SCK    |18 |
|VCC    |1  |
|GND    |9  |

### Kernel

Run `make && make install` in the `linux` directory

### Device Tree Overlay

```
cd dts
dtc -@ -I dts -O dtb -o i2s-soundcard.dtbo i2s-soundcard-overlay.dts
sudo cp i2s-soundcard.dtbo /boot/overlays
```

### Configuration

Add `admp441` to `/etc/modules`

Add `dtoverlay=i2s-soundcard,alsaname=mems-mic` to `/boot/config.txt`

### Reboot!
