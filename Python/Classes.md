# <font size='6'><center>Classes</center></font>

[toc]

## <font color='BCA1E3'>Object-oriented Programming</font>

- In object-oriented programming, you write *<u>**classes** that represent real-world things</u>* and situations, and you create **objects** based on these classes. 

- Making an object from a class is called **instantiation**, and you work with **instances** of a class.

<br>

***

## <font color='BCA1E3'>Creating and Using a Class</font>

### The `__init__()` Method

A <u>function</u> that’s part of a class is a ***method***.

```
class Restaurant:
    """define a new restaurant class"""

    def __init__(self, restaurant_name, cuisine_type):
        self.name = restaurant_name
        self.cuisine = cuisine_type

    def describe_restaurant(self):
        print(f"{self.name.title()} offers {self.cuisine}.")
# Wrong: print(f"{name.title()} offers {cuisine}.")
    
    def open_restaurant(self):
        print(f"The restaurant is open now.")

starbucks = Restaurant("starbucks", "coffee")
print(starbucks.cuisine)   # Access an attribute
starbucks.describe_restaurant()   # Call a method
starbucks.open_restaurant()
```
==Note: 
To display attributes, use `print(instance.attribute)`, attributes *don't need parenthesis*;
To display methods, use `instance.method()`, do not use print (will get None), and methods need parenthesis.==

*output:*
```
coffee
Starbucks offers coffee.
The restaurant is open now.
```

> - Use ***capitalized name*** to define a <u>class</u>, use ***lowercase name*** to define an <u>instance</u>;
> - The two variables defined (restaurant_name, cuisine_type) each have the **prefix self**. <u>Any variable prefixed with self is available to every method in the class</u>. Variables like this are called ==*attributes*==.
> 

<br>

### Setting Default Value
When an instance is created, attributes can be defined without being passed in as parameters. These attributes can be defined in the `__init__()` method, where they are assigned a **default value**.
```
class Restaurant:

    def __init__(self, first_name, last_name):
        self.first_name = first_name
        self.last_name = last_name
        self.age = 18
		
henry = User("henry", "feehily")
print(henry.age)
```
*output:*
```
18
```

<br>

Another way to set default value: pass in as parameter:
```
class User:

    def __init__(self, first_name, last_name, age=18):
        self.first_name = first_name
        self.last_name = last_name
        self.age = age

jack = User("jack", "john")
print(jack.age)

eric = User("eric", "butler", 20)
print(eric.age)
```
*output:*
```
18
20
```

<br>

### Modifying Attribute Values

1. Modifying an Attribute’s Value Directly
	```
	class User
		--snip--
	henry = User("henry", "feehily")
	henry.age = 20
	print(henry.age)
	```
	*output:*
	```
	20
	```
	
2.  Modifying/incrementing an Attribute’s Value Through a Method
	```
	Class User
		--snip--
	
	    def growth(self, years):
	        self.age = years
	
	henry = User("henry", "feehily")
	henry.growth(20)
	print(henry.age)
	```
	*output:*
	```
	20
	```
	Or to increment / decrement:
    ```
	def growth(self, years):
		self.age += years

	henry = User("henry", "feehily")
	henry.growth(20)
	print(henry.age)
	```
	*output:*
	```
	38
	```

<br>

***

## <font color='BCA1E3'>Inheritance</font>

- The original class is called the **parent class**, and the new class is the **child class**. The child class can inherit any or all of the attributes and methods of its parent class.
- When you create a child class, the parent class must be *<u>part of the current file</u>* and must *<u>appear before the child class</u>* in the file.
```
class User
	--snip--

class Student(User):

     def __init__(self, first_name, last_name):
         super().__init__(first_name, last_name)
# Wrong: super().__init__(self, first_name, last_name)
```

The `super()` function is a special function that allows you to call a method from the parent class. Here it calls the `__init__` function.
==Note: super(), no "self"==

1. Defining Attributes and Methods for the Child Class

	add a new attribute self.school and set its initial value to NTU
	```
	class User
		--snip--

	class Student(User):

  	  def __init__(self, first_name, last_name):
	  	super().__init__(first_name, last_name)
			self.school = "NTU"
         
  	  def describe_school(self):
	  	print(f"{self.first_name.title()} comes from {self.school}.")

	henry = Student("henry", "feehily")
	henry.describe_school()
	```
	*output:*
	```
	Henry comes from NTU.
	```
2. Overriding Methods from the Parent Class
	You can override any method from the parent class that doesn’t fit what you’re trying to model with the child class. To do this, you define a method in the child class **with the same name** as the method you want to override in the parent class.
	```
    	def growth(self):
     	   print("He didn't grow old.")
	henry.growth()
	```
	*output:*
	```
	He didn't grow old.
	```
	
3. **Instances as Attributes**

	```
	class Car:
	
		def __init__(self, make, model, year):
			self.make = make
			self.model = model
			self.year = year
	
	
	class Battery:
	
		def __init__(self, battery_size=75):
			self.battery_size = battery_size
			
		def charge(self, amount):
			self.battery_size += amount
		
		def describe_battery(self):
			print(f"This car has a {self.battery_size}-kWh battery.")


	class ElectricCar(Car):
		
		def __init__(self, make, model, year):
			super().__init__(make, model, year)
			self.battery = Battery()

	my_tesla = ElectricCar('tesla', 'model s', 2019)
	my_tesla.battery = Battery(100)
	my_tesla.battery.charge(30)
	my_tesla.battery.describe_battery()
	```
	*output:*
	```
	This car has a 130-kWh battery.
	```

<br>

***

## <font color='BCA1E3'>Importing Classes</font>

The same way as modules and functions, just import the class your instance needs.

<br>

***

## <font color='BCA1E3'>Styling Classes</font>

- Class names should be written in CamelCase. To do this, **capitalize the first letter of each word in the name**, and **don’t use underscores**;
	Instance and module names should be written **in lowercase with underscores** between words.

-  Within a class you can use **one blank line between methods**, and within a module you can use **two blank lines to separate classes**.
If you need to import a module from the standard library and a module that you wrote, **place the import statement for the standard library module first**. Then **add a blank line** and the import statement for the module you wrote.

<br>

***

## <font color='BCA1E3'>Python Docstring</font>

### Use `__doc__` attribute to retrive docstring
```
class Restaurant:
    """Define a new restaurant class."""
	--snip--
print(Restaurant.__doc__)
```
*output:*
```
Define a new restaurant class.
```

<br>

### With `help()` function
```
help(Restaurant)
```
*output:*
```
Help on class Restaurant in module __main__:

class Restaurant(builtins.object)
 |  Restaurant(restaurant_name, cuisine_type)
 |  
 |  define a new restaurant class
 |  
 |  Methods defined here:
 |  
 |  __init__(self, restaurant_name, cuisine_type)
 |      Initialize self.  See help(type(self)) for accurate signature.
 |  
 |  describe_restaurant(self)
 |  
 |  open_restaurant(self)
 |  
 |  ----------------------------------------------------------------------
 |  Data descriptors defined here:
 |  
 |  __dict__
 |      dictionary for instance variables (if defined)
 |  
 |  __weakref__
 |      list of weak references to the object (if defined)
 ```
 
 <br>
 
 ***
 
 ## <font color='BCA1E3'>Exercise</font>

Add an attribute called flavors that stores a list of ice cream flavors. Write a method that displays these flavors.
```
class Restaurant:
    """define a new restaurant class"""

    def __init__(self, restaurant_name, cuisine_type):
        self.name = restaurant_name
        self.cuisine = cuisine_type

    def describe_restaurant(self):
        print(f"{self.name.title()} offers {self.cuisine}.")

    def open_restaurant(self):
        print(f"The restaurant is open now.")


class IceCreamStand(Restaurant):

    def __init__(self, restaurant_name, cuisine_type):
        super().__init__(restaurant_name, cuisine_type)
        self.flavors = ["sweet", "salty", "spicy"]

    def display_flavors(self):
        for flavor in self.flavors:
            print(flavor)

icy = IceCreamStand("icy", "ice cream")
icy.display_flavors()
```
*output:*
```
sweet
salty
spicy
```

<br>

---

Write a separate Flavors class. Move the display_flavors() method to this class. Make a Flavors instance as an attribute in the IceCreamStand class. 
```
class Restaurant:
    --snip--


class Flavors():

    def __init__(self, flavors=["sweet", "salty", "spicy"]):
        self.flavors = flavors

    def display_flavors(self):
        for flavor in self.flavors:
            print(flavor)


class IceCreamStand(Restaurant):

    def __init__(self, restaurant_name, cuisine_type):
        super().__init__(restaurant_name, cuisine_type)
        self.flavor = Flavors()


icy = IceCreamStand("icy", "ice cream")
icy.flavor.display_flavors()
```
*output:*
```
sweet
salty
spicy
```
