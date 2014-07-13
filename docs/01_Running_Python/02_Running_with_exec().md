The built-in function `exec()` runs the latest version of a module automatically, without ever needing to `import` or `reload()`.  So that being the case, sometimes it's easier just to run a module, if you're not looking to access any of its attributes - say, for example, it only contains attributes necessary to run the commands that are run when the module is executed.

	>>> exec(open('script1.py').read())
	hello world

In effect, `exec()` runs the file exactly in place of the `exec()` command in the script, as though it had been pasted into the file in place of the `exec()` command.  Each time it runs, it calls the latest version of that module, so there's no `reload()` necessary as there is wtih `import`.

Much like `from`, `exec()` brings the variables, functions, etc. of the file being run into the namespace of the file running `exec()`.  However, the downside is that because the module is essentially pasted into place fot he `exec()`, there's potential to have namespace collisions (unintended overwrites of previously defined variables, functions, etc.).  A simple example is if both the file calling `exec()` and the module that is run by `exec()` both define a variable by the same name.

	# in the module to be run by exec, exec_me.py

	>>> x = 99

	# now in the file running exec

	>>> x = 88
	>>> exec(open('exec_me.py').read())
	>>> x
	99

