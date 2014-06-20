The first step to running some sweet, sweet Python is taking it to the Terminal.  For Python 2.x installations, you can invoke Python by typing `python`.  It'll spit out some good notes and hints.  If you opt to install version 3.x, you'll have to invoke by typing `python3`.  This can also be remedied by writing:

	alias python='python3'

To revert, simply type `\python` for any uses looking for Pythong 2.x. `Ctrl-D` exits an ineractive session.

Anyway, this will begin an interactive Python session.  The command prompt is replaced by a `>>>`, which indicates a new line waiting for a command.  Results of commands entered are displayed on new lines without any `>>>`.  For example:

	$ python

	>>> print('Hello World')
	Hello World

While operating in an interactive session, commands are executed as soon as they're entered.  It's worth noting that the `print(...)` expression isn't needed to have Python return data to you.

	>>> lumberjack = 'okay'
	>>> lumberjack
	'okay'

	>>> 2 ** 8
	256

The first statement set a variable to contain a string.  Notice no variable declaration.  The second and third are considered expressions - direct calls to display the results of the statement given.

The interactive prompt runs code immediately as it's entered, which means it's all done in memory.  No file is stored, nothing saved for later.  The plus side to this is that it's a great way to do some simple testing and experimenting with the Python language.  For example, let's say I want to know how strings and integers interact.  I pop open terminal and type:

	>>> "Spam!" * 8
	'Spam!Spam!Spam!Spam!Spam!Spam!Spam!Spam!'

Who knew?