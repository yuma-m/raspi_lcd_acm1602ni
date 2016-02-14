# Python LCD Controller (ACM1602NI)

This package contains LCD controller for Raspberry Pi.

- Raspbian Jessie
- Python 2.7
- LCD (ACM1602NI-FLW-FBW-M01)
- Raspberry Pi2 Model B
- Raspberry Pi Model A/B+ (unconfirmed)

## Usage

```sh
$ sudo python raspi_lcd.py "Message for line 1" ["Message for line 2"]
```

You have to enable I2C in advance. Please read Prerequisite section.

### Displayable Characters

- Half-width English numbers and letters
- Full-width / half-width Katakana
- Some special characters


## Configuration

If needed, edit `BUS_NUMBER` and `LCD_ADDR` in `config.py`.

## Prerequisite

### Enable I2C

#### Enable I2C

```sh
$ sudo raspi-config
```

1. Select `9 Advanced Options`
1. Select `A7 I2C`
1. Select `Yes` twice
1. Reboot Raspberry Pi

#### Install i2c-tools, python-smbus

```sh
$ sudo apt-get install i2c-tools python-smbus
```

#### Load Drivers

```sh
$ sudo modprobe i2c-bcm2708
$ sudo modprobe i2c-dev
```

#### Edit I2C Config

Open `/boot/config.txt` and add line below.

```sh
dtparam=i2c_baudrate=50000
```

Reboot Raspberry Pi.

### Breadboard wiring example

![Breadboard wiring of ACM1602NI](/images/breadboard_wiring.jpg)

## Attention

Do not use `i2cdetect` command when LCD(ACM1602NI) is connected. Read access to i2c bus will causes hungging up of LCD.
