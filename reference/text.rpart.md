# Place Text on a Dendrogram

Labels the current plot of the tree dendrogram with text.

## Usage

``` r
# S3 method for class 'rpart'
text(x, splits = TRUE, which = 4, label = "yval", FUN = text, 
    all.leaves = FALSE, pretty = NULL, digits = getOption("digits") - 2,
    tadj = 0.65, stats = TRUE, use.n = FALSE, bars = TRUE, 
    legend = FALSE, xadj = 1, yadj = 1, bord = FALSE, big.pts = FALSE,
    uniform = FALSE, branch = 1, nspace = -1, minbranch = 0.3, ...)
```

## Arguments

- x:

  fitted model object of class `rpart`. This is assumed to be the result
  of some function that produces an object with the same named
  components as that returned by the `rpart` function.

- splits:

  logical flag. If `TRUE` (default), then the splits in the tree are
  labeled with the criterion for the split.

- which:

  labels splits 1 = center, 2 = left, 3 = right , 4 = both.

- label:

  a column name of `x$frame`; values of this will label the nodes. For
  the `"class"` method, `label="yval"` results in the factor levels
  being used, `"yprob"` results in the probability of the winning factor
  level being used, and 'specific yval level' results in the probability
  of that factor level.

- FUN:

  the name of a labeling function, e.g. `text`.

- all.leaves:

  Logical. If `TRUE`, all nodes are labeled, otherwise just terminal
  nodes.

- tadj:

  Adjustment of text above (or below) splits.

- pretty:

  an integer denoting the extent to which factor levels in split labels
  will be abbreviated. A value of (0) signifies no abbreviation. A
  `NULL`, the default, signifies using elements of letters to represent
  the different factor levels.

- digits:

  number of significant digits to include in numerical labels.

- stats:

  If `TRUE` adds statistics to nodes.

- use.n:

  If `TRUE` adds N to labels. (\\events level1/ \\events level2/etc. for
  `class`, `n` for `anova`, and \\events/n for `poisson` and `exp`).

- bars:

  If `TRUE` adds barplots for multivariate regression trees.

- legend:

  If `TRUE` adds legends for multivariate regression trees.

- xadj, yadj:

  varies the size of barplots for multivariate regression trees.

- bord:

  Adds borders (boxes) to barplots for multivariate regression trees.

- big.pts:

  Adds color coded points to nodes. Useful to track groups to PCA plot
  (see `rpart.pca`).

- uniform:

  Uniform spacing of tree branches; defualt is FALSE.

- branch:

  branch parameter default = 1.

- nspace:

  branch parameter default = 1.

- minbranch:

  minimum branch parameter default = 0.3.

- ...:

  Graphical parameters may also be supplied as arguments to this
  function (see `par`).

## Side Effects

the current plot of a tree dendrogram is labeled.

## See also

[`text`](https://rdrr.io/r/graphics/text.html),
[`plot.rpart`](https://aurelienboye.github.io/mvpart/reference/plot.rpart.md),
[`rpart`](https://aurelienboye.github.io/mvpart/reference/rpart.md),
[`post.rpart`](https://aurelienboye.github.io/mvpart/reference/post.rpart.md),
[`abbreviate`](https://rdrr.io/r/base/abbreviate.html)

## Examples

``` r
data(car.test.frame)
z.auto <- rpart(Mileage ~ Weight, car.test.frame)
plot(z.auto)
text(z.auto, use.n=TRUE, all=TRUE)
```
