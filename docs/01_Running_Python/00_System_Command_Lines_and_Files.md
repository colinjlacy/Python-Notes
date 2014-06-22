Writing code in the command prompt isn't exactly the best way to do things.  Each time you execute a command, it's process and then ersed from memory, meaning you can't go back and access it.  You'll have to write it from scratch next time you need it.

To save a program permanently, it needs to be written in code files, usually known as *modules* - text files containing Python statements.  Once that happens the programs therein can be run any time, through any means accessible to Python.

When saving a Python file, we drop the file extension `.py` on the end if we're going to import it into another file.  If not, we could easily just leave the file extension off, but where's the fun in that?  Here's a very basic Python file, `script1.py`, right out of the book:

	# A first Python script!

	import sys
    print(sys.platform)
    print(2 ** 100)
    x = "Colin!"
    print(x * 8)

So this is a simple script that does the following:
* imports a Python module to fetch the name of the platform (via the `sys` module, built into Python)
* runs three print statements
* makes use of a variable with a declaration and an operation

##Running Giles with Command Lines##

Once you have a file saved, you can navigate to its parent folder, and type

	$ python script1.py

That will execute the Python script, and the results of the file will be output into the Terminal window.

	# the results are in:

	darwin
    1267650600228229401496703205376
    Colin!Colin!Colin!Colin!Colin!Colin!Colin!Colin!

Since we're running in the shell, we can use shell commands to do fun things like build files out of the results.  Let's say I want to save the results of this Python module in a `.txt` file:

	$ python script1.py > saveit.txt

Sure enough, in the same directory I've created a `saveit.txt` file with the same results from above filled in as the content.

###Some Pitfalls of Running Scripts in the Command Line###

1. **Use file extensions for command line executions, but not for imports**.  The import syntax leaves off the file extension.
2. **Don't use `print` statements**.  The results from any execution are printed automatically.  `print` is generally only used in saved files.

###Double-Clicking on Icons###

Depending on the application set as the default, running a Python script by double-clicking in the file window will result in the program running as well.  Since it requirs a place to display the output from the `print()` commands, it will open a Terminal window and display whatever results it produces therein.

