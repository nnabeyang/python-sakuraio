# Python library for SakuraIO ![travis-ci](https://travis-ci.org/sakuraio/python-sakuraio.svg?branch=master)

**WARNING: This library is under development with destructive changes.**

## Overview

This library contains two functions.
One is to connect to Sakura Communication Modules (for Hardware).
Another one is to connect to Platform API in https://api.sakura.io/ (for Service).


## Documentation

For API documentation, usage and examples see files in the `"./doc"`
directory.  The `".rst"` files can be read in any text editor or being converted to
HTML or PDF using [Sphinx](http://sphinx-doc.org/). An HTML version is online at

[![Docs](https://readthedocs.org/projects/python-sakuraio/badge/?version=latest)](http://python-sakuraio.readthedocs.io/)

http://python-sakuraio.readthedocs.io/


## For Hardware

It currently tested with Raspberry Pi only.

### Requirements

#### Python2

* Python = 2.7
* python-smbus (for I2C)
* python-rpi.gpio (for GPIO on Raspberry Pi)
* python-serial (for Serial)

#### Python3

* Python >= 3.4
* python3-smbus (for I2C)
* python3-rpi.gpio (for GPIO on Raspberry Pi)
* python3-serial (for Serial)

### Install

If you want to use python3 it may be required replace `pip` to `pip3`.

```bash
# From PyPi
sudo pip install sakuraio
# From Github.com
sudo pip install -e git+https://github.com/sakuraio/python-sakuraio.git#egg=sakuraio
```

### Example

#### I2C (SMBus)

```python
from sakuraio.hardware.rpi import SakuraIOSMBus

sakuraio = SakuraIOSMBus()
print(sakuraio.get_unique_id())
```

*NOTE*

Some linux kernel version of raspbian are not supported.

Please see [the document of this HAT](https://sakura.io/developer/pdf/sco-rpi-01_manual_v1.0.1.pdf).

**DO NOT update kernel by `rpi-update`**, it is reported that `OSError: [Errno 121] Remote I/O error` occurs with unofficial build version.


#### SPI (GPIO)

```python
from sakuraio.hardware.rpi import SakuraIOGPIO

sakuraio = SakuraIOGPIO()
print(sakuraio.get_unique_id())
```


### Serial (UART)

```python
from sakuraio.hardware.rpi import SakuraIOSerial

sakuraio = SakuraIOSerial("/dev/ttyS0")
print(sakuraio.get_unique_id())
```

*NOTE*

Disable serial console by using `raspi-config`.


#### output

```
16X0000001
```
