# Table of contents
- [String](#string)
- [Numeric](#numeric)
- [List](#list)
- [Set](#set)
- [Dict](#dict)
- [Tuple](#tuple)
- [To-do](#to-do)
- [Links](#links)


To-do
# String
## Basics
- Strings are [immutable](Glossary.md#immutable)
- Strings are [iterable](Glossary.md#iterable)
- Strings can be indexed (character can be accessed with bracket notation)
- Strings can be sliced

## Formating and f-strings
**.format()**  
print("My name is {}, I am {} years old.".format(name, age))

**f-strings (most common)**  
print(f"My name is {name}, I am {age} years old.")

## Commonly used methods
### Placeholder i guess - edit later
Example `text = " hello world "`
| Method           | Description                         | Example                |
|------------------|-------------------------------------|------------------------|
| **text.strip()** | remove leading and trailing spaces  | `"hello world"`        |
| **text.upper()** | convert to uppercase                | `"  HELLO WORLD  "`    |
| **text.lower()** | convert to lowercase                | `"  hello world  "`    |
| **text.replace("world", "Python")** | replace (by default all) occurences | `"  hello Python  "`    |
| **text.split()** | returns a list of the substrings in the string (by default whitespace separator)| `['hello', 'world']` |
| **"-".join(["a", "b", "c"])** | The string whose method is called is inserted in between each given string | `"a-b-c"`    |
| **text.count("l")** | returns the number of non-overlapping occurrences of substring  | `"3"`        |

### Searching in Strings
Example `text = "hello python"`
| Method           | Description                         | Example                |
|------------------|-------------------------------------|------------------------|
| **text.find("python")** | returns the lowest index where substring is found (-1 on failure)  | `6` |
| **text.startswith("he")** | returns True if string starts with the specified prefix (False otherwise)  | `True` |
| **text.endswith("on")** | returns True if string ends with the specified prefix (False otherwise)  | `True` |

Example `text = "hello python"`

| Membership test           | Description                         | Example                |
|------------------|-------------------------------------|------------------------|
| **"python" in text** | returns True if substring is part of string (False otherwise)  | `True` |


### Checks
| Method           | Description                         | Example                |
|------------------|-------------------------------------|------------------------|
| **"123".isdigit()** | returns True if the string is a digit string (False otherwise)  | `"True"`        |
| **"abc".isalpha()** | returns True if the string is a alphabetic string (False otherwise)  | `"True"`        |
| **"a2c".isalnum()** | returns True if the string is a alpha-numeric string (False otherwise)  | `"True"`        |

## Common problems / Tricks
1. Reverse a string (e.g palindrome)
2. Count vowels in string
3. Remove all spaces
4. [Count frequency for each character]
5. [Find first non-repeated character]
6. [Check if two string are anagrams]
7. [Find longest word in sentence]

# Numeric
## Basics (int and float) 
- numeric types are [immutable](Glossary.md#immutable)
- `int` is a built-in data type for whole numbers.
- `float` is a built-in data type for numbers with a decimal point
- both can be positive, negative, or zero

## Arithmetic operations
`a / b` division (result will be float)  
`a // b` - floor division (result will be int)  
`a % b` - modulus / remainder  
`a ** b` - exponent

## Type conversion
Example `num_str = "123"`  
`int(num_str)`  
`float(num_str)`  
`int(3.9)` - it will be truncated to 3

## Useful build-in functions
| function         | Description                         | Example                |
|------------------|-------------------------------------|------------------------|
| **abs(-7)** | returns absolute value  | `"7"`        |
| **pow(2,3)** | returns power  | `"8"`        |
| **divmod(10,3)** | returns tuple (quotient & remainder)  | `"(3, 1)"`        |
| **max(4,9,2)** | returns biggest number  | `"9"`        |
| **min(4,9,2)** | returns smallest number  | `"29"`        |
| **round(3.75)** | returns rounded number  | `"4"`        |
| **round(3.75,1)** | returns number rounded to 1 decimal   | `"3.8"`        |

## Float precision
Floats can have precision issues because of binary representation.
```python
print(0.1 + 0.2)   # 0.30000000000000004

print(round(0.1 + 0.2,2))   # 0.3
```

So avoid direct comparision of floats due to precision issues
```python
a = 0.1 + 0.2
b = 0.3

print(round(a, 2) == round(b, 2))  # True
print(a == b) # False

```

## Boolean context
Integers can behave like a True/False

```python
if 5: # All numbers other than 0 -> True in if statement
    print("This runs") 
if 0: # 0 -> False in if statement
    print("This won't run")
```


## Common problems / Tricks
1. [Check if number is odd or even]
2. [Sum of digits in number]
3. [Reverse a int]
4. Factorial of a number
5. Greates Common Divisor (build-in function exist but may be usefull + recursion)
6. Is number Armstrong number? (pierwsze slysze tbh)
7. Find all factors of a number
8. Is number a perfect numeber
9. fibonacci


# List
## Basics
- Lists are [mutable](Glossary.md#mutable)
- Lists are [iterable](Glossary.md#iterable)
- Lists can be indexed (element can be accessed with bracket notation)
- Lists can be sliced
- A list is an ordered (position matters) collection of items
- Items can be of any type: int, float, string, even other lists.

## Accessing Elements
```python
lst = [10, 20, 30, 40]
lst[0] # first element
lst[-1] # last element
lst[1:3] # [20, 30] (slicing)
lst[:2] # [10, 20]
lst[2:] # [30, 40] (from index 2 to end) 
```

## Modifying lists
```python
lst = [1, 2 ,3]

lst[0] = 10 # change first element [10, 2 ,3]
lst.append(4) # add to end [10, 2, 3, 4]
lst.insert(1, 15) # insert at index 1 [10, 15, 2, 3, 4]
lst.remove(2) # remove value 2 [10, 15, 3, 4]
lst.pop() # remove and return last element [10, 15, 3]
lst.pop(1) # remove and return element at index 1 [10, 3]
del lst[1] # remove element at index 1 [10]
```
`del` can remove slices


## Useful list methods/functions
```python
lst = [3, 1, 4, 2]

lst.sort() # [1, 2, 3, 4]
lst.sort(reverse=True) # [4, 3, 2, 1]
lst[::-1] # [2, 4, 1, 3]
lst.reverse() # [2, 4, 1, 3]

min(lst) # 1
max(lst) # 4
sum(lst) # 10
```
## Comprehension list
```python
lst = [1, 2, 3, 4, 5]

lst_even = [x for x in lst if x % 2 == 0] # [2, 4]

newlist_odd = [x for x in range(10) if x % 2 == 1] # [1, 3, 5, 7, 9]
```


## Common problems / Tricks
1. Sum all elements
2. Reverse a list
3. Remove duplicates
4. Create list B of even numbers from list A
5. Check if empty
6. Count occurences of element
7. Find index of element
8. Flatten a list (single lvl)
9. Comprehension list: Square of numbers





# To-do
https://www.w3schools.com/python/exercise.asp?x=xrcise_datatypes1  
dict, set i tuple  
Julia repo + swoj kod pod te common problems + komentarze niech sobie doda


# Links
https://docs.python.org/3/tutorial/introduction.html  
https://docs.python.org/3/glossary.html  
https://docs.python.org/3/library/stdtypes.html#