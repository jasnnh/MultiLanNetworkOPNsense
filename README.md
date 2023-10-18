# MultiLanNetworkOPNsense
Setting up a Multi-LAN Network and using a NGFW Firewall OPNsense.

What is a Multi-LAN Network?
A Multi-LAN Network A set of LAN Networks treated as one Network

Download a Windows 10 ISO Image, a VM application in this example we will use the Oracle VM & OPNsense image.

Windows 10 ISO:
https://www.microsoft.com/en-us/software-download/windows10

Oracle VM:
https://www.virtualbox.org/wiki/Downloads

OPNsense:
https://opnsense.org/download/

Lets configure our Network settings, File > Tools > Network Manager and under the NAT Networks tab click the create button and use the following settings in the image below. I'm naming my Network WAN with IP 192.168.10.0/24

![Screenshot](https://github.com/jasnnh/MultiLanNetworkOPNsense/blob/main/start.PNG)

After creating a VM with the OPNsense image lets configure the VM Network settings, right-click > Settings > Network under Adapter 1 set it to NAT Network and using the WAN that we just configured

![Screenshot](https://github.com/jasnnh/MultiLanNetworkOPNsense/blob/main/2.PNG)

Under Network settings Adapter 2 set it to Internal Network and name it LAN, and under Adapter 3 repeat this step however name it Guest_LAN instead now our network will have 3 networks WAN which will be our access to the internet and the 2 Guest Networks (our Multi-LAN)

![Screenshot](https://github.com/jasnnh/MultiLanNetworkOPNsense/blob/main/3.PNG)

Run the OPNsense VM, once ran you must configure the Firewall first before it's working so what we will be doing is Option 1 Assigning Interfaces assign our WAN network that we assigned as 192.168.10.0/24 and our LAN enter the configuration that is prompted after you select 1. After Assigning Interfaces we will now proceed to Option 2 Set Interface IP address you can use any settings that you want. Once finished OPNsense will give us a Link to access the firewall panel in the browser like below:

![Screenshot](https://github.com/jasnnh/MultiLanNetworkOPNsense/blob/main/image4.png)

use the Link given and configure and secure your Firewall! in my case my IP is http://192.168.2.1 the default login should be username: root & password: opnsense you can also go to the OPNsense VM and hit option 3 to reset the password, but once logged on go to Lobby > Password and change the default password. Also make sure to go into Systems and update to the latest version.

![Screenshot](https://github.com/jasnnh/MultiLanNetworkOPNsense/blob/main/image5.png)

Now by default we have WAN and LAN Networks setup we now need to add the 3rd network via OPNsense as the DHCP assigned IPs will be assigned by our OPNsense. so in the panel go to Interfaces > Assignments and add the 3rd Network and name it Guest_LAN now our Multi-LAN Network should be fully up and operational.

![Screenshot](https://github.com/jasnnh/MultiLanNetworkOPNsense/blob/main/image6.PNG)

Under Services > DHCPv4 > Guest_LAN you can set the IP address for this network i simply used 192.168.3.1, make sure it's enabled and configured correctly when u boot up PC1 and PC2 PC1 should be on the LAN Network (192.168.2.x) and PC2 should be on Guest_LAN (192.168.3.x)
