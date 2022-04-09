# main() in python

when we want to abstract away the functions, we can define our main function

```
def main():
    for i in range(3):
        meow()

def meow():
    print("meow")

main()
```
or you should add this at the very end of your code:

```
if __name__ == "__main__":
	main()
```

Difference between python and c:
in C, the variable declared in a loop cannot be accessed outside of the loop, but in python, as long as **it is still in the same function, the variable can be accessed outside the loop**.

