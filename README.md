# PersistentArrays.jl

[![Build Status](https://travis-ci.org/invenia/PersistentArrays.jl.svg?branch=master)](https://travis-ci.org/invenia/PersistentArrays.jl)
[![codecov.io](https://codecov.io/github/invenia/PersistentArrays.jl/coverage.svg?branch=master)](https://codecov.io/github/invenia/PersistentArrays.jl?branch=master)

[Fat node](https://en.wikipedia.org/wiki/Persistent_data_structure) implementation of a persistent array.

Usage:
```
# From test/runtests.jl

using PersistentArrays
using Base.Test

default_array = PersistentArray(4)
default_array[2] = 3.5

@test version(default_array) == 1

commit!(default_array)
@test version(default_array) == 2

@test default_array[1] == 0.0
@test default_array[2] == 3.5

default_array[2] = 2.5
commit!(default_array)
@test version(default_array) == 3

@test default_array[:] == [0.0, 2.5, 0.0, 0.0]
@test lookup(default_array, 1, :) == [0.0, 3.5, 0.0, 0.0]
```
