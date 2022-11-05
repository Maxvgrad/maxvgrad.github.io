---
title:  "Eloquent JavaScript"
date:   2022-08-01 21:18:58 +0200
categories: book-notes
img_src: https://eloquentjavascript.net/img/cover.jpg
---


Book notes [Eloquent JavaScript](https://eloquentjavascript.net)

## Intoduction
Most programming is done with programming languages. A programming language is an artificially constructed language used to instruct computers. It is interesting that the most effective way we’ve found to communicate with a computer borrows so heavily from the way we communicate with each other.
ECMAScript and JavaScript can be used interchangeably.



## Chapter 1: values, types, operators
JavaScript strings are encoded as a sequence of 16-bit numbers.
UTF-16, the format used by JavaScript strings, was invented. It describes most common characters using a single 16-bit code unit but uses a pair of two such units for others.
charCodeAt method gives you a code unit, not a full character code. The codePointAt method, added later, does give a full Unicode character. When you use for/of to loop over a string, it gives you real characters, not code units.


￼
Chapter 2: values, types, operators
To catch and hold values, JavaScript provides a thing called a binding, or variable.
The collection of bindings and their values that exist at a given time is called the environment.

Chapter 3: functions
A return keyword without an expression after it will cause the function to return undefined.
Bindings declared with let and const are in fact local to the block that they are declared in.
Old-style bindings, created with the var keyword, are visible throughout the whole function that they appear in—or throughout the global scope.
Each local scope can also see all the local scopes that contain it, and all scopes can see the global scope. This approach to binding visibility is called lexical scoping.

Function types:
Functions as values

Declaration notation
Function keyword is used at the start of a statement - This is a function declaration.Function declarations are not part of the regular top-to-bottom flow of control.
Arrow functions

Closure
local bindings are created anew for every call, and different calls can’t trample on one another’s local bindings.
being able to reference a specific instance of a local binding in an enclosing scope—is called closure. think of function values as containing both the code in their body and the environment in which they are created.

Recursion
Running through a simple loop is generally cheaper than calling a function multiple times.

Chapter 4: Data structures
Reading a property that doesn’t exist will give you the value undefined. The binary in operator, when applied to a string and an object, tells you whether that object has a property with that name.
There is no “deep” comparison operation built into JavaScript.
rest parameter is bound to an array containing all further arguments (...args). You can use a similar three-dot notation to call a function with an array of arguments.

Chapter 5: Higher-Order Functions
pure function does not modify
Chapter 6: Objects
the entity behind almost all objects, Object.prototype.
Functions derive from Function.prototype, and arrays derive from Array.prototype. prototype system can be interpreted as a somewhat informal take on an object-oriented concept called classes. put the keyword new in front of a function call, the function is treated as a constructor.
By convention, the names of constructors are capitalized
JavaScript classes are constructor functions with a prototype property.
Class declarations currently allow only methods—properties that hold functions—to be added to the prototype.
Like function, class can be used both in statements and in expressions.

let object = new class { getWord() { return "hello"; } };
console.log(object.getWord());

add a property to an object, whether it is present in the prototype or not, the property is added to the object itself. 
using plain objects as maps is dangerous.
create objects with no prototype
Object.keys returns only an object’s own keys, not those in the prototype. As an alternative to the in operator, you can use the hasOwnProperty method, which ignores the object’s prototype.
Symbols are values created with the Symbol function.
The object given to a for/of loop is expected to be iterable. This means it has a method named with the Symbol.iterator symbol (a symbol value defined by the language, stored as a property of the Symbol function).

Matrix.prototype[Symbol.iterator] = function() {
return new MatrixIterator(this);
};
methods that have static written before their name are stored on the constructor.

Chapter 7: Project: A Robot
These could then hold properties that describe their current state, such as the pile of parcels at a location, which we could change when updating the world.
This is wrong.
At least, it usually is. The fact that something sounds like an object does not automatically mean that it should be an object in your program.
Data structures that don’t change are called immutable or persistent.
The problem of finding a route through a graph is a typical search problem.
Chapter 8: Bugs and Errors
"use strict" at the top of your program rarely hurts and might help you spot a problem.
collections of tests (test suites)
resist the urge to start making random changes to the code to see whether that makes it better. Instead, think. Analyze what is happening and come up with a theory of why it might be happening.
Browsers come with the ability to set a breakpoint on a specific line of your code.
unwinding the stack. 

Chapter 9: Regular Expressions
JavaScript uses a convention where month numbers start at zero (so December is 11), yet day numbers start at one. This is confusing and silly. Be careful.

Chapter 10: Modules
Modules are an attempt to avoid these problems. A module is a piece of program that specifies which other pieces it relies on and which functionality it provides for other modules to use (its interface).
A package is a chunk of code that can be distributed (copied and installed). When using other people’s packages, make sure you are aware of their license.
The most widely used approach to bolted-on JavaScript modules is called CommonJS modules. Node.js uses it and is the system used by most packages on NPM.
Instead of calling a function to access a dependency, you use a special import keyword. Similarly, the export keyword is used to export things.
This is why the JavaScript standard from 2015 introduces its own, different module system. It is usually called ES modules, where ES stands for ECMAScript.
Because fetching a single big file tends to be faster than fetching a lot of tiny ones, web programmers have started using tools that roll their programs (which they painstakingly split into modules) back into a single big file before they publish it to the Web. Such tools are called bundlers.
And we can go further. Apart from the number of files, the size of the files also determines how fast they can be transferred over the network. Thus, the JavaScript community has invented minifiers.
Often defining new data structures can’t be avoided—only a few basic ones are provided by the language standard, and many types of data have to be more complex than an array or a map. But when an array suffices, use an array.
Chapter 11: Asynchronious programming

Chapter 12: Programming language
The reason we need to represent if as a special form, rather than a regular function, is that all arguments to functions are evaluated before the function is called, whereas if should evaluate only either its second or its third argument, depending on the value of the first.
Chapter 13: JavaScript and the Browser
The World Wide Web (not to be confused with the Internet as a whole) is a set of protocols and formats that allow us to visit web pages in a browser. 
Each document on the Web is named by a Uniform Resource Locator (URL)
