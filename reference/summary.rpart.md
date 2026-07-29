# Summarize a Fitted Rpart Object

Returns a detailed listing of a fitted `rpart` object.

## Usage

``` r
# S3 method for class 'rpart'
summary(object, cp=0, digits=getOption("digits"), file, ...)
```

## Arguments

- object:

  fitted model object of class `rpart`. This is assumed to be the result
  of some function that produces an object with the same named
  components as that returned by the `rpart` function.

- digits:

  Number of significant digits to be used in the result.

- cp:

  trim nodes with a complexity of less than `cp` from the listing.

- file:

  write the output to a given file name. (Full listings of a tree are
  often quite long).

- ...:

  arguments to be passed to or from other methods.

## Details

This function is a method for the generic function summary for class
`"rpart"`. It can be invoked by calling `summary` for an object of the
appropriate class, or directly by calling `summary.rpart` regardless of
the class of the object.

## See also

[`summary`](https://rdrr.io/r/base/summary.html),
[`rpart.object`](https://aurelienboye.github.io/mvpart/reference/rpart.object.md),
[`printcp`](https://aurelienboye.github.io/mvpart/reference/printcp.md).

## Examples

``` r
data(car.test.frame)
z.auto <- rpart(Mileage ~ Weight, car.test.frame)
summary(z.auto)
#> Call:
#> rpart(formula = Mileage ~ Weight, data = car.test.frame)
#>   n= 60 
#> 
#>           CP nsplit rel error    xerror       xstd
#> 1 0.59534912      0 1.0000000 1.0341282 0.17766961
#> 2 0.13452819      1 0.4046509 0.5907329 0.10524049
#> 3 0.06942684      2 0.2701227 0.4388141 0.07724889
#> 4 0.03449195      3 0.2006958 0.3910305 0.07021715
#> 5 0.01849081      4 0.1662039 0.3898483 0.07308486
#> 6 0.01571904      5 0.1477131 0.3831385 0.07292204
#> 7 0.01000000      7 0.1162750 0.3643134 0.08431422
#> 
#> Node number 1: 60 observations,    complexity param=0.5953491
#>   mean=24.58333, MSE=22.57639 
#>   left son=2 (45 obs) right son=3 (15 obs)
#>   Primary splits:
#>       Weight < 2567.5 to the right, improve=0.5953491, (0 missing)
#> 
#> Node number 2: 45 observations,    complexity param=0.1345282
#>   mean=22.46667, MSE=8.026667 
#>   left son=4 (22 obs) right son=5 (23 obs)
#>   Primary splits:
#>       Weight < 3087.5 to the right, improve=0.5045118, (0 missing)
#> 
#> Node number 3: 15 observations,    complexity param=0.06942684
#>   mean=30.93333, MSE=12.46222 
#>   left son=6 (9 obs) right son=7 (6 obs)
#>   Primary splits:
#>       Weight < 2280   to the right, improve=0.5030908, (0 missing)
#> 
#> Node number 4: 22 observations,    complexity param=0.01849081
#>   mean=20.40909, MSE=2.78719 
#>   left son=8 (6 obs) right son=9 (16 obs)
#>   Primary splits:
#>       Weight < 3637.5 to the right, improve=0.4084816, (0 missing)
#> 
#> Node number 5: 23 observations,    complexity param=0.01571904
#>   mean=24.43478, MSE=5.115312 
#>   left son=10 (15 obs) right son=11 (8 obs)
#>   Primary splits:
#>       Weight < 2747.5 to the right, improve=0.1476996, (0 missing)
#> 
#> Node number 6: 9 observations,    complexity param=0.03449195
#>   mean=28.88889, MSE=8.54321 
#>   left son=12 (3 obs) right son=13 (6 obs)
#>   Primary splits:
#>       Weight < 2337.5 to the left,  improve=0.607659, (0 missing)
#> 
#> Node number 7: 6 observations
#>   mean=34, MSE=2.666667 
#> 
#> Node number 8: 6 observations
#>   mean=18.66667, MSE=0.5555556 
#> 
#> Node number 9: 16 observations
#>   mean=21.0625, MSE=2.058594 
#> 
#> Node number 10: 15 observations
#>   mean=23.8, MSE=4.026667 
#> 
#> Node number 11: 8 observations,    complexity param=0.01571904
#>   mean=25.625, MSE=4.984375 
#>   left son=22 (3 obs) right son=23 (5 obs)
#>   Primary splits:
#>       Weight < 2650   to the left,  improve=0.6321839, (0 missing)
#> 
#> Node number 12: 3 observations
#>   mean=25.66667, MSE=0.2222222 
#> 
#> Node number 13: 6 observations
#>   mean=30.5, MSE=4.916667 
#> 
#> Node number 22: 3 observations
#>   mean=23.33333, MSE=0.2222222 
#> 
#> Node number 23: 5 observations
#>   mean=27, MSE=2.8 
#> 
```
