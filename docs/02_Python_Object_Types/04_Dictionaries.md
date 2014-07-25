In Python a dictionary is not considered a sequence, but actually a **mapping**, and mappings are collecitons of other objects - much like lists - but they store objects by key instead of by index.  So each object stored in a Python dictionary is the value in a key-value pairing.  As a result, they don't maintain any order about how data is stored.  They are also *mutable* and can grow and shrink on demand, like lists.

##Mapping Operations##

Dictionaries can be written as literals using curly braces, as a series of key-value pairs.  They look very much (or, exactly) like an object in JavaScript:

	>>> D = {'food': 'Spam', 'quantity': 4, 'color': 'pink'}

We can then reference any value in the dictionary by calling its key:

	>>> D['food']
	'Spam'

	>>> D['quantity'] += 1
	>>> D['quantity']
	5

Although this literal style of defining a dictionary works, there are other ways to do it that are far more common:

	>>> D = {}  # initializing an empty dictionary
	>>> D['name'] = 'Bob'
	>>> D['job'] = 'dev'
	>>> D['age'] = 40

	>>> D
	{'age': 40, 'job': 'dev', 'name': 'Bob'}

	>>> print(D['name'])
	Bob

###Nesting###

Very much like JavaScript objects, dictionaries can nest child dictionaries within key-value pairs.  For example, if we want the name property of the previous dictionary to be broken into a more complex dictionary, we ca do that like so:

	>>> rec = {'name': {'first': 'Bob', 'last': 'Smith},
				'job': ['dev', 'mgr'],
				'age': 40.5}

Notice that in this example, the first definition uses a **nested dictionary to support multiple parts**.  The second, `'job'` is defined with a **nested list to support multiple values and future expansion**.

	>>> rec['name']
	{'last': 'Smith', 'first': 'Bob'}

	>>> rec['name']['last']
	'Smith'

	>>> rec['job'][0]
	'dev'

	>>> rec['job'].append('janitor')
	>>> rec['job']
	['dev', 'mgr', 'janitor']

Notice that even though we're working with a dictionary on the parent level, we have access to object-specific methods when we call a key whose value is of a different object type.  This is clear in the code above, where we can access the first job by index, and append the value `'janitor'` to the `'job'` list.  This is because the job list is actually a separate piece of memory from the dictionary that contains it.

###Sorting Keys for Loops###

One of the useful type-specific operations that come with dictionaries is the ability to return only the keys, which is handy when we want to sort a dicitonary into a particular order.  As was said above, dictionaries don't keep an index, since they're mappings, not sequences.  Here's how this is done.

	>>> D = {'a': 1, 'b': 2, 'c': 3}

	>>> Ks = list(D.keys())
	>>> Ks
	['a', 'c', 'b']     # remember, no index, so not necessarily stored in the order we defined

	>>> Ks.sort()
	>>> Ks
	['a', 'b', 'c']     # a list, which can be sorted, sorted alphabetically

	>>> for key in Ks:
			print(key, '=>', D[key])        # note that this has to be indented, otherwise Python will throw an error

	a => 1
	b => 2
	c => 3

That's one way to do it.  Another way is to use the `sorted` built-in function, which returns the result of calling the object, and sorts a variety of object types, in this case the keys of the dictionary.

	>>> for key in sorted(D)
			print(key, '=>', D[key])

	a => 1
    b => 2
    c => 3

###The For Loop and While Loop###

The two examples above were a nice way to introduce the `for` loop, which iterates through an object and returns the values stored therein.  `for` loops access the current data value via a user-defined variable - in this case `key` - and use that to return or manipulate the current data in the loop.  It should be noted that both `for` and `while` are actually sequence operations, although they also operate on data types that are not sequences as well.  They comprise the most common tasks used to do repetitive work through types of data that contain multiple values.  Here is `for` operating on the characters in a string:

	>>> for c in 'spam':
			print(c.upper())

	'S'
	'P'
	'A'
	'M'

The `while` loop is a bit more general, and isn't necessarily tied to any restrictions set by the data being operated on:

	>>> x = 4
	>>> while x > 0:
			print('spam!' * x)

	spam!spam!spam!spam!
    spam!spam!spam!
    spam!spam!
    spam!

##Iteration and Optimization##

THe last example's `while` looks like a `for`.  That's because both are **iteration tools**, which will work on any object that follows the **iteration protocol**. In order to fit the iteration protocol, one of two things has to happen:
1. it has a physically stored sequence in memory
2. it generates one item at a time in the context of an iteration operation

An object falls into the latter category if it responds to the built-in `iter` command, with an object that advances in repsonse to `next`.  **Generators**, like the one we looked at earlier, acts this way.

For now, we'll just say that all Python tools that scan an object from left to right use the iteration protocol, including dictionaries.  This is why the `sorted` call works in the previous example, as dictionaries are iterable objects, with a `next` that returns successive keys.

For example, we can look at two versions of the same statement, both of which yield the same result:

	>>> squares = [x ** 2 for x in [1, 2, 3, 4, 5]]
	>>> squares
	[1, 4, 9, 16, 25]


	>>> squares = []
	>>> for x in [1, 2, 3, 4, 5]:
			squares.append(x ** 2)

	>>> squares
	[1, 4, 9, 16, 25]

THe second operates on list comprehension, as opposed to the first, which is an inline `for` loop.  In general, list comprehensions will run faster (sometimes twice as fast).  However it's always advisable to code for simplicity/readability first, and performance when it comes time to release if need be.

##if Tests##

Dictionaries have the capability to test for keys, so that you can run a conditional based on whether or not a key exists before trying to use it.  Trying something with a non-existent key will throw an error.  Since some data sets can't be relied on to have consistent keys defined for each dictionary (e.g. 'address 2'), we use the `in` membership expression that's available to dictionaries:

	# using a key that doesn't exist

	>>> D = {'a': 1, 'b': 2, 'c': 3}
	>>> D['f']
	... # some sweet error code ...
	KeyError: 'f'

	# now with the if statement

	>>> 'f' in D
	False

	>>> if not 'f' in D:
	        print('missing'

	missing

There's more to come about `if` statements, but for now we can see that it's written using the word `if` followed by a statement expression that is evaluated to either `true` or `false`, optionally followed by a block of code to run if the expression results to `true`.

The `if` can also be followed by an unlimited number of `elif` (else if) statements, or an `else` statement, both of which provide alternative logic for our code.  There's also the `get` method, which provides a default should the key being retrieved prove non-existent:

    >>> value = D.get('f', 0)
    >>> value
    0