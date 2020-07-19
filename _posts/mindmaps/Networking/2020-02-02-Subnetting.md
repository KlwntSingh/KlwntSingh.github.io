---
title: Subnetting
layout: post
---
      
 # Subnetting  
 ## Sub-network of network classes   
 ## Classes A, B, C, D(Classful addressing)   
 * Range for each of class is defined by bits in first octet   
 * classes tell us about number of octets used in network part and host part   
 *  #### class A   
  
 	* 0.0.0.0 - 127.255.255.255   
 	* first bit of first octet is fixed and is zero   
 	* first 8 bytes are network bits   
 	* second 24 bits are host bits   
 *  #### class B   
  
 	* 128.0.0.0 - 191.255.255.255   
 	* first 2 bits are fixed i.e 10   
 	* first 2 bytes are for network and next 2 bytes for host   
 *  #### class C   
  
 	* 192.0.0.0 - 223.255.255.255   
 	* first 3 bits are fixed. 110   
 	* first 3 octets are network bits. second octet for host bits.   
 *  #### class D   
  
 	* 224.0.0.0 - 239.255.255.255   
 	* multicast address   
 *  #### class E   
  
 	* 240.0.0.0 - 247.255.255.255   
 	* reserved address   
 ## Classless adressing   
 * no classes, any number of bits can define subnet mask   
 ## VLSM(Variable Length subnet mask)   
 * here subnets are not of fixed size   
 * Biggest subnet should be calculated first   
 * same as classless addressing?   
 ## network/broadcast address   
 *  #### network address   
  
 	* host part will have all zeros   
 *  #### broadcast address   
  
 	* host part will have all ones   
 ## No of bits borrowed depends on no of subnets to be created   
 ## Last limit of subnet mask we can achieve is 30 bits   
 ## Calculations   
 *  #### Cal of no of subnets in class network   
  
 	* borrow as many as no of bits as many you want for subnets   
 *  #### calculation of subnet mask   
  
 	* when left bits are 1, and right ones are zero   
 		* 256 - 2^(no of right zero bits)   
 	* It represent no of host bits and no of network bits   
 	* One time calculation and only calculated when no. of subnets have been decided   
 	* It tell us about no of host inside network   
 *  #### calculation of ip address of network address and broadcast address   
  
 	* It is calculation for every subnet we have   
 	* First calculation no of bits used in network part   
 	* calculate all bit combination of network parts   
 	* Inside each combination, keeping host bits all zero gives network address and keeping host bits all ones give broadcast address   
 	* network address can be calculated same way adding all the no. acc to bits which are one   
 * Ultimate method to calculate subnet mask and other addresses is to just count the decimal values of each bit set as 1   
 ## Route Summary   
 * we have calculate subnet mask by shift  variable bits toward host side   
 *  #### formula is   
  
 	* 256 - no of network to be summarized   
 ## Calculating Hexadecidmals   
 * first calculate binary   
 * convert 8 bit binary into 2 4 bit nibbles   
 * convert nibles to decimal   
 * convert decimals to hexadecimals   
 ## Wildcard mask   
 * 255 - subnet mask   
 ## cheat sheat   
 * pdf - 48   
 ## Default Route   
 * 0 means variable, 1 means it is fixedhence 0.0.0.0/0 means 0.0.0.0 is starting address and 0 as subnet mask means everything is variable   
