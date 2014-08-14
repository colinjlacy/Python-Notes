##Variables and Basic Expressions##

When we want to execute a math function (or any expression, really), we can save data values in *variables* - names, created by either the developer or Python, that are used to keep track of information for use and re-use.  Variables are:
* created when they are first assigned a value
* replaced with their values when used in expressions
* assigned before they can be used in expressions
* refer to objects and are never declared ahead of time

That means that the following creates two variables, `a` and `b`:

	>>> a = 3
	>>> b = 4

Now we can use them in expressions:

	>>> a + 1
	4

	>>> b * 2
	8

	>>> a - 1.0         # a mixed-type conversion (int and float)
	2.0

	>>> a % 2, b ** 2   # two expressions separated by a comma...
	(1, 16)             # the returned value is a tuple (note the parentheses)

##Comparisons##

When using comparative operators, we can write an expression evaluating two integers, floats, or anything really.  The returned value is always a boolean.

	>>> a < b
	True

	>>> a == b
	False

	>>> 1.0 <= 1
	True

In the last example, we can see that you can mix types in a comparison statement.  However this is a convention available to numbers only.

We can also chain expressions, which can make for simpler statements in the long run.  An unlimited amount of statements can be chained together to be evaluated.

	>>> x = 2
	>>> y = 4
	>>> z = 6

	>>> x < y and y < z     # long form
	True

	>>> x < y < z           # chained expressions
	True

It's important to know that Python will look at each link in the chain, and combine them with `and` statements.  Essentially, each statement is evaluated, and if all are true, then the entire statement is true.  However if one is false, then the entire statement is false - just like any chained `and` statement.