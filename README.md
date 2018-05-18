# Introduction
A silly script interpreter for the RFJ project. The interpreter is less than 1,000 LOC and can only understand the very limited subset of JavaScript.

## Language Specs

### Operators
Only the following operators are supported: `+`, `-`, `*`, `/`, `%`.

### Variables
Variables can be declared explicitly with the `var` statement.  
```js
var num = 123;
var str = "456";
```
- The `let` statement is **not** supported.
- String literals must be declared with double quotes. Using single quotes are **not** permitted.

### Objects
Object declarations must be in the following syntax.  
_Accessing member variables via the `this` keyword is **not** supported._
```js
var obj = {
  num: 123,
  str: "456",
  hello: function(args) { ...; return ...; }
};
```

### Functions
Function declarations must be in the following syntax.
```
var name = function (args) { ...; return ...; };
```
- Of course, the `return` statement is optional.
- An elderly syntax (i.e. `function name(){...}`) is **not** supported.

Function calls must be in the following syntax.
```js
func(...);
val.func(...);
val1.val2.func(...);
```
Method chaining (e.g. `val.func1(...).func2(...);`) is **not** supported. Separate those function calls.
```js
var intermediate = val.func1(...);
var result = intermediate.func2(...);
```

### Arrays
```js
var e = array[index];
array[index] = e + 1;
```
Arrays cannot be directly created.
The _only_ way to create an array is to call the `split` method on a string.  
Only the following methods and properties are supported: `splice`, `join`, `reverse`, `length`.

### Strings
```js
var str = "abc";
var e = str[1];
```
Only the following methods and properties are supported: `split`, `length`.  
_Escaping a double quote (`\"`) is **not** working at the moment._

### Comments
Comment blocks such as `//` and `/* ... */` are **not** supported.

### Control Flow Statements
Things like `if`, `for` and `while` are **not** supported.

### Classes? Exception? RegExp? Promise?
Nope.

### Arrow Functions? Destructuring Assignment? Template Literals?
😢

## License
Released under the [WTFPL](http://www.wtfpl.net/about/).
