# Functions

[toc]

## Defining a Function
```
def greet_user():
    """Display a simple greeting."""
	   # docstring: describes what the function does, enclosed in triple quotes
    print("Hello!")
greet_user()   # call the function
```
*output:*
```
Hello!
```

<br>

###  **Parameter** and **Argument**
```
def greet_user(name):   # parameter: name
    """Display a simple greeting."""
    print(f"Hello, {name.title()}!")
greet_user("eric")   # argument: "eric"
```
*output:*
```
Hello, Eric!
```

<br>

### Default parameter

```
def hello(to='world'):
	print('hello,', to)
```

### Passing arguments
1. Positional argument
match each argument in the function call with a parameter in the function definition based on the order:
	```
	def user_info(name, age):
		print(f"{name.title()} is {age} years old.")
	user_info("eric", 18)
	```
	*output:*
	```
	Eric is 18 years old.
	```

2. Keyword argument
	```
	def user_info(name, age):
	    print(f"{name.title()} is {age} years old.")
	user_info(age=18, name="eric")
	```
	
	<br>
	
	*Default value*
	```
	def user_info(name, age=18):
	    print(f"{name.title()} is {age} years old.")
	user_info("eric")
	user_info("jane", 20)
	```
	*output:*
	```
	Eric is 18 years old.
	Jane is 20 years old.
	```
	
> - If you specify a default value for a parameter, **no spaces** should be used on either side of the equal sign;
> - When you use default values, any parameter with a default value needs to be listed **after** all the parameters that don’t have default values.

<br>

***

## Return Value

```
def full_name(first, last, middle=""):   # make the argument "middle" optional
    if middle:
        name = f"{first} {middle} {last}"
    else:
        name = f"{first} {last}"

    return name   # once it reaches "return", the function ends there

actor = full_name("erik", "Destler")   
# When you call a function that returns a value, 
# you need to provide a variable that the return value can be assigned to.
print(actor)

```
*output*
```
Erik Destler
```

<br>

***

## Modifying a List in a Function

When you pass a list to a function, the function can modify the list. Any changes made to the list inside the function’s body are **permanent**.

```
def get_guests(unprocessed, processed):
    while unprocessed:
        processing = unprocessed.pop()
        processed.append(processing)


def print_guests(processed):
    for name in processed:
        print(f"invite {name.title()} to dinner")

unprocessed = ["eric", "jane", "marie"]
processed = []

get_guests(unprocessed, processed)
print_guests(processed)
```
*output:*
```
invite Marie to dinner
invite Jane to dinner
invite Eric to dinner
```
To prevent the function from modifying a list, pass the function a copy of original list
`get_guests(unprocessed[:], processed)`

> If your program or module has <u>more than one function</u>, you can separate each by **two blank lines** to make it easier to see where one function ends and the next one begins.

<br>

***

## Passing an Arbitrary Number of Arguments

`*` tells Python to make an **empty ==tuple==** called toppings and pack whatever values it receives into this tuple.
```
def make_pizza(*toppings):
    print(toppings)

make_pizza("mushroom")
make_pizza("mushroom", "extra cheese", "green pepper")
```
*output:*
```
('mushroom',)
('mushroom', 'extra cheese', 'green pepper')
```

<br>

### Mixing Positional and Arbitrary Arguments
The parameter that accepts an arbitrary number of arguments must *<u>be placed last</u>* in the function definition. Python matches positional and keyword arguments first and then collects any remaining arguments in the final parameter.
```
def make_pizza(size, *toppings):
    print(f"Make a {size} inch pizza with the following toppings: ")
    for topping in toppings:
        print(f"-{topping}")

make_pizza(20, "mushroom", "extra cheese", "green pepper")
# assign the first value it receives to the parameter size. 
# All other values that come after are stored in the tuple toppings.
```
*output:*
```
Make a 20 inch pizza with the following toppings: 
-mushroom
-extra cheese
-green pepper
```

<br>

### Using Arbitrary Keyword Arguments
`**` cause Python to create an **empty ==dictionary==** and pack whatever name-value pairs it receives into this dictionary:
```
def get_profile(first, last, **user_info):
    user_info["first_name"] = first
    user_info["last_name"] = last
    return user_info

Jimmy = get_profile("Jimmy", "Page",
                    height=186,
                    fav_color="blue")
print(Jimmy)
```
*output:*
```
{'height': 186, 'fav_color': 'blue', 'first_name': 'Jimmy', 'last_name': 'Page'}
```

<br>

***

## Storing Your Functions in Modules

A module is a file ending in **.py** that contains the code you want to import into your program. e.g. you can store your function make_pizza() in a file pizza.py

Now we create another file to make pizza in the same directory as pizza.py
1. Importing an <u>Entire Module</u>
	```
	import pizza
	
	pizza.make_pizza(16, 'pepperoni')
	```
	The line `import pizza` tells Python to open the file *<u>pizza.py</u>* and copy all the functions from it into this program. To call a function from an imported module, enter **the name of the <u>*module*</u> you imported**, pizza, **followed by the name of the *<u>function</u>***, `make_pizza()`, separated by a dot.

2. Importing <u>All Functions in a Module</u>
	```
	from pizza import *
	```
	The `*` in the import statement tells Python to copy every function from the module pizza into this program file. Because every function is imported, you can call each function by name **without using the dot notation**. 
	
	- However, it’s best not to use this approach when you’re working with larger modules that you didn’t write;
	- The best approach is to import the function or functions you want, or import the entire module and use the dot notation.
3. Importing <u>Specific Functions</u>
	
	- *from module_name import function_name*
	- *from module_name import function_0, function_1, function_2*
	```
	from pizza import make_pizza
	make_pizza(16, 'pepperoni')
	```
	You **don’t need to use the dot notation** when you call a function, because we’ve explicitly imported the function make_pizza() in the import statement
4. Using `as` to Give a Function/Module an Alias
	- *from module_name import function_name as fn*
	- *import module_name as mn*
	```
	from pizza import make_pizza as mp
	mp(16, 'pepperoni')
	```
	
	```
	import pizza as p
	p.make_pizza(16, 'pepperoni')
	```
	
<br>
	
***
	
## Styling Functions
	
- Functions should have *descriptive names*, and these names should use **lowercase letters and underscores**;
- Every function should have a *comment* that explains concisely what the function does;
- All *import statements* should be written <u>*at the beginning of a file*</u>;
- If there's a set of long parameters, *<u>press enter after the opening parenthesis on the definition line</u>*;
	On the next line, *<u>press tab twice</u>* to separate the list of arguments from the body of the function, which will only be indented one level. 
	
	```
	def function_name(
			parameter_0, parameter_1, parameter_2,
			parameter_3, parameter_4, parameter_5):
		function body...
	```

<br>

***

## Local and Global Variables

### Global Variables Can Be Read from a Local Scope
Since there is no parameter named eggs or any code that assigns eggs a value in the spam() function, when eggs is used in spam(), Python <u>considers it a reference to the global variable eggs</u>:
```
def spam():
    print(egg)

egg = 100
spam()
```
*output:*
```
100
```
In contrast, error happens when Python sees that there is an assignment statement for eggs in the spam() function and therefore considers eggs to be local. But because *<u>print(eggs) is executed before eggs is assigned anything</u>*, the local variable eggs doesn’t exist.
```
def spam():
    print(egg)
    egg = 0

egg = 100
spam()
```
*output:*
```
UnboundLocalError: local variable 'egg' referenced before assignment
```

<br>

### If you need to *<u>modify a global variable from within a function</u>*, use the global statement:
```
def spam():
    global egg
    egg = "0"

egg = 100
print(egg)
spam()
print(egg)
```
*output:*
```
100
0
```

