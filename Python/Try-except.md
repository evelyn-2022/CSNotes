# <font size='6'><center>Try-except</center></font>

[toc]

## <font color='BCA1E3'>Handling the `ZeroDivisionError`</font>

```
print("Enter two numbers, and I'll divide them.")
print("Enter 'q' to quit.")

while True:
    num_1 = input("Enter the first number: ")
    if num_1 =='q':
        break

    num_2 = input("Enter the second number: ")
    if num_2 =='q':
        break

    try:
        answer = int(num_1)/int(num_2)
    except ZeroDivisionError:
        print("You cannot divide by zero!")
    else:
        print(answer)
```

<br>

***

## <font color='BCA1E3'>Handling `FileNotFoundError` </font>

```
def count_words(filename):
    try:
        with open(filename, encoding='utf-8') as f:
            contents = f.read()
    except FileNotFoundError:
        pass
    else:
        words = contents.split()
        num = len(words)
        print(f'The file {filename} has {num} words.')

filenames = ['TWO YEARS AMONG NEW GUINEA CANNIBALS.txt', 'Little Woman.txt', 'Let Us Kiss and Part.txt' ]
for filename in filenames:
    count_words(filename)
```
*output:*
```
The file TWO YEARS AMONG NEW GUINEA CANNIBALS.txt has 61501 words.
The file Let Us Kiss and Part.txt has 80684 words.
```

### Notes:
-  Encoding argument (`encoding='utf-8`): this argument is needed when your system’s default encoding doesn’t match the encoding of the file that’s being read.
Without the encoding:
	```
	UnicodeDecodeError: 'gbk' codec can't decode byte 0x9d in position 1715: illegal multibyte sequence
	```
-  `pass`:
Python has a pass statement that tells it to <u>*do nothing in a block*</u>. 