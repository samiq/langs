# Dart Type System

Dart is an object oriented programming language where everything you can place in a variable is an object, and every object is an instance of a class. Even numbers, functions, and ```null``` are objects. All objects inherit from the Object class.

Specifying static types clarifies your intent and enables static checking by tools, but it’s optional.

Dart's dynamism provides developers a mechanism to circumvent or ignore types when convenient, but it also limits the effectiveness of ahead-of-time (AOT) compilation, specillay needed as Dart is increasingly being used as a cross platform language. To solve for such cases, the Dart team designed [Strong Mode](https://github.com/dart-lang/sdk/blob/master/pkg/dev_compiler/STRONG_MODE.md), to allow for better generated code by taking full advantage of the type information that programmers write.

## Variables

Variables are references.

```
var name = 'Bob';
```

Uninitialized variables have an initial value of ```null```. Even variables with numeric types are initially ```null```, because numbers are objects.

You have the option of adding static types to your variable declarations:

```
String name = 'Bob';
```

If you never intend to change a variable, use ```final``` or ```const```, either instead of ```var``` or in addition to a type.

A final variable can be set only once; a const variable is a compile-time constant.  If the const variable is at the class level, mark it static const.

```
final name = 'Bob';
const bar = 1000000;
const atm = 1.01325 * bar;
```

The ```const``` keyword isn’t just for declaring constant variables. You can also use it to create constant values, as well as to declare constructors that create constant values. Any variable can have a constant value.

```
var foo = const []; // where const [] creates an empty, immutable list.
```

## Built-in types

The Dart language has special support for the following types:

- **numbers:** ```num``` (parent class), ```int``` and ```double```
- **strings:** ```String``` : ```""``` or ```''```, for multiline strings use ```'''``` or ```"""```
- **booleans:** ```bool``` : ```true``` or ```false```, with ```true``` been the only true (ie. ```1``` or non ```null``` object are treated false)
- **lists:** also known as arrays: ```new List()``` or ```[]```, ```new List<type>()```, ```<type>[]```, ```new List(5)```, where ```5``` is the lenght for a fixed-lenght list.
- **maps:** ```new Map()``` or ```{ key: value, ... }```, ```new Map<String, String>``` or ```<String, String>{key : value, ..}```
- **runes:** UTF-32 code points of a string: ```var clapping = '\u{1f44f}'; // 👏 ```
- **symbols:**  you might never need them but when you dou see [here](https://www.dartlang.org/guides/libraries/library-tour#dartmirrors---reflection)

