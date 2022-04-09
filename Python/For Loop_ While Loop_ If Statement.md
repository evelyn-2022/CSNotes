
[toc]

## For Loop

```
names = ["eric", "chris", "lora", "scarlet"]
for name in names:
    print(name)
```
*output:*
```
eric
chris
lora
Scarlet
```

If we don't need the value in for loop, we can use _ instead:
```
for _ in range(4):
	print('meow')
```

<br>

***

## While Loop

### Using a Flag
For a program that should run only as long as many conditions are true, you can <u>*define **one variable** that determines whether or not the entire program is active*</u>. This variable, called a ==flag==, acts as a signal to the program. We can write our programs so they run while the flag is set to True and stop running when any of several events sets the value of the flag to False.
```
active = True
while active:
    message = input("enter a number: ")

    if message =="quit":
        active = False
    elif message == "out":
        active = False

    if message != "quit" and message != "out":
        print(f"the number you entered is {message}")
```
*output:*
```
enter a number: 4
the number you entered is 4
enter a number: quit
```

### Test valid input

```
while True:
	n = int(input("What's n?"))
	if n > 0:
		break
```

<br>

### Using `break` to exit a loop
Exit a loop immediately without running any remaining code in the loop.
You can use the `break` statement in any of Python’s loops (e.g. for loop)

<br>

### Using `continue` in a Loop
To <u>*return to the beginning of the loop*</u> based on the result of a conditional test (This is also what happens when the execution reaches the end of the loop.)

> Note: 
> You can use `break` and `continue` statements inside for loops as well. The continue statement will continue <u>*to the next value of the for loop’s counter*</u>, as if the program execution had reached the end of the loop and returned to the start.

<br>

### Trapped in an Infinite Loop
If you ever run a program that has a bug causing it to get stuck in an infinite loop, press **ctrl-C**. This will send a <u>*KeyboardInterrupt error*</u> to your program and cause it to stop immediately.

<br>

***

## If Statement

### Checking Whether a Value Is in a List `in` / `not in`

```
names = ["eric", "chris", "lora", "scarlet"]
print("eric" in names)
```
*output:*
```
True
```

```
names = ["eric", "chris", "lora", "scarlet"]
if "jane" not in names:
    print("not jane")
```
*output:*
```
not jane
```

<br>

### if-elif-else
```
age = 10
if age >= 18:
    print("adult")
elif age >= 16:
    print("adolescent")
else:
    print("child")
child
```

### Conditionals

In C:

```
char var = get_char();
bool alphabetic = isalpha(var) ? true : false;
```

In Python:

```
letters_only = True if input().isalpha() else False
```

### Ternary operator / Conditional expressions

```
def is_even(n):
	return True if n % 2 == 0 else False
	
	// A more pythonic way here:
	return n % 2 == 0
```