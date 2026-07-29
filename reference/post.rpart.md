# PostScript Presentation Plot of an Rpart Object

Generates a PostScript presentation plot of an `rpart` object.

## Usage

``` r
# S3 method for class 'rpart'
post(tree, title., 
     filename = paste(deparse(substitute(tree)), ".ps", sep = ""), 
     digits = getOption("digits") - 3, pretty = TRUE,
     use.n = TRUE, horizontal = TRUE, ...)
```

## Arguments

- tree:

  fitted model object of class `rpart`. This is assumed to be the result
  of some function that produces an object with the same named
  components as that returned by the `rpart` function.

- title.:

  a title which appears at the top of the plot. By default, the name of
  the `rpart` endpoint is printed out.

- filename:

  ASCII file to contain the output. By default, the name of the file is
  the name of the object given by `rpart` (with the suffix `.ps` added).
  If `filename = ""`, the plot appears on the current graphical device.

- digits:

  number of significant digits to include in numerical data.

- pretty:

  an integer denoting the extent to which factor levels will be
  abbreviated in the character strings defining the splits; (0)
  signifies no abbreviation of levels. A `NULL` signifies using elements
  of letters to represent the different factor levels. The default
  (`TRUE`) indicates the maximum possible abbreviation.

- use.n:

  Logical. If `TRUE` (default), adds to label (\\events level1/ \\events
  level2/etc. for method `class`, `n` for method `anova`, and \\events/n
  for methods `poisson` and `exp`).

- horizontal:

  Logical. If `TRUE` (default), plot is horizontal. If `FALSE`, plot
  appears as landscape.

- ...:

  other arguments to the `postscript` function.

## Side Effects

a plot of `rpart` is created using the `postscript` driver, or the
current device if `filename = ""`.

## Details

The plot created uses the functions `plot.rpart` and `text.rpart` (with
the `fancy` option). The settings were chosen because they looked good
to us, but other options may be better, depending on the `rpart` object.
Users are encouraged to write their own function containing favorite
options.

## See also

[`plot.rpart`](https://aurelienboye.github.io/mvpart/reference/plot.rpart.md),
[`rpart`](https://aurelienboye.github.io/mvpart/reference/rpart.md),
[`text.rpart`](https://aurelienboye.github.io/mvpart/reference/text.rpart.md)

## Examples

``` r
data(car.test.frame)
z.auto <- rpart(Mileage ~ Weight, car.test.frame)
post(z.auto, file = "")   # display tree on active device

   # now construct postscript version on file "pretty.ps"
   # with no title
post(z.auto, file = "pretty.ps", title = " ")
z.hp <- rpart(Mileage ~ Weight + HP, car.test.frame)
post(z.hp)
```
