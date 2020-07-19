---
title: Site Reliability Engineering by google
layout: post
---
      
 # Site Reliability Engineering
by google  
 ## service management   
 *  #### traditional approach   
  
 	* two teams   
 		* product developer   
 			* their goal to add new feature to product and user's getting used to it   
 				* they handle the situation of long reviews by sharding the product by having fewer features subject to launch reviews [anchor](xmind:#0qm81lnv61h7vvklcdfak071fq "anchor")  
 		* operations teams   
 			* sysadmins   
 				* their goal is to have system running and not let service break by decreasing number of changes   
 				* So to have system running without risk from changes, they adopts following strategy   
 					* launch and change gates   
 						* long list of every problem that has ever been caused during launch is explicitly checked is called launch review   
 *  #### google sre approach   
  
 	* Site Reliability Engineering teams focus on hiring software engineers to run products and create systems to accomplish the work that was otherwise performed, often manually, by sysadmins.   
 	* when software developer designs operation teams outcome is sre   
 	* 85-90% software engineer + 15-10%additional technical skills(unix internals and networking layer 1-3) useful for sre   
 	* sre circumvent the dsyfuntionality of dev/ops   
 ## statements   
 * Conflict can be avoided during offering of a software service.   
 ## challenges   
 * hiring sre because engineer should be from two discipline software engineering and system engineering   
 ## devops vs sre   
 * sre can be said as specific implementation of devops   
 ## sre vs ops   
 * sre is engineering deals with automating process to smartly handle situation of large load   
 * ops is manually handling situations. here if load/traffic on service increase, ops team has to increase to handle the increase in traffic/load   
 ## principles   
 *  #### ensuring durable focus on engineering   
  
 	* there is 50%cap for operational work for sre's   
 * Pursuing maximum change velocity without violating service's SLO   
 *  #### monitoring   
  
 	* alerts   
 	* tickets   
 	* logs   
 *  #### emergency response   
  
 	* mean time to failure   
 		* should me more   
 	* mean time to repair   
 		* should be less   
 *  #### change management   
  
 	* implementing progressive rollouts   
 	* quickly and accurately detecting problems   
 	* rolling back changes safely when problem arises   
 * demand forecasting and capacity planning   
 * provisioning   
 * efficiency and performance   
 # chapter 2  
 ## B4   
 * software defined networking architecture for globe-spanning network   
 ## jupiter   
 * google built switches in clos network fabric   
 ## hardware   
 *  #### computeBORG   
  
 	* distributed cluster operating system   
 		* job is collection of tasks   
 		* services have jobs   
 	* just like mesos   
 	* if compared with openstack   
 		* openstack is used to manage hardware by using hardware resources optimally   
 		* mesos or borg is used to manage services/server/software running over openstack so that they are always available. if service on one vm fails, it is started on another vm or is restarted   
 *  #### networking   
  
 	* sdn is used to manage the network   
 	* bandwidth enforcer   
 		* manages the available bandwidth   
 	* Global Software Load Balancer (GSLB)minimize latency for globally distributed services, we want to direct users to the closest datacenter with available capacity.   
 		* load balancing for dns requests   
 		* load balancing at user service level   
 		* load balancing at rpc   
 *  #### storage   
  
 	* D   
 		* local hdd or flash storage   
 		* colossus   
 			* layer on top of D and create cluster wide file system   
 		* services built on top of colossus   
 			* spanner   
 			* blobstore   
 			* bigtable   
 *  #### other   
  
 	* lock service   
 		* chubby   
 	* monitoring and alerting   
 		* borgmon   
 ## software   
 *  #### points   
  
 	* code is heavily multithreaded, task can use many cores   
 	* even call to subrouting in local program is made by rpc call, so that if subrouting is refactored to different server, code does not break   
 * stubby - closed source rpc infrastructuregrpc - open-source rpc framwork   
 * protocol buffer is way data is transfered. same as apache thirft   
 # undefined  
 ## terms   
 * risk   
 * reliability   
 * throughput   
 * cost   
 * tolerance   
 *  #### service level   
  
 	* different types of service   
 ## more reliable, less risk, more cost, less development velocity   
 ## different services have different requirements of reliability and risk   
 ## error budget   
 * amount of error we can perform after achieving the slo   
 *  #### slo | actual monitored metric | 100%   
  
 	* actual monitored metric changes as changes are introducted   
 # Sheet 4  
 ## different kinds of metrics available   
 * availabiity   
 * request latency   
 *  #### throughtput   
  
 	* interms of batch processings   
 *  #### durability   
  
 	* data will be retained for long period of time, usefull for storage system   
