# ProjectBen

ProjectBen is a protocol proposal for implementing secure one-way remote controllers based on Bluetooth Low Energy advertising packet.

Main features of ProjectBen protocol are:
- fits into standard Manufacturer Specific Data of Bluetooth 4.x advertising packet
- uses symmetric cryptography to encrypt payload
- payload depends on absolute time and encryption keys depends on random number: time dependency avoids replay attacks and random keys harden the protocol against brute force attacks

