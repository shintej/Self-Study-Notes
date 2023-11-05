# Basic Syntax

## Printing
```python
print("Hello world!")
```
Hello world!    
```python
print(1+2) #3
```
Can comment using """ ...... """"    
To modify ending using print(....,end = " ") or whatever end you want  (This is for end of line of entire print statement)
To modify seperation between entities of same print statement: print(..,..,..,sep="..")  

## Creating variables

```python
var_int = 4
var_string = "hello" #get length of string with len(string_name)
var_char = 'a'
```
Python does not require explicit variable declaration of type    

## Functions

```python
def get_pay_with_more_inputs(num_hours, hourly_wage, tax_bracket): #Multiple inputs defined here
    # Pre-tax pay
    pay_pretax = num_hours * hourly_wage #The scope of this variable is inside function only
    # After-tax pay
    pay_aftertax = pay_pretax * (1 - tax_bracket) #same for this variable
    return pay_aftertax
```
Also Possible with no arguments
```python
# Define the function with no arguments and with no return
def print_hello():
    print("Hello, you!")
    print("Good morning!")
    
# Call the function
print_hello()
```
Hello, you!    
Good morning!    

## Data types
Pretty standard stuffs. Some interesting points noted here:
```python
x = 14 # INT
x = 14. # FLOAT
pi = 3.141592653
also_pi = 22/7 # this will convert 22/7 into a decimal value
rounded pi = round (also_pi,5) # this will round the number to 5 decimal digits
```
## Conditional statements

```python
#observe that there is no bracket here for the conditional statements
def evaluate_temp_with_elif(temp):
    if temp > 38:
        message = "Fever!"
    elif temp > 35:
        message = "Normal temperature."
    else:
        message = "Low temperature."
    return message
```

## Lists

```python
flowers_list = ["pink primrose", "hard-leaved pocket orchid", "canterbury bells", "sweet pea", "english marigold", "tiger lily", "moon orchid", "bird of paradise", "monkshood", "globe thistle"]

# The list has ten entries
print(len(flowers_list))


print("First entry:", flowers_list[0]) 
print("Second entry:", flowers_list[1]) 

# The list has length ten, so we refer to final entry with 9
print("Last entry:", flowers_list[9])

#First entry: pink primrose
#Second entry: hard-leaved pocket orchid
#Last entry: globe thistle

print("First three entries:", flowers_list[:3])
print("Final two entries:", flowers_list[-2:])

#First three entries: ['pink primrose', 'hard-leaved pocket orchid', 'canterbury bells']
#Final two entries: ['monkshood', 'globe thistle']

flowers_list.remove("globe thistle")

flowers_list.append("snapdragon") #adds at end
```
If lists contain numbers
```python
hardcover_sales = [139, 128, 172, 139, 191, 168, 170]

print("Minimum:", min(hardcover_sales))
print("Maximum:", max(hardcover_sales))
#Minimum: 128
#Maximum: 191

print("Total books sold in one week:", sum(hardcover_sales))
#Total books sold in one week: 1107
```
Lists are mutable ie. they can be modified in place    
Just access the index and change. Note multiple adjacent indexes can be accessed too and modified at same time by assigning them to a list.

### List functions
```python
#sorting
sorted(my_list)
```
### List Methods
```python
planets.append('Pluto')

planets.pop() #list.pop removes and returns the last element of a list:

planets.index('Earth') #gives index of Earth; but error if it doesnt exist in list

"Earth" in planets #true
"Calbefraques" in planets #false
```
## Tuples
Same as lists but written using (  ) instead of [  ].    
They are immutable

## Loops and List Comprehensions
```python
# EXAMPLE 1
planets = ['Mercury', 'Venus', 'Earth', 'Mars', 'Jupiter', 'Saturn', 'Uranus', 'Neptune']
for planet in planets:
    print(planet, end=' ') # print all on same line

# EXAMPLE 2
s = 'steganograpHy is the practicE of conceaLing a file, message, image, or video within another fiLe, message, image, Or video.'
msg = ''
# print all the uppercase letters in s, one at a time
for char in s:
    if char.isupper():
        print(char, end='')        

# EXAMPLE 3
for i in range(5):
    print("Doing important work. i =", i) # prints from 0 to 4

# EXAMPLE 4
i = 0
while i < 10:
    print(i, end=' ')
    i += 1 # increase the value of i by 1
```
### List comprehension
```python
squares = []
for n in range(10):
    squares.append(n**2)
squares
```
[0, 1, 4, 9, 16, 25, 36, 49, 64, 81]    
But this syntax can be improved upon 

```python
squares = [n**2 for n in range(10)]
```
More examples:
```python
short_planets = [planet for planet in planets if len(planet) < 6]

loud_short_planets = [planet.upper() + '!' for planet in planets if len(planet) < 6]

[32 for planet in planets]

def count_negatives(nums):
    return len([num for num in nums if num < 0])
or
    return sum([num < 0 for num in nums])
```
## String methods

Note the strings are like lists but are immutable
```python
# String methods

claim = "Pluto is a planet!"

claim.upper() # all caps

claim.lower() # all lowercase

# Searching for the first index of a substring
claim.index('plan') # 11

claim.startswith(planet) # true

claim.endswith('planet') # false

words = claim.split() # ['Pluto', 'is', 'a', 'planet!']

datestr = '1956-01-31'
year, month, day = datestr.split('-')

'/'.join([month, day, year]) # '01/31/1956'
```

## Dictionaries

Dictionaries are a built-in Python data structure for mapping keys to values.    
```python
numbers = {'one':1, 'two':2, 'three':3}

numbers['one'] # 1

planets = ['Mercury', 'Venus', 'Earth', 'Mars', 'Jupiter', 'Saturn', 'Uranus', 'Neptune']
planet_to_initial = {planet: planet[0] for planet in planets}
planet_to_initial
{'Mercury': 'M',
 'Venus': 'V',
 'Earth': 'E',
 'Mars': 'M',
 'Jupiter': 'J',
 'Saturn': 'S',
 'Uranus': 'U',
 'Neptune': 'N'}
```
A for loop over a dictionary will loop over its keys
```python
for k in numbers:
    print("{} = {}".format(k, numbers[k])) #note this new syntax of format. pretty interesting!
```

We can access a collection of all the keys or all the values with dict.keys() and dict.values(), respectively.
```python
# Get all the initials, sort them alphabetically, and put them in a space-separated string.
' '.join(sorted(planet_to_initial.values()))
```

The very useful dict.items() method lets us iterate over the keys and values of a dictionary simultaneously. (In Python jargon, an item refers to a key, value pair)

```python
for planet, initial in planet_to_initial.items():
    print("{} begins with \"{}\"".format(planet.rjust(10), initial))
```
   Mercury begins with "M"
     Venus begins with "V"
     Earth begins with "E"
      Mars begins with "M"
   Jupiter begins with "J"
    Saturn begins with "S"
    Uranus begins with "U"
   Neptune begins with "N"

## Working with External Libraries

```python
from ... import * #imports all
from ... import ... #import as required, preferred
import ...
import ... as ... #use a custom name
```























