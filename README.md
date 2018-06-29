
<!-- README.md is generated from README.Rmd. Please edit that file -->
countess: Helpers for "dplyr"'s "count" Function
================================================

Convenience functions built on top of dplyr to count the number of instances of each value in columns of data frames.

-   `count_all()` is `group_by_all()` plus `tally()`.
-   `count_at()` is `group_by_at()` plus `tally()`.
-   `count_if()` is `group_by_if()` plus `tally()`.

Installation
------------

You can install this development version of countess using

``` r
# install.packages("remotes")
remotes::install_github("richierocks/countess")
```

Example
-------

This is a basic example which shows you how to solve a common problem:

``` r
library(dplyr)
library(countess)
n <- 100
quarks <- data_frame(
  first_gen = sample(c("up", "down"), n, replace = TRUE),
  second_gen = sample(c("charm", "strange"), n, replace = TRUE),
  third_gen = factor(sample(c("top", "bottom"), n, replace = TRUE))
)
quarks %>% count_all()
#> # A tibble: 8 x 4
#>   first_gen second_gen third_gen     n
#>   <chr>     <chr>      <fct>     <int>
#> 1 down      charm      bottom        6
#> 2 down      charm      top          15
#> 3 down      strange    bottom       15
#> 4 down      strange    top          14
#> 5 up        charm      bottom       15
#> 6 up        charm      top           9
#> 7 up        strange    bottom       18
#> 8 up        strange    top           8
quarks %>% count_at(vars(contains("ir")))
#> # A tibble: 4 x 3
#>   first_gen third_gen     n
#>   <chr>     <fct>     <int>
#> 1 down      bottom       21
#> 2 down      top          29
#> 3 up        bottom       33
#> 4 up        top          17
quarks %>% count_if(is.factor)
#> # A tibble: 2 x 2
#>   third_gen     n
#>   <fct>     <int>
#> 1 bottom       54
#> 2 top          46
```
