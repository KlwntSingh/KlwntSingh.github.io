---
title: Security Theory
layout: post
---
    
# Security Theory

## cryptography 
* #### private key cryptography or symmetric key cryptography 
	* two ways of doing it 
		* substitution(mapping) 
			* caesar 
			* vegeniere 
		* transposition(changing positions) 
			* rail fence 
			* matrix transposition 
	* two categories 
		* block ciphers 
			* steps 
				* substitution 
				* permutation 
				* looping 
			* examples 
				* des 
					* data encryption standard 
					* key size is 56 bitmessage size is 64 bit 
						* maximum key size is 56 bits 
				* 3des 
					* two waysboth uses ede 
						* 2 key 3 des 
							* k1=k2 
								* hence backward compatible with normal des 
						* 3 key 3 des 
							* k1 != k2 != k3 
					* max key size is 168 bits 
				* rjindael or aes 
			* techniques 
				* electronic code book method 
					* big message is broken in chunks of fixed bits 
						* each message chunk is encrypted with some bit key 
					* disadvantage 
						* since key is same, hence if m1 = m2 than c1 = c2 
							* hacker can see the pattern and deduce the key 
					* components 
						* message 
						* ecnryption algo i.e des or any other 
						* key 
				* cipher block chaining method 
					* each message block is changed by xor with previous message block cipher text except for first message block which is xored with IV 
						* after XOR operation, output is encrypted using encryption algorithm with key 
						* initialization vector here is sent to receiver in first message block encrypted 
					* components 
						* IV 
							* initialization vector 
						* message 
						* xor 
						* encryption algo i.e des or any other 
						* key 
		* stream ciphers 
			* concept 
				* components 
					* pseudo number generator 
					* xor gate 
					* secret key 
					* message 
				* secret is passed to pseudo number generator which generates pseudo random sequence and then this is xored with message to produce to cipher text 
			* generation of pseudo random sequence methods 
				* Linear feedback shift register(LFSR) method 
			* eg:- rc4 
* #### public key crypto/assymetric key system 
	* encryption 
		* encryption of message using public key of receiver 
	* digital signatures 
		* here encryption of message using private key of sender 
	* certificates 
		* here public keys of server are encrypted using private keys of certifficate provider whole public keys are present in borwsers 
* #### key exchange algorithms 
	* 3-way handshake 
		* when both client and server knows public keys of each other 
	* trusted third party 
	* diffie hellman exchange 
		* keys are never exchanged on line, only temporary data which helps to generate the keys on each end is exchanged on line 
		* this helps incase in future, private key is hacked than all the previous communication will be compromised 

## wireless security 
* #### standards 
	* wireless wan 
		* eg:- cellular networks, mobile wimax(802.20) 
	* wireless man 
		* eg:- fixed wimax(802.16) 
	* wireless lan 
		* eg:- wifi(802.11) 
		* standards 
			* 802.11i 
				* security standard, wpa2 
	* wireless pan 
		* 802.15 eg:- nfc, bluetooth, rfid 
* #### components and architecture 
	* all components are called as stations 
	* wireless client 
		* fixed nodes like desktop, mobile nodes like mobile phones 
	* Access points 
		* base stations 
	* basic building block of 802.11 wlan is called basic service set(bss) 
		* independent bss 
			* no access point. also called adhoc network 
		* infrastructure bss 
			* access point serve as base station for receiving and broadcasting 
* #### addresses 
	* bssid 
		* mac-address of ap 
	* ssid / essid 
		* chareacter string of max 32 bytes assigned by admin 
* #### different levels of security 
	* basic level security 
		* mac address filtering 
			* access points are configured to accept authentication from clients with legitimate mac-address. 
			* works similiar as access control list but at mac layer 
		* service set identifier 
			* we stop beaconing i.e ap broadcasting ssid in clear text to all the wireless clients. hence when any new user scans for available ssids, it will not be listed. only user who know the name of ssid will be able to connect 
	* medium level security 
		* wired equivalent privacy 
			* proposed to provide link level security 
			* intended security goals were confidentiality, integrity, authentication and access control 
				* but only were achieved authentication and confidentiality 
			* secret key size 40bits or 104bits 
				* after concatenation with 24 bit iv it is 64 or 128 bit 
			* encryption algorithm is similiar to rc4 
				* because it uses pseudo random number generator to generate pesudo sequence to encrypt plain text message 
			* concepts 
				* key is concatenated with IV(initialization vector) to form 64 or 128 bit long key which is passed through sequence number generator and gives random sequence number. ICV(integrity check value) is calculated over plaintext. ICV + plain text is xored with  random sequence number to give out cipher text. 
					* this cipher text is concatenated with IV and sent 
			* components 
				* IV 
					* Initializaiton vector 24 bits 
				* 40 or 104 bit key 
				* Pseudo random number generator 
				* plain text 
				* xor 
					* plaintext + ICV 
					* pseudo random sequence 
				* ICV 
					* integrity check value 
						* weaker integrity just like CRC 
			* wep authentication 
				* wireless client sends authentication request 
				* AP sends random challenge in text in clear 
				* client encrypts the challenge text and sends back it to the access point 
				* the access point authenticates the client by decrypting the challenge response 
	* high level security 
		* wifi protected access version 1 
			* components 
				* 802.1X 
					* security goals 
						* authentication 
					* authentication protocol 
						* generates session key by taking in credentials from user and than providing back the session credentials 
				* TKIP 
					* temporal key integrity protocol 
					* features 
						* change encryption and authentication keys every frame 
						* Stronger integrity check algorithm. algorithm mic(message integrity code) based on hmac is used 
						* sequence numbers are added to frame fragments to prevent replay attacks 
						* increased iv size i.e 48 bits 
					* security goals achieved 
						* confidentiality 
						* integrity 
					* encryption algorithm is similiar to rc4 
						* because it too uses psg to generate random seuqence to xor with plain text 
					* component 
						* phase 1 mixer 
							* 128 bit key generated by 802.1x 
							* source mac address 
							* output is intermediate key 
						* mic 
							* payload 
							* 28 bit key generated by 802.1s 
							* source mac addres and dest mac address 
							* ouput - payload + hash 
						* phase 2 mixer 
							* intermediate key 
							* sequence number 
							* ouput - concatenated seuqence number and internetidate key 
						* fragmenter 
							* payload + hash 
							* output - sequence number, concatenated fragments of message chunk 
				* wep 
					* third component is wep component for encryption 
				* weakness 
					* one way authenticaton in 802.1x 
					* management frames are not encrypted 
				* both 802.1x and TKIP is used.802.1X is used for authenticating users and generate secret key to use for session. 
		* wifi protected access version 2(802.11i) 
			* encryption algorithm used is AES called cipher block chaining mode message authentication code protocol 
			* 802.1X has been extended to provide bi-directional authentication 
			* components 
				* TKIP 
				* CCMP 
					* aes based encryption 
				* enhanced 802.1X 
			* weakness 
				* management frames are not encrypted 
			* attacks 
				* management frame flooding 
				* channel synchronization 
		* wireless vpns 
			* ipsec vpn protects only at network layer and above.any attack launched at physical layer or data link layer cannot be protected 

## Firewalls 
* #### first generation firewall: packet filter 
	* eg:- packet filtering routers 
		* they use acl's 
			* An acl can filter based on following parameters 
				* source ip 
				* destination ip 
				* protocol encapsulated like tcp, udp, icmp, igmp etc 
				* port no. i.e destination port no. 
				* incoming interface/ outgoing interface 
			* two types of acl 
				* standard 
					* deny based on source ip address only 
					* acl - number 
						* 0-99 
					* eg:- access-list ACL_NUMBER allow/deny SOURCE_IP SUBNET_MASK 
				* extended 
					* deny based on source, destination and encapsulated protocol 
					* acl-number 
						* 100 - 199 
					* eg:- access-list ACL_NUMBER permit/deny PROTOCOL SOURCE_IP SUBNET_MASK DESTINATION_IP SUBNET_MASK eq PORT 
	* eg:- gateways 
		* provides proxy services 
		* also there is concept of NAT 
			* static NAT 
			* dynamic NAT 
				* many to pool nat 
				* many to one natalso called as PAT(port address translation) 
					* here, source IP and Port are changed to ip address of gateway and random port no. 
* #### second generation firewall: statefull firewall 
	* table maintained at statefull firewall 
		* Subtopic 1 
			* Subtopic 1 
			* Subtopic 2 
			* Subtopic 3 
			* Subtopic 4 
			* Subtopic 5 
			* Subtopic 6 
			* Subtopic 7 
			* Subtopic 8 
* #### third generation: next generation firewall 
	* deep packet inspection 
	* IPS 
	* anti-virus solution 
	* application firewall 
	* focus is to protect internal client when accessing applications on internet 
* #### Web application firewall 
	* usually used to protect web application 
	* has advanced ssl/tls traffic decryption mechanism to scan web protocols 
	* deployed on server side to protect web servers/application 

## VPN [anchor](xmind:#757lttt5s8si528hbtdr2q2fcl "anchor")
* #### types of VPN 
	* remote access 
		* eg:- ssl vpn 
	* site to site 
		* eg:- ipsec 
* #### VPN protocols 
	* IPSec 
	* L2TP 
	* point to point tunneling protocol 
	* secure socket(SSL) and transport layer security 
* #### eg: of VPN's 
	* DMVPN 
		* layer 3 over layer 3 
	* MPLS vpn 
		* layer 3 over mpls 
	* VPLS 
		* Layer 2 over mpls 
	* IPSec tunnel 

## security goals 
* #### Confidentiality 
	* encryption 
* #### Integrity 
	* hash 
		* one way computation 
		* we encrypt hash using digital signature 
* #### Availability 
	* achieved by redundancy for protection against ddos 
* #### Certification 
	* for validity of source of information/ or other side 
* #### Access control/Authorization 
	* level of access for user 
* #### Authentication 
	* username/password. 
	* validity of requester 
* #### Non-Repudiation 
	* proof for transaction with receiver 
	* achieved using signature 
		* encryption is done by private key of sender and decrypted by receiver using public key of sender 

## hashes 
* #### md5 
	* output: 128 bit 
* #### sha256 
	* output: 256 bit 

## phases of security plan 
* discover/inspection 
* protection 
* detection 
* responding 
* recovering 

## ssl/tls 
* #### ssl1 
	* never released publicly 
* ssl2 
* #### ssl3 
	* replaced ssl2 completely 
* #### tls1 
	* improved version of ssl3 
* tls1.1 
* #### tls1.2 
	* latest 
	* very less improvement after tls1 
# IPSec

## phase 1 
* #### operates in two modes 
	* main mode 
		* uses 6 packets 
	* aggresive mode 
		* uses 3 packets 
* #### steps 
	* ike sa 
		* this association is bidirectional 
	* diffie helman exchange 
	* authentication 
* this is for management data between endpoints 

## phase 2 
* uses 3 packets to complete 
* #### stesps 
	* ipsec sa 
		* this is unidirecitonal association 
	* optional diffie helman exhcange 
* this is for encrypting actual data 

## esp vs ah 
* #### ah 
	* authentication header authenticates ip header too 
		* hence ip header cannot change during nat hence if nat traversal is used,  it will be break ah authenticated ip header. ah header is kept out of scope for nat traversal 
	* protocol no. 
		* 51 
	* header fields 
		* next header code 
			* 1 byte 
		* header length 
			* 1 byte 
			* In 4 byte word 
		* reserved 
			* 2 byte 
		* security parameters index 
			* 4 bytes 
		* sequence number 
			* 4 bytes 
		* authentication code 
			* multiple of 4 bytes 
			* variable length 
	* provides following feature 
		* authentication 
		* integrity 
		* integrity of ip header 
		* protects against replay attack 
* #### esp 
	* it encrypts the payload but does not provide authentication for ip header 
		* hence ip header can change, than why not change it during nat and it should work? 
			* In icmp, identifier can be used as port number. but in esp there is no identifier hence response cannot be mapped with request. So in nat(pat) we came with new concept of nat traversal 
			* new ip header | udp header nat traversal | esp header | encrypted payload | esp trailer 
	* protocol no in ip header 
		* 50 
	* header fields 
		* security parameter index 
			* 4 byte 
		* sequence number 
			* 4 byte 
		* encrypted part 
			* Subtopic 1 
		* padding 
			* Variable length to add to encrypted part to leave last 2 bytes from multiple of 4 byte 
		* padding length 
			* 1 byte 
		* next header 
			* 1 byte 
		* authentication code 
			* multiple of 4 bytes 
	* provides following feature 
		* provides integrity 
			* but only for esp layer and above 
		* authentication 
		* encryption/confidentiality 
		* protects against replay attacks 

## modes 
* #### tunnel 
	* protects the actual source/destination 
* transport mode 

## notes 
* a) A host MUST support both transport and tunnel mode.b) A security gateway is required to support only tunnelmode.  If it supports transport mode, that should be usedonly when the security gateway is acting as a host, e.g.,for network management. 
* #### fragmentation 
	* fragmentation should happen prior to ah/esp header so that, decryption can before reassembly 
	* transport mode 
		* here ipsec header is applied to whole ip datagrams 
		* as there will be only one ip header and if security protocol is applied on fragmented packet than for every fragment there will be security protocol header rather than one security header for whole packet which is than fragmented 
	* tunnel mode 
		* here ipsec is applied to fragmented 
		* here we have two ip headers, one which which is nested inside the tunnel 
		* here performance is improved by directly decrypting the packet before reassembling it 

## fields which uniquely identifies SA 
* security protocol i.e esp/ah 
* SPI 
* destination address 

## nat traversal 
* encapsulating esp header in udp header 
* esp header in upd port 4500 
* isakmp in udp port 500 
# VPN

## VPN protocols 
* IPSec 
* L2TP 
* point to point tunneling protocol 
* secure socket(SSL) and transport layer security 

## types of VPN 
* remote access 
* site to site 

## eg: of VPN's 
* #### DMVPN 
	* layer 3 over layer 3 
* #### MPLS vpn 
	* layer 3 over mpls 
* #### VPLS 
	* Layer 2 over mpls 
* IPSec tunnel 

## based on provisions 
* #### CE based provisions 
	* configuration, control and intelligence is provided by customer edge router 
	* eg:- gre, ipsec 
* #### PE based provisions 
	* configuration is done on providers network and hence called provider provisioned network 
	* eg: MPLS vpn 

## goals 
* privacy 
* connecting remote routers 
* using private addresses 
* bandwidth requirement 
* change in configuration for adding new customer site 

## two models 
* #### overlay model 
	* point to point link 
		* eg: atm, frame-relay 
	* IP over Ip netowrk 
		* eg: gre, ipsec 
* #### peer to peer model 
	* peership is made been CE and PE 
