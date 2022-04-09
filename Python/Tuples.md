# Tuples (immutable list)

If you want to define a tuple with one element, you need to include a trailing comma:
```
tup = (3,)
```

## Converting Types with the `list()` and `tuple()` Functions

```
print(tuple([1, 2, 3]))
print(list((1, 2, 3)))
print(list('hello'))
```
*output:*
```
(1, 2, 3)
[1, 2, 3]
['h', 'e', 'l', 'l', 'o']
```

Iteration:

```
presidents = [
	("Washington", 1789),
	("Adams", 1797),
	("Jefferson", 1801),
	("Madison", 1809)
]
for prez, year in presidents:
	print("In {1}, {0} took office".format(prez, year))
```

## Set

A set is a collection which is unordered, unchangeable*, unindexed and do not allow duplicate values.



