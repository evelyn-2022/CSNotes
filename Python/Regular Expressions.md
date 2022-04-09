# <font size='6'><center>Regular Expressions</center></font>

[toc]

## <font color='BCA1E3'>Regular Expression Matching</font>
- All the regex functions in Python are in the `re` module;
- Passing a string value representing your regular expression to `re.compile()`
returns a Regex pattern object (or simply, a **Regex object**);
- A Regex object’s `search()` method searches the string it is passed for any matches to the regex. The `search()` method will return <u>*None*</u> if the regex pattern is not found in the string. If the pattern is found, the search() method returns a **Match object**.

```
import re

phoneNumRegex = re.compile(r'\d\d\d-\d\d\d-\d\d\d\d')
mo = phoneNumRegex.search('My number is 415-555-4242.')
print(mo)
```
*output:*
```
<re.Match object; span=(13, 25), match='415-555-4242'>
```
Match objects have a `group()` method that will <u>*return the actual matched text*</u> from the searched string.
```
--snip--
print(mo.group())
```
*output:*
```
415-555-4242
```

<br>

***

## <font color='BCA1E3'>Grouping with Parentheses</font>

- Adding *parentheses* will create groups in the regex;
- The first set of parentheses in a regex string will be <u>*group 1*</u>. The second set will be <u>*group 2*</u>. Passing <u>*0 or nothing*</u> to the group() method will <u>*return the entire matched text*</u>.
```
import re

phoneNumRegex = re.compile(r'(\d{3})-(\d{3}-\d{4})')
mo = phoneNumRegex.search('My number is 415-555-4242.')

print(mo.group(1))
print(mo.group(2))
print(mo.group(0))
```
*output:*
```
415
555-4242
415-555-4242
```

If you only need to return true when a particular substring exists:

```
if re.search(r'(\d{3})-(\d{3}-\d{4})', text):
```
If you would like to retrieve all the groups at once, use the `groups()` method—note the *plural form* for the name.
```
print(mo.groups(0))
```
*output:*
```
('415', '555-4242')
```

Since `mo.groups()` returns a tuple of multiple values, you can use the <u>*multiple-assignment*</u> trick to assign each value to a separate variable:
```
area_code, main_number = mo.groups()
print(area_code)
print(main_number)
```
*output:*
```
415
555-4242
```


<br>

***

## <font color='BCA1E3'>the Pipe</font>

The `|` character is called a pipe. You can use it anywhere you want to match one
of many expressions. When more than one occur in the searched string, <u>*the first occurrence of matching text*</u> will be returned as the Match object.

```
import re

hero_regex = re.compile(r'Batman|Tina Fei')
mo = hero_regex.search('Tina Fey and Batman.')
print(mo.group())
```
*output:*
```
Batman
```

You can also use the pipe to match one of several patterns as part of your regex.
For example, say you wanted to match any of the strings 'Batman', 'Batmobile', 'Batcopter', and 'Batbat'. Since all these strings start with Bat, it would be nice if you could specify that prefix only once.
```
import re

batRegex = re.compile(r'Bat(man|mobile|copter|bat)')
mo = batRegex.search('Batmobile lost a wheel')
print(mo.group())
print(mo.group(1))
```
*output:*
```
Batmobile
mobile
```


<br>

***

## <font color='BCA1E3'>Optional Matching</font>

### Matching with Question Mark

The `?` character flags the group that precedes it as an optional part of the pattern:
```
import re

batRegex = re.compile(r'Bat(wo)?man')
mo1 = batRegex.search('The Adventures of Batman')
print(mo1.group())

mo2 = batRegex.search('The Adventures of Batwoman')
print(mo2.group())
```
*output:*
```
Batman
Batwoman
```

<br>

### Matching Zero or More with the Star `*`

```
batRegex = re.compile(r'Bat(wo)*man')
mo1 = batRegex.search('The Adventures of Batman')
print(mo1.group())

mo2 = batRegex.search('The Adventures of Batwowowowoman')
print(mo2.group())
```
*output:*
```
Batman
Batwowowowoman
```

<br>

### Matching One or More with the Plus `+`

```
batRegex = re.compile(r'Bat(wo)+man')
mo1 = batRegex.search('The Adventures of Batman')
print(mo1)

mo2 = batRegex.search('The Adventures of Batwowowowoman')
print(mo2.group())
```
*output:*
```
None
Batwowowowoman
```

<br>

***

## <font color='BCA1E3'>Repetitions with Curly Brackets</font>

- If you have a group that you want to repeat a specific number of times, follow the group in your regex with a number in curly brackets. For example, the regex `(Ha){3}` will match the string `HaHaHa`, but it will not match `HaHa`.
- You can specify a range by writing <u>*a minimum, a comma, and a maximum*</u> in between the curly brackets. For example, the regex `(Ha){3,5}` will match `HaHaHa`, `HaHaHaHa`, and `HaHaHaHaHa`.
- You can also leave out the first or second number in the curly brackets to <u>*leave the minimum or maximum unbounded*</u>. For example, `(Ha){3,}` will match three or more instances of the (Ha) group, while `(Ha){,5}` will match zero to five instances.

<br>

***

## <font color='BCA1E3'>Greedy and Nongreedy Matching</font>

Python’s regular expressions are **greedy by default**, which means that in ambiguous situations they will match the longest string possible. The nongreedy version of the curly brackets, which matches the shortest string possible, has the closing curly bracket **followed by a question mark**.
[Greedy vs Non-greedy](../Python/Greedy%20vs%20Non-greedy.md)
```
batRegex = re.compile(r'(Ha){3,5}')
mo1 = batRegex.search('HaHaHaHaHa')
print(mo1.group())

batRegex = re.compile(r'(Ha){3,5}?')
mo2 = batRegex.search('HaHaHaHaHa')
print(mo2.group())
```
*output:*
```
HaHaHaHaHa
HaHaHa
```

*Note that the question mark can have two meanings in regular expressions: declaring a nongreedy match or flagging an optional group. These meanings are entirely unrelated.*

<br>

***

## <font color='BCA1E3'>The `findall()` Method</font>


While `search()` will return a **Match object** of the first matched text in the searched string, the `findall()` method will return **a list of strings** (if there are no groups in the regular expression) or **a list of tuples** (if there are groups) of every match in the searched string:
```
phoneNumRegex = re.compile(r'\d{3}-\d{3}-\d{4}')
mo1 = phoneNumRegex.findall('Cell: 415-555-9999 Work: 212-555-0000')
print(mo1)

phoneNumRegex = re.compile(r'(\d{3})-(\d{3}-\d{4})')
mo2 = phoneNumRegex.findall('Cell: 415-555-9999 Work: 212-555-0000')
print(mo2)
```
*output:*
```
['415-555-9999', '212-555-0000']
[('415', '555-9999'), ('212', '555-0000')]
```

<br>

***

## <font color='BCA1E3'>Character Classes</font>

### Shorthand Character Classes

|Shorthand character class|Represents|
|-------------------------|----------|
| \d | 0 - 9 |
| \D | Any character that is not a numeric digit|
| \w | Any letter, numeric digit, or the underscore character.(Think of this as matching “word” characters.)|
| \W | Any character that is not a letter, numeric digit, or the underscore character. |
| \s | Any space, tab, or newline character. (Think of this as matching “space” characters.) |
| \S | Any character that is not a space, tab, or newline. |

<br>

### Making Your Own Character Classes

- You can include ranges of letters or numbers by using a hyphen. For example, the character class [a-zA-Z0-9] will match all lowercase letters, uppercase letters, and numbers.
Note that inside the square brackets, the normal regular expression symbols are not interpreted as such. This means you <u>do not need to escape the ., *, ?, or () characters with a preceding backslash</u>. For example, the character class [0-5.] will match digits 0 to 5 and <u>*a period*</u>.
- By placing a caret character `^` just after the character class’s opening bracket, you can make a **negative character class**. A negative character class will match all the characters that are not in the character class.
```
consonantRegex = re.compile(r'[^aeiouAEIOU .]')
print(consonantRegex.findall('RoboCop eats baby food. BABY FOOD.'))
```
*output:*
```
['R', 'b', 'C', 'p', 't', 's', 'b', 'b', 'y', 'f', 'd', 'B', 'B', 'Y', 'F', 'D']
```

<br>

***

## <font color='BCA1E3'>The Caret `^` and Dollar Sign `$` Characterss</font>

- You can use the caret symbol `^` at the start of a regex to indicate that a match must occur **at the beginning** of the searched text. Likewise, you can put a dollar sign `$` at the end of the regex to indicate the string must **end with** this regex pattern. 
- You can use the `^` and `$` together to indicate that the ***entire string must match the regex***—that is, it’s not enough for a match to be made on some subset of the string.
```
wholeStringIsNum = re.compile(r'^\d+$')
print(wholeStringIsNum.search('1234567890'))
print(wholeStringIsNum.search('12345xyz67890'))
print(wholeStringIsNum.search('12 34567890'))
```
*output:*
```
<re.Match object; span=(0, 10), match='1234567890'>
None
None
```

<br>

***

## <font color='BCA1E3'>The Wildcard `.` Character</font>

The `.` (or dot) character in a regular expression is called a **wildcard** and will match any character **except for a newline**.
```
atRegex = re.compile(r'.at')
print(atRegex.findall('The cat in the hat sat on the flat mat.'))
```
*output:*
```
['cat', 'hat', 'sat', 'lat', 'mat']
```
Remember that the dot character will match just one character, which is why the match for the text flat in the previous example matched only lat. 

<br>

### Matching Everything with Dot-Star `.*`
The dot-star will match everything except a newline.
```
nongreedyRegex = re.compile(r'<.*?>')   # non-greedy
# wrong: ......= re.compile(r'<.*>?')
mo = nongreedyRegex.search('<To serve man> for dinner.>')
print(mo.group())
greedyRegex = re.compile(r'<.*>')   # greedy
mo = greedyRegex.search('<To serve man> for dinner.>')
print(mo.group())
```
*output:*
```
<To serve man>
<To serve man> for dinner.>
```

<br>

### Matching Newlines with the Dot Character `re.DOTALL`
The dot-star will match everything except a newline. By passing `re.DOTALL` as the second argument to `re.compile()`, you can make the dot character match all characters, including the newline character:
```
newlineRegex = re.compile('.*', re.DOTALL)
print(newlineRegex.search('Serve the public trust.\nProtect the innocent.\nUphold the law.').group())
```
*output:*
```
Serve the public trust.
Protect the innocent.
Uphold the law.
```

<br>

***

## <font color='BCA1E3'>Case-Insensitive Matching `re.I`</font>

To make your regex case-insensitive, you can pass `re.IGNORECASE` or `re.I` as a second argument to `re.compile()`.

```
robocop = re.compile(r'robocop', re.I)
print(robocop.search('RoboCop is part man, part machine, all cop.').group())
```
*output:*
```
RoboCop
```

<br>

***

## <font color='BCA1E3'>Substituting Strings with the `sub()` Method</font>

The `sub()` method for Regex objects is passed two arguments. The first argument is a string to replace any matches. The second is the string for the regular expression. The `sub()` method returns a string with the substitutions applied.
```
agentNamesRegex = re.compile(r'Agent \w*')
agentNamesRegex = agentNamesRegex.sub('####', 'Agent Alice told Agent Carol that Agent Eve knew Agent Bob was a double agent.')
print(agentNamesRegex)
```
*output:*
```
#### told #### that #### knew #### was a double agent.
```

Sometimes you may need to use the matched text itself as part of the substitution. In the first argument to `sub()`, you can type \1, \2, \3, and so on, to mean “Enter the text of group 1, 2, 3, and so on, in the substitution.”
```
agentNamesRegex = re.compile(r'Agent (\w)(\w)\w*')
agentNamesRegex = agentNamesRegex.sub(r'\1\2****', 'Agent Alice told Agent Carol that Agent Eve knew Agent Bob was a double agent.')
print(agentNamesRegex)
```
*output:*
```
Al**** told Ca**** that Ev**** knew Bo**** was a double agent.
```
The `\1` in that string will be replaced by whatever text was matched by group 1, group 2—that is, the `(\w)(\w)` groups of the regular expression.

<br>

***

## <font color='BCA1E3'>Managing Complex Regexes `re.VERBOSE`</font>

Regular expressions are fine if the text pattern you need to match is simple. But matching complicated text patterns might require long, convoluted regular expressions. You can mitigate this by telling the `re.compile()` function to **ignore whitespace and comments <u>inside the regular expression string</u>**. This “verbose mode” can be enabled by passing the variable `re.VERBOSE` as the second argument to `re.compile()`.

```
phoneRegex = re.compile(r'''(
	(\d{3}|\(\d{3}\))?              # area code
	(\s|-|\.)?                      # separator
	\d{3}                           # first 3 digits
	(\s|-|\.)                       # separator
	\d{4}                           # last 4 digits
	(\s*(ext|x|ext.)\s*\d{2,5})?    # extension
	)''', re.VERBOSE)
 ```

<br>

***

## <font color='BCA1E3'>Combining` re.I`, `re.DOTALL`, and `re.VERBOSE`</font>

Unfortunately, the `re.compile()` function takes only *<u>a single value as its second argument</u>*. You can get around this limitation by combining the `re.IGNORECASE`, `re.DOTALL`, and `re.VERBOSE` variables using the pipe character `|`, which in this context is known as the [bitwise operator](https://wiki.python.org/moin/BitwiseOperators).
```
someRegexValue = re.compile('foo', re.IGNORECASE | re.DOTALL | re.VERBOSE)
```

<br>

***

## <font color='BCA1E3'>Project</font>

### Strong Password Detection
Write a function that uses regular expressions to make sure the password string it is passed is strong. A strong password is defined as one that is at least eight characters long, contains both uppercase and lowercase characters, and has at least one digit. You may need to test the string against multiple regex patterns to validate its strength.
[valid_password.py](https://gitee.com/riding-a-bucket/python_work/blob/python_learning/regular_expression/valid_password.py)

<br>

### Regex Version of strip()
Write a function that takes a string and does the same thing as the `strip()` string method. If no other arguments are passed other than the string to strip, then whitespace characters will be removed from the beginning and end of the string. Otherwise, the characters specified in the second argument to the function will be removed from the string.
[def_strip.py](https://gitee.com/riding-a-bucket/python_work/blob/python_learning/regular_expression/def_strip.py)