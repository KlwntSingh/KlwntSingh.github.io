---
layout: post
title:  "ECMAScript 6 Series Part – 1"
date:   2017-06-29 19:46:47 -0300
categories: ECMAScript 6,es6, javascript
tags: ECMAScript 6,es6, javascript
---
*ECMAScript 6* also known as *ECMAScript 2015*  or es6  was released in 2015 and is considered major release after es5 in 2009. ECMAScript is not javascript but it standardizes javascript. *ECMAScript 7* is the latest version released in 2016 is not the major release as it only has two additional features over es6.

## What to expect?
New features of es6 will be discussed. Comparison of the syntax of es5 with es6 will be shown *syntactic sugar* provided by es6. This will be a two-part series.

First part will focus on following things

1. Keywords to declare and define variables with block scoping.
2. New syntax for defining a function - Arrow functions.
3. Concatenating strings without double or single quotes.
4. Defining object from variables and vice versa.

## Let's Start
### 1. Declaring variables -

Till now, we could declare a variable with *var* keyword or just write a name of a variable.

> *var a;*  
> *b*

The difference between two is that **var a** is function scoped while **b** is a global variable. 

Let's understand terms  
* Function Scoped  
  The scope of variables is limited to function in which they are defined.
  Block of curly brace `{}` do not limit scope of variable.

      function run(){
          var a = 1;

          if(a == 1){
              var b = 0;
          }
          console.log(a); // print 1
          console.log(b); // print 0
          // 
          //    Why value of b got printed ? 
          //    Reason - b is defined in block but variables with var are function scoped. 
          //
      }
      console.log(a); // throws error
      // Because a is printed outside function 


* Block Scoped  
  When the scope of a variable is defined by a block of curly brace `{}`.  
  If in above example, After console logging *b* error is thrown, then variable b could have been block scoped. 

  > *console.log(b);* // throws error

  Ecmascript-6 introduced keyword **let** which makes variable block scoped.

      function execute(){

          if(true){
              let b = 1;
          }
          console.log(b); //throws error
          // Because b is declared and defined in block.
      }

Another keyword is **const** which is block scoped for defining constants in an application. Once value assigned to *const* variable, its value cannot change. If we assign an object to *const* variable than new properties can be added or removed from object but the reference of object in variable cannot change.

> *const PI = 3.14732*; 

----
### 2. Arrow functions -

Arrow Function is just new syntax to declare and define functions which have some syntactic sugar over traditional method of defining a function.

    var multiply = function multiply(a, b){
        return a*b;
    }

what if above function can be defined in single line with arrow function.

    var multiply = (a, b) => a*b;

Looks nice, right? 

we can use multiple statements too in arrow functions.

    var multiply = (a, b) => {
        console.log("First number is:" + a);
        console.log("Second number is:" + b;
        return a*b;;
    }

Let's now look how *this* behaves in arrow function.
In Arrow function, *this* behaves differently than *this* in normal function. 
In Normal Function, *this* returns instance object if function is constructor, context object if called as method of object, *undefined* when in `'strict mode'`. But *this* in arrow function returns lexical scoped *this*.
Series of example to understand the difference of *this* in both syntaxes of function.

    function one(){
        console.log(this); // prints windows object
    }

    var two = () => this; // prints windows object

    function third(a){
        this.x = a;
    }
    third.prototype.giveThis = function(){
        console.log(this); // prints instance of two
    }
    third.prototype.giveLexThis = () => console.log(this) // prints windows object

    function fourth(){
        setTimeout(function(){
            console.log(this); // prints windows object
        }, 10)
    }

    function fifth(){
        setTimeout(() => {
            console.log(this); // prints lexically scoped this;
        }, 10)
    }

**Note** - when printing *this* in NodeJs, it will print *global* object rather than *window* object.

-----
### 3. String concatenation/interpolation -

let us understand how string concatenation is made easy in es6 using an example.

    var a = 5;
    var b = 3;

    console.log(" Sum of 'a' and 'b' is: " + (a+b));

    function getValue(a){
        return a;
    }

    console.log("The value from \"getValue('a')\" is:" + getValue('a'));

You can see that we used escape characters(*\\*) in string concatenation to achieve a simple requirement. Now same thing in es6 can be done easily as in below example.

    var a = 5;
    var b = 3;

    console.log(` Sum of 'a' and 'b' is: ${a+b}`);

    function getValue(a){
        return a;
    }

    console.log(`The value from "getValue('a')" is: ${getValue('a')}`);

We used backtick *`* and we can write double *"* and single *'* quotes any number of times we want. We can execute javascript statements while in *backtick* using as

> \`  ${ a }  \`

amazed ?. Not yet!  
Okay, then lets move to next helpful feature.

----
### 4. Defining Variables from Object -

Suppose we have object and we need to extract values from object to variables.
First, we will discuss **json** object and then about **array** object.

    var obj = {
        a : 1,
        b : 2,
        c : {
            d : 1
        }
    }

    //  Ecmascript 5 Syntax
    var a, b, nestedD;
    a = obj['a'];
    b = obj['b'];
    nestedD = obj['c']['d'];


    //  Ecmascript 6 Syntax
    var { a, b } = obj;
    console.log(a); // 1
    console.log(b); // 2

    // for nested object
    var { c: {d: nestedD } } = obj;
    console.log(nestedD); // 1

The last example looks complex, easy way to remember is -
> *var { FROM : TO } = obj*;

`FROM` - property in obj from where we want to get value.  
`TO` - variable which stores value of a property.

Now, defining variables from *array* object.

    var a, b, d;
    var arr = [1, 2, 3];

    [a, b] = [1,2,3];

    [,,d] = [1,2,3];

    console.log(a); // 1
    console.log(b); // 2
    console.log(d); // 3

----
### 5. Defining Object from Variables -

Variables can be used as property name and their assigned value as value in json object.

    var a = 4
        ,b = 3;
    

    var obj = {
        a, b
    } 

    console.log(obj); // prints { a: 4, b: 3}

    obj = {
        nest : {
            a
        },
        b
    }

    console.log(obj); // prints { nest: { a: 4}, b: 3 }

----
### 5. Three dot operator `...` -

` ...arr = COMMA_SEPARATED_VALUES `

Consider the above statement as formula.

1. `...` - predefined three dot operator
2. `arr` - This is array variable. 
3. `COMMA_SEPARATED_VALUES` - comma separated values.

Either of, `arr`, `COMMA_SEPARATED_VALUES`
will be defined and left out variable will be assigned value according to the above formula.

Certain example of using `...`

* Rest of Params

      // Rest of Parameter example
      function multiply(a, ...b){
          let result = a;
          b.forEach(val){
              result *= val;
          }
          return result;
      }

      multiply(1, 2, 3, 4, 5) // returns 120
        
  understanding above example using formula

  parameters `a, ...b` are provided with arguments `1, 2, 3, 4, 5` then `a = 1` and ` ...b = 2,3,4,5`.  Since b is array then it will contain value [2, 3, 4, 5].

* Spread Operator   
  Using the above formula in reverse helps to understand how spread operator works.

      let a1, b1, c1;
      var arr = [1, 2, 3, 4];
       [a1, b1, c1] = [...arr]

      console.log(a1); // 1
      console.log(b1); // 2
      console.log(c1); // 3

      function execute(a, b){
          return a*b;
      }

      execute(...arr); // returns 2


That's it for this part. We will continue the discussion on *Class*, *Generator functions*,  *Map*, *Set*, *Weak Map* and *Weak Set* etc in next part of series.



