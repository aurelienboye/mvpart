# Create Split Labels For an Rpart Object

This function provides labels for the branches of an `rpart` tree.

## Usage

``` r
# S3 method for class 'rpart'
labels(object, digits=4, minlength=1, pretty, collapse=TRUE, ...)
```

## Arguments

- object:

  fitted model object of class `rpart`. This is assumed to be the result
  of some function that produces an object with the same named
  components as that returned by the `rpart` function.

- digits:

  the number of digits to be used for numeric values. All of the `rpart`
  functions that call labels explicitly set this value, with
  `options("digits")` as the default.

- minlength:

  the minimum length for abbreviation of character or factor variables.
  If 0 no abbreviation is done; if 1 then single letters are used with
  `"a"` for the first level, `"b"` for the second and so on. If the
  value is greater than 1, the `abbreviate` function is used.

- pretty:

  an argument included for backwards compatibility:

  `pretty=0` implies `minlength=0`,

  `pretty=NULL` implies `minlength=1`, and

  `pretty=TRUE` implies `minlength=4`.

- collapse:

  logical. The returned set of labels is always of the same length as
  the number of nodes in the tree. If `collapse=TRUE` (default), the
  returned value is a vector of labels for the branch leading into each
  node, with `"root"` as the label for the top node. If `FALSE`, the
  returned value is a two column matrix of labels for the left and right
  branches leading out from each node, with `"leaf"` as the branch
  labels for terminal nodes.

- ...:

  optional arguments to `abbreviate`.

## Value

Vector of split labels (`collapse=TRUE`) or matrix of left and right
splits (`collapse=FALSE`) for the supplied `rpart` object. This function
is called by printing methods for `rpart` and is not intended to be
called directly by the users.

## See also

[`abbreviate`](https://rdrr.io/r/base/abbreviate.html)
