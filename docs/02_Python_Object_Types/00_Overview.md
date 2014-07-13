There's a hierarchy in Python to the types of code that can be used to do things.  By things, I mean run programs, build software, and move mountains.  From the top-down, it looks like this:

1. Programs are composed of modules
2. Modules contain statements
3. Statements contain expressions
4. Expressions create and process objects

##Using Built-In Objects##

Python comes with a lot of handy built-in objects that can be used for many simple programs, and can actually end up solving a lot of real world problems. On top of that, since they're already written, using them is just a matter of knowing they're there.  Plus, they're easy to extend, should a custom object be needed.

###The Built-In Data Types###

* Numbers: 1234, 123.4, 3+4j, Decimal, Fraction
* Strings: 'this', "that's", 'those?!', a'list'
* Lists: [1, [2, b, "two"] 3]
* Dictionaries: {'this': 'that', 'these': 'those}
* Tuples: (1, "two", 3, 'four')
* Files: myfile = open('eggs', 'r')
* Sets: set(abc) = {'a', 'b', 'c'}
* Booleans: a = true
* Program Unit Types: Functions, modules, classes

In truth, much like in JavaScript, everything in Python is an object.  However this list covers just about all of the objects you'll be using, and how you'll likely intend to use them.

Objects in Python are both dynamically typed, and strongly typed.  What does that mean?

* Dynamically typed means that objects are given types automatically, without having to explicitly define which type they are by hand (think Java)
* Strongly typed means that once an object has been created, it can only be operated on using operations that are available to that object type

An object, once given a type, will have that type forever. The object can be used to create another object (say, for example, floating a number string), but the original object will still be one type, and the resulting object will be whatever type given to it upon creation.  Because objects are strongly typed, an object will only have the operation set available to it upon its creation, for all eternity.