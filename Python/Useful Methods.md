# <font size='6'><center>Useful Methods</center></font>

[toc]

## <font color='BCA1E3'>`replace()` Method</font>
 
You can use the `.replace()` method to replace any word in a string with a different word. Here’s a quick example showing how to replace 'dog' with 'cat' in a sentence:
```
message = "I really like dogs."
new_message = message.replace('dog', 'cat')
print(new_message)
```
*output:*
```
I really like cats.
```
==Note: You have to assigned the replaced message to an attribute==

**Wrong way:**
```
message = "I really like dogs."
message.replace('dog', 'cat')
print(message)
```
*output:*
```
I really like dogs.
```

<br>

***

## <font color='BCA1E3'>`.split()` Method</font>

```
filename = 'Let Us Kiss and Part.txt'

with open(filename, encoding='utf-8') as f:
    contents = f.read()

words = contents.split()
print(f"Total words: {len(words)}")
```
*output:*

```
Total words: 80684
```

<br>

***

## <font color='BCA1E3'>`count()` Method</font>

```
filename = 'Let Us Kiss and Part.txt'

with open(filename, encoding='utf-8') as f:
    contents = f.read()

num_the = contents.count('the')
print(f"Number of words containing 'the': {num_the}")

num_the_The = contents.lower().count('the')
print(f"Number of words containing 'the'/'The': {num_the_The}")

num_the__ = contents.lower().count('the ')
print(f"Number of 'the'/'The' only: {num_the__}")
```
*output:*
```
Number of words containing 'the': 5009
Number of words containing 'the'/'The': 5435
Number of 'the'/'The' only: 3813
```
Count how many times the word 'the' appears in each text. This will be an approximation because it will also count words such as 'then' and 'there'. To count 'the ', <u>*add a space in the string*</u>.


