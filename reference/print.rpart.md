# Print an Rpart Object

This function prints an `rpart` object. It is a method for the generic
function `print` of class `rpart`.

## Usage

``` r
# S3 method for class 'rpart'
print(x, minlength=0, spaces=2, cp, digits= getOption("digits"), ...)
```

## Arguments

- x:

  fitted model object of class `rpart`. This is assumed to be the result
  of some function that produces an object with the same named
  components as that returned by the `rpart` function.

- minlength:

  Controls the abbreviation of labels: see
  [`labels.rpart`](https://aurelienboye.github.io/mvpart/reference/labels.rpart.md).

- spaces:

  the number of spaces to indent nodes of increasing depth.

- digits:

  the number of digits of numbers to print.

- cp:

  prune all nodes with a complexity less than `cp` from the printout.
  Ignored if unspecified.

- ...:

  arguments to be passed to or from other methods.

## Side Effects

A semi-graphical layout of the contents of `x$frame` is printed.
Indentation is used to convey the tree topology. Information for each
node includes the node number, split, size, deviance, and fitted value.
For the `"class"` method, the class probabilties are also printed.

## Details

This function is a method for the generic function `print` for class
`"rpart"`. It can be invoked by calling print for an object of the
appropriate class, or directly by calling `print.rpart` regardless of
the class of the object.

## See also

[`print`](https://rdrr.io/r/base/print.html),
[`rpart.object`](https://aurelienboye.github.io/mvpart/reference/rpart.object.md),
[`summary.rpart`](https://aurelienboye.github.io/mvpart/reference/summary.rpart.md),
[`printcp`](https://aurelienboye.github.io/mvpart/reference/printcp.md)

## Examples
