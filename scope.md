Scope for functions in global env
================

``` r
devtools::load_all()
```

    ## Loading scope

Define `f_local()` in the global environment:

``` r
f_local <- function(x){
  y <<- x
}
```

Set a value for `y`, also in the global environment:

``` r
y <- 0
```

Now, since the parent environment of `f_local()` is the global
environment, calling `f_local()` changes the value of `y`:

``` r
f_local(5)
y
```

    ## [1] 5

Compare this to `f_package()`. Since the environment of the function
`f_package()` is the package namespace, it finds the definition of `y`
in `f_package.R`, not the `y` in the global environment, and `y` doesn’t
appear changed:

``` r
f_package(10)
y
```

    ## [1] 5

Although it actually changed this other `y`:

``` r
scope::y
```

    ## [1] 10
