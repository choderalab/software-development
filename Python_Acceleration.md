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

### Cython

Sometimes, you don't want to add an extra dependency, or the libraries available do not cover your use case. Short of resorting to writing your code directly in C, with the attendant boilerplate to connect back to Python. Fortunately, there is a solution in the Python ecosystem: [Cython](http://cython.org/). Cython itself is a superset of Python, allowing type declarations and seamless import of C and C++ functions. It is also an optimizing compiler that first converts the Cython into C, and then compiles the C into native code, which can be delivered as a binary. To install, if you have Anaconda (see above if you don't), it's just `conda install cython`

Cython is also a straightforward way to connect Python code to C code, as Cython can both be readily imported by Python, and can readily access C libraries. As with Numba, it can require some finesse to ensure that the Cython code you write does not need to call the intepreter very often. To judge this, one can simply use `cython -a my_code.pyx` to generate an HTML file with lines highlighted based on the frequency of interpreter calls.

#### Example
As an example of code that has been optimized such that no intepreter calls are necessary at all, we have reproduced some code from one of our own projects, [Yank](https://github.com/choderalab/yank), a free energy calculation tool:

```cython
cimport cython
from libc.math cimport exp, isnan
from libc.stdio cimport printf
cdef extern from 'stdlib.h' nogil:
    double drand48()

@cython.wraparound(False)
@cython.cdivision(True)
@cython.boundscheck(False)
cpdef long _mix_replicas_cython(long nswap_attempts, long nstates, long[:] replica_states, double[:,:] u_kl, long[:,:] Nij_proposed, long[:,:] Nij_accepted) nogil:
    cdef long swap_attempt
    cdef long i, j, istate, jstate, tmp_state
    cdef double log_P_accept
    for swap_attempt in range(nswap_attempts):
        i = <long>(drand48()*nstates)
        j = <long>(drand48()*nstates)
        istate = replica_states[i]
        jstate = replica_states[j]
        if (isnan(u_kl[i, istate]) or isnan(u_kl[i, jstate]) or isnan(u_kl[j, istate]) or isnan(u_kl[j, jstate])):
            continue
        log_P_accept = - (u_kl[i, jstate] + u_kl[j, istate]) + (u_kl[j, jstate] + u_kl[i, istate])
        Nij_proposed[istate, jstate] +=1
        Nij_proposed[jstate, istate] +=1
        if(log_P_accept>=0 or drand48()<exp(log_P_accept)):            
            tmp_state = replica_states[i]
            replica_states[i] = replica_states[j]
            replica_states[j] = tmp_state
            Nij_accepted[i,j] += 1
            Nij_accepted[j,i] += 1
    return 0
```

As you can see, while it shares a lot of Python's nice clean syntax, we also declare variable types and manage them carefully. By doing this, we can ensure that we get the performance of C, but where using the code is as simple as:
```python
        from .mixing._mix_replicas import _mix_replicas_cython

        replica_states = md.utils.ensure_type(self.replica_states, np.int64, 1, "Replica States")
        u_kl = md.utils.ensure_type(self.u_kl, np.float64, 2, "Reduced Potentials")
        Nij_proposed = md.utils.ensure_type(self.Nij_proposed, np.int64, 2, "Nij Proposed")
        Nij_accepted = md.utils.ensure_type(self.Nij_accepted, np.int64, 2, "Nij accepted")
        _mix_replicas_cython(self.nstates**4, self.nstates, replica_states, u_kl, Nij_proposed, Nij_accepted)
```

Note that we have some extra calls to ensure that the type is as we declared. However, it is otherwise as simple as calling a Python function.

## Recommendations

Although your application may fit another paradigm, in general, we recommend pursuing acceleration in this order:

* NumPy - Your code should already be using this, but if it's not, this could be an easy speedup

* Numba - May require only a simple decorator; in more involved cases, may just require rearranging some variables

* Tensorflow/Theano - Operates under a different paradigm, but very useful for some communities (e.g., deep learning), also provides automatic differentiation. 

* Cython - When nothing else fits your application, Cython is a productive option. Pure Python is still valid Cython, so you can change the code slowly to add static typing and other performance-enhancing features until desired performance is achieved.

* C/C++ extensions - Sometimes for very application-specific purposes this is the best option (especially when communicating with GPUs and other specialized devices). However, it can be very time consuming, and should be used as a last resort. 
