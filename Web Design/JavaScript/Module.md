# Module

[toc]

ES6 introduced a way to easily share code among JavaScript files. A script that uses  **module** type can now use the `import` and `export` features you will learn about in the upcoming challenges.

## Export

 In order to share a function with these other files, you first need to export it.
 
 You can export multiple things by repeating the first example for each thing you want to export:
 
 ```
 export const add = (x, y) => {
  return x + y;
}
```

Or by placing them all in the export statement of the second example, like this:

```
const add = (x, y) => {
  return x + y;
}

// snap
export { add, subtract };
```

## Import

```
import { add, subtract } from './math_functions.js';
```
The `./` tells the import to look for the *math_functions.js* file in the same folder as the current file. 

You can use `*` to import all:

```
import * as myMathModule from "./math_functions.js";
```

This inports all the functions into an object called `myMathModule`. Here's how you can use the add and subtract functions that were imported:

```
myMathModule.add(2,3);
myMathModule.subtract(5,3);
```

## export and import default

### export default

Usually you will use this syntax if only one value is being exported from a file. It is also used to create a fallback value for a file or module.

```
export default function add(x, y) {
  return x + y;  // Named
}

export default function(x, y) {
  return x + y;  // Anonymous
}
```

Since export default is used to declare a fallback value for a module or file, you can only have *one value* be a default export in each module or file. Additionally, you cannot use export default with var, let, or const.

### import default

To import a default export, you need to use a different import syntax. In the following example, add is the default export of the math_functions.js file. Here is how to import it:

```
import add from "./math_functions.js";
```
The syntax differs in one key place. The imported value, add, is **not surrounded by curly braces (`{}`)**. add here is simply a *variable name* for whatever the default export of the math_functions.js file is. You can use any name here when importing a default.
