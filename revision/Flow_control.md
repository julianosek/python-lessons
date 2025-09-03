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


