# fccStuffs

Properties are the most important part of any JavaScript object.

The syntax for accessing the property of an object is:
objectName.property          // person.age
or
objectName["property"]       // person["age"]
or
objectName[expression]       // x = "age"; person[x]  // The expression must evaluate to a property name.

The JavaScript for...in statement loops through the properties of an object.
for (variable in object) {
    code to be executed
}

The delete keyword deletes a property from an object:
delete person.age;   // or delete person["age"];

In JavaScript, all attributes can be read, but only the value attribute can be changed (and only if the property is writable).

JavaScript objects inherit the properties of their prototype.The delete keyword does not delete inherited properties, but if you delete a prototype property, it will affect all objects inherited from the prototype.


A JavaScript method is a property containing a function definition.

In JavaScript, the thing called this, is the object that "owns" the JavaScript code. The value of this, when used in a function, is the object that "owns" the function.


It is considered good practice to name constructor functions with an upper-case first letter.


The way to create an "object type", is to use an object constructor function.

In a constructor function this does not have a value. It is a substitute for the new object. The value of this will become the new object when a new object is created.

The JavaScript prototype property allows you to add new properties and/or methods to object constructors.
Person.prototype.nationality = "English";

Only modify your own prototypes. Never modify the prototypes of standard JavaScript objects.



Semicolons are used to separate executable JavaScript statements.
Since a function declaration is not an executable statement, it is not common to end it with a semicolon.

Functions defined using an expression are not hoisted. Hoisting is JavaScript's default behavior of moving declarations to the top of the current scope.

Function expressions will execute automatically if the expression is followed by (), but you cannot self-invoke a function declaration.

JavaScript functions can be used in expressions:
Example
function myFunction(a, b) {
    return a * b;
}
var x = myFunction(4, 3) * 2;

The typeof operator in JavaScript returns "function" for functions. But, JavaScript functions can best be described as objects.

A function defined as the property of an object, is called a method to the object.
A function designed to create new objects, is called an object constructor.





























