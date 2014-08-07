In Python, an expression is the combination of numbers and operators, which computes a value when executed by Python.  Conveniently this is done using the usual mathematical notation and operators.  For example, adding two numbers `x` and `y` is done by saying `x + y`.

##Mixed Operators Follow Operator Precedence##

Python follows the order of operations that is generally accepted in the mathematical universe.  So if a statement combines multiplication and addition, Python will evaluate the multiplication aspect first, and then move on to addition.

##Parentheses Group Sub-Expressions##

Like you'd expect to find when doing the math, parentheses take precedence over the order of operations.  Anything in parentheses is computed first, and if parentheses are nested, then the deepest nested parentheses take priority, and Python will work its way out.

##Mixed Types##

Python can operate on multiple types of numbers at a time, but it first takes the step of revising them to be the same type.  So for example, you can write an operation that takes place between an integer and a float:

	>>> 3 + 1.4
	4.4

What happens here is Python converts the simplest number type up to the complexity of the more complex number type.  In this case, the simpler integer `3` is converted to a float, in order to work with the more complex float `1.4`.  The result yielded will be as complex as the most complex operand.

You can force a conversion by using built-in functions that will simplify or complicate a number type:

	>>> int(1.4)
	1

	>>> float(3)
	3.0

However this is a rare happening, as Python usually converts for you, and you'll generally only do this when aiming for less accurate returns (e.g. converting a float into a date-time).

Note that these conversions only happen when working with numeric data types, and do not work when working with other data types. For example, you can't add a string to an integer, unless you were first to convert one to the other's data type manually.
