Tuples are essentially lists that are immutable, and cannot be changed.  Remember how lists are mutable and can be changed?  Yeah, not tuples.  They can be contatenated on, indexed, sliced, etc.  But just as with strings, those operations will return a completely different object.  Observe:

	>>> T = (1, 2, 3, 4)
	>>> T + (5, 6)
	(1, 2, 3, 4, 5, 6)

	>>> T
	(1, 2, 3, 4)

	>>> Tt = T + (5, 6)
	>>> Tt
	(1, 2, 3, 4, 5, 6)

Tuples have two type-specific callable methods that we can play with.  The first is `index()`:

	>>> T.index(4)
	3

This says that the number `4` is at index position 3.

The second is the `count()` method:

	>>> T.count(4)
	1

This says that there is only one `4` in the tuple.

Like lists and dictionaries, tuples support mixed types and nesting.  So the following will work:

	>>> TT = ('spam', 3.0, [11, 22, 33])
	>>> TT[1]
	3.0

	>>> TT[2][0]
	11

##Why Tuples?##

And why not a list instead?  Because when you write something in a tuple you know it will never be changed.  Lists are more flexible since they have more type-specific methods; however in a larger program, where you don't control everything, you run the danger of having your list overwritten if you pass it around quite a bit.  You'll never have that problem with a tuple, since it's immutable.