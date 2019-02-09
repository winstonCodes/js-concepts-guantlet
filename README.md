## Introduction

I created this repo to help myself master the concepts of Javascript. I am taking the concepts outlined in the popular repo [33 Concepts Every JavaScript Developer Should Know](https://github.com/leonardomso/33-js-concepts), and actually doing the research. If any others find value in my work, [let me know!](https://twitter.com/winstoncodes)

---

## Table of Contents

1. **[Call Stack](#1-call-stack)**
2. **[Primitive Types](#2-primitive-types)**
3. **[Value Types and Reference Types](#3-value-types-and-reference-types)**
4. **[Implicit, Explicit, Nominal, Structuring and Duck Typing](#4-implicit-explicit-nominal-structuring-and-duck-typing)**
5. **[== vs === vs typeof](#5--vs--vs-typeof)**
6. **[Function Scope, Block Scope and Lexical Scope](#6-function-scope-block-scope-and-lexical-scope)**
7. **[Expression vs Statement](#7-expression-vs-statement)**
8. **[IIFE, Modules and Namespaces](#8-iife-modules-and-namespaces)**
9. **[Message Queue and Event Loop](#9-message-queue-and-event-loop)**
10. **[setTimeout, setInterval and requestAnimationFrame](#10-settimeout-setinterval-and-requestanimationframe)**
11. **[JavaScript Engines](#11-javascript-engines)**
12. **[Bitwise Operators, Type Arrays and Array Buffers](#12-bitwise-operators-type-arrays-and-array-buffers)**
13. **[DOM and Layout Trees](#13-dom-and-layout-trees)**
14. **[Factories and Classes](#14-factories-and-classes)**
15. **[this, call, apply and bind](#15-this-call-apply-and-bind)**
16. **[new, Constructor, instanceof and Instances](#16-new-constructor-instanceof-and-instances)**
17. **[Prototype Inheritance and Prototype Chain](#17-prototype-inheritance-and-prototype-chain)**
18. **[Object.create and Object.assign](#18-objectcreate-and-objectassign)**
19. **[map, reduce, filter](#19-map-reduce-filter)**
20. **[Pure Functions, Side Effects and State Mutation](#20-pure-functions-side-effects-and-state-mutation)**
21. **[Closures](#21-closures)**
22. **[High Order Functions](#22-high-order-functions)**
23. **[Recursion](#23-recursion)**
24. **[Collections and Generators](#24-collections-and-generators)**
25. **[Promises](#25-promises)**
26. **[async/await](#26-asyncawait)**
27. **[Data Structures](#27-data-structures)**
28. **[Expensive Operation and Big O Notation](#28-expensive-operation-and-big-o-notation)**
29. **[Algorithms](#29-algorithms)**
30. **[Inheritance, Polymorphism and Code Reuse](#30-inheritance-polymorphism-and-code-reuse)**
31. **[Design Patterns](#31-design-patterns)**
32. **[Partial Applications, Currying, Compose and Pipe](#32-partial-applications-currying-compose-and-pipe)**
33. **[Clean Code](#33-clean-code)**

---

## 1. Call Stack

A call stack (aka execution stack, program stack, run-time stack, or "the stack" ) is the list of functions a code-interpreter scheduled to run. When an interpreter runs a function, any subfunctions of that function are pushed/added into the queue. Once the subfunction runs, it is then popped/removed from the queue. If a subfunction calls another function, it is added to the stack further up. The order that these functions are ran is "Last In, First Out", meaning the higher up a function is on the stack, the sooner its going to be ran. If the stack takes up more room than the memory allocated for it, a "stack overflow" error is thrown
**Rough Draft**

*sources:*
* [Call Stack - *MDN*](https://developer.mozilla.org/en-US/docs/Glossary/Call_stack)
* [Call Stack - *Wikipedia*](https://en.wikipedia.org/wiki/Call_stack)
* [The JS Call Stack Explained in 9 minutes - *Youtube* by Colt Steele](https://www.youtube.com/watch?v=W8AeMrVtFLY)

###### **[⬆ Back to Top](#table-of-contents)**
---

## 2. Primitive Types

A primitive is data that is not an object and has no methods. These values are immutable/ cannot be altered. Note: Methods that are ran on primitives (ex. String.toUpperCase()) return a new primitive, while leaving the original primitive value alone.

The six data types that are primitives:
  * Boolean: *true/false*
  * Null: *the **intentional** absence of any object value*
  * Undefined: *a value automatically assigned to variables with no value. Differs from null as null is a value*
  * Number: *0-9*
  * String: *characters used to represent text*
  * Symbol: *tokens that serve as unique IDs*

*sources:*
* [JavaScript data types and data structures - MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Data_structures#Primitive_values)
* [Methods of Primitives](https://javascript.info/primitives-methods)
* [Symbols in Ecmascript 6](http://2ality.com/2014/12/es6-symbols.html)

**Rough Draft**

###### **[⬆ Back to Top](#table-of-contents)**
---

## 3. Value Types and Reference Types

Value types: All primitives
Reference types: Objects, arrays and functions

A variable can store either a value/primitive or a reference. When you manipulate a variable holding a primitive, you change the stored value of the variable. When you manipulate an object, the variable that stores the object is accessed by reference

Example:
```
var a = 5;
var b = a;
console.log(a); // returns 5
console.log(b); // returns 5

a += 5;
console.log(a) // returns 10
console.log(b) // returns 5

b += 5;
console.log(a) // returns 10
console.log(b) // returns 10


var objectA = { value: 5 }
var objectB = objectA;
console.log(objectA.value) // returns 5
console.log(objectB.value) // returns 5

objectA.value += 5;
console.log(objectA.value) // returns 10
console.log(objectB.value) // returns 10

objectB.value += 5;
console.log(objectA.value) // returns 15
console.log(objectB.value) // returns 15

```

*sources:*
* [Understand Value and Reference Types in JavaScript - Zsolt Nagy](https://www.zsoltnagy.eu/understand-value-and-reference-types-in-javascript/)
* [JavaScript Primitive vs. Reference Values](http://www.javascripttutorial.net/javascript-primitive-vs-reference-values/)

### **[⬆ Back to Top](#table-of-contents)**
---

## 4. Implicit, Explicit, Nominal, Structuring and Duck Typing

Implicit coercion is JavaScript deciding on its own


### **[⬆ Back to Top](#table-of-contents)**
---

## 5. == vs === vs typeof

== uses implicit coercion to decide if two values are the same. The two pieces of data do not have to be the same type
ex.
```
3 == "3" // returns true

null == undefined // returns true
```

=== decides if two pieces of data are both the same value and same type
ex.
```
3 === "3" // returns false
3 === 3 // returns true

null === undefined // returns false
```

the typeof operator returns a string indicating the type of its operand
ex.
```
typeof 5 // returns "number"
typeof "5" // returns "string"

typeof {} // returns "object"
typeof [] // returns "object"

typeof undefined // returns "undefined"
typeof null // returns "object"
```

Note the behavior above, as some may find it unexpected. The return value when the operand is an array is "object". Arrays are special, pre-defined objects whose keys in its key-value pairs are an index starting from 0. The array prototype (Array) has a series of methods used to perform traversal and mutation methods. One of these methods is .isArray(), which does a better job than typeof when determining if an operand is an array.
ex.
```
typeof [] // returns "object"
Array.isArray([]) // returns true
```

*sources:*
* [typeof - JavaScript | MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/typeof)
* [Array - JavaScript | MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array)
* [Array.isArray() - JavaScript | MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/isArray)

### **[⬆ Back to Top](#table-of-contents)**
---

## 6. Function Scope, Block Scope and Lexical Scope



### **[⬆ Back to Top](#table-of-contents)**
---

## 7. Expression vs Statement



### **[⬆ Back to Top](#table-of-contents)**
---

## 8. IIFE, Modules and Namespaces



### **[⬆ Back to Top](#table-of-contents)**
---

## 9. Message Queue and Event Loop



### **[⬆ Back to Top](#table-of-contents)**
---

## 10. setTimeout, setInterval and requestAnimationFrame



### **[⬆ Back to Top](#table-of-contents)**
---

## 11. JavaScript Engines



### **[⬆ Back to Top](#table-of-contents)**
---

## 12. Bitwise Operators, Type Arrays and Array Buffers



### **[⬆ Back to Top](#table-of-contents)**
---

## 13. DOM and Layout Trees



### **[⬆ Back to Top](#table-of-contents)**
---

## 14. Factories and Classes



### **[⬆ Back to Top](#table-of-contents)**
---

## 15. this, call, apply and bind



### **[⬆ Back to Top](#table-of-contents)**
---

## 16. new, Constructor, instanceof and Instances



### **[⬆ Back to Top](#table-of-contents)**
---

## 17. Prototype Inheritance and Prototype Chain



### **[⬆ Back to Top](#table-of-contents)**
---

## 18. Object.create and Object.assign



### **[⬆ Back to Top](#table-of-contents)**
---

## 19. map, reduce, filter



### **[⬆ Back to Top](#table-of-contents)**
---

## 20. Pure Functions, Side Effects and State Mutation



### **[⬆ Back to Top](#table-of-contents)**
---

## 21. Closures



### **[⬆ Back to Top](#table-of-contents)**
---

## 22. High Order Functions



### **[⬆ Back to Top](#table-of-contents)**
---

## 23. Recursion



### **[⬆ Back to Top](#table-of-contents)**
---

## 24. Collections and Generators



### **[⬆ Back to Top](#table-of-contents)**
---

## 25. Promises



### **[⬆ Back to Top](#table-of-contents)**
---

## 26. async/await



### **[⬆ Back to Top](#table-of-contents)**
---

## 27. Data Structures



### **[⬆ Back to Top](#table-of-contents)**
---

## 28. Expensive Operation and Big O Notation



### **[⬆ Back to Top](#table-of-contents)**
---

## 29. Algorithms



### **[⬆ Back to Top](#table-of-contents)**
---

## 30. Inheritance, Polymorphism and Code Reuse



### **[⬆ Back to Top](#table-of-contents)**
---

## 31. Design Patterns



### **[⬆ Back to Top](#table-of-contents)**
---

## 32. Partial Applications, Currying, Compose and Pipe



### **[⬆ Back to Top](#table-of-contents)**
---

## 33. Clean Code



### **[⬆ Back to Top](#table-of-contents)**
---
