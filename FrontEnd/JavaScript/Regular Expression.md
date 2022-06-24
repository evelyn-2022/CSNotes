# Regular Expression

## Test a regex `.test()`

One way to test a regex is using the `.test()` method. The `.test()` method takes the regex, applies it to a string (which is placed inside the parentheses), and _returns true or false_ if your pattern finds something or not.

```js
let testStr = "freeCodeCamp";
let testRegex = /Code/;
testRegex.test(testStr);
```

## Extract match `.match()`

```js
"Hello, World!".match(/Hello/);
```

==Note:== the .match syntax is _the "opposite" of_ the .test method you have been using thus far.

To search for more than one patterns, use `|`:

```js
/yes|no|maybe/;
```

## Flags

- `i` flag: to ignore cases, e.g., `/ignorecase/i`
- `g` flag: to search or extract a pattern _more than once_

## Wild card

You can use the wildcard character just like any other character in the regex. For examplem, if you wanted to match hug, huh, hut, and hum, you can use the regex `/hu./`

## Character Classes

You can search for a literal pattern with some flexibility with character classes. Character classes allow you to define _a group of characters_ you wish to match by placing them inside square (`[ and ]`) brackets. For example, you want to match bag, big, and bug but not bog. You can create the regex `/b[aiu]g/` to do this.

use a `-` to match a large range of characters. For example, to match lowercase letters a through e you would use `[a-e]`. It also works to match a range of numbers. Also, it is possible to combine a range of letters and numbers in a single character set: `/[a-z0-9]/`.

## negated character sets

To create a negated character set, you place a caret character (`^`) **after the opening bracket** and before the characters you do not want to match. For example, `/[^aeiou]/gi` matches all characters that are not a vowel.

## Match beginning string pattern

**Outside of a character set**, the caret `^` is used to search for patterns at the beginning of strings.

## Matching ending

You can search the end of strings using the dollar sign character `$` at the end of the regex.

## Match items that occur one / zero or more times

### One or more

You can use the `+` character to check if an item occurs **one or more** times. Remember, the character or pattern has to be _present consecutively_.
For example, `/a+/g` would find one match in 'abc' and return ["a"], in 'aabc' it will return ["aa"]. In 'abab', it would find two matches and return ["a", "a"].

### Zero or more

Use `*`

## Greedy and lazy match

A ++greedy match++ finds the _longest_ possible part of a string that fits the regex pattern and returns it as a match; a ++lazy match++, which finds the _smallest_ possible part of the string that satisfies the regex pattern.

You can apply the regex `/t[a-z]*i/` to the string "titanic". Regular expressions are by default greedy, so the match would return `["titani"]`. However, you can use the `?` character to change it to lazy matching. "titanic" matched against the adjusted regex of `/t[a-z]*?i/ `returns `["ti"]`.

## Shortcut

- `\w`: equal to `[A-Za-z0-9_]`. This character class matches upper and lowercase letters plus numbers. Note, this character class also includes the underscore character (`_`).

- `\W`: same as `[^A-Za-z0-9_]`

- `\d\`: look for digit characters, equal to the character class `[0-9]`
- `\D`: match All Non-Numbers, equal to the character class `[^0-9]`
- `\s`: matches whitespace, return, tab, form feed, and new line characters, similar to `[ \r\t\f\n\v]`.
- `\S`: matches non-whitespaces

## Quantity specifiers

Quantity specifiers are used with curly brackets ({ and }). You put two numbers between the curly brackets - for the lower and upper number of patterns. For example, to match only the letter a appearing between 3 and 5 times in the string ah, your regex would be `/a{3,5}h/`. To only specify **the lower number of patterns**, keep the first number followed by a comma. To specify **a certain number of patterns**, just have that one number between the curly brackets.

## Possible existence

You can specify the possible existence of an element with a question mark, `?`.

```js
let american = "color";
let british = "colour";
let rainbowRegex = /colou?r/;
rainbowRegex.test(american);
rainbowRegex.test(british);
```

## Lookaheads

A _positive lookahead_ will look to make sure the element in the search pattern is there, but won't actually match it. A positive lookahead is used as `(?=...)` where the ... is the required part that is not matched. A _negative lookahead_ will look to make sure the element in the search pattern is not there. A negative lookahead is used as `(?!...)` where the ... is the pattern that you do not want to be there.

A practical use of lookaheads is to check two or more patterns in one string. Here is a (naively) simple password checker that looks for between 3 and 6 characters and at least one number:

```js
let password = "abc123";
let checkPass = /(?=\w{3,6})(?=\D*\d)/;
checkPass.test(password);
```

## Check for groups of characters

Sometimes we want to check for groups of characters using a Regular Expression and to achieve that we use parentheses `()`. If you want to find either Penguin or Pumpkin in a string, you can use the following Regular Expression: `/P(engu|umpk)in/g.`

## Capture groups

### Match a string

Capture groups are constructed by enclosing the regex pattern to be captured in _parentheses_. The substring matched by the group is saved to a temporary "variable", which can be accessed within the same regex using _a backslash and the number_ of the capture group (e.g. \1). Capture groups are automatically numbered by the position of their opening parentheses (left to right), starting at 1.

Use capture groups in reRegex to match a string that consists of only the same number repeated exactly three times separated by single spaces.

```js
let repeatNum = "42 42 42";
let reRegex = /^(\d+)(\s)\1\2\1$/;
let result = reRegex.test(repeatNum);
```

### Replace a string

You can search and replace text in a string using `.replace()` on a string. The inputs for `.replace()` is first the regex pattern you want to search for. The second parameter is the string to replace the match or a function to do something.

You can also access capture groups in the replacement string with dollar signs ($).

```js
"Code Camp".replace(/(\w+)\s(\w+)/, "$2 $1"); // Output: Camp Code
```

```js
let str = "one two three";
let fixRegex = /(one)\s(two)\s(three)/;
let replaceText = "$3 $2 $1";
let result = str.replace(fixRegex, replaceText); //Output: three two one
```

## Example 1

You need to check all the usernames in a database. Here are some simple rules that users have to follow when creating their username.

Usernames can only use alpha-numeric characters.

The only numbers in the username have to be at the end. There can be zero or more of them at the end. Username cannot start with the number.

Username letters can be lowercase and uppercase.

Usernames have to be at least two characters long. A two-character username can only use alphabet letters as characters.

```js
let userCheck = /^[a-z][a-z]+\d*$|^[a-z]\d\d+$/i;

// Or
const userCheck = /^[a-z]([0-9]{2,}|[a-z]+\d*)$/i;
```

`[0-9]{2,0`} - ends with two or more numbers

## Example 2

Write a regex and use the appropriate string methods to remove whitespace at the beginning and end of strings.

```js
let hello = "   Hello, World!  ";
let wsRegex = /^\s+|\s+$/g;
let result = hello.replace(wsRegex, "");
```
