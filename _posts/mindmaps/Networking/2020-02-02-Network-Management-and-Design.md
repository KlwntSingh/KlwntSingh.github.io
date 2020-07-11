
# Management  

## OpenFlow   

* Application   

* API   

* Controller   

### openflow   

* protocol works on tcp and uses 6653 port   

### datapath(switch)   

#### components   

##### tables   

###### flow table   

* process packets   
it is set of fields   
match   

* condition under which packet is matched   
priority   

* used to set precedence of flow entry   
counter   

* no. of matching packets for entry   
instruction   

* action to be performed   
timeout   

* amount of time before entry is expired   
hard timeout   

* absolute time for flow entry to be deleted   
idle timeout   

* if no matching packet comes in idle timeout than flow entry is deleted   
cookie   

* used by controller to filter flow entries   
flag   

* used to alter the way flows are managed   

* uniquely identified by matching fields and priority   

###### metre table   

* implement QoS operations   

###### group tables   

* provide additional methods for forwarding   

##### intructions and actions   

* action list   

* action set   

* action buckets   

#### when connection with controller fails   

##### fail secure mode   

* switch continues to operate but does not send messages/packets to controller and flow entries are removed with as usual timeout   

##### fail standalone mode   

* This switch reverts to operating as standlone switch. This mode is usually only used by hybrid switches.   

##### when connection is restablished, than controller can   

* either keep the existing flow table entries   

* delete the entries and send new entries   

#### connection establishment   

* connection is initiated by switch to controller   

##### after tcp 3 way handshake intiated by switch   

* 1. each entity send ofpt_Hello message with protocol version set to highest openflow protocol version   

###### 2. feature request/reply   

* feature request sent by controller   

* reply is sent by switch with datapath id and list of features   

###### 3. set_config   

* if controller wants to change the configuration on switch, it send ofpt_set_config message   
It includes   

* 1. configuration flags   

* 2. max bytes of packet that datapath should send to controller in packet-in messagesdefault 128 bytes   

###### multipart request   

* OFPT_MULTIPART_REQUEST   

* they are used when to encode request/replies greater than 64KB   

* they are used to get statistics or state from switch   
multipart reply   

* ofpmpf_reply_more=0, when no more multipart replies are there   

###### flow mod   
table flow entries can be installed   

* proactively   
reactively   

* in response to packet_in message from switch   

* switch does not ack flow modification message unless there is error in request   
messages   

* add   

* modify   

* delete   

* overlapping entries   

* strict matching   

* non-strict matching   

* cookies   

###### packet_in   

* when switch cannot find flow table entry to matching packet header it sends packet_in request to controller either with whole packet or only with packet header   

* 3. echo request/reply   

#### table miss   

* when matching flow entry is not present in switch for packet than, it can either be dropped to sent to controller based on table miss entry by controller   

### message types   

#### controller to switch   

* to add/delete/moidy flow entries   

* to get statistics of switch   

#### asychronous messagesswitch to controller   

* to tell controller to packet header whose match is not found in table   

* notify controller for any change in flow state/port state   

#### symetric messagesby both switch/controller to each other   

* hello messages exchanged on connection start-up   

* echo request/ echo replies as keepalives   

## fcaps   

### fault   

#### active/passive monitoring   

* monitoring against functional errors and malicious attacks   

#### fault alerts   

* when monitoring, alerts can be generated in case of any issue with app   

#### recover   

* recovering incase service failed from functional errors or security reason   

### configuration   

* version control   

* baseline   

#### topology discovery   

* using topology discovery tool and inventory tools   

#### configuration audit   

* checking the configurations of devices regulary incase any thing weak interms of security is present   

* usefull when dependent on third party for configuration   

#### equipment hardening   

* disabling unprotected protocols   

* restricting physical and logical access to aouthorized personnel   

##### some things which we when hardening   

* remove default accounts   

* close unused network ports   

* enforce password complexity   

* remove unneeded services   

* patch known vulnerabilities   

* configure and manage user priviledge   

### accounting   

* metrics, monitoring resource usage   

### performance   

#### utilization monitoring   

* checking utilizaiton of certain resources and events   

#### event correlation   

* many tools try to correlate events to detect incidents   

#### traffic analysis   

* awareness of type of data flowing in and out of network can be gained by using protocols such as Netflow   

### security   

* centralized authentication   

* multi access privilege   

* access logging   

## design steps   

### 1. understanding business goals   

#### 1. understanding business goals   

* eg:- advantages this project will bring to project   

#### 2. business constraint   

* 1. budget   

* 2. time limit - project scheduling   

* 3. staffing constraints   

* 4. politics and policies   

#### 3. understand the project   

* 1. problem to be solved   

* 2. capabilities to be added   

* 3. what is considered as success   

* 4. what are consequences if project fails   

#### 4. understand customer biases   

* 1. do customers want to avoid certain technologies/products   

### 2. understanding technical goals   

#### scalability   

* like user numbers, location and expected growth   

#### availability   

* 1. disaster recovery   

* 2. specifying availability requirements   

* 3. five nines availability   

* 4. cost of downtime   

#### network performance   

* interactivity: measure of response time of system when interacting with a human   

* delay and delay variation   

#### application requirements   

* 1. applications that use the network now   

* 2. applications to be used after project is complete   

##### 3. different application types   

###### mission critical   

* guaranteed reliability requirements   

* 1. should be always available / important2. should return deterministic and correct information   

###### delay sensitive   

* delay matters   
classified into real-time, interactive   
real-time   

* data might be worthless after some time boundary   

* eg:- telemetry   
interactive   
burst   

* eg:- telnet   
bulk   

* eg:- ftp   

###### rate critical   
bandwidth/capacity matter   
bandwidth   

* theoretical capacity of component in network   
throughput   

* realizable capacity of network or component   
specified by   

* 1. thresholds   

* 2. bounds   

* 3. minimum, peak and sustained capacity   

#### host/device requirements   

##### type of hosts and equipment   

###### generic computing devices   

* single user   

###### servers   

* provide service to one or more users   

* more powerful   

###### specialized equipment   

* gather, produce or process info   

* do not support direct access to appl.   

##### performance characterstics   

* overall performance   

* impact on information flow   

* location dependence   

##### location info   

* provides info on concentration of users   

* reveals location dependencies   

#### network requirements   

##### performance   

###### reliability   
defined interms of   

* availability   
recoverability   

* MTTF(mean time to failure)   

* MTTR(mean time to recover)   
error and loss rates   

* ber - bit error rateper - packet error rate   

###### capacity   

* PDR - peak data rate   

* minimum data rate   

* SDR - sustained data rate   
burstiness - peak rate/average rate   

* tells how often do app send bursty traffic   

###### delay   

* time it takes for data to travel from source to destination   
causes   
propagation   

* cannot be eliminated   

* transmission   

* queuing   

* processing   

##### scalability   

* ability to refer to future requirements   

###### interms of   

* new sites   

* new users   

* new services   

* availability   

##### manageability   

* refers to ability required to manage(operate) and monitor network   

###### management is of   

* performance metrics   

* accountabilty   

* configuration   

* security problems   

* faults   

##### interoperability   

* proprietary technologies reduce adaptability   

* network must be adaptable for changes   

* network should be vendor neutral   

##### security   

* policies   

###### risk assesment   

* it is done to compromise security for accessiblity   

###### risks   

* loss of customer data   

* loss of propriety info   

* service disruption   

##### affordability   

###### recurring cost   

* power   

* floor   

* network operations, administration and maintainence   

* service contracts   

* training   

###### non-recurring cost   

* design   

* deployment   

* hardware/software components   

* installation/establishment of services from service providers   

* affordablity can be interms of time also   

* 3. understanding current internetwork   

* 4. understanding network flow   

### 5. designing logical network   

* 1. designing network topolgy   

* 2. designing adressing and numbering   

* 3. selecting switching and routing protocols   

* 4. developing network security strategies   

* 5. developing network management strategies   

### 6. physical network design   

* 1. selecting technology and devices for campus network   

### 7. testing, optimizing and document network deisgn   

#### 1. testing network design   

##### testing tools   

* 1. network management and monitoring tools   

* 2. traffic generation tools   

* 3. modeling and simulation tools   

* 4. QoS and service level management tools   

* 2. optimizing network design   

* 3. documenting network design   

### top down network design methodology   

* 1. structured network design process   

* 2. System development life cycle   

* 3. plan design implement operate optimize(PDIOO) network life cycle   

* requirement gathering   

* Understanding current state of network   

* designing, implementing and operating   

# Design  

## Backbone Networks   

### design considerations   

#### Node Placement   

* choosing nodes at centre of major traffic volumes   

* Performance and reliability reflected in selection and design of network nodes and links   

#### Connectivity   

##### Centralized Networks   

* concentrator combining low speed lines into higher speed lines   

* Distributed Networks   

### add algo   

* greedy algo   

* It is made for the ability of network to communicate with external networks (like Internet). It is a root of the network tree.   

## Cisco Hierariechal Design   

### Layers   

#### Access Layer   

* Layer 2 switch as more switchports are required to connect end users hence layer 3 will be very costly   

* Security is provided based on VLANS   

* Multiple uplinks required   

* function: used to connect to server   

#### Distribution Layer   

* Layer 3 switch   

* Multiple uplinks required   

* function: used for communication between servers   

#### Core Layer   

* No packet manipulation here   

* High throughput and availibility required   

* function: used to take traffic out from datacentre   

### Redundancy   

* we deploy redundant switch for every switch in distribution layer and core layer   

* Pair of switch, switch and redundant switch at distribution layer is called switch block   

#### SwitchBlock   

##### There are different designs for switch block   

* using same vlan for access layer switches   

* using different vlan for access layer switches   

* using layer 3 at access and distribution   

### variations   

#### 2 tier   

* collapsed   

* redundant   

## ISP Network   

### funtions   

* 1. provide internet related services to residential customer and businesses   

* 2. provide high-speed connectivity between backbone networks   

### components   

#### PoP   

##### Point of presence   

###### Provides following services   
residential user connections   

* xDSL, cable, wireless   
business customer connections   

* xDSL, Fibre   
ISP services   

* DNS, NTP, DHCP, LDAP, Web-Cache   
NOC   

* Network Operation Centre   
Network Management Software to monitor   

* Netflow, Radius, Syslog   

* Billing and Accounting   
Upstream ISP connections   
transit   

* taking services from another ISP to pass the traffic   

* required to reach part of internet which otherwise cannot be reachd   

* Transit ISP charges for transit services   
peer   

* another ISP with which local ISP has agreed to exchange locally sourced routes and traffic   

* can have as many peer as needed   
private interconnection   

* two ISP connect their network with private link   
Internet Exchange   

* physical infrastructure where ISP can connect to each other   

* here every ISP has choice to connect to any other ISP without any additional cost of link   
Backbone link   

* routed or switched backbone   

* point to point circuits   

* MPLS   

* provide services using access network   

#### Backbone   

* connects PoP   

#### Access   

* is used to reach end-user   

### Security Threats   

#### DDos   

* DDos protection by ISP is provided at edge i.e transit and peer points   

##### techniques by ISP   

###### blackholing   

* throwing away all the traffic for some subnet   

* it throws away legitimate traffic too   

* ISP sometimes ask upstream ISP to filter the traffic   

###### selective blackholing   

* blackingholing selectively based on some source or other criteria   

###### scrubbing   

* asking third party to filter away bad traffic   

* traffic engineering   

* local filtering   

* Excessive traffic   

#### BGP hijacking   

* router hardening   

* BGP authentication   

* DNS redirect   

* Infrastructure compromise   

## Data Centre   

### models   

#### multi-tier model   

##### three tier   

* web servers   

* application services   

* database servers   

* built resilience and security   

* support many web service architectures   

#### Server cluster model   

##### types   

* type 1: Parallel message passing   

* type 2: Distributed I/O processing   

* type 3: Parallel file processing   

##### components   

* front end   

* master node   

* compute node   

* high speed fabric   

* storage path   

* common file system   

##### Design features   

* ECMP   

* L3 plus L4 hashing algorithm   

* scalable server density   

* scalable fabric bandwidth   

* combining multiple cpu's to appear as unified high performance system using special software and high speed network interconnects   

#### Colocation model   

* provide space,power, cooling and physical security for rent to other organizations and connect them via wan to internet   

* each pod or rack is dedicated to different customer organization   

### Network Design   

#### traditional cisco 3-tier architecture   

* this architecture is well suited for data centers with north-south(in and out of datacenter) communication   

##### recent trends in data center for requirements of cloud computing, virtualization and big data apps. Now east-west(server to server withing datacenter) communication has increased with these requirments.   

###### multi-level hierarchical architecture with effiecient interconnecting architecture   
2nd layer switch   

* ToR are connected using 2nd layer switches   
1st layer switch or ToR(Top of rack)   

* servers are connected to ToR   

* servers   
interconnection solutions   
Clos Network   

* circuit switching network   
three stages   

* ingress switch   

* middle switch   

* egress switch   
variables   

* n - number of sources feed into each ingress switch   

* m - number of outputs for ingress switch or no. of middle switches   

* r - number of ingress and egress switches   
leaf spine   

* packet switched without oversubscription   

* every leaf switch is connected to each spine switch   
3 stage clos fabric   

* leaf switch only connected to some spine switches   
fat tree topology   

* special case of clos topology   
three layer tree   
aggregation switches   

* total - (k/2)^2   
L2 switches   

* inside pod   
each pod has k/2   

* because each ToR switch is connected to k/2 L2switch   
ToR switchTop of rack   

* inside pod   
each pod has k/2   

* because each L2 switch is connected to k/2 ToR switch   
servers   
each pod has (k/2)^2 servers   

* because each ToR switch is connected to k/2 servers and we have k/2 ToR switches inside pod   

* others   

##### advantages   

* scalability   

* ease of implementation   

* ease of trouble shooting   

###### predictabilty   

* behaviour of network is predictable which makes capacity planning easier   

* protocol support   

* manageability   

##### disadvantage   

###### restrictive   

* strict boundaries on areas are imposed   

* not ideal for east-west traffic   

### terms   

#### oversubscription   

* it increases as traffic moves up the layers   

##### eg: 4:1 - 48 racks in bottom(leaf), 12 racks in spine   

* means 1 spine is handling 4 times more leaf   

* completing non-blocking network is when oversubscription is 1:1   

#### 1:1 redundancy   

* under utilization   

#### ECMP(equal cost multi path)   

* having redudant links of equal capacity   

* traditional topologies only have two redundant paths at most   

## flow analysis   

* to find the capacity of devices to be used in physical topology. It is good to find individual flows in network and find composite flows   

### steps   

* 1. we have physical topology   

* 2. we find flows by having various application network which will be used and direction of traffic   

#### 3. than we find composite flows and flow boundaries   

* flow boundaries means distinguishing different networks   

### flow   

* set of application, protocol and control information that has some common attributes i.e source address, destination address, information type, directionality etc   

### models   

* peer to peer   

* client server model   

* distributed computing model   

### process   

* 1. determine general requirements   

* 2. identify sink and source   

* 3. determine individual flows   

* 4. establish flow boundaries   

* 5. find composite flows   

## lan design   

### approaches   

* manual   

#### optimization   

* when represented as objective function   

#### heuristic   

* approach to solve a problem which might not be optimal   

* simulation   

### Layers   

#### layer 1   

##### cabling system   

###### elements of cabling system   

* entrance facility   

* cross connects   

* vertical cabling   
equipment room   

* it house main cross connect/intermediate cross connect   

* telecommunication room   

* horizontal cabling   

* work area   

* outlets   

###### horizontal cabling   
cabling distances   

* 90 metres   
additional jumpers and patch cords should not exceed 6 m   

* this cable is in telecommunication room from switch to patch panel   

* additional 3m for cable from outlet to workstation   
topologies   

* star topology   

* extended star topology   
media   

* working area has two outlets   

###### backbone cabling   

* communication with telecommunication closet   

* should be hierarichal star   
cabling distance   

* telecommunication room to intermediate connect/main be less than 30m   

* In main cross connect, lenght of patch cord should be less than 20m   
topology   

* start   

* bus   

* ring   

#### layer 2   

* three tier model   

## requirment analysis   

### categories   

* Users   

* Application   

* Hosts   

* Networks   

### how to categorize requirements   

#### users   

* if requirement is from user and can be technical/non-technical   

* eg:- time limit, vendor preference   

#### application   

* anything which does not change network but add something additional to network   

#### host   

* talks about devices, servers,placement of server   

#### network   

* talks about changing network cables, routing protocols, area coverage   

### provides with RFP   

* customer gives supplier list of requirements   

* designer reviews the requirements and comes with proposal   

* customer approves the proposal before implementation of proposal   

#### sections   

##### section 1 and 2   

* they provide information about existing network, they provide lot of detail on exisiting equipment being used   

##### section 3   

* this lists the requirements of what they want their network to be   
