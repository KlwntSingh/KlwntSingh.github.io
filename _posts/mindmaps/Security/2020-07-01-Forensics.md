---
title: Forensics
layout: post
---
      
 # Forensics  
 ## mobile   
 * tools   
 *  #### iphone   
  
 	* phone disk   
 		* for navigating through phone like navigating through hard disk   
 	* iphone backup extractor   
 ## OS [anchor](file:Certifications.xmind "anchor")  
 ## malware forensics   
 *  #### online tools   
  
 	* virustotal   
 	* cuckoo   
 *  #### static analysis   
  
 	* MiTCe Exe   
 		* to see detail of windows executables   
 	* strings   
 		* to see all the strings used in execucatble   
 	* PEiD   
 		* to see if executable is packed  or noot   
 *  #### dynamic analysis   
  
 	* process explorer   
 		* detailed view of processe   
 	* procmon   
 		* to see all the system calls by process   
 	* olly debug   
 *  #### malware analysis ways   
  
 	* hash based detection   
 		* calculating and matching simple md5, sha1 hashed   
 		* if 1 bit of executable code changes, hash changes   
 	* signature based detection   
 		* languages like YARA is used to create rules which is basically finding certain strings etc in binary files   
 	* behaviour based detection   
 		* running the executable file and watching it's behaviour   
 ## material   
 * lenas reversing for newbies   
 ## PE file format   
 *  #### format   
  
 	* Dos header   
 		* totoal size - 64 bytes   
 		* used to tell dos if this can run in dos if yes, dos stub is executed   
 		* struct   
 			* magic   
 				* word - first 2 bytes   
 				* if MZ means valid dos header and dos stub can be default one   
 			* lfanew   
 				* DWrod(4 bytes double word)   
 				* this specifies offset of PE header in reverse order related to file beginning(specifies the address)   
 	* dos stub   
 		* default stub is printing "The program must run in Microsoft windows"   
 	* PE header   
 		* defines structure named Image_nt_header   
 			* signature   
 				* dword - 4 bytes   
 				* valid values   
 					* PE   
 			* file header   
 				* 20 bytes   
 				* is also struct and its members are   
 					* machine   
 						* word - 2 bytes   
 					* numberOfSection   
 						* word - 2 bytes   
 					* timeDateStamp   
 					* PointerToSymbolTable   
 					* NumberOfSymbols   
 					* SizeOfOptionalHeader   
 						* word - 2 bytes   
 					* Characterstics   
 						* defines whether is executable or dll   
 						* word - 2 bytes   
 			* optional header   
 				* 224 bytes   
 				* struct   
 					* Data Directory   
 						* 128 bytes   
 					* AddressOfEntryPoint   
 						* double word - 4 bytes   
 						* specifies the address of first instruction to be executed.   
 						* packers usually change this value to point to decompression stub. starforce protection is that extracted code section is not written to disk but kept in memory   
 	* Section Table   
 	* Section 1   
 	* Section 2   
 ## tools   
 *  #### Helix   
  
 	* creates ram image   
 *  #### volatility   
  
 	* scans ram image file taken from any memory imaging tool   
 *  #### livekd   
  
 	* included in sysinternal tools   
 	* also used to take image of memory   
 	* requires wdk(windows driver toolkit)   
 *  #### FTK imager   
  
 	* free and working file imager   
 *  #### CFF   
  
 	* binary file header analyser and editor   
 *  #### PEStudio   
  
 	* for analysis binary files   
 *  #### sysinternal tools   
  
 	* task manager   
 		* enable command line in details page   
 ## Facts   
 * word - 2 bytes   
 # Malware Analysis  
 ## windows   
 *  #### modes   
  
 	* usermode   
 	* kernel   
 *  #### process   
  
 	* manages object   
 	* thread is actual runnable entity   
 *  #### objects and handles   
  
 	* objects are static structures in kernel   
 		* kernel mode can directly access these objects directly   
 	* handles are used to access these objects from user mode   
 ## malware acquisation   
 * getting it from infected end user computer   
 * downloading/searching search engine   
 * setting a honeypot for malware   
 ## steps for malware analysis   
 * 1. scanning with different A/V softwares   
 *  #### 2. opening binary with hex editor   
  
 	* is used to see if packer is used   
 *  #### 3. anlaysis   
  
 	* 1. code analysis   
 	* 2. dynamic analysis   
 		* before performing dynamic anlaysis, service packs are installed, hotfixes are done.networking should be host only because we need to isolate VM so that malware cannot spread. bridge/nat both are dangerous. also take snapshot before executing installing malware with all analysis tools required and hotfixes and patches   
 		* keep 4 tools running when starting to analyse malware   
 			* process explorer   
 			* tcpview   
 			* windump   
 			* explorer   
 ## terms   
 *  #### dissambler   
  
 	* assembly to readable code   
 *  #### debugger   
  
 	* checking flow of execution as code runs   
 *  #### decompiler   
  
 	* byte code to readable code   
 *  #### packer   
  
 	* when using packer, binary is packed and when unpacked rather than being written to disk the unpacked binary remains in memory hence difficult to detect   
 ## tools   
 *  #### static analysisstudying code to see behaviour   
  
 	* IDA pro   
 	* strings   
 		* to see ascii string/codes in binaries   
 	* winhex   
 		* hex editor   
 *  #### dynamic analysisdebugging or run-time analysis(checking behaviour as we run binary)   
  
 	* winanalysis   
 		* to take snapshots before and after running malware to compare the any changes in system   
 	* ollydbg   
 		* feature rich   
 		* user mode debugging   
 		* things to do when doing analysis   
 			* 1. import statements tell us scope of application i.e what it can do?   
 			* different ways to detect packed applciation   
 				* 1. tail jump, where packer ends is where malware starts and it usuaaly after long jump   
 	* windbg   
 		* usermode and kernel mode debugging   
 	* IDA pro   
 		* debugger and dissambler   
 # Reverse Egnineering  
 ## Debugger   
 * oly   
 * immunity   
 * ida   
 * kernel   
 * usermode   
 ## disassembler   
 * ida   
 * machine code to assembly   
 ## system monitoring tool   
 * procmon   
 * api monitor   
 * process hacker   
 ## misc tools   
 * execinfo   
 * gmer   
 * cuckoo sandbox   
 * volatility   
 * hook analyser   
 * hxd   
 * jd-gui   
 *  #### ghidra   
  
 	* reverse engineering tool   
 	* alternate of ida pro etc   
 	* open source   
 *  #### udtrace   
  
 	* tracing library for unix domain sockets   
 ## malware analysis   
 *  #### high level   
  
 	* use cuckoo   
 *  #### actually want to see how it works   
  
 	* debugger   
 # Sysinternal tools  
 ## process monitor   
 * process explorer + other monitoring tools together   
 *  #### features   
  
 	* using filter to filter events related only to interesting processes   
 		* usually available filters are same as available columns we can have   
 		* usefull   
 			* operation   
 			* event class   
 	* drop all filters and defaults filters too   
 	* using find to find string in all the columns   
 	* bookmark   
 		* we can highlight selected event   
 		* use ctrl+b, or event-->bookmark   
 		* In wireshark, shortcut is ctrl+m   
 	* stack   
 		* lower entry is one calling above function   
 	* all networking related events sometimes might not be associated with process   
 		* because process monitor register handles for packet sent and recieved in kernel, so timing too does not represent time at which packet was sent but represent time at packet sent was completed   
 ## process explorer   
 * task manager on steriod   
 * use to see opened handles(resouces)/dlls   
 ## regmon   
 * monitoring registry   
 # osint  
