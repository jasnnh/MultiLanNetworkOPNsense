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
![Screenshot](https://github.com/jasnnh/MultiLanNetworkOPNsense/blob/main/1.PNG)
