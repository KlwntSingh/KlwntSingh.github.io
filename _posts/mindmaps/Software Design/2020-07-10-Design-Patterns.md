---
title: Design Patterns
layout: post
---
      
 # Design Patterns  
 ## Decorator pattern   
 * adding something over existing functionality without changing original functionality   
 * Create subclass of classes which you want to decorate, and add instance of these original classes as argument to constructor of subclasses(decorator) classes   
 ## Creational Design Patterns   
 *  #### class creation patterns   
  
 	* uses inheritance during instantiation   
 *  #### object creation patterns   
  
 	* uses delegation   
 *  #### factory pattern   
  
 	* layer of indirection which creates object of particular class/interface type to be used in application   
 	* when we need to change the object, we don't change code in factory method but create inherit factory method with new type of object we want to return and use that inherited method as factory method   
 *  #### Abstract Factory Design Pattern   
  
 	* product of families   
 	* Abstract factory which has method for each product   
 	* implementations for each family or platform is created as derived class for abstract factory   
 	* Eg:- all the required things(products) to be instantiated will be placed in abstract factory class.we will create multiple implementation for this abstract factory for each platform. Inside each implmentation we will return actual instance of product for that platform   
 *  #### Builder Design pattern   
  
 	* when builder which set's different value for different fields of classes is used to create object   
 	* we can create factory as layer over builder which returns object of built class for which builder was created.   
 ## Behaviour Design Pattern   
 * strategy pattern   
 *  #### state pattern   
  
 	* An object cannot change its class during its lifetime. There is a solution, however, the State pattern   
 	* there is not much difference of it with strategy pattern. strategy refers to implementation but state refers to state of object   
 ## Principles   
 * separating code which changes from code that does not change by encapsulating the code which changes hence not affecting the code which does not change   
 * program to an interface/supertype   
 # Paradigms  
 ## how   
 * one type of language talks about doing particular kind of thing   
 ## what   
 * one type of language talks about doing what to achieve   
 ## different paradigms   
 * imperative   
 * declarative   
 *  #### procedural   
  
 	* grouping together statements to form procedures   
 	* eg:- c, c++   
 *  #### functional   
  
 	* language with no privilege to change state   
 	* eg: haskell   
 *  #### object oriented   
  
 	* state and execution are wapped together   
 	* e: java   
 *  #### structural   
  
 	* focuses on what to do rather than how to do it   
 	* eg:- mysql   
 ## concurrency   
 * make program to be multi-threaded   
 ## parallel programming   
 ## multi-threading   
 ## multi-processing   
 ## typing   
 *  #### strong typing   
  
 	* once type defined, cannot be changed   
 *  #### weak typing   
  
 	* type can be changed   
 *  #### static typing   
  
 	* typing checked at compile time   
 *  #### dynamic typing   
  
 	* checked at run time   
 # similarity between patterns  
 ## factory pattern   
 ## abstract factory pattern   
 ## singleton   
 ## flyweight   
 ## template method   
 ## visitor   
 ## chain of responsibility   
 ## command   
 ## adapter   
 ## bridge   
 ## mediator   
 ## observer   
 ## iterator   
 ## prototype   
 ## composite   
 ## builder   
 ## decorator   
 ## facade   
 ## proxy   
 ## memento   
 ## state   
 ## strategy   
 ## making complex   
 *  #### classes   
  
 	* by combining classes   
 *  #### object   
  
 	* by combining objects   
 	* by setting values in object   
 	* by changing view of object   
 ## making compatible   
 * adding additional layer   
 * giving certain view   
 # thoughts  
 ## ways to add additional functionality in functions   
 * adding additional function in same class parallel to original function   
 * if original function is has separate class, than we can inherit that class and implement it with additional functionality   
 *  #### if we are using python, than we can improve original function itself by having args with default vaue   
  
 	* similar to way to in language where defaults args are not supproted is by inheritance.eg:- inherit the original class and function with additional args. kind of function overloading   
 ## inheritance   
 *  #### base class has set of functions, child class has set of function(variations) but now need to add new function which are only valid for child class   
  
 	* For now adding functions in child class, eg: autotestcode fct   
 ## about assert statements   
 * should all assert statments be at bottom of code and as code flow set variables which will be assserted later. But this thing fails when we don't want to continue code flow if one of variable is not as expected   
 # Drawings  
 ## DerivedClass2 extends BaseClass   
 ## DerivedClass1 extends BaseClass   
 ## Interface   
 ## Implementation1 implements interface   
 ## Implementation2 implements interface   
