# This file is a set of notes that will document a python study on NUMPY

## NUMPY:

Numpy is a numerical analysis package used by python to create and manipulate
arrays and matrices.

This study will :
1. Import the package
2. Create an array
3. Reshape the arrays
4. Print out the first 3 and last three rows
5. Build an array WITH named types
6. Create, slice, and manipulate an array with and without altering it
7. Take the mode of data in an arrays
8. Read in a csv file and retrieve values using dtype

# 0. Installing numpy in conda

Open a new environment and install NUMPY
```conda
conda create -n my-env
conda activate my-env

conda config --env --add channels conda-forge

conda install numpy

#or

pip install numpy
```

# 1. Import the package

```python
# Import the numpy package as np...common pythonic convention
import numpy as np
```

# 2. Create and manipulate an array

```python
import numpy as np

# Creates a 3x3 array filled with ones
a = np.array([[1, 1, 1],[1, 1, 1]])

# can directly reasign the values at indexes (array in python are null indexed)
a[0, 2] = 5

# Can print the values of an array using slices
print(a[:, 2]) # Prints the values of the third column over all rows

# Can get the type of the array, as well as its size in memory
sys.getsizeof(a) # Returns the memory size of the array; 144 in this case

# Can use the dtype() method to identify the type of the array
a.dtype() # Returns type int32
```

# 3. Reshape the arrays
```python
a = np.array(10)# Creates a ten item vector beginning with 0
b = a.reshape(5, 2)# Will reshape a to a 5x2 matrix; item tally and dims must work!
c = np.arange(10).reshape(5,2) # Identical to b
```
```conda
>>> a = np.arange(10)
>>> b = a.reshape(5, 2)
>>> c = np.arange(10).reshape(5, 2)
>>> a
array([0, 1, 2, 3, 4, 5, 6, 7, 8, 9])
>>> b
array([[0, 1],
       [2, 3],
       [4, 5],
       [6, 7],
       [8, 9]])
>>> c
array([[0, 1],
       [2, 3],
       [4, 5],
       [6, 7],
       [8, 9]])
>>>
```

-   Notice the outputs:  b is a brand new assignment; it in no way effected a
-   c is an identical setup to b, but built more directly.

# 4. Print out the first 3 and last three rows

Numpy arrays can be indexed using the ':' operator for all items, '-1, -n' operaetors to get the last item, or the nth from the last item, slice '1:9' to get pieces of the array, or simply hard indexing 'a\[1\]'

```python
a = np.arange(25)
b = a.reshape(5, 5)
print(b[:, 1:3])

print(a.ndim)
print(b.shape)
```

```conda
>>> a = np.arange(25)
>>> b = a.reshape(5,5)
>>> print(b[:, 1:3])
[[ 1  2]
 [ 6  7]
 [11 12]
 [16 17]
 [21 22]]

>>> print(b)
[[ 0  1  2  3  4]
 [ 5  6  7  8  9]
 [10 11 12 13 14]
 [15 16 17 18 19]
 [20 21 22 23 24]]

 >>> print(b.shape)
(5, 5)
```

# 5. Build an array WITH named types

We can build arrays that are a mixed types

```python
a = np.array([3,5,7])
b = np.array([['A', 4, 6.78],['B', 3, 5]])
print(b.dtype.name)
```
-   These arrays can be accessed in the same way as the previous examples
-   Notably, everything that is inside of the array is of type 'str'
-   We can recast the items on the fly using 'dtype=\[\('marker', 'type')]'
-   See the example below:

```conda
x = np.array([('Rex', 9, 81.0), ('Fido', 3, 27.0)],
               dtype=[('name', 'U10'), ('age', 'i4'), ('weight', 'f4')])

print(x)
print(x['name'])  # (Rex, Fido)
```
-   Notably, the 'marker' name will be assigned to the 0-column values for all rows and will be assigned the value type 'U10' which is a string type
-   similar behavior will be observed if x is called using 'age' or 'weight'
-   This behavior reminds me of dict{} but with a different build style, and less memory usage

# 6. Create, slice, and manipulate an array with and without altering it

Did something very similar to this in \#3
