# Strings

[toc]

## F-Strings
The f is for format, because Python formats the string by replacing the name of any variable in braces with its value.

```
first = "ade"
last = "bill"
full = f"{first} {last}"
print(full)
```
*output*
```
ade bill
```

[To format a string:](https://docs.python.org/3/library/string.html#format-examples)

Using the comma as a thousands separator:

```
n = 123456
print(f'{n:,}')  
print('{:,}'.format(n))   // Prints: 123,456
```

Specify the number of digits:
```
m = 1234.5678
print(f'{m:,.2f}')
print('{:.2f}'.format(m))   // Prints: 1,234.57
```

<br>

***
## String Operations
- The `+` operator performs string concatenation, which means it joins the strings by linking them end-to-end;
- The `*` operator also works on strings; it performs repetition. For example, `'Spam'*3` is `'SpamSpamSpam'`. If one of the values is a string, the other has to be an integer.
- The `in` and `not in` Operators with Strings
  Strings use indexes and slices <u>the same way lists do</u>. 
	```
	print('hello' in 'hello world')
	```
	*output:*
	```
	True
	```
<br>

***

## Useful String Methods

### The `.title()` Method

```
first = "ade"
last = "bill"
full = first+" "+last
print(full.title())
```
*output:*
```
Ade Bill
```

<br>

### The  `upper()`, `lower()`, `isupper()`, and `islower()` String Methods
Note that these methods <u>do not change the string itself</u> but ==return new string values==. If you want to change the original string, you have to call `upper()` or `lower()` on the string and then <u>assign the new string to the variable</u> where the original was stored (`spam = spam.upper()`). (*This is just like if a variable eggs contains the value 10. Writing eggs + 3 does not change the value of eggs, but eggs = eggs + 3 does.*)
- `isupper()`, and `islower()`
  Return a ==Boolean True value== if the string has at least one letter and all the letters are uppercase or lowercase
  ```
  message = 'Hello'
  print(message.islower())
  print(message.lower().islower())
  ```
	*output:*
	```
	False
	True
	```
 
<br>

### The `.isX()` String Methods
Along with `islower()` and `isupper()`, there are several string methods that have names beginning with the word ==is==. These methods return a Boolean value that describes the nature of the string.
- `isalpha()` returns True if the string consists only of letters and is <u>not blank</u>.
- `isalnum()` returns True if the string consists <u>only of letters and numbers</u> and is not blank.
- `isdecimal()` returns True if the string consists only of <u>numeric characters</u> and is not blank.
- `isspace()` returns True if the string consists only of <u>spaces, tabs, and newlines</u> and is not blank.
- `istitle()` returns True if the string consists only of words that <u>begin with an uppercase letter followed by only lowercase letters</u>.

&nbsp;

`.isX()` can be used to validate user input
  ```
  # If age is a valid (decimal) value, we break out of this while loop. 
  while True:
    print('Enter your age:')
    age = input()
    if age.isdecimal():
        break
    print('Please enter a number for your age.')
```
*output:*
```
	Enter your age:
	ERIC
	Please enter a number for your age.
	Enter your age:
	4
```
<br>

### The `startswith()` and `endswith()` String Methods
Return True if the string value they are called on begins or ends (respectively) with the string passed to the method.
```
print("hello world".startswith("hello"))
```
*output:*
```
True
```

<br>

### The `join()` and `split()` String Methods
- `join()` is ==called on a string value== and ==is passed a list value==.
  The string `join()` calls on is inserted between each string of the list argument. 
	```
	message = ' '.join(['I', 'am', 'happy'])
	print(message)
	```
	*output:*
	```
	I am happy
	```
	
	```
	message = 'ABC'.join(['I', 'am', 'happy'])
	print(message)
	```
	*output:*
	```
  IABCamABChappy
	```
- The `split()` method does the opposite: It’s called on a string value and returns a list of strings.
By default, the string is split wherever <u>whitespace characters</u> such as the space, tab, or newline characters are found. 
You can pass a delimiter string to the `split()` method to specify a different string to split upon.
	```
	message = 'my name is simon'
	print(message.split('m'))
	```
	*output:*
	```
	['', 'y na', 'e is si', 'on']
	```
	
<br>

### Adding White Space to Strings
To add a new tab, use `\t`; to add a newline, use `\n`
```
print("hello\tDavid\n\tgood\tmorning")
```
*output:*
```
hello	David
	good	morning
```

<br>

### Striping White Space
Strip whitespace from the left side `.lstrip()`, from the right `.rstrip()`, both sides `.strip()`
```
name = "  Anna    "
name = name.rstrip()
print(name)
name = name.lstrip()
print(name)
```
*output:*
```
  Anna
Anna
```
&nbsp;
Optionally, a string argument will specify which characters on the ends should be stripped:
```
spam = 'SpamSpamBaconSpamEggsSpamSpam'
print(spam.strip('ampS'))
```
*output:*
```
BaconSpamEggs
```
Passing `strip()` the argument 'ampS' will tell it to strip occurences of a, m, p, and capital S <u>from both ends of the string</u> stored in spam. The order of the characters in the string passed to `strip()` does not matter: `strip('ampS')` will do the same thing as `strip('mapS')` or `strip('Spam')`.

<br>

### Justifying Text with `rjust()`, `ljust()`, and `center()`
- The `rjust()` and `ljust()` string methods return a padded version of the string they are called on, with spaces inserted to justify the text. 
	```print('hello'.rjust(10))
	print('hello'.ljust(10))
	```
	*output:*
	```
          hello
	hello  
	```
	`'hello'.rjust(10)` says that we want to right-justify 'Hello' ==in a string of total length 10==. 'Hello' is five characters, so five spaces will be added to its left, giving us a string of 10 characters with 'Hello' justified right.
	
	An optional second argument to rjust() and ljust() will <u>specify a fill character other than a space character</u>.
	```
	print('hello'.rjust(20, "*"))
	print('hello'.ljust(20, "#"))
	```
	*output:*
	```
	***************hello
	hello###############
	```
- The `center()` string method works like `ljust()` and `rjust()` but centers the text rather than justifying it to the left or right.
	```
	print('hello'.center(20, "="))
	```
	*output:*
	```
	=======hello========
	```
These methods are especially useful when you need to print tabular data that has the correct spacing:
```
picnicItems = {'sandwiches': 4, 'apples': 12, 'cups': 4, 'cookies': 8000}
def printPicnic(itemsDict, leftWidth, rightWidth):
    print('Picnic Items'.center(leftWidth + rightWidth, '-'))
    for k, v in itemsDict.items():
        print(k.ljust(leftWidth, '.') + str(v).rjust(rightWidth))
printPicnic(picnicItems, 20, 10)
```
*output:*
```
---------Picnic Items---------
sandwiches..........         4
apples..............        12
cups................         4
cookies.............      8000
```
<br>

### Copying and Pasting Strings with the pyperclip Module
The pyperclip module has `copy()` and `paste()` functions that can send text to and receive text from your computer’s clipboard. 
```
import pyperclip
print(pyperclip.paste())
```
*output:*
```
The pyperclip module ... (something currently on my clipboard)
```
How to install third - party tool: [Installing Third-Party Tools](../Python/Installing%20Third-Party%20Tools.md)
<br>

***

## Escape Characters
An escape character lets you use characters that are otherwise impossible to put into a string. An escape character consists of a <u>backslash (\) followed by the character</u> you want to add to the string.
```
message = "\"Hellen\" is her name."
print(message)
```
*output:*
```
"Hellen" is her name.
```
|Escape characters|Print as|
|-----------------|--------|
| \\' | Single quote |
| \\" | Double quote |
| \\t | Tab |
| \\n | Newline |
| \\\ | Backslash |

<br>

***

## Raw Strings
You can place an `r` before the beginning quotation mark of a string to make it a raw string. A raw string completely <u>ignores all escape characters and prints any backslash</u> that appears in the string.

Raw strings are helpful if you are typing string values that contain many backslashes.
```
message = r"\"Hellen\" is her name."
print(message)
```
*output:*
```
\"Hellen\" is her name.
```

<br>

***
## Multiline Strings with Triple Quotes
A multiline string in Python begins and ends with either <u>three single quotes</u> or <u>three double quotes</u>. Any quotes, tabs, or newlines in between the “triple quotes” are considered part of the string. 

Python’s indentation rules for blocks do not apply to lines inside a multiline string.
```
print('''Dear Alice,
Eve's cat has been arrested for catnapping, cat burglary, and extortion.
Sincerely,
Bob''')
```
*output:*
```
Dear Alice,
Eve's cat has been arrested for catnapping, cat burglary, and extortion.
Sincerely,
Bob
```
&nbsp;
### Multiline Comments
A multiline string is often used for comments that span multiple lines:
```
"""This is a test Python program.
This is a comment.
"""
```

