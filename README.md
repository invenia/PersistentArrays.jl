# PersistentArrays.jl

[![Build Status](https://travis-ci.org/invenia/PersistentArrays.jl.svg?branch=master)](https://travis-ci.org/invenia/PersistentArrays.jl)
[![codecov.io](https://codecov.io/github/invenia/PersistentArrays.jl/coverage.svg?branch=master)](https://codecov.io/github/invenia/PersistentArrays.jl?branch=master)

[Fat node](https://en.wikipedia.org/wiki/Persistent_data_structure) implementation of a persistent array, which in this case is just stored as an array of arrays. This datastructure is ideal when you need to store multiple versions of an array, but the elements in the array are rarely changing.

## Usage:

Please see the test cases for common usage [here](https://github.com/invenia/PersistentArrays.jl/blob/master/test/runtests.jl).


## Complexity:

Summary Table of method complexity per element selected.

Method | Complexity 
--- | --- 
`setindex!(a, x, i...)` | O(m) 
`getindex(a, i...)` | O(1) 
`update!(a, x, v, i...)` | O(mlog(m)) 
`lookup(a, v, i...)` | O(log(m))

The space complexity is O(n x m) where n is the number of elements and m is the number of versions. This worst case scenario could occur if all elements in the array change for every version.
