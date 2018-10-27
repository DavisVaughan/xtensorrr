
<!-- README.md is generated from README.Rmd. Please edit that file -->

# xtensorrr

[![Lifecycle:
experimental](https://img.shields.io/badge/lifecycle-experimental-orange.svg)](https://www.tidyverse.org/lifecycle/#experimental)

The goal of xtensorrr is to bundle all of the required headers of
`xtensor` and `xtl` into one package, along with the headers of
`xtensor-r`, so you can get started working with the headers right away,
without having to worry about the `cmake` setup that `xtensor` (for good
reason) uses.

Below we provide a few examples.

## Installation

``` r
devtools::install_github("DavisVaughan/xtensorrr")
```

## Example

``` r
devtools::load_all()
#> Loading xtensorrr
```

Just get a 2x2 numeric matrix back from an `xarray<double>`. There is
some dynamic sizing happening here

``` r
two_by_two_rarray()
#>      [,1] [,2] [,3]
#> [1,]    1    2    3
#> [2,]    5    5    5
```

Just get a 2x2 numeric matrix back from an xtensor\<double, 2\> you have
to be more explicit about sizing here

``` r
two_by_two_rtensor()
#>      [,1] [,2] [,3]
#> [1,]    1    2    3
#> [2,]    5    5    5
```

Add 1 to an R object Using xarray means the dimensions are determined
dynamically

``` r
plus_one(c(1, 2))
#> [1] 2 3

plus_one(matrix(c(1, 2)))
#>      [,1]
#> [1,]    2
#> [2,]    3

plus_one(array(1, dim = c(2, 2, 2)))
#> , , 1
#> 
#>      [,1] [,2]
#> [1,]    2    2
#> [2,]    2    2
#> 
#> , , 2
#> 
#>      [,1] [,2]
#> [1,]    2    2
#> [2,]    2    2
```

``` r
# Interestingly, I think ALTREP breaks some of this
plus_one(1:5)
#> [1] 1 1 1 1 1

plus_one(1:5 + 1) # <- this is fine
#> [1] 3 4 5 6 7
```
