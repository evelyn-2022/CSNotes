# <font size='6'><center>Running Programs</center></font>

## Shebang Line
The first line of all your Python programs should be a **shebang line**, which tells your computer that you want Python to execute this program. The shebang line begins with `#!`, but the rest depends on your operating system.
- On Windows, the shebang line is **`#! python3`**.
- On OS X, the shebang line is #! /usr/bin/env python3.
- On Linux, the shebang line is #! /usr/bin/python3.

You will be able to run Python scripts from IDLE without the shebang line, but the line is needed to run them from the command line.

<br>

***

## Running Python Programs on Windows
- On Windows, the Python 3.4 interpreter is located at <u>*C:\Python34\python.exe*</u>. Alternatively, the convenient py.exe program will read the shebang line at the top of the .py file’s source code and run the appropriate version of Python for that script.
- To make it convenient to run your Python program, create a *<u>.bat</u>* **batch file** for running the Python program with py.exe. To make a batch file, make **a new text file containing a single line** like the following:

	> ==@py.exe C:\path\to\your\pythonScript.py %*== or ==python filename.py==

	Replace this path with the absolute path to your own program, and save this file with a .bat file extension. This batch file will keep you from having to type the full absolute path for the Python program every time you want to run it. 
- The C:\MyPythonScripts folder should be **added to the system path** on Windows so that you can run the batch files in it from the Run dialog.

You can now run the program in cmd just by entering the .py file.
```
C:\Users\moche>car.py
This car has a 75-kWh battery.
This car can go about 315 miles on a full charge.
```