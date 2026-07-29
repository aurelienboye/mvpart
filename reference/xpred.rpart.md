# Return Cross-Validated Predictions

Gives the predicted values for an `rpart` fit, under cross validation,
for a set of complexity parameter values.

## Usage

``` r
xpred.rpart(fit, xval=10, cp)
```

## Arguments

- fit:

  a `rpart` object.

- xval:

  number of cross-validation groups. This may also be an explicit list
  of integers that define the cross-validation groups.

- cp:

  the desired list of complexity values. By default it is taken from the
  `cptable` component of the fit.

## Value

a matrix with one row for each observation and one column for each
complexity value.

## Details

Complexity penalties are actually ranges, not values. If the `cp` values
found in the table were \\.36\\, \\.28\\, and \\.13\\, for instance,
this means that the first row of the table holds for all complexity
penalties in the range \\\[.36, 1\]\\, the second row for `cp` in the
range \\\[.28, .36)\\ and the third row for \\\[.13,.28)\\. By default,
the geometric mean of each interval is used for cross validation.

## See also

[`rpart`](https://aurelienboye.github.io/mvpart/reference/rpart.md)

## Examples

``` r
data(car.test.frame)
fit <- rpart(Mileage ~ Weight, car.test.frame)
xmat <- xpred.rpart(fit)
xerr <- (xmat - car.test.frame$Mileage)^2
apply(xerr, 2, sum)   # cross-validated error estimate
#> 0.79767456 0.28300396 0.09664299 0.04893534 0.02525439 0.01704869 0.01253756 
#>  1382.9856   846.2579   583.7998   478.4855   524.4801   541.8674   544.5723 

# approx same result as rel. error from printcp(fit)
apply(xerr, 2, sum)/var(car.test.frame$Mileage) 
#> 0.79767456 0.28300396 0.09664299 0.04893534 0.02525439 0.01704869 0.01253756 
#>   60.23708   36.85946   25.42789   20.84083   22.84416   23.60148   23.71930 
printcp(fit)
#> 
#> Regression tree:
#> rpart(formula = Mileage ~ Weight, data = car.test.frame)
#> 
#> Variables actually used in tree construction:
#> [1] Weight
#> 
#> Root node error: 1354.6/60 = 22.576
#> 
#> n= 60 
#> 
#>         CP nsplit rel error  xerror     xstd
#> 1 0.595349      0   1.00000 1.02206 0.174870
#> 2 0.134528      1   0.40465 0.53486 0.100522
#> 3 0.069427      2   0.27012 0.39369 0.077349
#> 4 0.034492      3   0.20070 0.39239 0.077192
#> 5 0.018491      4   0.16620 0.47390 0.102950
#> 6 0.015719      5   0.14771 0.48335 0.110221
#> 7 0.010000      7   0.11627 0.46711 0.111425
```
