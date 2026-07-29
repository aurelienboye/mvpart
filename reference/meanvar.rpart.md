# Mean-Variance Plot for an Rpart Object

Creates a plot on the current graphics device of the deviance of the
node divided by the number of observations at the node. Also returns the
node number.

## Usage

``` r
# S3 method for class 'rpart'
meanvar(tree, xlab="ave(y)", ylab="ave(deviance)", ...)
```

## Arguments

- tree:

  fitted model object of class `rpart`. This is asumed to be the result
  of some function that produces an object with the same named
  components as that returned by the `rpart` function.

- xlab:

  x-axis label for the plot.

- ylab:

  y-axis label for the plot.

- ...:

  additional graphical parameters may be supplied as arguments to this
  function.

## Value

an invisible list containing the following vectors is returned.

- x:

  fitted value at terminal nodes (`yval`).

- y:

  deviance of node divided by number of observations at node.

- label:

  node number.

## Side Effects

a plot is put on the current graphics device.

## See also

[`plot.rpart`](https://aurelienboye.github.io/mvpart/reference/plot.rpart.md).

## Examples

``` r
data(car.test.frame)
z.auto <- rpart(Mileage ~ Weight, car.test.frame)
meanvar(z.auto, log='xy')
```
