# Displays CP table for Fitted Rpart Object

Displays the `cp` table for fitted `rpart` object.

## Usage

``` r
printcp(x, digits=getOption("digits") - 2)
```

## Arguments

- x:

  fitted model object of class `rpart`. This is assumed to be the result
  of some function that produces an object with the same named
  components as that returned by the `rpart` function.

- digits:

  the number of digits of numbers to print.

## Details

Prints a table of optimal prunings based on a complexity parameter.

## See also

[`summary.rpart`](https://aurelienboye.github.io/mvpart/reference/summary.rpart.md),
[`rpart.object`](https://aurelienboye.github.io/mvpart/reference/rpart.object.md)

## Examples
