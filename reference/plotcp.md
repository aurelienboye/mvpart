# Plot a Complexity Parameter Table for an Rpart Fit

Gives a visual representation of the cross-validation results in an
`rpart` object.

## Usage

``` r
plotcp(x, xvse = 1, minline = TRUE, lty = 3, col = 1,
  upper = c("size","splits", "none"), tab, resub.err = TRUE,
  adj.df = FALSE, ...)
```

## Arguments

- x:

  an object of class `rpart`

- xvse:

  multiplier for xvse \* SE above the minimum of the curve.

- minline:

  whether a horizontal line is drawn 1SE above the minimum of the curve.

- lty:

  type of lines used in plot, default = 3.

- col:

  color of lines, default =1.

- upper:

  what is plotted on the top axis: the size of the tree (the number of
  leaves), the number of splits or nothing.

- tab:

  used for multiple cross-validation.

- resub.err:

  use resubstitution error for calculations of SEs.

- adj.df:

  adjust df of resubstitution error estimate for calculations of SEs.

- ...:

  additional plotting parameters

## Value

None.

## Side Effects

A plot is produced on the current graphical device.

## Details

The set of possible cost-complexity prunings of a tree from a nested
set. For the geometric means of the intervals of values of `cp` for
which a pruning is optimal, a cross-validation has (usually) been done
in the initial construction by
[`rpart`](https://aurelienboye.github.io/mvpart/reference/rpart.md). The
`cptable` in the fit contains the mean and standard deviation of the
errors in the cross-validated prediction against each of the geometric
means, and these are plotted by this function. A good choice of `cp` for
pruning is often the leftmost value for which the mean lies below the
horizontal line.

## See also

[`rpart`](https://aurelienboye.github.io/mvpart/reference/rpart.md),
[`printcp`](https://aurelienboye.github.io/mvpart/reference/printcp.md),
[`rpart.object`](https://aurelienboye.github.io/mvpart/reference/rpart.object.md)
