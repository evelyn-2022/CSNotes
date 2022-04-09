# <font size='6'><center>Useful Functions</center></font>

[toc]

## <font color='BCA1E3'>`range()` Function</font>

### One Argument
```
for i in range(2):
    print(i)
```
*output:*
```
0
1
```

<br>

### Two Arguments

```
lis = list(range(1, 5))
print(lis)
```
*output:*
```
[1, 2, 3, 4]
```

<br>

### Three Arguments

If you pass a third argument to `range()`, Python uses that value as a <u>step size</u> when generating numbers.

```
even_numbers = list(range(2, 10, 2))
print(even_numbers)
```
*output:*
```
[2, 4, 6, 8]
```

<br>

***

## <font color='BCA1E3'>`min()`, `max()`, `sum()` Functions</font>

```
even_numbers = list(range(2, 10, 2))
print(min(even_numbers))
print(max(even_numbers))
print(sum(even_numbers))
```
*output:*
```
2
8
20
```

<br>

***

## <font color='BCA1E3'>`print()` Function</font>

`print()` is a function that returns `None`:
```
print(print("a"))
```
*output:*
```
a
None
```

<br>

### Optional parameters:
	print(...)
		print(value, ..., sep=' ', end='\n', file=sys.stdout, flush=False)
1. `end=`
	`print()` function automatically **adds a newline character** to the end of the string it is passed. However, you can set the end keyword argument to change this.
	```
	print('Hello', end='')
	print("There")
	```
	*output:*
	```
	HelloThere
	```
2. `sep=`
	When you pass multiple string values to `print()`, the function will automatically **separate them with a single space**:
	```
	print("cat", "dog", "owl")
	```
	*output:*
	```
	cat dog owl
	```
	You could replace the default separating string by passing the sep keyword argument:
	```
	print("cat", "dog", "owl", sep="+")
	```
	*output:*
	```
	cat+dog+owl
	```
	
