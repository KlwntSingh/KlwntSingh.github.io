---
title: Design Patterns Head first book
layout: post
---
      
 # Flow  
 ## How?   
 *  #### Duck{	quack()	swim()	abstract display()	fly() }   
  
 	* MarlurdDuck{	overridden display()}   
 	* RedheadDuck{	overridden display()}   
 	* RubberDuck{	quack(){		//queak	}	fly(){		//don't fly 	}	overridden display()}   
 ## How?   
 * fly function in base class   
 * inheritance has greate use when talking about reuse   
 ## Problems solved   
 * can have as many duck species as we want without duplicate quack and swim code. each duck species can implements it's own display code   
 ## Problems   
 * Adding new behaviour to base class is inherited to all subclasses where this behaviour is inappropriate.every duck species inherited fly function, even rubber duck species which cannot fly   
 ## Game showing large number of duck species1. Duck Superclass with swim, quack and abstract display functions2. each of different species of duck will extend this base class and implement respective display method   
 ## How?   
 * Simple Extend   
 * Duck{quack()swim()abstract display() }   
 ## Solution - override fly function in duck to do nothing   
 ## Problems   
 * wooden duck don't fly and don't quack   
 * Whenever new species of duck as added, some of them will not fly and quack, hence overriding them everytime will be problem. this is not clean   
 ## Solution   
 * Interfaces   
 * Lets take out fly and quack method from base class and make Flyable, Quakable interfaces and implements interfaces in respective duck species   
 ## How?   
 *  #### Duck{	IFlyBehaviour flybehaviour	IQuackBehaviour quackbehaviour	performQuack()	performFly()	swim()	abstract display()	setFlyBehaviour()	setQuackBehaviour()}   
  
 	* WoodenDuck{	overridden display()}   
 	* RubberDuck{	overridden display()	quack(){		//queak	}}   
 	* MarlurdDuck{	overridden display()}   
 	* RedheadDuck{	overridden display()}   
 *  #### IFlyBehaviour{	fly()}   
  
 	* nofly   
 	* highfly   
 	* lowfly   
 *  #### IQuackBehaviour{	quack()}   
  
 	* squeak   
 	* quack   
 	* noquack   
 * DuckSimulator{	Duck d = new MarlurdDuck()	d.setFlyBehaviour(new highfly())	d.performFly()}   
 ## How?   
 *  #### Duck{	swim()	abstract display()}   
  
 	* WoodenDuck{	overridden display()}   
 	* RubberDuck{	overridden display()	quack(){		//queak	}}   
 	* MarlurdDuck{	overridden display()}   
 	* RedheadDuck{	overridden display()}   
 * IQuackable{	quack()}   
 * IFlyable{	fly()}   
 ## Problems   
 * Every duck species has to implements it's own fly and quack method, hence no code reusebility and duplicate code. Problematic when making change to fly method implementation to all of duck species implementing Iflyable. maintainence nightmare   
 * my doubt, Calling method will use Duck reference hence will never be able to call fly, quack on object   
 ## Problems solved   
 * inappropriate behaviour in duck species is removed   
 ## Solution   
 * Acc. to design principle, take out variable thing, and make a separate clas for it.eg:- we will take out quack and fly methods from duck class and create separate duck behaviour classes, set of quack classes, set of fly classes which can be used in duck class [anchor](xmind:#6gb4c4uecrvklks2ndj9eh38v4 "anchor")  
 * Another additional improvement is set these behaviours using getter setter making behaviour change in ducks dynamic [anchor](xmind:#42lo7tn8g22j82kqboi8ft181r "anchor")  
 * we will compose these behaviours in duck class   
 ## Requirement - add fly functions to duck   
 *  ####    
  
 	* Added fly functionality in base class   
 		*    
 			*    
 				*    
 					* Overridden fly on rubber duck   
 						*    
 							*    
 								*    
 									* New species of duck addedWooden duck   
 										*    
 											*    
 												*    
 													*    
 														*    
 															*    
 																*    
 																	*    
 																		* Interfaces IntroducedFlyable, Quackable   
 																			*    
 																				*    
 																					*    
 																						*    
 																							*    
 																								*    
 																									*    
 # Chapter1  
 ## Design Principals:rules which are followed in design pattern   
 *  #### encapsulate what varies   
  
 	* strategy pattern   
 	* encapsulating part which varies with every new requirement, let us change/extend it without effecting other parts   
 	* possible cases where this is applicable   
 		* if/else   
 		* same code with different implementations [anchor](xmind:#7tmrqrn0kea9ek0obu3pn39mv2 "anchor")  
 	* eg: [anchor](xmind:#7tmrqrn0kea9ek0obu3pn39mv2 "anchor")  
 *  #### code to supertype(interface or abstract class)   
  
 	* strategey pattern   
 	* code to interface rather than implementation   
 		* using new operator means coding to implementation   
 		* Using supertype to refer a object   
 		* favor interface over abstract class because once abstract class is inherited, no other class can be inherited, which is serious limitation   
 	* Program to interface and not implementation [anchor](xmind:#6k5hthb33d20lrounv8ugjfsvv "anchor")  
 	* factory pattern is power technique to do this   
 *  #### favor composition over inheritance [anchor](xmind:#64a3q5hbo7i48npaerajam6n0i "anchor")  
  
 	* strategey pattern   
 *  #### Strive for loosely coupled design between objects that interact   
  
 	* observer patten   
 		* way observer is notified from observable without observable knowing about observers   
 *  #### classes should be open for extension but closed for modification   
  
 	* another example is observer patter, subject or observable can be extended by adding new observers without changing any code in subject   
 	* two ways of doing it   
 		* inheritance   
 		* composition is way to do it.we can compose new objects to add new functionality rather than changing existing code   
 			* decorator pattern   
 *  #### depend upon abstraction. do not depend upon concrete class   
  
 	* factory method and abstract factory method makes your code indpendent of concrete class   
 	* helps in loosely coupled concrete classes from application   
 	* dependency inversion principle   
 		* factory method is one technique adhering to it   
 		* depend upon abstractions do not depend upon concrete classes   
 *  #### principle of least knowledge. talk only to close friends   
  
 	* facade pattern helps in implementing the pattern   
 		* facade makes client only to be friends with facade class and not dependent on other classes   
 *  #### Hollywood principle; don't call us, we will call you   
  
 	* factory method, strategy pattern, template pattern   
 	* high level components calls the methods of algorithm in subclasses and not vice versa   
 * Single Responsibility Principle: class should have only reason to change   
 ## inheritance   
 *  #### use   
  
 	* code reuse   
 *  #### baggage   
  
 	* if subclass don't want to use any method from superclass, than it is not possible   
 	* child class will not able to inherit any other class   
 *  #### alternative to inheritance are   
  
 	* composition   
 	* wrapping object or decorator pattern   
 *  #### It is compile time   
  
 	* extension at runtime is more powerful then at compile time using inheritance   
 *  #### two benefits   
  
 	* behaviour reuse   
 	* type control   
 ## composition   
 *  #### use   
  
 	* encapsulate family of algorithms in it's own classes, hence code reuse   
 	* runtime change of algorithm   
 * baggage   
 * it is runtime   
 ## patterns   
 *  #### Strategy   
  
 	*    
 *  #### Observer Pattern   
  
 	* defines loosely coupled design   
 *  #### Decorator pattern   
  
 	* adding additional responsibilities to object dynamically. it provides flexibility alternative to subclassing or extending functionality   
 	* decorating class has-a and is-a relationship with decorated class   
 *  #### factory method   
  
 	* subclass decides which object to create   
 * abstract factory   
 *  #### singleton   
  
 	* ensure class has only one instance and provide global point of access to it   
 *  #### command pattern   
  
 	* adds level of indirection   
 	* different types of object getting wrapped by class implementing same interface   
 *  #### adapter pattern   
  
 	* class implements the interface compatible with client and composes object which client needs to use but was incompatible   
 *  #### facade pattern   
  
 	* wrapping multiple objects together to call methods on object easier   
 	* violates Single responsiblility principle   
 *  #### template method pattern   
  
 	* high level classes calling low level classes   
 *  #### iterator pattern   
  
 	* provides way to access elements without client knowing the underlying aggregate structure used   
 ## personal notes   
 *  #### decision on making new subclass or object will be enough is based on following points   
  
 	* if different methods, than subclass   
 	* if different instance variables, than subclass   
 	* if different values of instance variables than objects   
 * abstract class is class which is just above implementation in class hierarchy   
 *  #### we need to think of classss and bojects close to rela world   
  
 	* eg: if there can only be one of anything present, we need make only one object of that thing in our application   
 *  #### questions to ask while designing   
  
 	* with every new NOUN(class name)?   
 		* tells you to design interface/class, which is independent of implementation. gives you a way to think in abstract   
 	* tries to break the problem as much as you can   
 ## problems patterns solve   
 * resusability   
 *  #### maintainability   
  
 	* because of change   
 * extensibility   
 ## different types of design patterns   
 *  #### used at runtime/compile   
  
 	* runtime   
 		* strategy pattern   
 		* decorator pattern   
 			* dynamic mix and match class saves a lot number of class   
 		* singleton pattern   
 		* factory method and abstract factory   
 	* compile   
 		* command pattern   
 		* decorator pattern   
 			* because developer does not have to write all the classes   
 *  #### code structuralwhich code flow   
  
 	* observer pattern   
 	* command pattern   
 # Strategy  
 ## eg: - duck example, different fly, quack behaviours   
 ## family of interchangeable algorithm, and pattern let algorithm vary, independently from client   
 # Observer  
 ## difference between observer pattern and strategy pattern   
 *  #### strategy pattern   
  
 	* one to one relation ship   
 *  #### observer pattern   
  
 	* one to many relation ship   
 ## there are two ways to implement observer pattern   
 *  #### pull   
  
 	* here observer pull state changes from observable after observer has been notified   
 		* here all the interesting state variables can be pulled by observer   
 *  #### push   
  
 	* here observable push state changes to observer   
 		* problem here is that in case any observer needs any additional state change, than all observers code needs to be changed hence not recommended   
 ## Java API   
 *  #### Java Util package for observer and observable   
  
 	* 1. Observable is class and not interface hence the subclass of observable class can not extend any other class in case it is required. Hence it pose certain kind of limitation.2. This package does not even have Observable interface to implement, this means we can't swap out java implementation of observable3. setChanged method in Observable class is protected meaning, we can't compose this class, we have to subclass to use this method   
 	* Incase it is required, we should implement our own observer pattern   
 *  #### Swings gui implements objserver pattern   
  
 	* eg:- action listerners for button   
 ## problem multiple objects are interested or dependent on state of object   
 ## eg:   
 * weather station with different display elements   
 # Decorator  
 ## problem is class explosion   
 ## eg:   
 * coffee shop with different beverages and number of condiments   
 ## Decorator pattern is basically using composition and inheritance at same time   
 *  #### inheritance   
  
 	* is used to have same type   
 	* this is compile time decoration   
 *  #### composition   
  
 	* is used to have behaviour of wrapped object   
 	* this is run-time decoration   
 ## one doubt   
 *  #### why decoratorCondimentClass have abstract description function   
  
 	* constructor of sublcass of CondimentClass should just set description instance variable in beverage class. hence no need to define description function.Reason for why this should be done, any new user defining decorator will not have to do to base class code to understand and write decorator pattern   
 		* problem with this is description set in base class is replaced by new description set using constructor   
 	* Reason why we have abstract function is, we now have more flexibility of how to add new decorator keyword to original name based on how it is changing the behaviour   
 ## initial design   
 *  #### having all the methods related to condiments in base abstract class   
  
 	* this had issue like   
 		* if condiments don't go with beverage   
 		* if multiple condiments required like double mocha   
 		* new condiments require new methods to be added but it should be like adding new class   
 		* price change will make us to alter code   
 ## Java API   
 * IO package implements decorator pattern   
 ## problem with decorator pattern   
 * if calling code is dependent on type of concrete class, than adding decorator will create problems because types has now been changed to decorator   
 * It creates number of small classes which makes it difficult for others to understand   
 * To create simple object, has to wrap base object with number of decorators   
 ## Alternate designs forcoffee shop with multiple beverages with condiments   
 *  #### Make as many subclasses of beverage class as many combinations of beverages with condiments are there   
  
 	* problems: 1. class explosion   
 *  #### Having condiments as boolean variable in base class beverage   
  
 	* problems:1. even subclass which does no go with particular condiment, has as property variable2. adding new condiment requires code change   
 *  #### Having list variable which presents condiments, hence condiments can be added dynamic and only those condiments can be added which are suitable with beverage   
  
 	* my solution   
 *  #### Decorator pattern: having condiment object wrapping beverage object, beverage object can be nested in as many objects we like   
  
 	* problems:1. condition on concrete beverage cannot be applied if it is wrapped with decorators2. chance of coding errors increases because number of different combinations to create any type of beverage increases, of course this is solved by factory and builder pattern   
 # Factory  
 ## letting subclass decide what object to create   
 * or instantiation is deferred to subclass   
 * subclasses only implement the factory method and create object   
 ## eg:   
 * different types of pizza according to different styles according to region   
 ## Abstract Factory pattern   
 * provide interface for creating families of related or dependent objects without specifying the concrete class   
 # Sheet 6  
 ## why not global variable   
 * becuae multipel instance can be created and assigned to global variable   
 * pollutes the global namespace   
 * global makes initilization of object to be eager   
 ## problem with singleton   
 *  #### when multiple threads are involved   
  
 	* sovled using 3 techniques   
 		* syncronizing getInstance method   
 			* problamatic when frequency of calling getinstance is high. performance intensive   
 		* initialization of class during static variable declaration   
 			* problematic if single object is resource intensive, make it eager   
 		* double checked locking   
 			* solves both the problem   
 			* syncronization is applied to only piece of code wihc creates new instance   
 * when multiple classloaders are involved   
 * in jvm version 1.2 and before, garbage collector used to destrory the object of singleton class because of reference to it was inside from class. it was bug   
 ## pattern helps creates object of class from inside class hence it is assured that no two instances will be created for this class   
 ## we cannot create subclass of private constructor in base class   
 ## eg: chocolate boiler   
 # Sheet 7  
 ## it adds level of indirection   
 ## command class wraps receiver and request together   
 ## different components in this pattern   
 * receiver   
 *  #### command object   
  
 	* command object is created for each operation possible receiver   
 	* single execute operation is created   
 ## multiple commands can be wrapped inside command object   
 # Sheet 8  
 ## components   
 *  #### client   
  
 	* understands target interface   
 *  #### adapter   
  
 	* implement target interface and wraps adaptee   
 *  #### adaptee   
  
 	* one who is getting adapted   
 ## similiar to facade pattern   
 ## adapter converts interface of class to interface client expects   
 ## two types of adapter pattern   
 *  #### class adapter   
  
 	* class adapter requires multiple inheritance hence cannot be used in java   
 	* here we inherit from both target interface and adaptee   
 *  #### object adapter   
  
 	* we use this in java   
 	* here we inherit from target interface while compose adaptee   
 ## eg:   
 *  #### adapting enumeration to iterator   
  
 	* client   
 		* iterator   
 	* adaptee   
 		* enumeration   
 ## adapter vs decoratoer   
 *  #### decorator   
  
 	* adds new functionality wihtout altering the interface   
 *  #### adaptor   
  
 	* coverts one interface to another interface   
 ## Facade pattern   
 * converts complex interface to easy interface   
 * it also decouples client from subsystems   
 *  #### components   
  
 	* client   
 	* subsystems   
 	* facade   
 * just add different classes as components to current class   
 # Sheet 9  
 ## steps of algorithm is represent by method in base class and some steps of algorithm are implemented by subclasses   
 # Sheet 10  
 ## Single Responsibility Principle   
 * should have only one reason to change   
 ## Open Closed Principle   
 * open for extension but closed for modification   
 ## Liskov Substitution Principle   
 *  #### child classes should be substitutable for parent class   
  
 	* Eg: - father Don and son is Cook   
 ## Interface Segregation Principle   
 * If class is implmenting some methods from which should not be in class, than divide the interface the into two   
 ## Dependency Inversion Principle   
 * higher level modules should not be dependent on lower level modules   
 # Quotes  
 ## Instead of code reuse, with patterns we get experience reuse   
 ## Design patterns help code change easy to do. Only constant thing in software development is change.   
 ## all patterns provide a way to let part of system change independently of other parts of program   
 ## reuse above maintainability and extensibility   
 ## Principles are rules while patterns are their concrete examples.   
 # Why Software Change?  
 ## change in requirement   
 ## change in libraries we are using   
 ## code refactoring   
 ## adding new functionality   
 ## changing third party dependencies   
 ## change in dependencies   
 # Questions  
 ## what design principles in decorating pattern example of having classes for all combinations of condiments with beverage are violating?   
 * favoring composition over inheritance   
 * Encapsulate what varies   
 * open for extension, closed for modification   
 ## how to decide wether to pass instance variable or create instance inside class?   
