In Python, a String is considered a simple Sequence Object, as it is an ordered sequence of one-character strings, ordered from left to right.  There are more types of Sequences in Python, but those are covered later.  

##Sequence Operations##

Strings come with sequence-related properties that give us access to quite a bit of data.

    >>> S = "spam"
    >>> len(s)
    4
    >>> S[0]
    's'
    >>> S[3]
    'm'
    >>> S[-2]
    'a'

Because a string, as a sequence, has a specific positional order of the elements it contains, we can access its elements by their position index, as seen above.  This also works counting backwards, with the last item in the sequence having a backward-index of `-1`. We can also use the built-in `len` property method, which gives us access to the amount of characters the string contains.

One of the nice things about position indexing is that we can reference an index by entering a number, variable, or expression in the square brackets, and Python will understand what's going on as it is interpreted.

    >>> S[len(S)-1]    # equivalent of saying 4-1
    'm'

It's also possible to slice a string by an index, which returns a new string object:

    >>> S[1:3]
    'pa'

This works by setting an initial offset before the `:`, and and ending/stopping offset after.  The returned sting is everything starting at and including the first offset, before reaching the second offset.  Thus, the second isn't included.  There are a lot of ways to play with this:

    >>> S[:3]    # everything but the character at index 3
    'spa'

    >>> S[1:]    # everything starting at index 1, with no ending offset
    'pam'

    >>> S[0:-1]    # everything starting at index 0, but before the first index when counting backwards, aka index 3
    'spa'

In addition to slicing, string can be **concatenated** and **repeated**.  Python (like everyone but PHP) uses the `+` plus-sign to indicate a concatenation operation.  This is actually the result of a larger topica called **polymorphism**, covered later.  

    >>> S + "alot"
    'spamalot'

Repetition happens by using the `*` asterix, which is also responsible for multiplication in mathematical operations.  Pretty easy to remember.

    >>> S * 3
    'spamspamspam'

##Immutability##

Every object in Python is either considered **mutable** or **immutabile**, which translates to changeable or not changeable.  Where as a string object can be overwritten or redeclared based on its original value, a string is actually immutable, and can't be changed.

    >>> S[0] = 'z'    # won't work
    ...some error text omitted...
    TypeError: 'str' object does not support item assignment

    >>> S = z + S[1:]
    >>> S
    'zpam'

##Type-Specific Methods##

Every object-type in Python comes with methods that only it can access.  Strings, for example, have their own methods that are separate from those accessible to other sequence objects, which can access the ones listed above.  As a general rule, generic functions, or functions that can be used by multiple object types, are called on the module's root scope, not as a property of any specific object:

    >>> l = 'string'
    >>> len(l)
    6
    >>> l[0]
    's'

On the other hand, type-specific functions are considered methods of the object-type, and therefore methods of the string on which they are being called.

    >>> l.replace('str', b)
    'bing'
    >>> l.find('g')
    5

###Find###

The string `find` method returns the index of a substring passed as an argument of the string's method:

    >>> S.find('pa')
    1

    >>> S.find('m')
    3

###Replace###

The `replace` method takes two arguments, one that identifies the substring to be replaced, and the other that indicates what it will be replaced with.  Note that this does not actually replace the content of the string object; rather it returns an entirely new string object, which a responsible developer would store in a variable.

    >>> S.replace('pa', 'XYZ')
    'sXYZm'

    # This is the same as writing the following:

    >>> S[0] + 'XYZ' + S[3]
    'sXYZm'

###Split###

`split` breaks a string into a list, based on a delimeter:

    >>> line = 'aaa,bbb,cc,d'
    >>> line.split(',')
    ['aaa', 'bbb', 'cc', 'd']

###Text Processing###

Python can do some simple text processing that comes in handy in various situations:

    >>> S.upper()
    'SPAM'

    >>> S.isalpha()
    True

    >>> S.isdigit()
    False

    >>> line = 'aa,bb,cc\n'
    >>> line.rstrip()    # strips whitespace characters on either side of the string
    >>> line
    'aa,bb,cc'

###Formatting###

There are two ways to format data in Python, both of which are acceptable, although the latter was introduced in Python 2.6 and 3, so is probably the better choice moving forward.

    # the original way
    >>> '%s eggs and %s' % ('green', 'spam')
    'green eggs and spam'

    # the new way
    >>> '{0} eggs and {1}'.format('green', 'spam')

##Getting Help##

If there's ever a point when you want to see what methods are accessible to a string (or any object, for that matter), you can use the `dir()` method, which will return every property that can be accessed for that object.

    >>> S = 'string'
    >>> dir(S)
    ['__add__', '__class__', /*...too many to list...*/ 'upper', 'zfill']

You can also call for help on a specific method within the Python shell:

    >>> help(S.replace)
    # ...returns an explanation of what to do

This later function call is part of a documentation interface called **PyDoc**, which pulls documentation from specific objects.  More on that later.
