## <font color='BCA1E3'>Multiple Assignment</font>

```
x, y, z = 1, 2, 3
print(y)
print(z)
```
*output:*
```
2
3
```
Also works in a list
```
cat = ["grey", "young", "little"]
color, age, size = cat
print(age)
```
*output:*
```
young
```

<br>

***

## <font color='BCA1E3'>Constants</font>
Python programmers use <u>all capital letters</u> to indicate a variable should be treated as a constant and never be changed.
```
MAX_CONNECTIONS = 5000
```

<br>

***

## <font color='BCA1E3'>Boolean Operators</font> 
`and`, `or`, `not`
```
print(not 2 + 2 == 5)
```
*output:*
```
True
```

<br>

***

## <font color='BCA1E3'>Boolean Expression</font> 

When the name of a list is used in an if statement, Python <u>returns True if the list contains at least one item</u>; **an empty list evaluates to False** (same in while loop)

```
requested_toppings = []
if requested_toppings:
    for requested_topping in requested_toppings:
        print(f"Adding {requested_topping}.")
        print("\nFinished making your pizza!")
else:
    print("Are you sure you want a plain pizza?")
Are you sure you want a plain pizza?
```