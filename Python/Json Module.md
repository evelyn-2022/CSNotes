# <font size='6'><center>Json Module</center></font>

[toc]

## <font color='BCA1E3'>Using `json.dump()` and `json.load()`</font>

use `json.dump()` function to **store data** into file, `json.load()` to **read data from file into memory**

### Store data
```
import json

numbers = [2, 3, 5, 7, 11, 13]

filename = 'numbers.json'
with open(filename, 'w') as f:
	json.dump(numbers, f)
```

<br>

### Load data
```
import json

filename = 'numbers.json'
with open(filename) as f:
	numbers = json.load(f)

print(numbers)
```