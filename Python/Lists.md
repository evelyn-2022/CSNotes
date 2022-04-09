# <font size='6'><center>Lists</center></font>

[toc]

## Changing, Adding, and Removing Elements

### Finding a Value in a List with the `index()` Method

When there are duplicates of the value in the list, the index of <u>its first appearance</u> is returned.
```
names = ["eric", "chris", "lora", "scarlet", "chris"]
print(names.index("chris"))
```
*output:*
```
1
```

<br>


### Modifying Elements
```
names = ["eric", "chris", "lora", "scarlet"]
print(names)
names[0] = "Jane"
print(names)
```
*output:*
```
['eric', 'chris', 'lora', 'scarlet']
['Jane', 'chris', 'lora', 'scarlet']
```

<br>

### Adding Elements to a List
- Appending elements to <u>the end of a list</u>
	```
	names = ["eric", "chris", "lora", 		"scarlet"]
	print(names.append("Rose"))

	names.append("Jack")
	print(names)
	```
	*output:*
	```
	None
	['eric', 'chris', 'lora', 'scarlet', 'Rose', 'Jack']
	```
	
	or use `+` to concatenate lists:
	
	```
	names += ["Jack"]
	```
	
- Inserting elements into a list
	```
	names = ["eric", "chris", "lora", "scarlet"]
	names.insert(4, "jack")
	print(names)
	```
	*output:*
	```
	['eric', 'chris', 'lora', 'scarlet', 'jack']
	```
	
	This is the same as:
	
	```
	names = ["eric", "chris", "lora", "scarlet"]
	names[len(names):] = ["jack"]
	```
	
<br>

### Removing Elements from a List
- If you <u>know the position</u> of the item use the `del` statement
	```
	names = ["eric", "chris", "lora", "scarlet"]
	del names[0]
	print(names)
	```
	*output:*
	```
	['chris', 'lora', 'scarlet']
	```
- The `pop()` method removes <u>the last item</u> in a list, but it lets you work with that item after removing it.
	```
	names = ["eric", "chris", "lora", "scarlet"]
	popped = names.pop()
	print(popped)
	print(names)
	```
	*output:*
	```
	scarlet
	['eric', 'chris', 'lora']
	```
	
	
	use `pop()` to remove an item from any position in a list by including <u>the index of the item</u>
	```
	names = ["eric", "chris", "lora", "scarlet"]
	popped = names.pop(2)
	print(popped)
	print(names)
	```
	*output:*
	```
	lora
	['eric', 'chris', 'scarlet']
	```
- `pop()` or `del`
when you want to delete an item from a list and <u>not use that item</u> in any way, use the del statement; 
If you want to use an item as you remove it, use the pop() method.
- Removing an Item by Value
If you only know the value of the item you want to remove, you can use the `remove()` method.
If the value appears multiple times in the list, <u>only the first instance</u> of the value will be removed.
	```
	names = ["eric", "chris", "lora", "scarlet"]
	male = "eric"
	names.remove(male)
	print(names)
	```
	*output:*
	```
	['chris', 'lora', 'scarlet']
	```
	
<br>

***

## Organizing a List

### Sorting a List <u>Permanently</u> with the `sort()` Method
Sort in reverse alphabetical order (`reverse=True`)
```
names = ["eric", "chris", "lora", "scarlet"]
names.sort()
print(names)
names.sort(reverse=True)
print(names)
```
*output:*
```
['chris', 'eric', 'lora', 'scarlet']
['scarlet', 'lora', 'eric', 'chris']
```
To sort the values in regular alphabetical order, pass `str.lower` for the ==key keyword argument==:
```
lis = ['D', 'a', 'z', 'm', 'n', 'B']
print(sorted(lis))
print(sorted(lis, key=str.lower))
```
*output:*
```
['B', 'D', 'a', 'm', 'n', 'z']
['a', 'B', 'D', 'm', 'n', 'z']
```
<br>

### Sorting a List <u>Temporarily</u> with the `sorted()` Function
```
names = ["eric", "chris", "lora", "scarlet"]
print(sorted(names, reverse=True) )
```
*output:*
```
['scarlet', 'lora', 'eric', 'chris']
```

<br>

### Reversing order permanently `.reverse()`
```
names = ["eric", "chris", "lora", "scarlet"]
names.reverse()
print(names)
```
*output:*
```
['eric', 'chris', 'lora', 'scarlet']
```

<br>

### Finding the Length of a List `len()`
```
names = ["eric", "chris", "lora", "scarlet"]
print(len(names))
```
*output:*
```
4
```

<br>

***

## Working With Part of a List

### Slicing a list
```
names = ["eric", "chris", "lora", "scarlet"]
print(names[-3:])
```
*output:*
```
['chris', 'lora', 'scarlet']
```

<br>

### Copying a list

#### Copying without changing original one using slicing
```
names = ["eric", "chris", "lora", "scarlet"]
guests = names[:]
print(guests)
```
*output:*
```
['eric', 'chris', 'lora', 'scarlet']
```
<br>

#### Creating an alias of original list
When you assign a list to a variable, you are actually assigning ==a list reference== to the variable. A reference is <u>a value that points to some bit of data</u>, and a list reference is a value that points to a list.

<center><img src="https://i.loli.net/2021/11/26/GjZWa4YD7Q3zdkH.png"  title='copying_a_list_1.png' width='260' /></center>

```
spam = ["eric", "chris", "lora", "scarlet"]
cheess = spam
cheese.append("Jane")
print(spam)
```
*output:*
```
['eric', 'chris', 'lora', 'scarlet', 'Jane']
```
Then the reference in spam is copied to the variable cheese. <u>Only a new reference was created and stored in cheese</u>, <u>not a new list</u>. Note how both references refer to the same list.

<center><img src="https://i.loli.net/2021/11/26/ONh3y59bQcRtBdG.png"  title='copying_a_list_2.png' width='260' /></center>

When you alter the list that cheese refers to, the list that spam refers to is also changed, because both cheese and spam <u>refer to the same list</u>.

> **Mutable data types**(lists or dictionaries): uses <u>references</u> to list values; 
> **Immutable data types**(strings, integers, or tuples): store <u>the value itself</u>.

<br>

#### The copy Module’s `copy()` and `deepcopy()` Functions
`copy()` can be used to make a duplicate copy of a <u>mutable value</u> like a list or dictionary, <u>not just a copy of a reference</u>: 

<center><img src="https://i.loli.net/2021/11/26/i8YgQFKsyNSHPDf.png"  title='copying_a_list_3.png' width='260' /></center>

```
import copy

spam = ["A", "B", "C", "D"]
cheese = copy.copy(spam)
cheese [1] = 42
print(cheese)
print(spam)
```
*output:*
```
['A', 42, 'C', 'D']
['A', 'B', 'C', 'D']
```

Now the spam and cheese variables <u>refer to separate lists</u>, which is why only the list in cheese is modified when you assign 42. As you can see in figure, <u>the reference ID numbers are no longer the same</u> for both variables because the variables refer to independent lists.

<br>

#### `deepcopy()` function
If the list you need to copy contains lists, then use the `copy.deepcopy()` function instead of `copy.copy()`. The deepcopy() function will <u>copy these inner lists</u> as well.

<br>

***

## ==List Comprehension==

```
squares = [value**2 for value in range(1, 5)]
print(squares)
```
*output:*
```
[1, 4, 9, 16]
```

<br>

***

## Exceptions to Indentation Rules in Python

<u>Lists can span several lines</u> in the source code file. The indentation of these lines do not matter; Python knows that until it sees the ending square bracket, the list is not finished. 

```
spam = ['apples',
        'oranges',
        'bananas',
        'cats']
print(spam)
```
*output:*
```
['apples', 'oranges', 'bananas', 'cats']
```

You can also <u>split up a single instruction</u> across multiple lines using the `\` line continuation character at the end.
```
print("apples" + \
      "oranges" + \
      "bananas")
```
*output:*
```
applesorangesbananas
```