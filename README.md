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

      var a = "a" / 2;

      a;                //NaN
      typeof a;         //"number"
      isNaN(a);         //true

      isNaN("foo");     //true WTF??






