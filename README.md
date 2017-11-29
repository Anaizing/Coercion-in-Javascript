# Coercion-in-Javascript
Important things I learned from Kyle Simpson, YDKJS

## Primitive Types

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






