In simple terms, any file that ends in the `.py` file extension is considered a module eligible for import.  `import` operations load another file into the importing file, and grant access to the imported file's contents.  The contents of that file are made available through its `attributes`.

Importing is one of the main features of the Python programming architecture - complex programs tend to be comprised of several imported files, all called by one *top-level* or main file launched to start the entire program.  THe big takeaway here is that importing a file, runs its code.

A quick example shows this happening in the console:

	# notice we're already in a python prompt...

	>>> import script1
	# ...
	# prints out some results.
	# ...

Notice that if you try importing twice, only the first time will display any results. This is because the import process is only happening once.  Importing is considered too expensive of a process to duplicate, as each time the Python compiler has to fine, compile, and import the file into the executed program.  Way too much overhead to do more than once.

If it's really necessary to import a file more than once, it can be done with `reload`. In 2.6, this is a standard function; in 3.0 it has to be loaded from a module.  The following example comes from 3.0:

	>>> from imp import reload
	>>> import script1
	# ...
	# prints out some results.
	# ...
	>>> import script1 # prints out nothing
	>>> reload(script1)
	# ...
	# prints out some results.
	# ...

This also picks up changes that might have been made between the first import and the reload execution.  So if something should change programmatically in an imported file as your files are run, reloading will catch those changes while importing will not.  However, `reload` is smart and expects the name of a file that has already been successfully imported.  It also has parentheses, as compared to `import` which does not.  The former is a function that is *called*, while the latter is a *statement*.  As a result, called functions have to have arguments, which in this case is the imported file name.  What shows is the return value of the `reload()` function, rather than the result of `script1.py` - although ultimately they end up being the same.

##Attributes##

In the grander scheme of things, a module is a package of variable names, known as a *namespace*.  The names iwthin that package are known as *attributes*, or a variable name that is attached to a specific object or module.  Kind of like an object property in JavaScript.  `import`, `from`, and `reload()` all give access to those names found within a module, making it easy to program up some functions that are intended to be used widely throughout a program or series of programs.  Kind of like a class in PHP.

If I create a file called `myfile.py`, and set a variable within as `title = "The Meaning of Life`, any time I import that file I will have access to the `title` variable, as it is an attribute of the module being imported.

    >>> import myfile
    >>> print(myfile.title)
    The Meaning of Life

Unlike JavaScript or PHP imports, where a file name is essentially disregarded once it's brought into another file, Python treats the imported content as attributes of the module that is the file being imported.  Hence the script above uses dot-notation on the imported module to access its variable attribute.

An alternative is to **copy** (not import) an attribute from a module by passing it to the `from` statement.

	>>> from myfile import title
	>>> print(title)
	The Meaning of Life

Notice that it has become a localized variable once it is copied, and doesn't have to be expressed as an attribute of `myfile`.

