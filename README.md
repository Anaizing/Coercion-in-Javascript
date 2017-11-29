# Coercion-in-Javascript
Important things I learned from Kyle Simpson, YDKJS

## Part 1 Primitive Types

### List of Primitive Types

      undefined
      string
      number
      boolean
      object
      function
      null
      

### Using the typeof operator
      typeof foo;                     //"undefined"
      typeof "foo";                   //"string"
      typeof 123;                     //"number"
      typeof true                     //"boolean"
      typeof { a : 1};                //"object"
      type of function() {alert(x);}  //"function"
      
      typeof null;                    //"object" (bug)

### Exercises
typeof returns STRING VALUES

      var foo;
      typeof foo;                   //"undefined"

      var bar = typeof bar;
      bar;                          //"undefined"-Has not been defined
      typeof bar;                   //"string"-typeof "undefined" is a string

      typeof typeof 2               //"string"-because typeof2 is "number" and typeof "number" is a string

### Special Values

      NaN                     (supposed to stand for not a number)
      Infinity, -infinity     (positive and negative)
      null                    (a key word)
      undefined               (an identifier, cant set a value to it in strict mode)
      +0,-0

### NaN
Remember typeof NaN is "number"
NaN is not equal to itself, its the only value in the language that is not equal to itself.
isNaN is a global utility to test for NaN-but it has a bug

      var a = "a" / 2;

      a;                //NaN- a string divided by a number is NotANumber
      typeof a;         //"number"- because typeof Nan is "number"
      isNaN(a);         //true

      isNaN("foo");     //true WTF?? (bug)
      
Es6 gives us a utility we can use to test NaN, with Number.isNaN that can be polyfilled.

      if (!Number.isNaN) {
            Number.isNaN = function(num) {
                  return (
                        typeof num === "number" && window.isNaN(num)
                  );
            }
      }
Since NaN is the only value that is not equal to itself, the test can be written like this.

      if (!Number.isNaN) {
                  Number.isNaN = function(num) {
                        return num !== num;
                  };
       }

### Negative Zero
The spec says there is one, although its hard to print.

      var foo = 0/-3;
      foo === -0;             //true
      foo === 0;              //true
      0 === -0;               //true
      (0 / .3) === (0 / 3);   //true

      foo;                    //-0

How to test for a negative zero

      function isNeg0(x) {
            return x === 0 && (1 / x) === -infinity;
      }

      isNeg0(0 / -3);         //true
      isNeg0(0 / 3);         //false

## New ES6 feature, Object.is 
Its a utility.
Prefered way to test for NaN and negative zero.
This is basically like the === operator, although its not recommended as a replacement.
Object.is will not lie to you about NaNs and negative zeros 

      Object.is("foo", NaN);  //false
      Object.is(NaN, NaN);    //true

      Object.is(0, -0);       //false
      Object.is(-0, -0);      //true

### Exercise
Answers to the right, test yourself!
Remember typeof infinity is "number"

      var baz = 2;            
      typeof baz;      =========> //"number"
      var baz;
      typeof baz;      =========> //"number"
      baz = null;
      typeof baz;      =========> //"object"- the bug

      baz = "baz" * 3;        
      baz;             =========> //NaN
      typeof baz;      =========> //"number"

      baz = 1 / 0;
      baz              =========> //infinity
      typeof baz;      =========> //"number"-because typeof infinity is "number"

### Natives
In addition to objects, they are functions
The purpose of String, Number and Boolean is TYPE COERCION
Its not a good idea to put `new` in front of one of these Natives

      String      |     String()
      Number      |     Number()
      Boolean     |     Boolean()
      Function    |     Function()
      Object      |     Object()
      Array       |     Array()
      RegExp      |     RegExp()
      Date        |     Date()
      Error       |     Error()

### Exercise














