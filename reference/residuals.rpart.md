# Residuals From a Fitted Rpart Object

Method for `residuals` for an `rpart` object.

## Usage

``` r
# S3 method for class 'rpart'
residuals(object, type = c("usual", "pearson", "deviance"), ...)
```

## Arguments

- object:

  fitted model object of class `"rpart"`.

- type:

  Indicates the type of residual desired.

  For regression or `anova` trees all three residual definitions reduce
  to `y - fitted`. This is the residual returned for `user` method trees
  as well.

  For classification trees the `usual` residuals are the
  missclassification losses L(actual, predicted) where L is the loss
  matrix. With default losses this residual is 0/1 for correct/incorrect
  classification. The `pearson` residual is
  (1-fitted)/sqrt(fitted(1-fitted)) and the `deviance` residual is
  sqrt(minus twice logarithm of fitted).

  For `poisson` and `exp` (or survival) trees, the `usual` residual is
  the observed - expected number of events. The `pearson` and `deviance`
  residuals are as defined in McCullagh and Nelder.

- ...:

  further arguments passed to or from other methods.

## Value

vector of residuals of type `type` from a fitted `rpart` object.

## References

McCullagh P. and Nelder, J. A. (1989) *Generalized Linear Models*.
London: Chapman and Hall.

## Examples

``` r
data(solder)
fit <- rpart(skips ~ Opening + Solder + Mask + PadType + Panel,
       data=solder, method='anova')
summary(residuals(fit))
#>     Min.  1st Qu.   Median     Mean  3rd Qu.     Max. 
#> -13.8000  -1.0361  -0.5583   0.0000   0.9639  16.2000 
plot(predict(fit),residuals(fit))
```
