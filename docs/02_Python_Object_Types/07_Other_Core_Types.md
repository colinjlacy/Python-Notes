##Sets##

The first core type we'll look at is a set, which is a recent addition, and is neither a mapping, nor a sequence.  Rather they are unordered collections of unique immutable objects.  They can be created using the built-in `set()` function, or by creating set-literals and expressions, a feature new to 3.0.  The set-literal syntax matches that of dictionaries, as they are essentially dictionaries with keys that have no values.

	# Two ways to create sets

	>>> X = set('spam')
	>>> Y = {'h', 'a', 'm'}
	>>> X, Y
	({'a', 's', 'p', 'm'}, {'a', 'h', 'm'})

Notice that the order is rearranged based on whatever methodology it is that motivates Python to rearrange things.

Sets support mathematical operations:

	# Intersection
	>>> X & Y
	{'a', 'm'}

	# Union
	>>> X | Y
	{'a', 'h', 's', 'p', 'm'}

	# Difference
	>>> X - Y
	{'p', 's'}

	# Set comprehension
	>>> {x ** 2 for x in [1, 2, 3, 4]}
	{16, 1, 9, 4}

##Type##

The type object is a bit of data returned by the `type()` built-in function, and gives the type of another object.  It is therefore called upon another object.  In Python 3, the result is referred to as a *class*, not a type.

    # the type function in Python 3

    >>> type(X)
    <class 'set'>

	>>> type(type(X))
	<class 'type'>

A useful application for this functionality is to test for a certain object type:

	# type testing

	>>> if type(X) == set:
			print('yes')
	yes

##User-Defined Classes##

In some cases, we'll need to create our own data types in order to fit certain needs.  Let's say we want to create a data type for an employee roster.

	>>> class Worker:
			def _init_(self, name, pay):        # Initialize when created
				self.name = name                # self is the new object
				self.pay = pay
			def lastName(self):
				return self.name.split()[-1]    # Split string on blanks
			def giveRaise(self, percent):
				self.pay *= (1.0 * percent)     # Update pay in-place

	# Now we create a worker...

	>>> bob = Worker('Bob Smith', 50000)
	>>> bob.lastName()
	'Smith'

	>>> sue = Worker('Sue Jones', 60000)
	>>> sue.giveRaise(.10)
	>>> sue.pay
	66000.0