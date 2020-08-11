---
title: Building Microservices by Sam Newman
layout: post
---
    
# Chapter 1

## different architectures 
* traditional tiered 
* service oriented 
* distributed system 
* microservices 

## Characterstics 
* small 
* #### Autonomous 
	* achieving decoupling 
		* have less exposure of data models to other services. if there is too much sharing, services beocmes coupled 
		* having technology agnostic api's 

## Benefits 
* #### technology heterogenity 
	* Using best technology which suites the service. differen technologies can be used for different service 
		* eg: For high performing services, we can decide technology which delivers high performance 
	* adopting new technology is easy as we don't have write whole system in new technology just the service we want to implement 
* Resilience 
* Scaling 
* Ease of Deployment 
* Organizational Alignment 
* Composability 
* Optimizing for replaceability 

## Comparing with others 
* #### SOA 
	* microservice is just better real experience understanding of SOA, with microservices we try to avoid problems of SOA 
* #### Decompositional techniques 
	* shared libraries 
	* modules 

## Problems 
* #### there are challenges when we have more moving parts(services) 
	* newer technologies themselves provide ease with deployment 
* mostly problems are same as of distributed system 

---
# Chapter 2

## wrong comparison with other professions 
* people from professions are held accountable for mistake they do 
* It is difficult for other professions to change things like architect building a bridge, but in software engineering responding to change is very important 

## Zoning 
* architects are like town planner, we focus less on individual building(service) and more on communication between services 

## making decision is about trade-offs, architect just need to make right trade-offs which does not negatively affect in long run 

## principled approach 
* architects should have set of principles and practices which will guide us in project 
* principles are rules and practices ensure our principles are carried out 

## strategic goals 
* make sure technology is aligned with where you organization is headed 

## required standard 
* picture how good service should look like 

## monitoring 
* To make this as easy as possible, I would suggest ensuring that all services emit health and general monitoring-related metrics in the same way. 

## Interfaces 
* Picking a small number of defined interface technologies helps integrate new consumers. 
* If you pick HTTP/REST, for example, will you use verbs or nouns? How will you handle pagination of resources? How will you handle versioning of end points? 

## Architectural Safety 
* We have to ensure that our services shield themselves accordingly from unhealthy, downstream calls. 
* This means you will probably want to mandate as a minimum that each downstream service gets its own connection pool, and you may even go as far as to say that each also uses a circuit breaker. 

## Governance Through code 
* I have seen work well here are using exemplars and providing service templates. 
* #### Exemplars 
	* Ideally, these should be real-world services you have that get things right, rather than isolated services that are just implemented to be perfect examples. 
* #### Tailored Service template 
	* if you embraced multiple disparate technology stacks, you’d need a matching service template for each. This may be a way you subtly constrain language choices in your teams, though. 

## Technical Debt 
* Often, we need to make a choice to cut a few corners to get some urgent features out. This is just one more trade-off that we’ll find ourselves having to make. 
* #### eg: 
	* Sometimes technical debt isn’t just something we cause by taking shortcuts. What happens if our vision for the system changes, but not all of our system matches? In this situation, too, we have created new sources of technical debt. 

## Exception Handling 
* exception of principles and practice 
* If you are working in an organization that places lots of restrictions on how developers can do their work, then microservices may not be for you. 

## Governance and Leading from the Center 
* team of leaders from other teams for proper sharing of principles, pratices and tracking technical debt and risk 

---
# Chapter 3

## Good Service should have high cohesion and loose coupling 
* #### high cohesion 
	* We want related behavior to sit together, and unrelated behavior to sit elsewhere. 
	* problem with low cohesion 
		* If we have to change that behavior in lots of different places, we’ll have to release lots of different services (perhaps at the same time) to deliver that change. Making changes in lots of different places is slower, and deploying lots of services at once is risky — both of which we want to avoid. 
* #### loose coupling 
	* change in one service does not requite in other service 
	* eg: A classic mistake is to pick an integration style that tightly binds one service to another. 
	* how to 
		* A loosely coupled service knows as little as it needs to about the services with which it collaborates. This also means we probably want to limit the number of different types of calls from one service to another, because beyond the potential performance problem, chatty communication can lead to tight coupling. 

## Bounded Context 
* The idea is that any given domain consists of multiple bounded contexts, and residing within each are things (Eric uses the word model a lot, which is probably better than things) that do not need to be communicated outside as well as things that are shared externally with other bounded contexts. Each bounded context has an explicit interface, where it decides what models to share with other contexts. 
* eg: At MusicCorp, our warehouse is a hive of activity — managing orders being shipped out (and the odd return), taking delivery of new stock, having forklift truck races, and so on. Elsewhere, the finance department is perhaps less fun-loving, but still has a very important function inside our organization. These employees manage payroll, keep the company accounts, and produce important reports. Lots of reports. They probably also have interesting desk toys. 
* #### Shared and Hidden Models 
	* So there is the internal-only representation, and the external representation we expose. 
* #### Modules and Services 
	* When you’re starting out on a new codebase, this is probably a good place to begin. So once you have found your bounded contexts in your domain, make sure they are modeled within your codebase as modules, with shared and hidden models. These modular boundaries then become excellent candidates for microservices. 
	* Steps to Microservice 
		* monolithic ---> diving code into modules --->  spinning module as separate servicemonolithic(may be highly coupled, less cohesive) ---> bounded context ----> modular boundaries -----> service boundaries(microservices) 
* #### Premature Decomposition 
	* Prematurely decomposing a system into microservices can be costly, especially if you are new to the domain. In many ways, having an existing codebase you want to decompose into microservices is much easier than trying to go to microservices from the beginning. 

## Business Capabilities 
* When you start to think about the bounded contexts that exist in your organization, you should be thinking not in terms of data that is shared, but about the capabilities those contexts provide the rest of the domain. 
* So ask first “What does this context do?”, and then “So what data does it need to do that?” 

## Same Pattern all the way down 
* you will probably identify a number of coarse-grained bounded contexts. But these bounded contexts can in turn contain further bounded contexts. 
* For example, you could decompose the warehouse into capabilities associated with order fulfillment, inventory management, or goods receiving. 
* #### Two approaches 
	* Nested approach 
	* Full Separation approach 
		* taking out nested bound context and deploying it as independent service 
* #### How to make decision 
	* Another reason to prefer the nested approach could be to chunk up your architecture to simplify testing. 
	* Can be based on your organizational structure. 

## Communication in terms of business Concept 
* communication between these microservices in terms of the same business concepts. 
* changes we implement to our system are often about changes the business wants to make to how the system behaves. 

## Technical Boundary 
* #### when services are modeled incorrectly 
	* Changes frequently had to be made to both services. Both services spoke in terms of lowlevel, RPC-style method calls, which were overly brittle. The service interface was also very chatty too, resulting in performance issues. This resulted in the need for elaborate RPC-batching mechanisms. 
* #### eg: 
	* Front end as one microservice and backend as another microservice 
		* Here, however, rather than taking a vertical, business-focused slice through the stack, the team picked what was previously an in-process API and made a horizontal slice. 

---
# Chapter 4

---
