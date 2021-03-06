.. include:: defs.rst

Features
--------

Devices
~~~~~~~

* All FTDI device ports (UART, MPSSE) can be used simultaneously.

  * However, it is not yet possible to use both GPIO and MPSSE modes on the
    same port at once

* Several FTDI adapters can be accessed simultaneously from the same Python
  runtime instance.

Supported features
~~~~~~~~~~~~~~~~~~

UART
....

Serial port, up to 12 Mbps. PyFtdi_ includes a pyserial_ emulation layer that
offers transparent access to the FTDI serial ports through a pyserial_-
compliant API. The ``serialext`` directory contains a minimal serial terminal
demonstrating the use of this extension, and a dispatcher automatically
selecting the serial backend (pyserial_, PyFtdi_), based on the serial port
name.


SPI master
..........

Supported devices:

=====  ===== ====== ====================================================
Mode   CPol   CPha  Status
=====  ===== ====== ====================================================
  0      0      0   Supported on all MPSEE devices
  1      0      1   Supported on -H series (FT232H_/FT2232H_/FT4232H_)
  2      1      0   Not supported (FTDI HW limitation)
  3      1      1   Supported on -H series (FT232H_/FT2232H_/FT4232H_)
=====  ===== ====== ====================================================

PyFtdi_ can be used with pyspiflash_ module that demonstrates how to
use the FTDI SPI master with a pure-Python serial flash device driver for
several common devices.

Only half-duplex communication is supported for now.

GPIOs can be used while SPI mode is enabled.

|I2C| master
............

Supported devices: FT232H_, FT2232H_, FT4232H_

For now, only 7-bit address are supported.

GPIOs cannot be used while |I2C| mode is enabled (not yet implemented).

JTAG
....

JTAG is under development and is not fully supported yet.

Status
~~~~~~

This project is still in beta development stage.

However, PyFtdi_ is being forked from a closed-source software implementation
that has been successfully used for over several years - including serial
@ 3Mbps, spi and jtag protocols. PyFtdi_ is developed as an open-source
solution.
