# System Door Lock

System Design Objectives:

* Tamper and sabotage resistant
* Cheaply, easily sourced and quickly interchangable parts.
* Semi-decentralized. Network attached.

## Overview

Raspberry Pi's with Raspbian, relays, strike locks and RFID/NFC readers.

## Status

Pi operates relay and NFC readers and opens the strike lock through GPIO
pins with shell scripts.

See the [door repo](https://github.com/hackeriet/door) for more
information.

## Documentation

* [How to add a key to the door system](How-to-add-a-Keycard.md)
* [How to restart the door system](How-to-reset-the-door.md)

## Further work

* http://dx.com/p/contactless-smart-id-card-reader-black-143889
* http://www.seeedstudio.com/wiki/index.php?title=13.56Mhz\_RFID\_module\_\\-*IOS/IEC\_14443\_type*
