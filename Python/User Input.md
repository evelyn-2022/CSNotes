# <font size='6'><center>User Input</center></font>


Sometimes you’ll want to write a prompt that’s longer than one line. You can <u>assign your prompt to a variable</u> and pass that variable to the `input()` function.
```
prompt = "If you tell us who you are, we can personalize the messages you see."
prompt += "\nWhat is your first name? "
name = input(prompt)
print(f"\nHello, {name}!")
If you tell us who you are, we can personalize the messages you see.
What is your first name? eric

Hello, eric!
```

<br>

## Letting the User Choose When to Quit

```
prompt = "\nTell me something, and I will repeat it back to you:"
prompt += "\nEnter 'quit' to end the program. "

# first define message as an empty string, give it an initial value
message = ""  
while message != 'quit':
    message = input(prompt)
    print(message)
```