# Sys Module

[toc]

## Input and output using `sys`

The sys modules provide variables for better control over input or output. We can even redirect the input and output to other devices. This can be done using three variables –
- stdin
- stdout
- stderr
<br/>

### `stdin`

It can be used to <u>get input from the command line directly</u>. It used is for standard input. It <u>internally calls the `input()` method</u>. It, also, automatically adds `"\n"` after each sentence.

```
import sys

for line in sys.stdin:
	if 'q' == line.rstrip():
		break
	print(f'Input : {line}')

print("Exit")
```
*output:*
```
C:\Users\moche>sys.py
tq
Input : tq

q
Exit
```
&nbsp;

### `stdout`
A built-in file object that is analogous to the interpreter’s standard output stream in Python. stdout is used to <u>display output directly to the screen console</u>.

```
import sys
sys.stdout.write('Geeks')
```
*output:*
```
C:\Users\moche>sys.py
Geeks
```
<br/>

### `stderr`
Whenever an exception occurs in Python it is written to sys.stderr.
<br/>


***

## Command line arguments
Command-line arguments are those which are <u>passed during the calling of the program along with the calling statement</u>. To achieve this using the sys module, the sys module provides a variable called `sys.argv`. It’s main purpose are:
- It is a list of command-line arguments.
- `len(sys.argv)` provides the number of command-line arguments.
- `sys.argv[0]` is the name of the current Python script.

```
import sys

# total arguments
n = len(sys.argv)
print("Total arguments passed:", n)

# Arguments passed
print("\nName of Python script:", sys.argv[0])

print("\nArguments passed:", end = " ")
for i in range(1, n):
	print(sys.argv[i], end = " ")

# Addition of numbers
Sum = 0

for i in range(1, n):
	Sum += int(sys.argv[i])

print("\n\nResult:", Sum)
```
*output:*
```
C:\Users\moche>sys.py 1 2 5 9
Total arguments passed: 5

Name of Python script: D:\Files\CS _Notes\Python\python_work\sys.py

Arguments passed: 1 2 5 9

Result: 17
```



