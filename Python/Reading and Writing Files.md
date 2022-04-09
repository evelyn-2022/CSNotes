# <font size='6'><center>Reading and Writing Files</center></font>

[toc]

## <font color='BCA1E3'>Files and File Paths</font>

### Creating Strings for Filenames `os.path.join()`

```
import os

myFiles = ['accounts.txt', 'details.csv', 'invite.docx']
for filename in myFiles:
    print(os.path.join('C:\\Users', 'Eric' , filename))
```
*output:*
```
C:\Users\Eric\accounts.txt
C:\Users\Eric\details.csv
C:\Users\Eric\invite.docx
```

<br>

### The Current Working Directory

You can get the current working directory as a string value with the `os.getcwd()` function and change it with `os.chdir()`:

```
>>> os.getcwd()
'C:\\WINDOWS\\system32'
>>> os.chdir('D:\\Files\\CS _Notes\\Python')
>>> os.getcwd()
'D:\\Files\\CS _Notes\\Python'
>>> 
```

<br>

### Absolute vs. Relative Paths

- *Absolute path*: always begins with the root folder
- *Relative path*: relative to the program’s current working directory

There are also the dot (.) and dot-dot (..) folders. A single period (“dot”) for a folder name is shorthand for “this directory.” Two periods (“dot-dot”) means “the parent folder.”

<center><img src="https://i.loli.net/2021/12/01/lyn3QYiwcm4HtkB.png" alt='alternative text' title='ice bear' width='460' /></center>

<br>

### Creating New Folders with `os.makedirs()`

```
>>> os.makedirs('D:\\fruits\\apples')
>>> os.chdir('D:\\fruits\\apples')
>>> os.getcwd()
'D:\\fruits\\apples'
```

<br>

***

## <font color='BCA1E3'>The `os.path` Module</font>

### Handling Absolute and Relative Paths

- Calling `os.path.abspath(path)` will return a string of the absolute path of the argument. This is an easy way to *<u>convert a relative path into an absolute one</u>*.
- Calling `os.path.isabs(path)` will return True if the argument is an absolute path and False if it is a relative path.
- Calling `os.path.relpath(path, start)` will return a string of a *<u>relative path from the start path to path</u>*. If *start* is not provided, the *current working directory* is used as the start path.

```
>>> os.path.abspath('.')
'D:\\fruits\\apples'
>>> os.path.isabs('.')
False
>>> os.path.relpath('python_work', 'fruits')
'..\\python_work'
```

Calling `os.path.dirname(path)` will return a string of everything that comes before the last slash in the path argument. Calling `os.path.basename(path)` will return a string of everything that comes after the last slash in the path argument:

```
>>> os.path.basename('D:\\Files\\CS _Notes\\Python\\python_work\\analyse.py')
'analyse.py'
>>> os.path.dirname("D:\\Files\\CS _Notes\\Python\\python_work\\analyse.py")
'D:\\Files\\CS _Notes\\Python\\python_work'
```

If you need a path’s dir name and base name together, you can just call `os.path.split()` to get a tuple value with these two strings:
```
>>> filepath = 'D:\\Files\\CS_Notes\\Python\\pythonlearn.pdf'
>>> os.path.split(filepath)
('D:\\Files\\CS_Notes\\Python', 'pythonlearn.pdf')
```

Note that `os.path.split()` does not take a file path and *<u>return a list of strings of each folder</u>*. For that, use the `split()` string method and split on the string in `os.sep`. 

```
>>> filepath.split(os.path.sep)
['D:', 'Files', 'CS_Notes', 'Python', 'pythonlearn.pdf']
```

<br>

### Finding File Sizes and Folder Contents

- Calling `os.path.getsize(path)` will return the size in bytes of the file in the path argument;
- Calling `os.listdir(path)` will return a list of filename strings for each file in the path:
```
>>> filepath = 'D:\\Files\\CS_Notes\\Python\\pythonlearn.pdf'
>>> os.path.getsize(filepath)
2385989
>>> os.listdir('D:\\Files\\CS_Notes\\Python\\python_work')
['analyse.py', 'fav_num.py', 'fav_num.txt', 'files.py', 'interesting_projects', 'Let Us Kiss and Part.txt', 'pi.txt', 'pizza.py', 'pizzashell.bat', 'plot.py', 'restaurant.py', 'string.py', 'sys.py', 'syshell.bat', 'TWO YEARS AMONG NEW GUINEA CANNIBALS.txt', 'user.py', '__pycache__']
```

If I want to find the total size of all the files in one directory, I can use `os.path.getsize()` and `os.listdir()` together:
```
>>> total_size = 0
>>> filepath = 'D:\\Files\\CS_Notes\\Python'
>>> for item in os.listdir(filepath):
	total_size += os.path.getsize(os.path.join(filepath, item))
	
>>> print(total_size)
76917343
```

<br>

### Checking Path Validity

- Calling `os.path.exists(path)` will return True if the file or folder referred to in the argument exists and will return False if it does not exist.
- Calling `os.path.isfile(path)` will return True if the path argument *<u>exists and is a file</u>* and will return False otherwise.
- Calling `os.path.isdir(path)` will return True if the the path argument *<u>exists and is a folder</u>* and will return False otherwise.

<br>

***

## <font color='BCA1E3'>The File Reading/Writing Process</font>


### Saving Variables with the `shelve` Module

- **Plaintext files**: contain only basic text characters and do not include font, size, or color information.
- **Binary files** are all other file types, such as word processing documents, PDFs, images, spreadsheets, and executable programs. 

You can save variables in your Python programs to binary shelf files using the `shelve` module. 

```
>>> os.chdir('D:\\Files\\CS_Notes\\Python')
>>> shelf_file = shelve.open('mydata')
>>> type(shelf_file)
<class 'shelve.DbfilenameShelf'>
>>> cats = ['Bob', 'Simon', 'Theo']
>>> shelf_file['cats'] = cats
>>> shelf_file.close()
```
After running the previous code on Windows, you will see three new files in the current working directory: mydata.bak, mydata.dat, and mydata.dir. 
Shelf values don’t have to be opened in read or write mode—they can do both once opened.
```
>>> shelf_file = shelve.open('mydata')
>>> shelf_file['cats']
['Bob', 'Simon', 'Theo']
```

You can make changes to the shelf value as if it were a ***dictionary***. Shelf values have `keys()` and `values()` methods that will return list-like values of the keys and values in the shelf. 
```
>>> shelf_file = shelve.open('mydata')
>>> shelf_file['cats']
['Bob', 'Simon', 'Theo']
>>> list(shelf_file.keys())
['cats']
>>> list(shelf_file.items())
[('cats', ['Bob', 'Simon', 'Theo'])]
```

<br>

### Saving Variables with the `pprint.pformat()` Function

`pprint.pprint()` function will “pretty print” the contents of a list or dictionary to the screen, while the `pprint.pformat()` function will return this same text *<u>as a string</u>* instead of printing it. It can be written to *.py* file. 
```
>>> import pprint
>>> cats = [{'name': 'Zophie', 'desc': 'chubby'}, {'name': 'Pooka', 'desc': 'fluffy'}]
>>> pprint.pformat(cats)
"[{'desc': 'chubby', 'name': 'Zophie'}, {'desc': 'fluffy', 'name': 'Pooka'}]"
>>> fileObj = open('myCats.py', 'w')
>>> fileObj.write('cats = ' + pprint.pformat(cats) + '\n')
83   # the size of the written content (excluding \n)
>>> fileObj.close()
```


This file will be your very own module that you can import whenever you want to use the variable stored in it.

```
>>> import cat
>>> cat.cats
[{'desc': 'chubby', 'name': 'Zophie'}, {'desc': 'fluffy', 'name': 'Pooka'}]
>>> cat.cats[0]['name']
'Zophie'
```

The benefit of creating a *.py* file (as opposed to saving variables with the shelve module) is that because it is a text file, the contents of the file can be read and modified by anyone with a simple text editor. For most applications, however, saving data *using the shelve module is the preferred way to save variables to a file*. *Only basic data types such as integers, floats, strings, lists, and dictionaries can be written to a file as simple text.* File objects, for example, cannot be encoded as text.


<br>

***

## <font color='BCA1E3'>Project</font>

### Generating Random Quiz Files

Here is what the program does:
- Creates 35 different quizzes.
- Creates 50 multiple-choice questions for each quiz, in random order.
- Provides the correct answer and three random wrong answers for each question, in random order.
- Writes the quizzes to 35 text files.
- Writes the answer keys to 35 text files.
 
This means the code will need to do the following:
- Store the states and their capitals in a dictionary.
- Call open(), write(), and close() for the quiz and answer key text files.
- Use `random.shuffle()` to randomize the order of the questions and multiple-choice options.

<br>

==*Note:*==
1. `%s` and `%d` are Format Specifiers or placeholders for formatting strings / decimals / floats etc:
	`%s`: string
	`%d`: decimals
	`%f`: float
	```
	>>> print("Hello, my name is %s and I'm %d years old." % ('John', 25) )
	Hello, my name is John and I'm 25 years old.
	
	>>> fir = 289.5
	>>> sec = 25
	>>> print("%f multiplied by %d is %f." % (fir, sec, fir*sec) )
	289.500000 multiplied by 25 is 7237.500000.

	```

	In Python 3.0, the `%` operator is supplemented by a more powerful string formatting method `.format`:
	```
	>>> print("Hello, my name is {} and I'm {} years old.".format('John', 25) )
	Hello, my name is John and I'm 25 years old.
	```
	
2. `random.shuffle` and `random.sample`
	- `random.shuffle()` shuffles the original list, meaning the shuffling can be done in-place;
	- `random.sample()` returns a new shuffled list, based on the original list.

	
	```
	>>> import random
	>>> a_list = ['welcome', 'to', 'datagy', 'where', 'you', 'will', 'learn', 'Python', 'and', 'more']
	>>> random.shuffle(a_list)
	>>> print(a_list)
	['welcome', 'more', 'and', 'datagy', 'will', 'learn', 'where', 'to', 'you', 'Python']
	
	>>> picked = random.sample(a_list, 5)
	>>> print(picked)
	['learn', 'where', 'Python', 'welcome', 'to']
	```
	
[quiz_generator.py](https://gitee.com/riding-a-bucket/python_work/blob/python_learning/quiz_generator.py)
	
<br>

***

### Multiclipboard

The program will save each piece of clipboard text under a keyword. For example, when you run py mcb.pyw save spam, the current contents of the clipboard will be saved with the keyword spam. This text can later be loaded to the clipboard again by running py mcb.pyw spam. And if the user forgets what keywords they have, they can run py mcb.pyw list to copy a list of all keywords to the clipboard.

- *.pyw* file
	Python scripts (files with the extension *.py*) will be executed by *python.exe* by default. This executable <u>*opens a terminal*</u>. If you do not want this to happen, use the extension *.pyw* which will cause the script to be executed by *<u>pythonw.exe</u>* by default (both executables are located in the top-level of your Python installation directory). This suppresses the terminal window on startup.
- remove a key from dictionary: `dic.pop(key_to remove, not_found)`
- remove all keys in dictionary: `dic.clear()`

[mcb.pyw](https://gitee.com/riding-a-bucket/python_work/blob/python_learning/multiclipboard/mcb.pyw)
[mcb.bat](https://gitee.com/riding-a-bucket/python_work/blob/python_learning/multiclipboard/mcb.bat)

<br>

***

### Mad Libs

Create a Mad Libs program that reads in text files and lets the user add their own text anywhere the word ADJECTIVE, NOUN, ADVERB, or VERB appears in the text file. For example, a text file may look like this:
> The ADJECTIVE panda walked to the NOUN and then VERB. A nearby NOUN was unaffected by these events.

The program would find these occurrences and prompt the user to replace them.
[mad_lib.py](https://gitee.com/riding-a-bucket/python_work/blob/python_learning/mad_lib/mad_lib.py)

<br>

***

### Regex Search
Write a program that opens all .txt files in a folder and searches for any line that matches a user-supplied regular expression. The results should be printed to the screen. 

- how to select txt files:
	 ```
	    if filename.endswith('.txt'):
        fhand = open(filename, encoding='utf-8')
	```
[search_txt.py](https://gitee.com/riding-a-bucket/python_work/blob/python_learning/search_txt.py)

