# Dictionaries

[toc]

## Modifying dictionary (add and del)

```
dic = {}
dic["color"] = "red"
dic["size"] = 5
print(dic)
```
*output:*
```
{'color': 'red', 'size': 5}
```

```
del dic["size"]
print(dic)
```
*output:*
```
{'color': 'red'}
```

<br>

***

## Format long dictionary

```
fav_lang = {
    "Jack": "python",
    "John": "C",
    "Eric": "R",
    "Steven": "Java",
    }
```
It’s good practice to include a comma after the last key-value pair as well, so you’re ready to add a new key-value pair on the next line. 

<br>

***
## Using `get()` to Access Values

```
dic = {"color": "blue", "size": 5, "speed": "slow"}
age = dic.get("age", "No value assigned")
print(age)
```
*output:*
```
No value assigned
```

<br>

***

## Looping Through a Dictionary

### Looping Through All Key-Value Pairs `.items()`

```
fav_lang = {
    "jack": "python",
    "john": "C",
    "eric": "R",
    "steven": "Java",
    }
for k, v in fav_lang.items():
    print(f"{k.title()}'s favourite language is {v}.")
```
*output:*
```
Jack's favourite language is python.
John's favourite language is C.
Eric's favourite language is R.
Steven's favourite language is Java.
```

<br>

### Looping Through Keys `.key()`

```
fav_lang = {
    "jack": "python",
    "john": "C",
    "eric": "R",
    "steven": "python",
    }
for name in fav_lang.keys():
    print(f"{name.title()}")
```
*output:*
```
Jack
John
Eric
Steven
```

looping through the keys is actually the default behavior when looping through a dictionary:

```
--snip--
if "jane" not in fav_lang:
    print("Jane, take our poll!")
```

*output:*
```
Jane, take our poll!
```

<br>

### Looping Through Values `.values()`

To see each value without repetition, we can use `set()`. 
```
fav_lang = {
    "jack": "python",
    "john": "C",
    "eric": "R",
    "steven": "python",
    }
for language in set(fav_lang.values()):
    print(f"{language.title()}"
```
*output:*
```
R
Python
C
```

You can build a **set** directly using braces and separating the elements with commas:
```
languages = {'python', 'ruby', 'python', 'c'}
print(languages)
{'python', 'c', 'ruby'}
```

<br>

### Returning a True List

The values returned by `.keys()`, `.values()`, `.items()` methods <u>*are not true lists*</u>: They cannot be modified and do not have an `append()` method. 

The `list(spam.keys())` line takes the dict_keys value returned from keys() and passes it to `list()`, which then returns a list value.

```
spam = {'color': 'red', 'age': 42}
print(spam.keys())
print(list(spam.keys()))
```
*output:*
```
dict_keys(['color', 'age'])
['color', 'age']
```

<br>

***

## The `setdefault()` Method

You’ll often have to set a value in a dictionary for a certain key only if that key does not already have a value. With `setdefault()` method, the first argument passed to the method is the key to check for, and the second argument is the value to set at that key if the key does not exist. If the key does exist, the setdefault() method <u>returns the key’s value</u>.

```
cat = {'color': 'black', 'size': 'small'}
cat.setdefault('age', 'old')
print(cat)
cat.setdefault('age', 'young')
print(cat['age'])
```
*output:*
```
{'color': 'black', 'size': 'small', 'age': 'old'}
old
```

When spam.setdefault('age', 'young') is called next, the value for that key is not changed to 'young' because spam already has a key named 'age'.

<br>

### Use setdefault or get to avoid key error
```
message = 'It was a bright cold day in April, and the clocks were striking thirteen.'
count = {}
for character in message:
    # count.setdefault(character, 0)
    # count[character] = count[character] + 1
    count[character] = count.get(character, 0) + 1
print(count)
```
*output:*
```
{'I': 1, 't': 6, ' ': 13, 'w': 2, 'a': 4, 's': 3, 'b': 1, 'r': 5, 'i': 6, 'g': 2, 'h': 3, 'c': 3, 'o': 2, 'l': 3, 'd': 3, 'y': 1, 'n': 4, 'A': 1, 'p': 1, ',': 1, 'e': 5, 'k': 2, '.': 1}
```

<br>

***

## Pretty Printing `pprint()` and `pformat()`

```
import pprint
Message = …
 --snip--
pprint.pprint(count)
```
*output:*
```
{' ': 13,
 ',': 1,
 '.': 1,
 'A': 1,
 'I': 1,
 'a': 4,
 'b': 1,
 'c': 3,
 'd': 3,
 'e': 5,
 'g': 2,
 'h': 3,
 'i': 6,
 'k': 2,
 'l': 3,
 'n': 4,
 'o': 2,
 'p': 1,
 'r': 5,
 's': 3,
 't': 6,
 'w': 2,
 'y': 1}
 ```
 
 Equivalent way:
 ```
print(pprint.pformat(count))
```