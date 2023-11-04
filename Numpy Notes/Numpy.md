``` 
import numpy as np
```

## Creating Arrays
```
a = np.array([1,2,3])
b = np.array([[1.5,2,3], [4,5,6]], dtype = float)
```
Note that when array becomes 3D or above extra newline spaces are added after every one dimension to help distinguish the arrays.

## Initial Placeholders

```
a = np.zeros((3,4)) #array of zeros with 3 rows, 4 columns (computer will move backward)
```
Note that in computers things work backwards. say we were to say reshape d=a.reshape(3,2,4) where a = np.zeros(2,3,4). So see this as new array having 3 z-axis, 2 rows, 4 columns as when we will make a array in computer we will work outward na	
```
a = np.ones((2,3,4)) #array of ones
a = np.arange(10,25,5) #even space values from [10,25) with step 5
a = np.linspace(0,2,9) # 9 evenly spaced values from [0,2]
a = np.random.random((2,2)) #array with random values
a = np.empty((3,2)) # empty array
```
## I/O
### Saving & Loading on Disk
```
np.save('my_array',a) # save array to .npy binary format
np.savez('array.npz',a,b) #save multiple arrays in a zip format of .npz, should be default .npz imo idk tho
#by default arrays are assigned name arr_0,arr_1 etc. but can be changed by using argument a=a,b=b
np.load('my_array') 
```

### Saving and Loading Text Files
```
```
## Inspecting Your Array
```
a.shape() # Array dimensions
len(a) # Length of array
a.ndim() # Number of array dimensions
a.astype(int) # convert an array to a different datatype
```

