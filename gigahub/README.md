# The Gigahub

![Bell Aliant's Gigahub](/gigahub/gigahub.jpg)

## Hardware Requirements / Recommendations:

This bypass is a little tricky and requires some technical skills. I will try to walk through it as simply as I can.

You will need an XPS-PON (>= 3Gb Plan) or a GPON (1/1.5Gb Plans).

## Warning:

Please be careful when handling fibre cables, depending on intensity and your FTTH setup, their lasers can fall under Class 2 laser hazard classification - safe for 1/4 of a second exposure, but do not stare into the laser*

*Read More: [Laser Safety Facts](https://www.lasersafetyfacts.com/laserclasses.html)

| Technology: | Module: | Speeds: | Bell Aliant Plans: |
|-|-|-|-|
| XGS-PON | SFP+ | 5Gb / 10Gb  | >= 3Gb      |
| GPON    | SFP  | 1Gb / 2.5Gb | 1Gb / 1.5Gb |

You will need access to the SFP(+) module via a desktop or over the network.
- SFP(+) Port in a Network device.
- PCI Card with SFP(+) Port.
- Media Converter to Ethernet.

## 1Gb / 1.5Gb

You will require a Router that can do VLANing and has an SFP or SFP+ port. The GPO ONT SFP module operates at 1G and 2.5G speeds, so choosing your hardware here can affect your Speeds if you have the 1.5G Fibre Package from Bell Aliant.

If your router does not provide Wireless connectivity, you will need a Wireless Access Point as well.

## 3Gb

There are two ways to approach the XGS-PON setup:

1. Buy an XGS-PON Modem
2. Buy a Router with an SFP+ Port.

If your router does not provide Wireless connectivity, you will need a Wireless Access Point as well.

## Compatibility:

| | |
|-|-|
| Internet     | ✓ |
| IPTV         | X |
| VoIP / Phone | X |

## Guide:

1. You will need to grab the following information from your Gigahub:
   - Mac Address of the WAN Port
   - Serial Number of the ONT

2. You will need to prep your hardware for accessing the firmware of the ONT:
    - Configure the interface to connect to your ONT per the following information provided by the folks @ [Hack the GPON](https://hack-gpon.org/ont/).

    Need more help? See [here.](#how-to-find-your-ont-information)

    - If you used a Modem, connect to it.

3. Following the steps from Hack the GPON, "spoof" the Serial Number to match the Serial number from your Gigahub's ONT. Make sure to reboot, and confirm the Serial Number has been saved to your ONT before continuing.

If you used a modem, make sure to "spoof" the Serial Number to match that of the Gigahub's ONT. Once again, make sure to confirm the Serial Number has been saved and confirm it matches before continuing.

4. Next, log in to your replacement router, and we will start configuring the WAN port.

- Configure the WAN port with the MAC Address from the Gigahub WAN port.*
  *This step is not 100% mandatory in some cases, but for the sake of things not going wrong, I recommend doing it anyways.

- Configure the WAN Port with the following VLANs:
   - Internet: VLAN 35

    Remember that IPTV and VoIP provided by Bell do not work here. Adding VLAN34 and VLAN36 to the port does not fix this issue.

    You should end up with something like:
    ```
    eth0.35
    ```
    where `eth0` is your WAN port.

5. Next configure your LAN subnet(s) however you choose.

6. Once you are satisfied with your configurations, replace the Gigahub by plugging your modified ONT into your Router.
   - Remove the Fibre from the module, and be careful not to look into the fibre termination or the module. Fibre network connectivity is completed using high-power lasers that can cause damage to the eyes.

   - Plug in the fibre. Make sure the fibre cable has some slack and is not at too much of an angle to damage the fibre inside the sleeve.

7. If you encounter any issues with your Internet not working, you may need to reboot the router, or release and renew the IP Address on your WAN Port.

In my experience, rebooting the router does the trick better than the release and renew.

If you use DynDNS at Home, you will need to run your service to check for the changed Public IP Address.

## How to find your ONT information
   - Find the model of your ONT, most likely a [Huawei](https://hack-gpon.org/ont-huawei/) or [Nokia/Alcatel](https://hack-gpon.org/ont-nokia/) if you get it from Bell Aliant.  If not, you can buy some online from vendors of optical equipment or hardware vendors.
   - For reference, mine was a Nokia/Alcatel G-010-S-A that I got from a Bell Aliant Technician.

## Additional Help with ONT "Spoofing"

If you're having issues figuring out Serial Numbers and converting them, you will need to know some tricks.

`$ onu gtcsng`

Outputs: `errorcode=0 serial_number="## ## ## ## ### ### ### ###"`

The first 4 numbers are Decimal Points of ASCII Characters.

The last 4 numbers are Decimal Points of Hex Characters.

Use this [ASCII Table](https://www.sciencebuddies.org/science-fair-projects/references/ascii-table) to convert the value.

The first 4 numbers are the Manufacturer ID.

The last 4 numbers are the Serial Number.

```
ONTUSER@SF:/#ritool set MfrID SMBS
ONTUSER@SF:/#ritool set G984Serial 09F90090
ONTUSER@SF:/#ritool set YPSerialNum 09F90090
```
