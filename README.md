
<!-- README.md is generated from README.Rmd. Please edit that file -->
countess: Helpers for "dplyr"'s "count" Function
================================================

Convenience functions built on top of dplyr to count the number of instances of each value in columns of data frames.

-   `count_all()` is `group_by_all()` plus `tally()`.
-   `count_at()` is `group_by_at()` plus `tally()`.
-   `count_if()` is `group_by_if()` plus `tally()`.

Installation
------------

You can install the released version of countess from [CRAN](https://CRAN.R-project.org) with:

``` r
install.packages("countess")
```

Example
-------

This is a basic example which shows you how to solve a common problem:

``` r
#' library(dplyr)
#' n <- 100
#' quarks <- data_frame(
#'   first_gen = sample(c("up", "down"), n, replace = TRUE),
#'   second_gen = sample(c("charm", "strange"), n, replace = TRUE),
#'   third_gen = factor(sample(c("top", "bottom"), n, replace = TRUE))
#' )
#' quarks %>% count_all()
#' quarks %>% count_at(vars(contains("ir")))
#' quarks %>% count_if(is.factor)
```
