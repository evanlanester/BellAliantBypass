# Fibe R3000

![Bell Aliant's Actiontec R3000](/R3000/r3000.jpg)

## Hardware Requirements / Recommendations:

You will require a Router that can do VLANing, most home office grade routers can do this out of the box. If not, maybe choose something that can be flashed with OpenWRT or DD-WRT.

If your home office router does not provide Wireless connectivity, you will need a Wireless Access Point as well.

## Compatibility:
| | |
|-|-|
| Internet     | ✓ |
| IPTV         | ✓ |
| VoIP / Phone | ✓ |

## Guide:

I recommend first configuring the device that will be replacing your R3000.

1. You will need to grab the following information from your R3000:
   - Mac Address of the WAN Port

2. Next, log into your replacement router, and we will start configuring the WAN port.

- Configure the WAN port with the MAC Address from the R3000 WAN port.*
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

4. Once you are satisfied with your configurations, replace the R3000 by unplugging it from the ONT and plugging your replacement router's WAN port to the ONT.

5. If you encounter any issues with your Internet lighting up, you may need to reboot the router, or release and renew the IP Address on your WAN Port.

In my experience, rebooting the router does the trick.

If you use DynDNS at Home, you will need to run your service to check for the changed Public IP Address.