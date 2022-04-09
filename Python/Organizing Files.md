# <font size='6'><center>Organizing Files</center></font>

[toc]

## <font color='BCA1E3'>The `shutil` (shell utilities) Module</font>

### Copying and Renaming

Calling `shutil.copy(source, destination)` will copy the file at the path source to the folder at the path destination. (Both source and destination are strings.) This function returns a string of the path of the copied file.

```
>>> import shutil, os
>>> os.chdir('C:\\')
>>> shutil.copy('C:\\spam.txt', 'C:\\delicious')
'C:\\delicious\\spam.txt'
```

If destination is a *<u>filename</u>*, it will be used as the *<u>new name of the copied file</u>*. 

```
>>> shutil.copy('eggs.txt', 'C:\\delicious\\eggs2.txt')
'C:\\delicious\\eggs2.txt'
```

`shutil.copytree()` will copy an entire folder and every folder and file contained in it:
```
>>> import shutil, os
>>> os.chdir('C:\\')
>>> shutil.copytree('C:\\bacon', 'C:\\bacon_backup')
'C:\\bacon_backup'
```
The `shutil.copytree()` call creates a new folder named bacon_backup with the same content as the original bacon folder.

<br>

### Moving and Renaming Files and Folders

Calling `shutil.move(source, destination)` will move the file or folder at the path *source* to the path *destination* and will return a string of the absolute path of the new location.

- If destination points to a <u>*folder*</u>, the source file gets moved into destination and keeps its current filename:
	```
	>>> import shutil
	>>> shutil.move('C:\\bacon.txt', 'C:\\eggs')
	'C:\\eggs\\bacon.txt'
	```

	If there had been a *bacon.txt* file already in *C:\eggs*, it would have been **overwritten**.

- The destination path can also specify a <u>*filename*</u>. In the following example, the source file is ***moved and renamed***.

	```
	>>> shutil.move('C:\\bacon.txt', 'C:\\eggs\\new_bacon.txt')
	'C:\\eggs\\new_bacon.txt'
	```


If the directory doesn't exist:

- `move()` can’t find a folder named eggs in the *C:\ directory* and so assumes that destination must be specifying a filename, not a folder. So the *bacon.txt* text file is renamed to *eggs* (a text file without the *.txt* file extension).
	```
	>>> shutil.move('C:\\bacon.txt', 'C:\\eggs')
	'C:\\eggs'
	```
- The folders that make up the destination must already exist, or else Python will throw an exception:
	```
	>>> shutil.move('spam.txt', 'c:\\does_not_exist\\eggs\\ham')
	Traceback (most recent call last):
 	File "C:\Python34\lib\shutil.py", line 521, in move
 	--snip--
	Traceback (most recent call last):
 	File "<pyshell#29>", line 1, in <module>
 	shutil.move('spam.txt', 'c:\\does_not_exist\\eggs\\ham')
 	--snip--
	FileNotFoundError: [Errno 2] No such file or directory: 'c:\\does_not_exist\\eggs\\ham'
	```

<br>

***

## <font color='BCA1E3'>Deleting Files and Folders</font>

### Permanently Deleting in `os` Module

- Calling `os.unlink(path)` will delete the file at path.
- Calling `os.rmdir(path)` will delete the folder at path. This folder must be empty of any files or folders.
- Calling `shutil.rmtree(path)` will remove the folder at path, and all files and folders it contains will also be deleted.

Be careful when using these functions in your programs! It’s often a good idea to first run your program with these calls <u>*commented out*</u> and with `print()` calls added to show the files that would be deleted:
```
import os
for filename in os.listdir():
	if filename.endswith('.rxt'):
		#os.unlink(filename)
		print(filename)
 ```
 
 <br>
 
 ### Safe Deletes with the `send2trash` Module
 
Using send2trash is much safer than Python’s regular delete functions, because it will send folders and files to your computer’s **trash or recycle bin** instead of permanently deleting them. 
```
>>> import send2trash
>>> baconFile = open('bacon.txt', 'a') # creates the file
>>> baconFile.write('Bacon is not a vegetable.')
25
>>> baconFile.close()
>>> send2trash.send2trash('bacon.txt')
```

<br>

***

## <font color='BCA1E3'>Walking a Directory Tree</font>

`os.walk()` generate the file names in a directory tree by walking the tree either top-down or bottom-up. For each directory in the tree rooted at directory top (including top itself), it yields a ***3-tuple*** (dirpath, dirnames, filenames).
<center><img src="https://s2.loli.net/2021/12/04/vbwI3GmqV9xOziR.jpg" alt='alternative text' title='ice bear' width='300' /></center>

```
import os

for root, dirs, files in os.walk('C:\\users\\moche\\Desktop\\Test'):
    print(root)
    print(dirs)
    print(files)
    print('')
```

*output:*

```
C:\users\moche\Desktop\Test
['A', 'B', 'C']
['Test4.txt']

C:\users\moche\Desktop\Test\A
['A1', 'A2']
[]

C:\users\moche\Desktop\Test\A\A1
[]
['Test1.txt']

C:\users\moche\Desktop\Test\A\A2
[]
['Test2.txt']

C:\users\moche\Desktop\Test\B
[]
['Test3.txt']

C:\users\moche\Desktop\Test\C
[]
[]
```
To traverse all it’s branches completely from bottom to top:

```
for (root,dirs,files) in os.walk('Test', topdown=False):
```

To print out every file and folder in the path:
```
import os

for root, dirs, files in os.walk('C:\\users\\moche\\Desktop\\Test'):
    print('The current folder is ', root)

    for dir in dirs:
        print(os.path.join(root, dir))

    for file in files:
        print(os.path.join(root, file))
    print('')
```

*output:*

```
The current folder is  C:\users\moche\Desktop\Test
C:\users\moche\Desktop\Test\A
C:\users\moche\Desktop\Test\B
C:\users\moche\Desktop\Test\C
C:\users\moche\Desktop\Test\Test4.txt

The current folder is  C:\users\moche\Desktop\Test\A
C:\users\moche\Desktop\Test\A\A1
C:\users\moche\Desktop\Test\A\A2

The current folder is  C:\users\moche\Desktop\Test\A\A1
C:\users\moche\Desktop\Test\A\A1\Test1.txt

The current folder is  C:\users\moche\Desktop\Test\A\A2
C:\users\moche\Desktop\Test\A\A2\Test2.txt

The current folder is  C:\users\moche\Desktop\Test\B
C:\users\moche\Desktop\Test\B\Test3.txt

The current folder is  C:\users\moche\Desktop\Test\C
```

<br>

***

## <font color='BCA1E3'>Compressing Files with the zipfile Module</font>

