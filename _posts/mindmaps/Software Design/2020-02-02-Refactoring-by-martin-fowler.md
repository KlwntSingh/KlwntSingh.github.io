---
title: Refactoring by martin fowler
layout: post
---
      
 # index  
 ## chapter 1 [anchor](xmind:#7l4c5ibfgc2t5jofque38qmeqv "anchor")  
 ## chapter 2Principles in Refactoring [anchor](xmind:#3c5k0aa4qakdr1fe71fqjt7ee2 "anchor")  
 ## other authors   
 * McConnel   
 *  #### kent beck   
  
 	* extreme programming   
 * Bill Opdyke   
 ## chapter 3Bad smells in code [anchor](xmind:#5n4jlg7tumocngrch9fdj415c2 "anchor")  
 * this chapter deals with different types of bad smell(code) and what refactoring to do to handle that bad smell   
 # chapter 1  
 ## tips   
 * when adding a new feature, if it is difficult to add feature than refactor the code until it is easy to add the feature   
 * should have  strong test cases before refactoring the code   
 * refactor the changes in small steps   
 ## steps   
 *  #### extracting logic from big methods into small methods"Extract Method"   
  
 	* care to be given to local variables which might be passed as argument to new method to be created   
 	* Of all the methods extracted it is very less common to use parameters as they can get values from class properties   
 	* Note- in book, loop body is extracted and not the entire loop and body is extracted into new method   
 	* Note- we can break logic inside one loop body to multiple loops with each loop having the one logic inside it's body. we should do it in refactoring phase. it might cause performance issue but we can say that until we profile the code to how long it takes to run loops and also to see the frequency the loops being called. We see about performance in optimization phase as at that point we will have more and better options   
 * rename variable names to meaningful   
 *  #### move methods to right class"Move Method"   
  
 	* In most cases a method should be on the object whose data it uses. thus method needs to moved to respective classes   
 	* Sometimes the old method is left to delegate to the new method. This is useful if it is a public method and hence no need to change the interface of the other class(old method class).   
 * Replace Temp variables with Query   
 *  #### Replacing the Conditional Logic with Polymorphism"Replace Conditional with Polymorphism"   
  
 	* Note- It is a bad idea to do a switch based on an attribute of another object. If you must use a switch statement, it should be on your own data, not on someone else's.   
 	* State pattern" Replace Type Code with State/Strategy" [anchor](file:Design%20Patterns.xmind "anchor")  
 ## statements   
 * Good code should communicate what it is doing clearly, and variable names are a key to clear code.   
 * Any fool can write code that a computer can understand. Good programmers writecode that humans can understand.   
 * Type information generallytends to be more volatile.   
 * when change of adding new types of anything happens, it should not have ripple effect to other classes   
 * rhythm of refactoring: test, small change, test,small change, test, small change.   
 ## Notes   
 * 1 [anchor](xmind:#5nr8okp5rt0f6tfslj96dt8buc "anchor")  
 * 2 [anchor](xmind:#29itskoe98krftsj71v74e1htp "anchor")  
 # chapter 2  
 ## definations   
 *  #### noun   
  
 	* refactoring   
 		* change made to make code easier to understand and cheaper to modify   
 		* It is step   
 *  #### verb   
  
 	* refactor   
 		* to restructure and use series of of refactorings   
 		* using multiple steps(refactoring)   
 *  #### contrast to refactoring is performance optimization   
  
 	* because we dont change the observable behaviour but we change internal structure of application to make it faster. we might make code harder to understand with changes related to performance optimization   
 *  #### purpose   
  
 	* easier to understand and modify   
 	* with no change in observable behaviour   
 ## two hats by kent beck   
 *  #### adding new feature   
  
 	* when adding new feature we dont change existing code   
 	* we add new test cases   
 *  #### refactoring   
  
 	* we don't add any new features/functions   
 	* we change existing code   
 	* we don't change test cases unless some important test cases were missing or inorder to cope with changes in interface   
 *  #### two kinds of values   
  
 	* what we can do today   
 	* what we can do tomorrow   
 	* four reasons that makes it hard to work with programs(time for refactoring)   
 		* hard to read means hard to modify tomorrow   
 		* duplicate code means hard to modify   
 		* if adding new feature means modifying the existing code are hard to modify   
 		* code with complex conditional logic is hard to modify   
 *  #### indirection   
  
 	* to enable sharing of logic   
 		* method invoked from different places   
 		* method in superclass used in subclasses   
 	* to explain intention and implementation   
 		* intention is expressed by using good class name, variable names and method names   
 		* internals of class explain how intention is realized, we can write internals in form of intention   
 	* isolate change   
 		* let say a object is used at two different places and i want to change implementation of object in one of case. I will create sub-class of object and use it the case where we need different behaviour   
 	* to encode conditional logic   
 		* conditions can be easily coded using polymorphism and other techniques   
 *  #### how to increawe value of program   
  
 	* by increasing quality   
 		* less bugs   
 	* by decreasing the cost   
 		* cost to add new features   
 	* we can increase quality/reduce cost by refactoring   
 		* by introducing indirection and adding qualities   
 		* by removing parasitic indirection by removing costly indirection   
 ## why refactoring?benefits of refactoring   
 *  #### to preserve the design of software   
  
 	* code added to realize short term goals or added without complete comprehension of design make software looses it's design.   
 	* harder it is to understand design, harder it is to reserve the design   
 	* we also try to remove duplicate code which makes code easy to modify without making errors   
 *  #### refactoring makes code easier to understand so that future developers can make changes without spending much time in understanding the code   
  
 	* we should put everything we remember about code into the code so don't have to remember the code   
 *  #### refactoring helps to find bugs very easily   
  
 	* kent beck said "I am not great programmer; I m just good programmer with great habbits"   
 *  #### refactoring helps you write program faster   
  
 	* good design means rapid development. if design of code starts degrading than speed of adding new feature slows down   
 *  #### when we need to fix the bug   
  
 	* we make code easily understandable to see the bug   
 *  #### refactoring as you do code reviews   
  
 	* code reviews with individuals   
 	* design reviews with groups   
 	* active code review with extreme programming by practice of pair programming   
 ## when should the refactoring done?   
 *  #### we don't have specific schedule for refactoring.   
  
 	* eg:- after month of development, 2 weeks for refactoring   
 * we refactor all the time in little bursts   
 *  #### rule of three   
  
 	* first we do something, we just do it   
 	* second time we try to do something similiar, we wince at it   
 	* third time we try to do something similiar we do refactoring   
 * we refactor when we add new functionality to make code easily understandable   
 * other driving force is when design does not let me add new feature   
 ## review is different from refactoring   
 ## problems with refactoring   
 *  #### why changing database is difficult task?   
  
 	* database schema might be tightly coupled with business application   
 	* if database schema changes than data migration is long and fraught task   
 *  #### changing interface   
  
 	* when changing the interface, it means caller will be changed. we can do that change in our code but problem comes when we have published interface, because we can change caller code in code to which don't have access, so have to make this transition follow a path having both interfaces and old interface calling new interface and depricating the old interface so that who are accessing the old interface they will know.   
 	* when throwing new exception from interface   
 		* when exception is checked, than compiler will not complile the progam if interface is changed by throwing new exception   
 		* when exception is unchecked, than there will be problem but than user's will not know that change is coming in inteface   
 			* but here we can let know the users that exception will become checked exception in future   
 		* exceptions   
 			* checked   
 				* untill the thrown exception is handled, program will not compile   
 			* unchecked   
 				* program can compile even if exception is not handled   
 			* runtime exceptions and errors are consired unchecked and all the others are checked exceptions   
 *  #### design changes that are difficult   
  
 	* to see if deisgn change is easy, than we can do refactoring. But if design change is difficult than we have to lot of effort into design   
 *  #### when cannot the refactoring be done   
  
 	* when code is messy that you can't stablilize it   
 		* code has to work mostly correctly before you refactor   
 	* one compromising path to refactoring is to refactor large system into components with storing encapsulation, so that you can refactor each component separately.   
 	* other time to avoid refactoring is when deadline is too close   
 ## Refactoring and Design   
 *  #### before refactoring   
  
 	* upfront design should be right   
 	* design should be flexible so that changes can be incorporated into it   
 		* flexibility has cost   
 			* code becomes more complex   
 			* code becomes difficult to maintain   
 *  #### after refactoring   
  
 	* design should be simple so we can refactor it to the new changes   
 		* now we ask question how difficult it will be change simple design to flexible design rather than implementing the flexible design   
 * refactoring is not alternative to upfront design   
 ## Refactoring and Performance   
 * Even if you know exactly what is going on in your system,measure performance, don't speculate.   
 * The secret to fast software, in all but hard real-time contexts, is to write tunable software first and then to tune it for sufficient speed.   
 *  #### approaches   
  
 	* time bugedting   
 	* constant attention approach   
 	* in this approach you only fine tune the part of program which effects the performance, and that you find the part of program by using profilers   
 *  #### how well factored program effects   
  
 	* it is easy to change well-factored code after the piece of code which is lacking in performance is found   
 	* will well factored code, profiling the code at fine granularity is very easy   
 ## tips   
 *  #### we should not publish interface prematurely. also ownership policy should change in company to soothe out refactoring   
  
 	* sometimes in same organization in team of 3 people, interface published by one person are being used by other two.   
 ## statements   
 * 1 [anchor](xmind:#0kgmb9jo7lp27t0sq9bbpokvkp "anchor")  
 * 2 [anchor](xmind:#6uar1pb7f6l7e8r499gu8tuhbe "anchor")  
 * 3 [anchor](xmind:#2j4coa6861c0d4j9ba40vslpjb "anchor")  
 # chapter 3  
 ## personal thoughts   
 * we should have good models to write good business logic impelmeentation   
 ## statements   
 * global data is evil and usually painful.   
 ## questions to ask in refactoring   
 * how it works   
 * when to use   
 * operating it   
 ## smell   
 * means bad code   
 ## duplicate code   
 *  #### same expression in two methods of same class   
  
 	* use 'extract method' and invoke the code from both places   
 *  #### expression in two sibling subclasses   
  
 	* same expression   
 		* 'extract method' in both the classes and 'pull up field'   
 	* if code is similiar but not same   
 		* use 'extract method' to separate similiar bits from different bits   
 			* use can then use form template method   
 	* if methods to same thing but with different algorithms   
 		* use 'substitute algorithm'   
 *  #### duplicate code in unrellated classes   
  
 	* 'extract class' and use it it another   
 ## long methods   
 * Older languages carried an overhead in subroutine calls, whichdeterred people from small methods. Modern OO languages have pretty much eliminated that overhead for in-process calls.   
 * whenever feel like commenting the method, create create new method with code which needs to be commented with good method name explaining the intention of method rather than how does it do   
 * 'extract method' is used to shorted the method   
 *  #### if there is problem while extracting method like large number of parameters and temporary variables which might needs to be passed   
  
 	* extract method [anchor](xmind:#2mu84eff2um54gm9hqln1b12tf "anchor")  
 	* replace temporary variable with query [anchor](xmind:#7g7gqv5t1mmrv87tje48knra6r "anchor")  
 	* preserve whole object [anchor](xmind:#53i8c3l8rlbuglm0srgfq1u415 "anchor")  
 	* Introduce Parameter Object [anchor](xmind:#0ock59ersg846gl0du1jv6f8m2 "anchor")  
 	* Replace Method with Method Object [anchor](xmind:#6n7eotrktcik752ot11n55pfen "anchor")  
 *  #### loops and conditions are also sign of extractions   
  
 	* Decompose Conditional [anchor](xmind:#28g617rflca68s799csjnovem3 "anchor")  
 ## large class   
 *  #### class with too many instance variables   
  
 	* variables inside class whose value is different for every instance   
 	* 'extract class'   
 	* 'extract subclass'   
 *  #### class with long methods   
  
 	* 'extract class'   
 	* 'extract subclass'   
 	* extract ineterface   
 *  #### sometimes in large class, we need to move some data and behaviour into different classes and have to keep duplicate data and keep sync of data   
  
 	* 'duplicate observed data'   
 ## long parameters   
 *  #### statements   
  
 	* statement1   
 	* A lot of what a method needs is available on the method's host class. In object-oriented programs parameter lists tend to be much smaller than in traditional programs.   
 *  #### 'Replace Parameter with Method'   
  
 	* try to get object by calling a method rather than getting that object as parameter   
 *  #### 'Preserve Whole Object'   
  
 	* rather than getting number of data from object, try getting whole object as parameter   
 *  #### 'Introduce Parameter Object.'   
  
 	* if you have lot of data without any logical object   
 * if you do want to create dependency from object to larger object than you have no other choice than to keep long parameter list   
 ## divergent change   
 *  #### sometimes to handle new case, we make changes in same class   
  
 	* so to handle any change, there should be variation only in single class and new class should express the variation. we should have different objects for different cases   
 	* 'extract class' to clean this up   
 	* eg: - to handle new database connection,  we make changes to class   
 ## shotgun surgeryoposite of divergent change   
 *  #### everytime you make a change, you have to make little little changes at number of places, which makes it easy to miss a change   
  
 	* we solve it by bring all the changes to single class   
 		* 'move method'   
 		* 'move field'   
 ## feature envy   
 * package data with processes that uses that data   
 *  #### if method uses data from different class. we call it envy   
  
 	* 'move method'   
 *  #### sometimes only part of method suffers from envy   
  
 	* 'extract method' on jealous bit and 'move method'   
 *  #### sometimes, method uses data from serveral classes   
  
 	* 'extract method'   
 *  #### patterns which breaks it   
  
 	* visitor   
 	* strategy pattern   
 ## data clumps   
 *  #### some data items always hangs out together called clamps   
  
 	* same fields in couple of classes   
 		* 'extract class' on fields to turn clamps into object   
 	* parameters in many method signatures   
 		* 'introduce parameter object'   
 		* 'preserve whole object'   
 * after removing data clumps consider doing feature envy beahviour to move to newly created class   
 ## primitive obsession   
 *  #### use small object which wraps primitives   
  
 	* 'Replace Data Value with Object'   
 	* 'Replace Type Code with Class'   
 	* 'Replace Type Code with Subclasses'   
 	* 'Replace Type Code with State/Strategy'   
 *  #### if you have number of fields, that you think should go together   
  
 	* 'Extract Class'   
 	* 'Introduce Parameter Object'   
 	* 'Replace Array with Object'   
 ## Switch statements   
 *  #### problem with switch is duplication. if switch logic is present in one place it will be present at different place too.   
  
 	* use polymorphism to solve the problem   
 		* 'Extract Method' and 'Move Method '   
 		* 'Replace Type Code with Subclasses' or ReplaceType Code with State/Strategy   
 		* 'Replace Conditional with Polymorphism'   
 ## parallel inheritance hierarchy   
 *  #### same as shotgun surgery but here change is when we create sublass of one class, we have to create subclass of another class   
  
 	* The general strategy for eliminating the duplication is to make sure that instances of one hierarchy refer to instances of the other. If you use Move Method and Move Field, the hierarchy on the referring class disappears   
 ## Lazy class   
 *  #### each class has cost and if class is not doing enough to pay for itself   
  
 	* for useless subclass we use, 'Collapse Hierarchy'   
 	* for useless component, 'Inline Class'   
 ## speculative generality   
 * we have the  hooks and special cases to handle things that aren't required   
 ## temporary field   
 *  #### when class have some instance variables which are not used all the time,   
  
 	* we do 'extract class' with these variables and methods that require them   
 ## message chains   
 *  #### when object calls another object and that object in turn calls another object. this long chain has problem that client is coupled with structure of navigation and if intermediate object changes, it causes the client to change   
  
 	* 'Hide Delegate'   
 	* 'extract method' to take out piece of code that uses the chain the push the code down the chain   
 ## middle man   
 *  #### prime feature of object is encapsulation. encapsulation often leads to delegation.   
  
 	* we see the implementation of interface is delegating to other class.   
 		* 'Remove Middle Man' to remove the implementation and directly call the other class   
 		* if methods in other class are not doing much, use 'inline method'   
 		* if there is additional behaviour to methods in other class, we can 'ReplaceDelegation with Inheritance' to turn middle class into subclasses   
 ## inappropriate intimacy   
 *  #### sometimes classes far too much time delving in each other private parts   
  
 	* 'move method' and 'move field' to separate pieces which reduce intimacy   
 	* 'Change Bidirectional Association to Unidirectional.'   
 	* ' Extract Class' to take out common things to new class   
 	* 'Hide Delegate' to let another class act as go-between   
 ## Divergent change is one class that suffers many kinds of changes, and shotgun surgery is onechange that alters many classes. Either way you want to arrange things so that, ideally, there is aone-to-one link between common changes and classes.   
 # Sheet 5  
 ## extract method   
 * ch 3 > long method [anchor](xmind:#2otbto0rh7fdh0ivoau43ut6ns "anchor")  
 ## Replace Temp with Query   
 * ch 3 > long method [anchor](xmind:#2otbto0rh7fdh0ivoau43ut6ns "anchor")  
 ## Preserve Whole Object   
 * ch 3 > long method [anchor](xmind:#2otbto0rh7fdh0ivoau43ut6ns "anchor")  
 ## Introduce ParameterObject   
 * ch 3 > long method [anchor](xmind:#2otbto0rh7fdh0ivoau43ut6ns "anchor")  
 ## Replace Method with Method Object   
 * ch 3 > long method [anchor](xmind:#2otbto0rh7fdh0ivoau43ut6ns "anchor")  
 ## Decompose Conditional   
 * ch3 > long method [anchor](xmind:#5qq1gttme8ds9r2ba9d9rj17rr "anchor")  
 ## extract class   
 * ch3> large class   
 ## extract subclass   
 * ch3> large class   
 # Sheet 6  
 ## component   
 * class   
 ## domain object   
 ## canarying   
 * while deployment, testing the feature on small subset of typical workload   
