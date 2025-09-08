# If/elif/else Statements
## Fizzbuzz
```python
for number in range(0,47,1):
    
    if number % 3 == 0 and number % 5 == 0:
        print(number, "fizzbuzz")

    elif number % 3 == 0:
        print(number, "fizz")

    elif number % 5 == 0:
        print(number, "buzz")
    
```

# For Loops
## Modifying iterable object while iterating over it
```python
# Create a sample collection
users = {'Hans': 'active', 'Éléonore': 'inactive', 'Mark': 'active'}

# strategy 1: iterate over copy
# dont want to interate over collection which we are modifying at same time
users_copy = users.copy() 

for user, status in users_copy.items(): 
    if status == 'inactive':
        users.pop(user)

# strategy 2: make new collection
active_users = {}

for user, status in users_copy.items(): 
    if status == 'active':
        active_users[user] = status

```

# Range Function
```python
range(start = 0, end, step = 1)
```
- Behaves like a list in many ways, but it is its own object (range object). 
- Returns successive elements when you iterate over it.
- Doesnt store everything in memory unlike list.
- Not an iterator (does not exhaust itself)

## Iterate Over Indexes of Sequence
```python
a = [1, 2, 3, 4]

for i in range(len(a)):
    print(i, a[i])

# enumerate can do this nicer
for i, value in enumerate(a):
    print(i, value)
```

# Break and Continue
- Break statements breaks out of innermost for or while loop.
- Continue statement continues with the next iteration of the loop.

```python
for i in range(15):

    if i % 2 == 0:
        print(f"{i} is even.")
        continue # next iteration if i is even

    if i == 9:
        break # ends loop if i == 9

    print(f"{i} is odd.") # only prints if i is less than 9 and odd

```
# For Else (niE)
- Usually used with a break statement.
- Loops else clause runs when no break occurs. 

```python
for n in range(2, 10):
    for x in range(2, n):
        if n % x == 0:
            print(n, 'equals', x, '*', n//x)
            break
    else:
        # loop fell through without finding a factor
        print(n, 'is a prime number')
```

# Pass Statement
- Placeholder to put in functions or under statements when they are incomplete to prevent errors.

```python
def incomplete_function(a, b):

    if a > b: # complete later
        pass

```

# Match Statement
- Only the first case that matches gets excecuted. 
- _ is default case that excecutes if no other cases match.

```python
def http_error(status):
    match status:
        case 400:
            print("Bad request")
        case 401 | 403:
            print("Not allowed")
        case 404 | 400: # works only for 404 as 400 will match before
            print("Not found")
        case 418:
             print("I'm a teapot")
        case _:
            print("Something's wrong with the internet")
```

# Default Arguements and *args **kwargs 
- Default arguement does not need to be given when you call a function as a default value already exists.
```python
def fun(arguement, default_arguement = 0):
    pass
```
- Default values are evaluated at the point of function definition (ONLY ONCE). Example:
```python
i = 5
def foo(arg = i):
    print(arg)

foo() # 5
i = 6
foo() # 5
```
```python
def foo_2(a, L = []):
    L.append(a)
    return L

print(foo_2(2)) # [2]
print(foo_2(3)) # [2, 3]
```

```python
def parrot(voltage, state='a stiff', action='voom', type='Norwegian Blue'):
    pass

parrot(1000)                                          # 1 positional argument
parrot(voltage=1000)                                  # 1 keyword argument
parrot(voltage=1000000, action='VOOOOOM')             # 2 keyword arguments
parrot(action='VOOOOOM', voltage=1000000)             # 2 keyword arguments
parrot('a million', 'bereft of life', 'jump')         # 3 positional arguments
parrot('a thousand', state='pushing up the daisies')  # 1 positional, 1 keyword


def function(a):
    pass

function(0, a=0)
# Traceback (most recent call last):
#   File "<stdin>", line 1, in <module>
# TypeError: function() got multiple values for argument 'a'
```

- *args are extra arguements added when you call a function, *kwargs are extra keyword arguements (ex. "hello" is an arguement, greeting="hello" is a keyword arguement.)

```python
def cheeseshop(kind, *args, **kwargs):
    print("-- Do you have any", kind, "?")
    print("-- I'm sorry, we're all out of", kind)
    for arg in args:
        print(arg)
    print("-" * 40)
    for kw in kwargs:
        print(kw, ":", kwargs[kw])


cheeseshop("Limburger", "It's very runny, sir.",
        "It's really very, VERY runny, sir.",
        shopkeeper="Michael Palin",
        client="John Cleese",
        sketch="Cheese Shop Sketch")
```


# Lambda
- Shorter way of writing one line functions.
- Lambda keyword creates a small anonymous function.
```python
add_3 = lambda x: x + 3
add_3(5)
```

# zip() 
- used to iterate over two or more sequences at the same time.
- By default zip() stops when the shorter iterable is exhausted. It ignores the remaining items in the longer iterable.
## zip() function definition
```python
zip(*iterables, strict = False)
```
- using strict:
```python
lst = ["do", "re", "mi", "fa"]
rnge = range(0, 10, 1)

print(list(zip(rnge, lst))) # [(0, 'do'), (1, 're'), (2, 'mi'), (3, 'fa')]
print(list(zip(rnge, lst, strict=True))) # error since lst length is different than rnge
```

# reversed()
- Returns reversed iterator
```python
for i in reversed(range(1,5,1)):
    print(i) # 4 3 2 1
```

# sorted() vs .sort()
- sorted() returns a new sorted list while leaving source iterable unaltered.
- .sort() alters and sorts source list.
- reverse=True to sort in reverse order.