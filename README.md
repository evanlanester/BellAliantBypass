# Bell Aliant Modem Bypass
How to Bypass your Bell Aliant provided Modems guides for a variety of the Bell Aliant provided hardware.

## General Information on Bell Aliant's Infrastructure

Bell Aliant provides Atlantic Canadians with Passive Optical Networking in the form of GPON and now XGS-PON.

PON allows for multiple services to be provided by Internet Service Providers such as Internet, VoIP and IPTV. Subscribers to Bell Aliant Services receive their services across either a COAX or Fibre to the Home (FTTH) setup. 

The line from Bell Aliant originates from their Optical line terminal (OLT) terminates in a Optical Network Termina (ONT) device or module.

The Virtual Lcal Area Networks (VLAN) used to segregate Internet, VoIP and IPTV are:

| Service | VLAN |
|-|-|
| IPTV     | 34 |
| Internet | 35 |
| VoIP     | 36 |

Bell Aliant uses the Serial Numbers of your ONT device or module to authenticate your connection. There is no PPPoE User or Password used to authenticate your connection in Atlantic Canada.*

*Very old or some Rural setups with Bell Aliant have used PPPoE in the past.

## Legacy

- [Actiontec R3000](/r3000/README.md)

## Fibre to the Home

- [Homehub 3000](/hh3k/README.md)
- [GigaHub](/gigahub/README.md)

# Recommended Resources:

https://hack-gpon.org/

[Van Tech YouTube's Nokia G-010-S A](https://youtube.com/watch?v=3g6mRDfUppQ)

[ASCII Table](https://www.sciencebuddies.org/science-fair-projects/references/ascii-table)

https://github.com/hwti/G-010S-A