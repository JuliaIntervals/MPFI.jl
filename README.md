# MPFI.jl

## Julia wrapper for the Multiple Precision Floating-point Interval library (MPFI)

This is a Julia package that wraps [MPFI](http://perso.ens-lyon.fr/nathalie.revol/software.html). 
All functions should be available, except `mpfi_put_*` and `mpfi_urandom`.

## Documentation

Documentation is available at http://mpfijl.readthedocs.org/en/latest/

## Installation

You will first need to install the MPFI library.

- On Ubuntu:

      sudo apt-get install libmpfi-dev
    
- On Mac:

      brew install mpfi
    
Now install the Julia package from within Julia with

    julia> Pkg.add("MPFI")

## Examples

```jl
# MPFI uses BigFloats in its internal representation
# For convenience, let's just use 53 bits (as a Float64)
julia> setprecision(53)
53

julia> using MPFI

# The following creates an interval centered on 1.1.
# Since 1.1 isn't exactly representable as a floating-point number,
# the shortest interval that includes it is returned.
julia> x = Interval("1.1")
[1.0999999999999999e+00, 1.1000000000000001e+00] with 53 bits of precision

# It is also possible to create an interval through its endpoints.
julia> y = Interval(1, 2)
[1e+00, 2e+00] with 53 bits of precision

julia> Interval("[1, 2]")
[1e+00, 2e+00] with 53 bits of precision

julia> x + y
[2.0999999999999996e+00, 3.1000000000000001e+00] with 53 bits of precision
```

Warning: currently the return values and the error handling from MPFI are ignored.


## Author

The original author is [Alessandro Andrioni](https://github.com/andrioni).
