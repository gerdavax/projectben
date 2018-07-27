# ProjectBen

![ProjectBen official icon](/images/projectben_official_icon.png)

ProjectBen is a protocol proposal for implementing secure one-way remote controllers based on Bluetooth Low Energy advertising packet.

Main features of ProjectBen protocol are:
- fits into standard Manufacturer Specific Data field of Bluetooth 4.x advertising packet
- uses symmetric cryptography to encrypt payload
- payload depends on absolute time and encryption keys depends on random number: time dependency avoids replay attacks and random keys harden the protocol against brute force attacks
- relies on a one-way scheme, like traditional remote controllers 
- no persistent connection is needed and receiver address is never exposed

The device implemeting the remote controller (i.e., the transmitter, TX) acts as a Bluetooth Low Energy "Broadcaster", while the controller device (i.e., the receiver, RX) acts as a Bluetooth Low Energy "Observer".

The TX can be a modern smartphone or other device running Android or iOS operating systems and with support for Peripheral operation or a custom device tailored to reproduce a typical remote controller. A working TX sample implementation has been written for Android 6.x upward and WearOS 2.0. The RX can be any device able to scan for Bluetooth Low Energy advertising packets and to control any external component through a relay or other servo controller. A working prototype has been implemented using Raspberry PI3 with Android Things 1.1.

# Technical Details
- Messages are encrypted using AES128 (The fastest known technique requires 2^126 operations to recover an AES-128 key)
- Keys are full-length 16bytes machine generated (Brute-force on typical 5-6 digit PINs is not applicable) 
- Messages are time-based (A message sent “now” becomes invalid in a few seconds, making any replay attack impossible)
- Target ID, salt and MD5 operations increase computational power needed to attack the target
- Based on the Bluetooth Low Energy Advertising (no need to open connection. The RX radio will be never exposed)

# Packet Structure

![ProjectBen TX](/images/projectben_tx.png)

![ProjectBen RX](/images/projectben_rx.png)

# License
ProjectBen is (C) 2018 by Stefano Sanna and it is released as open source software under the terms of the Apache License 2.0.
Attribution is *not* optional.
