# <font size='6'><center>Greedy vs Non-greedy</center></font>

Lets see an example considering HTML snippet - `<p>Hello</p><span>Awesome</span><p>World</p>`. Our task is to extract first p tag. i.e pattern matching should return `<p>Hello</p>`.

Immediate solution is to write regex - `r'<p>.*</p>'`. But it would match the whole string.

## <font color='BCA1E3'>Greedy</font>

The reason it matches whole string is because * (and also +) is greedy. So, the engine will repeat the dot as many times as it can. The dot matches H, then e and so on till the matched string is `<p>Hello</p><span>Awesome</span><p>World</`. The dot again matches next character `p` and moves on to next character which is `>`. The dot matches it again and the engine continues repeating the dot. <u>**The dot will match all remaining characters in the string**</u>. The dot fails when the engine has <u>*reached the void after the end of the string*</u>. At this point the regex engine continue matching with the next token: `<`.

So far, `<p>.*` has matched `<p>Hello</p><span>Awesome</span><p>World</p>` and the engine has arrived at the end of the string where `<` cannot match. This is where the engine will start ==backtrack==. It will **reduce the repetition of the star <u>*by one</u>*** and then **continue trying the remainder of the regex**.

So the match of `.*` is reduced to `<p>Hello</p><span>Awesome</span><p>World</p`. The next token in the regex is still `<`. But now the next character in the string is the last `p`. This cannot match, causing the engine to ==backtrack further==. So the engine continues backtracking until the match of `.*` is reduced to `<p>Hello</p><span>Awesome</span><p>World`. Now, `<` can match the next character in the string. This process continues until all literals of regex is matched against the string thus matching the whole string. 

<br>

## <font color='BCA1E3'>Non-greedy or Lazy</font>

The fix to this problem is to make the star lazy instead of greedy. You can do that by putting a question mark `?` after the star in the regex `r'<p>.*?</p>'`. Let's have another look on how the regex engine matches the string with lazy star.

`<p>` will match starting `<p>` of the string. Next regex literal is `.*` followed with question mark. This tells the regex engine to **repeat the dot as few times as possible**. So the engine matches the dot with H and the engine continues with matching `<` with `e`. This fails causing regex engine to backtrack. But this time, the backtracking will force the lazy star to **expand repetition** rather than reduce its reach. So the match of `.*?` is expanded to `He`. Backtrack and matching will continue till lazy star matches Hello. Now the next literal is `<` matching against next character of string which is `<`. It succeeds and the matching continues until the regex engine stops after matching `<p>Hello</p>`.