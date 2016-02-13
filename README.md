# Python LCD Controller (ACM1602NI)

This package contains LCD controller for Raspberry Pi.

- LCD (ACM1602NI-FLW-FBW-M01)
- Raspberry Pi 2 Model B
- Raspberry Pi A/B+ (unconfirmed)
- Raspbian Jessie

## Usage

```sh
$ sudo python raspi_lcd.py "Message for line 1" ["Message for line 2"]
```

You have to enable I2C in advance. Please read Prerequisite section.

## Configuration

Set `BUS_NUMBER` and `LCD_ADDR` in `config.py`.

## Prerequisite

### Enable I2C

#### Enable I2C

```sh
$ sudo raspi-config
```

`9 Advanced Options` > `A7 I2C` > `Yes`

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

## Attention

Do not use `i2cdetect` command. Read access to i2c bus causes hungging up of LCD(ACM1602NI).
