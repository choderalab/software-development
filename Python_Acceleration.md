# Accelerating Python Code

Python is a very clean and readable language for scientific (and other) development activities, but the same flexibility that makes code easy to write can often make it rather slow. Fortunately, the popularity of Python has created a number of solutions so that you don't have to go too far outside the Python ecosystem (sometimes not at all) in order to accelerate your code. In this brief, we will explore several options for accelerating your numerical computations in Python

## Python Libraries

### NumPy
Before delving into Python extensions, we should first discuss the library you should already be using: NumPy.

[NumPy](http://www.numpy.org/), a powerful library for arrays, linear algebra, and more, is extremely popular and common. If you are using Continuum Analytics [Anaconda](https://www.continuum.io/downloads) to manage your Python packages (and if you aren't, you should be), you can install it easily by `conda install numpy`. NumPy is very easy to use, but many of its array functions and linear algebra routines have been written in C, allowing maximum performance. 

### Tensorflow and Theano
While NumPy is an excellent resource for most applications, others require more custom computation graphs that can run on specialized hardware like GPUs, and benefit from [automatic differentiation](https://en.wikipedia.org/wiki/Automatic_differentiation) (note that this is not numerical differentiation). There are libraries that exist to fill this niche, such has [Theano](http://deeplearning.net/software/theano/) and [Tensorflow](https://www.tensorflow.org/). A full comparison and discussion of these libraries is beyond the scope of this document.

### Numba

What about when you have Python code written, but it's just not fast enough? [Numba](http://numba.pydata.org/), a library sponsored by Continuum Analytics, may be the solution for you. As with NumPy, its installation is easy: `conda install numba`, if you have the Anaconda Python package manager. So, how involved is it to use Numba? We'll take a look at an example on the site.

#### Code before Numba
```python
from numpy import arange
def sum2d(arr):
    M, N = arr.shape
    result = 0.0
    for i in range(M):
        for j in range(N):
            result += arr[i,j]
    return result

a = arange(9).reshape(3,3)
print(sum2d(a))
```

#### Code after Numba
```python
from numba import jit
from numpy import arange
@jit
def sum2d(arr):
    M, N = arr.shape
    result = 0.0
    for i in range(M):
        for j in range(N):
            result += arr[i,j]
    return result

a = arange(9).reshape(3,3)
print(sum2d(a))
```


That's it. Just a decorator. What happens under the hood? The `jit` decorator takes the bytecode for the function, and compiles it to native code. Of course, there are some caveats. Sometimes, if you're using Python's dynamic typing convenience, the native code will just call the interpreter, and much of the speed increase will be lost. Guidelines on how to properly use Numba's facilities can be found on the [website](http://numba.pydata.org/).


## Extensions to Python

Sometimes, you don't want to add an extra dependency, or the libraries available do not cover your use case. Short of resorting to writing your code directly in C, with the attendant boilerplate to connect back to Python. Fortunately, there is a solution in the Python ecosystem: [Cython](http://cython.org/). Cython itself is a superset of Python, allowing type declarations and seamless import of C and C++ functions. It is also an optimizing compiler that first converts the Cython into C, and then compiles the C into native code, which can be delivered as a binary.

Cython is the 

