# Cost-complexity Pruning of an Rpart Object

Determines a nested sequence of subtrees of the supplied `rpart` object
by recursively `snipping` off the least important splits, based on the
complexity parameter (`cp`).

## Usage

``` r
# S3 method for class 'rpart'
prune(tree, cp, ...)
```

## Arguments

- tree:

  fitted model object of class `rpart`. This is assumed to be the result
  of some function that produces an object with the same named
  components as that returned by the `rpart` function.

- cp:

  Complexity parameter to which the `rpart` object will be trimmed.

- ...:

  further arguments passed to or from other methods.

## Value

A new `rpart` object that is trimmed to the value `cp`.

## See also

[`rpart`](https://aurelienboye.github.io/mvpart/reference/rpart.md)

## Examples

``` r
data(car.test.frame)
z.auto <- rpart(Mileage ~ Weight, car.test.frame)
zp <- prune(z.auto, cp=0.1)
plot(zp) #plot smaller rpart object
```
