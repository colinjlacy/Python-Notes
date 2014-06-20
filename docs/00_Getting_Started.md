##Introducing the Python Interpreter##

An interpreter is a type of program that runs other programs.  It's essentially the software bits between the developer's Python code, and the hardware and software that operates the computer machine box thingy.  Depending on the flavor of Python chosen, the interpreter may be written in Java, C, or wahtever.  Either way, an interpreter is essential before any Python can be run, as Python must always be run by an interpreter.  It's worth noting that Linux and Mac already have Python installed, and some compile directly from the full source code distribution package.

What it means to execute a Python program largely depends on the view of the execution - whether it's from the eyes of the programmer, or the eyes of the interpreter.

###Programmer's View###

Simply put, a Python program is a file containing Python scripts.  I could name the following `script.py`, and I wouldn't be wrong in calling it a Python program.

	print('hello world')

Once this file has been made, it's required that we tell Python to execute the file, which it does in order from top to bottom.  For example, in Terminal, I'd say:

	$ python script.py

And it would tell me:

	hello world

That's the gist of it, as is the case with just about any scripting/programming language.  As for the interpreter's view, a bit more is happening.

###Python's View###

Before anything happens and my code starts running, Python takes a few steps towards making it digestible.  First, it compiles my code into "byte code", which is then routed to a "virtual machine".

####Byte Code Compilation####

Byte code is simply a platform-independent representation of the source code that runs much quicker than the actual source code would.  For the most part, this can go unseen; although the computer will store these byte-code interpretations in files that end with a `.pyc`, which means "compiled .py source".  The logic behind this is that once the `.pyc` file is made, it's stored so that the interpreter can access the pre-compiled byte-code, rather than compiling all over again.  It compares timestamps for each file to make sure nothing has changed.  If the code has changed, it is re-compiled the next time it's run.  Kind of like caching, in a way.  It is possible to write-protect and disallow the interpreter from writing `.pyc` files to the system.  In that case, it's compiled and stored in memory, then disregarded once it's been used.  However, none of this is ideal, since byte-code runs much faster once it has been created and stored.

####The Python Virtual Machine (PVM)####

Essentially this is just a big loop function that iterates over the byte-code and runs whatever programs are stored therein - the runtime engine.  It's the part of the Python system that actually "runs" the scripts, and can be considered the last step of the Python interpreter.  It's worth noting that this is all hidden from the developer's point of view.  But it's nice to know how your engine runs.

The byte-code run by the PVM isn't the same as the binary code run, for example, by C; so it's not as low-level and also not as fast. It's a special type of code that only the PVM understands, and requires more work than binary operating on a CPU chip.  On the other hand, once the byte-code file has been stored, it doesn't need to compile again. This gives it speed advantages over traditional interpreted languages like PHP.

 For developers, this all ends up becoming a bit trivial.  Since all of this happens at runtime, there's no need to worry about what's compiled into byte-code and what isn't.  Byte-code can include and execute source code just fine, and there's no hiccups or coughs in the process.