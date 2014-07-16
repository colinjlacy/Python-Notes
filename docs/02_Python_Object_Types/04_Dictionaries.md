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

