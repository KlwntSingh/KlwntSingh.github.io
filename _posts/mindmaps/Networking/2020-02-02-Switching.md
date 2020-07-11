---
title: Switching
layout: post
---
      

# Switching  

* VLAN [anchor](xmind:#660743mpfkat87movef51paff9 "anchor")  

## VTP(VLAN Trunking Protocol)   

### server   

* also act as client,when advertisements are coming from other server in domain   

* for any change in vlan i.e creation, modification deletion, advertisements will be sent to all vtp client and also increase in version number   

* default mode on unconfigured switches   

### client   

* with higher version number can update server   

* vlan cannot be manually created/deleted on clients   

* receives and forwards vtp updates   

### transparent   

* only forward advertisements   

* do not take participate in vtp   

### VTP prunning   

* to save bandwidth from traffic of vlan which is not present on switch, vtp removes vlan from trunk port whole acess port do no exist on end switch   

* VTP traffic cannot travel over access link because wrapped by trunking header and it always use vlan id - 1 even if native vlan is other than 1   

## DTP(Dynamic Trunking Protocol)   

* negotiation protocol for trunking mode(access, trunk) of interface   

### Disabling DTP   

* switchport nonegotiate   

* and should manually configure interfaces to be either trunk, access   

* cisco proprietary   

## Troubleshooting   

### interface downshow interface NAME NUMBER   

* Cable issue i.e cross-over or straight cable or broken cable   

* interface issue   

* duplexity   

* speed   

* port security   

* protocol mismatchLayer 2 protocols like hdlc, ppp   

### Vlan   

* interfaces in different vlan   

#### interfaces with different switchport mode   

* on having access and other having trunk   

* VACL(Vlan access list)   

#### encapsulation protocol  mismatch   

* one running isl and other running dot1q when two switches are connected   

* Trunk allows VLAN or not   

## commands   

### sh interfaces NameNumber   

* to give detail of interface if it up and if there is error, what is the error   

### sh interfaces NameNumber switchport   

* gives information about switchport operational mode, administrative mode, encapsulation protocol etc   

* sh port-security interface NAMENUMBER   

### sh interface NameNumber trunk   

* gives information about allowed vlans on trunk   

* STP [anchor](xmind:#05ei4hj8mtu5krsvknhk3f311f "anchor")  

## Security   

### DHCP snooping   

* helps use make interface connected to host as untrusted which blocks DHCP offer from that interface   

* Also block particular interface receiving too much of dhcp discover packets   

## Discovery protocols   

### CDP   

* cisco discovery protocol   

### LLDP   

* Link layer discovery protocol   

* IEEE 802.1ab   

## ip routing command   

* with ip routing command, we can run routing protocols on switch   

### with no ip routing command   

* directly connected routes and static routes can exists   

* packet can switch if comming to any network on switch from any interface   

* packet cannot switch if comming from one interface and supposed to get out of another interface   

### ways to make switch layer 3   

#### svi   

* vlan interface   

* loopback interface   

* ip on interface   

## headers stacked   

* bpdu(stp - 35 bytes) can travel on both trunk and access, vlan trunking(VTP) - can travel only on trunking   

* dot1q header(4 bytes)   

* ethernet 802.3(18 bytes)   

## Layer 2 protocols   

### stp   

* loop prevention mechanism   

### cdp   

* device discovery protocol   

### dtp   

* trunking mode negociation protocol   

### vtp   

* vlan creation/sharing protocol   

# STP  

## Why?   

### to avoid loops because we use extra cables for redundancy   

#### how loops affect?broadcast traffic will overburden the switch   

* arp broadcast traffic   

* when switch does not know the mac-address to interface mapping   

* Ethernet frames does no have ttl   

* lowest bridgeId is considered root bridge   

* woks on both trunk and access ports   

## bpdu   

### bridge id8 bytes   

#### priority   

* total: 2 bytes   

##### bridge priority   

* 4 bits   

##### extended system id   

* 12 bits   

#### mac address   

* 6 bytes   

* total: 35 bytes   

## Uses BPDU(Bridge protocol data unit) which STP uses and contains   

* priority   

* mac address   

## Port Roles   

### 802.1dSpanning tree protocol   

* root port   

* designated port   

* blocked port   

### 802.1wRapid Spanning tree protocol   

* root port   

* designated port   

#### blocked port   

* does not forward any frame   

* only accepts BPDU and not any other data frames which are dropeed   

#### Alternate Port   

* 802.1w   

#### Backup Port   

* 802.1w   

## Different states   

### disabled state   

* non operational port   

* administratively down port   

### Blocking state   

* when port is non-designated port or alternate port than it is in blocking state   

* remains there for 20 secs when topology changes   

* all ports are in this state by default when stp starts. Here port only listens for BPDU   

* selection process of root bridge happens   

* if blocked port stop receiving BPDU's than it will move to listening state after 20 sec   

### listening   

* 15 second   

* Just forwards BPDU from root bridge   

* Switch does not learn mac-address and no data transmission   

* does not forward data frames   

### learning   

* 15 seconds   

* Forwards BPDU's from root bridge   

* listen to data frames but does not forwards them   

* Switch start learning address but no data transmission   

### forwarding   

* data trasmission started   

## portfast   

### when enabled   

* there will be no topology change update generated on interface with it enabled   

* interface will go directly to forwarding state without it going to listening and learning state   

* should only be enabled on interfaces which are connected to host and are in access mode   

* cisco proprietary   

* method of making port state switch to forwarding fast   

## Many Versions   

* Per-Vlan SPT(Cisco Proprietary)Default on cisco switches   

### RSTP   

#### port states   

* discarding   

* learning   

* forwarding state   

#### port roles   

* root port   

* designated port   

* alternate port   

* backup port   

* bpdu are generated by every node and exchanged with neighbor while in case of normal stp, bpdu are only created by root bridge   

## timers   

### hello time   

* 2 sec   

* every 2 sec bpdu will be sent   

### age time   

* 20 sec   

* if no bpdu arrives in 20 second, than something has changed and need to check topology again   

### forwarding delay   

* 15 sec   

* This is the time for each of listening and learning state before going into forwarding state   

## time lapse   

### 1. Every bridge think themselve of bridge and every port is in blocking state   

* what this means every bridge is generating bpdu's, with themselves as root bridge   

### 2. As, Adjacent switches start receiving BPDU, they compare them and change root bridge to the bridge with lowest bridge ID.   

* Only root bridge can generate BPDU's, other's can just listen to them   

#### This keep continuing for around 20 sec, and after 20 secons   

* On root, every port changes state to listening state   

* On other bridges, Only ports on which BPDU with lowest bridge ID received is changed to listening   

### After 20 seconds, state has been changed to listening for some of ports   

#### Reason for choosing 20 seconds is because In Ideal Topology where STP can be stable   

* BPDU from root can reach extreme end bridge in 14 secs and each bridge adding 1 second to received max age   

* After other 15 seconds, listening is moved to learning   

* After other 15 seconds, it is moved to forwarding   

* After Learning state only, port roles can be decided   

## different versions   

### 802.1d   

* normal stp   

### 802.1w   

* rapid stp   

### pvstp   

* similiar to stp but per vlan   

### rvstp   

* similiar to rvstp but per vlan   

### pvstp+   

* plus means stp run over 802.1q trunks   

* rvstp+   

### problems with per vlan stp's   

* they do not scale if no. of vlan's increases   

# VLAN  

## trunking mode   

### trunk   

* form unconditional turnk   

* with vlan identifier but native vlan without indentifier   

#### encapsulation types   

* dot1q   

##### isl   

* cisco proprietary   

### accessnontrunking   

* always without vlan identifier   

### dynamic auto   

* depends on other port, if trunk it will be trunk. if other side interface is access, it will be access. if other port is also dynamic auto, it will be access   

* default on newer switches   

* forms trunk if request by far end   

### dynamic desirable   

* It will try to form trunk   

* default in older switches   

* attempts to form trunk   

* link for better explanation [anchor](http://www.ciscopress.com/articles/article.asp?p=2181837&seqNum=8 "anchor")  

## Voice Vlan   

* ip phone will have three ports, one for switch, one for itself and one for computer.   

* trunk mode will be used between switch and ip phone even though in configuration it will say non trunking   

* data traffic will be untagged while voice traffic will be tagged   

* data traffic will be sent over access mode and voice traffic over voice vlan   

* IP phone will learn about vlans using cdp, lldp   

## InterVlan Routing   

### router on stick   

* creating sub interfaces on router interface   

#### advantages   

* no need to buy layer 3 switches   

#### disadvantage   

* router is single point of failure   

* traffic flows up and down on same link hence chances of congestion   

### svi(Switched virtual interface)   

* assigning ip address to virtual interfaces   

#### when ip address is assigned, routing table entry is created   

* routing table is enabled by using ip routing command   

* This is also used for remote management of switch   

#### certain conditions for svi to be up   

* vlan should be active   

* vlan should have atleast 1 access or trunk port   

* ip address of svi will be used as default gateway for hosts   

* routing protocols can be enabled to create dynamic route for remote switch with svi   

### Routed port on switches   

* Making layer 2 switches layer 3 switches   

#### commands   

* no switchport in interface configuration mode   

* port have no knowledge of any vlans   

* does not suport subinterfaces like router does   

* routing protocols can be enabled   

* Connecting two ports of switch two ports of router   

## Security   

### bpdu guard   

* protects from getting bpdu's from host and host should be connected using access mode on interface   

## trunking   

### header   

#### dot1q   

* 4 bytes   

##### vlan id   

* 12 bit   

#### isl   

* 26 bytes header   

* 4 bytes trailer   

## default VLAN's   

* max vlans - 4096(0-4095)   

### 0   

* reserved   

### 1   

* default   

### 1002   

* fddi-default   

### 1003   

* tr   

### 1004   

* fdnet   

### 1005   

* trnet   

### 1006-4094   

* extended   

### 4095   

* reserved   
