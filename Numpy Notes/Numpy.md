```python 
import numpy as np
```

## Creating Arrays
```python
a = np.array([1,2,3])
b = np.array([[1.5,2,3], [4,5,6]], dtype = float)
```
Note that when array becomes 3D or above extra newline spaces are added after every one dimension to help distinguish the arrays.

## Initial Placeholders

```python
a = np.zeros((3,4)) #array of zeros with 3 rows, 4 columns (computer will move backward)
```
Note that in computers things work backwards. say we were to say reshape d=a.reshape(3,2,4) where a = np.zeros(2,3,4). So see this as new array having 3 z-axis, 2 rows, 4 columns as when we will make a array in computer we will work outward na	
```python
a = np.ones((2,3,4)) #array of ones
a = np.arange(10,25,5) #even space values from [10,25) with step 5
a = np.linspace(0,2,9) # 9 evenly spaced values from [0,2]
a = np.random.random((2,2)) #array with random values
a = np.empty((3,2)) # empty array
```
## I/O
### Saving & Loading on Disk
```python
np.save('my_array',a) # save array to .npy binary format
np.savez('array.npz',a,b) #save multiple arrays in a zip format of .npz, should be default .npz imo idk tho
#by default arrays are assigned name arr_0,arr_1 etc. but can be changed by using argument a=a,b=b
np.load('my_array') 
```
### Saving and Loading Text Files
```python
```
## Inspecting Your Array
```python
a.shape() # Array dimensions
len(a) # Length of array
a.ndim() # Number of array dimensions
a.astype(int) # convert an array to a different datatype
```

## Array Mathematics

All of the following operations happens element wise.
```python
# arrays a,b

# Subtraction
g = a-b
np.subtract(a,b)

# Addition
b+a
np.add(b,a)

# Division
a/b
np.divide(a,b)

# Multiplication
a*b
np.multiply(a,b)

# Dot Product
a.dot(b)
np.dot(a,b)

np.exp(b)
np.sqrt(b)
np.sin(a)
np.cos(a)
np.log(a)
```

```python
a == b #T/F elementwise
a<2 #T/F elementwise
```

## Aggregrate functions
```python
a.sum() # sum
a.min() # min of entire array. axis=0,1.. can be specified as parameter if we want for a particular row
a.max() #max and axis same
a.mean()
np.median(a) 
```

## Copying arrays
```python
b = np.copy(a) #shallow copy, not preferred
b = a.copy() #deep copy, preferred
```

## Sorting 
```python
a.sort() # sort the array
a.sort(axis = 0) # sort the elements of arrays axis
```

## Subsetting, Slicing, Indexing
```python
a[2] #element at 2nd index
b[1,2] # element at row 1 column 2
b[1][2] # same as above

a[a<2] # select elements from a less than 2
```

## Array Manipulation
```python
# Transposing array
i = np.transpose(b)
b.T

# changing shape
b.ravel() #flatten array
g.reshape(3,2) # change dimensions to 3 rows 2 columns
g.reshape(-1) #flatten array

# combining arrays
np.concatenate((a,d),axis=0)
np.vstack((a,b)) # stack arrays vertically, row wise
np.hstack((a,b)) # stack arrays horizontally, column wise

# splitting arrays
np.hsplit(a,3) # split array horizontally at the 3rd index
np.vsplit(a,2) # split the array vertically at the 2nd index 

```





