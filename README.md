# Banking-System-Network

Banking Network Design: 7th–8th floor (HR, CS, MK – 40 users + 40 IP phones + 1 AP each; LM, IT – 20 users + 20 IP phones + 1 AP each). Dual ISP (Safaricom, JTL), scalable, redundant, secure HQ ↔ Server-Side WAN.


<img width="686" height="411" alt="Banking" src="https://github.com/user-attachments/assets/0ee7cf1e-e0a6-4cde-87f5-f2fecb0a7e84" />




Zones/Segmentation: Separate VLAN per department (HR, CS, MK, LM, IT), Voice VLAN120 (10.10.10.0/24), Data 192.168.20.0/24 (subnetted per dept), Public 190.200.100.0.

HW: 2x Cisco 2911 (HQ + Server-Side), 1x Cisco 2811 (VoIP GW), 2x Multilayer Switch (HQ Core), 6x Access Switches (Dept), External Server-Site (DHCP/DNS/WEB/EMAIL).

Routing: OSPF (routers + L3 switches), Inter-VLAN SVI + router-on-a-stick where required.

Redundancy: Dual ISP uplinks per router, hierarchical design (Core–Access).

Security: ACL policies (HQ ↔ Server-Site), Standard ACL on VTY (SSH only IT dept), Port-Security (sticky MAC, violation shutdown – server switch), NAT PAT (outbound int IP + ACL), IPsec Site-to-Site VPN + ACL.

Services: DHCP (Data – Server-Side), DHCP (Voice – Router), Static IP (Servers), VoIP dial plan (4xx), WLAN per department.

Basic Config: Hostnames, console/enable passwords, banner MOTD, service password-encryption, no ip domain-lookup, SSH on all routers + L3 switches.

PT Implementation: VLAN segmentation (data + voice), trunking, OSPF area config, DHCP scopes, NAT/PAT, IPsec VPN, ACL filtering, VoIP config, WLAN config, full comms testing verified.

Secure, redundant, scalable enterprise banking infrastructure.
