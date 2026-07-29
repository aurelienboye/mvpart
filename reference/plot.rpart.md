# Plot an Rpart Object

Plots an rpart object on the current graphics device.

## Usage

``` r
# S3 method for class 'rpart'
plot(x, uniform=FALSE, branch=1, compress=FALSE, nspace,
     margin=0, minbranch=.3, bar,...)
```

## Arguments

- x:

  a fitted object of class `rpart`, containing a classification,
  regression, or rate tree.

- uniform:

  if `TRUE`, uniform vertical spacing of the nodes is used; this may be
  less cluttered when fitting a large plot onto a page. The default is
  to use a non-uniform spacing proportional to the error in the fit.

- branch:

  controls the shape of the branches from parent to child node. Any
  number from 0 to 1 is allowed. A value of 1 gives square shouldered
  branches, a value of 0 give V shaped branches, with other values being
  intermediate.

- compress:

  If `FALSE`, the leaf nodes will be at the horzontal plot coordinates
  of `1:nleaves`. If `TRUE`, the routine attempts a more compact
  arrangement of the tree. The compaction algorithm assumes
  `uniform=TRUE`; surprisingly, the result is usually an improvement
  even when that is not the case.

- nspace:

  the amount of extra space between a node with children and a leaf, as
  compared to the minimal space between leaves. Applies to compressed
  trees only. The default is the value of `branch`.

- margin:

  an extra percentage of white space to leave around the borders of the
  tree. (Long labels sometimes get cut off by the default computation).

- minbranch:

  set the minimum length for a branch to `minbranch` times the average
  branch length. This parameter is ignored if `uniform=TRUE`. Sometimes
  a split will give very little improvement, or even (in the
  classification case) no improvement at all. A tree with branch lengths
  strictly proportional to improvement leaves no room to squeeze in node
  labels.

- bar:

  length of bar at root (default = 0.03) – used instead of char "\|"

- ...:

  arguments to be passed to or from other methods.

## Value

the coordinates of the nodes are returned as a list, with components `x`
and `y`.

## Side Effects

an unlabeled plot is produced on the current graphics device.

## Details

This function is a method for the generic function `plot`, for objects
of class `rpart`. The y-coordinate of the top node of the tree will
always be 1.

## See also

[`rpart`](https://aurelienboye.github.io/mvpart/reference/rpart.md),
[`text.rpart`](https://aurelienboye.github.io/mvpart/reference/text.rpart.md)

## Examples

``` r
data(car.test.frame)
fit <- rpart(Price ~ Mileage + Type + Country, car.test.frame)
plot(fit, compress=TRUE)
text(fit, use.n=TRUE)
```
