Lists are general ordinal sequences of arbitrary object types - numbers, strings, whatever. They come with the same sequence functions that we saw in strings:

    >>> l = [1, 'two', 3]
    >>> l + [4, 'five']
    [1, 'two', 3, 4, 'five']

    >>> len(l)
    3

    >>> l[1]
    'two'

##Type-Specific Methods##

List methods have a lot in common with array methods in JavaScript and PHP, so a lot of this might seem familiar.  On top of that, a list **is** mutable, so it can be changed inline with its method properties.  You'll notice that's the case with all of the following methods.

###Append###

Grows the list by the argument passed to the `append` method

    >>> l.append('four')
    >>> l
    [1, 'two', 3, 'four']

###Pop###

Removes an item from the list, indicated by the index passed as an argument:

    >>> l.pop(3)
    'four'

    >>> l
    [1, 'two', 3]

###Sort & Reverse###

Sets an order as either ascending or descending, or reverses the order of the items in the list

    >>> m = [2, 1, 3]
    >>> m.sort()
    >>> m
    [1, 2, 3]

    >>> m.reverse()
    >>> m
    [3, 2, 1]

##Bounds Checking##

It's worth noting that while you can set an index inline, and replace its previous value (e.g. `m[0] = 'one'`), you can't go way off the end of the list and declare an index far beyond the list's boundaries:

    >>> m[99] = 'error'
    # returns an error

##Nesting##

Python supports nesting lists, and allows lists to be nested with arbitrary object types.  So a list can have a nested list, with one item being a dictionary, which has an item defined as a list with its own nested list.  Crazy, no?  Our examples won't be that crazy:

    >>> n = [[1, 2, 3],    # gasp, a matrix!
             [4, 5, 6],    # commands can span multiple lines if they're wrapped in square brackets
             [7, 8, 9]]

The result is a multidimensional array, which we can work with in a manner similar to that of PHP:

    >>> n[1]    # returns the item at index 1
    [4, 5, 6]

    >>> n[1][0]    # returns the item at index 0 in the item at index 1
    4

##Comprehensions##

Python lists can run complex operations that return values based on declarations known as **list comprehension expressions**.  So, for example, let's say I want to return the second item in each row of our matrix up above.

    >>> col2 = [row[1] for row in n]
    >>> col2
    [2, 5, 8]

    >>> n    # the matrix is unchanged
    [[1, 2, 3], [4, 5, 6], [7, 8, 9]]

There are some key things to know about building a comprehension.  

*First*, comprehensions are always declared using square brackets - `[..]` - almost as if to remind us that the output will be a list object.

*Second*, list comprehensions are built with an expression that declares what elements you're looking to have returned, and a looping construct that indicates that objects being looped over in the specified list.  The expression and looping construct share the same variable name.  In our example above, those two are `row[1]` and `row in n`, respectively.  The above expression would be written out verbally as: "Give me the items at index 1 (second item) for each row in list n".

*Third*, they can have a filter applied to them as well.  In the example below, the if statement filters out any odd values, so that only those items in index 1 of their respective row get added to the returned list.

    >>> col2 = [row[1] for row in n if row[1] % 2 == 0]
    >>> col2
    [2, 8]

*Fourth*, comprehensions can get pretty nuts.  For instance, you can get creative with expressions by adding additional operations to the variable being iterated on:

    >>> col3 = [row[1] + 1 for row in n]
    >>> col3
    [3, 6, 9]

Or, you can go really nuts and reference the list you're iterating on by creating a list local to the declaration:

    >>> diag = [n[i][i] for i in [1, 2, 3]]    # that's freakin' bonkers
    >>> diag
    [1, 5, 9]

This example shows how you can reference any iterable object for a comprehension expression. You can even loop over a string, since a string has the same sequence properties as a list:

    >>> doubles = [c * 2 for c in 'spam']
    >>> doubles
    ['ss', 'pp', 'aa', 'mm']
