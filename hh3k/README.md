# Home Hub 3000 (HH3K)

![Bell Aliant's Home Hub 3000](/hh3k/hh3k.jpg)

## Hardware Requirements / Recommendations:

You will require a Router that can do VLANing and has a SFP or SFP+ port. The GPO ONT SFP module operates at 1G and 2.5G speeds, so choosing your hardware here can effect your Speeds if you have the 1.5G Fibre Package from Bell Aliant.

If your router does not provide Wireless connectivity, you will need a Wireless Access Point as well.

## Compatibility:
| | |
|-|-|
| Internet     | ✓ |
| IPTV         | ✓ |
| VoIP / Phone | ✓ |

## Guide:

I recommend first configuring the device that will be replacing your HH3k.

1. You will need to grab the following information from your HH3K:

- Mac Address of the WAN Port

2. Next, log into your replacement router, and we will start configuring the WAN port.

- Configure the WAN port with the MAC Address from the HH3K WAN port.*
  *This step is not 100% mandatory in some cases, but for the sake of things not going wrong, I recommend doing it anyways.

- Configure the WAN Port with the following VLANs:
   - IPTV: VLAN 34
   - Internet: VLAN 35
   - VoIP: VLAN 36

    You should end up with something like:
    ```
    eth0.34
    eth0.35
    eth0.36
    ```
    where `eth0` is your WAN port.

3. Next configure your LAN subnet(s) however you choose.

4. Once you are satisfied with your configurations, replace the HH3K by removing the GPON ONT SPF from your Homehub 
   - Remove the Fibre from the module, and be careful to not look into the fibre termination or the module. Fibre network connectivity is completed using high power lasers that can cause damage to the eyes.
   - Remove the GPON ONT SPF from the HH3K. Be careful to remove it properly, by pulling down the lever and then pulling it out.

   - Plug the GPON ONT SPF into your Router's SPF port, and then plug in the fibre. Make sure the fibre cable has some slack, and is not at too much of an angle to damage the fibre inside the sleeve.

5. If you encounter any issues with your Internet lighting up, you may need to reboot the router, or release and renew the IP Address on your WAN Port.

In my experience, rebooting the router does the trick.

If you use DynDNS at Home, you will need to run your service to check for the changed Public IP Address.