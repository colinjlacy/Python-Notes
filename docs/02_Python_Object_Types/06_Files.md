Files are a different type of data object in Python.  To create a file, there's no specific syntax needed.  Instead, you use the built-in `open` function, passing a file name as the first argument, and a processing mode in the form of a string as the second argument.

To creat a `data.txt` file, we would pass the name of the file, and the `'w'` string as the processing mode (for `write`):

	>>> f = open('data.txt', 'w')
	>>> f.write('Hello\n')
	6

	>>> f.write('world\n')
	6

	>>> f.close()

Notice that when you write a string of bytes to the file, it returns the number of bytes written.  The code above created a new file in the current directory called `data.txt`, and added two lines of text to it.  The file name can include a full path, in case we're not looking to write the file to the current directory.

To read what's in the file, we pass the `'r'` processing mode as the second argument (for `read`), or no argument at all since `read` is the default.

	>>> f = open('data.txt')
	>>> text = t.read()
	>>> text
	Hello
	world