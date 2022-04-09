# <font size='6'><center>Files</center></font>

[toc]

## <font color='BCA1E3'>Opening a File</font>

> *pi.txt:*
> 3.1415926535
> 8979323846
> 2643383279

### One way to open `open()`

```
fhand = open('pi.txt')
print(fhand)
for line in fhand:
    print(line.strip())
```
*output:*
```
<_io.TextIOWrapper name='pi.txt' mode='r' encoding='cp936'>
3.1415926535
8979323846
2643383279
```
If the open is successful, the operating system returns us a **file handle**. The file handle is *<u>not the actual data contained in the file</u>*, but instead it is a “handle” that we can use to read the data. The <u>*for loop actually causes the data to be read*</u> from the file.

<br>

### A better way to open file using `with`

```
with open("pi.txt") as fhand:
    for line in fhand:
        print(line.rstrip())
```
*output:*
```
3.1415926535
8979323846
2643383279
```
The keyword `with` <u>*closes the file once access to it is no longer needed*</u>. It’s not always easy to know exactly when you should close a file, but with the structure shown here, Python will figure that out for you.

<br>

### ==Note:==
Outside with structure, the file is closed. So if you need access to the contents outside the with block, <u>*store the contents to a variable inside the block*</u>.
```
with open("pi.txt") as fhand:
    print(fhand)
contents = fhand.read()
print(contents)
```
*output:*
```
Traceback (most recent call last):
  File "D:\Files\CS Notes\python_work\file_reader.py", line 5, in <module>
    contents = fhand.read()
ValueError: I/O operation on closed file.
<_io.TextIOWrapper name='pi.txt' mode='r' encoding='cp936'>
```

<br>

***

## <font color='BCA1E3'>Reading a File</font>

### Making a List of Lines from a File `.readlines()`

```
file_name = 'pi.txt'
with open(file_name) as fhand:
    lines = fhand.readlines()
print(f"lines: ", lines)
```
*output:*
```
lines:  ['3.1415926535\n', '8979323846\n', '2643383279']
```
The `readlines()` method takes each line from the file and **stores it in a list**. This list is then assigned to lines, which we can continue to work with after the with block ends.

<br>

### Making a String from a File `.read()`
```
file_name = 'pi.txt'
with open(file_name) as fhand:
    contents = fhand.read()
print(f"contents: ", contents)
print(f"type_contents: ", type(contents))
```
*output:*
```
contents:  3.1415926535
8979323846
2643383279
type_contents:  <class 'str'>
```

<br>

#### Make It into a Single Line
```
file_name = 'pi.txt'
with open(file_name) as fhand:
    lines = fhand.readlines()
pi_string = ''
for line in lines:
    pi_string += line.strip()
print(pi_string)
```
*output:*
```
3.141592653589793238462643383279
```

<br>

### Note
- Reading a file: 
	When Python reads from a text file, it <u>*interprets all text in the file as a string*</u>. If you read in a number and want to work with that value in a numerical context, you’ll have to convert it to an integer using the `int()` function or convert it to a float using the `float()` function.
- Writing a file:
Python can only write strings to a text file. If you want to store numerical data in a text file, you’ll have to convert the data to string format first using the `str()` function.

<br>

***

## <font color='BCA1E3'>Writing to a File</font>

To write text to a file, you need to call `open()` with a second argument telling Python that you want to write to the file. 
The second argument, 'w', tells Python that we want to open the file in write mode. You can open a file in **read mode ('r')**, **write mode ('w')**, **append mode ('a')**, or a mode that allows you to **read and write to the file ('r+')**. If you omit the mode argument, Python opens the file in **read-only mode by default**.
```
file_name = 'pi.txt'
with open(file_name, 'a') as fhand:
    fhand.write('Maths is exciting!')
```
The output of the file *pi.txt*:
3.1415926535
8979323846
2643383279
Maths is exciting!

<br>

***

## <font color='BCA1E3'>File Paths</font>

When you pass a simple filename like *pi.txt* to the `open()` function, Python looks in the directory where the program that’s currently being executed is stored.
1. Relative path
If the target file is in a subdirectory (text_files) of the current directory:
	```
	with open('text_files/filename.txt') as file_object:
	```
2. Absolute path
	```
	file_path = '/home/ehmatthes/other_files/text_files/filename.txt'
	with open(file_path) as file_object:
	```
### Note:
- Windows systems use a backslash (`\`) instead of a forward slash (`/`) when displaying file paths, but you can still use forward slashes in your code. 
- If you try to use backslashes in a file path, you’ll get an error because the backslash is used to **escape characters** in strings. For example, in the path `C:\path\to\file.txt`, the sequence \t is interpreted as a tab. If you need to use backslashes, you can escape each one in the path, like this: `C:\\path\\t\\file.txt`.


<br>

***

## <font color='BCA1E3'>Project</font>

Write a function named `printTable()` that takes a list of lists of strings and displays it in a well-organized table with each column right-justified. Assume that all the inner lists will contain the same number of strings.
```
tableData = [['apples', 'oranges', 'cherries', 'banana'],
            ['Alice', 'Bob', 'Carol', 'David'],
            ['dogs', 'cats', 'moose', 'goose']]

def printTable(tableData):
    vol = len(tableData)
    row = len(tableData[0])

    colWidths = [0] * vol
	# create a list containing 0s as the number of inner lists in tableData

    for i in range(vol):
        lis = tableData[i]
        for item in lis:
            if len(item) > colWidths[i]:
                colWidths[i] = len(item)

    for y in range(row):
        for x in range(vol):
            print(tableData[x][y].rjust(colWidths[x]), end=' ')
        print('')

printTable(tableData)
```
*output:*
```
  apples Alice  dogs 
 oranges   Bob  cats 
cherries Carol moose 
  banana David goose
 ```
