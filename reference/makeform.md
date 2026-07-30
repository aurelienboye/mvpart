# Formula Constructor

This function constructs a formula from a data frame given the locations
of the response and other variables. It is useful for long or repetitive
formulas.

## Usage

``` r
makeform(data, ycol, xcol, zcol, FUN, maxy = 20, extra)
```

## Arguments

- data:

  The data frame or matrix for which the formula is to be contructed,

- ycol:

  The locations (or names) of the response variables in `data`.

- xcol:

  The locations (or names) of the explanatory variables in `data`.

- zcol:

  The locations (or names) of the conditioning variables in `data`; for
  use in the `vegan` package.

- FUN:

  A function to apply to the response.

- maxy:

  The number of multivariate responses before abbreviated notation is
  used. see examples below.

- extra:

  Extra term(s) for the RHS of the formula.

## Details

makeform constructs a formula and is useful for long and/or repetitive
formulae. See examples below.

## Value

Returns a formula.

## Examples

``` r
data(spider)
makeform(spider,1,13:18)
#> arct.lute ~ water + sand + moss + reft + twigs + herbs
#> <environment: 0x562308113780>
# arct.lute ~ water + sand + moss + reft + twigs + herbs

makeform(spider,1:12,13:18)
#> cbind(arct.lute, pard.lugu, zora.spin, pard.nigr, pard.pull, 
#>     aulo.albi, troc.terr, alop.cune, pard.mont, alop.acce, alop.fabr, 
#>     arct.peri) ~ water + sand + moss + reft + twigs + herbs
#> <environment: 0x562308173960>
# cbind(arct.lute, pard.lugu, zora.spin, pard.nigr, pard.pull, 
# aulo.albi, troc.terr, alop.cune, pard.mont, alop.acce, alop.fabr, 
# arct.peri) ~ water + sand + moss + reft + twigs + herbs

makeform(spider,1:12,13:15,16:18)
#> cbind(arct.lute, pard.lugu, zora.spin, pard.nigr, pard.pull, 
#>     aulo.albi, troc.terr, alop.cune, pard.mont, alop.acce, alop.fabr, 
#>     arct.peri) ~ water + sand + moss + Condition(reft + twigs + 
#>     herbs)
#> <environment: 0x56230827a3c8>
# cbind(arct.lute, pard.lugu, zora.spin, pard.nigr, pard.pull, 
# aulo.albi, troc.terr, alop.cune, pard.mont, alop.acce, alop.fabr, 
# arct.peri) ~ water + sand + moss + Condition(reft + twigs + herbs)

makeform(spider,1:12,13:15,maxy=6)
#> as.matrix(spider[, 1:12]) ~ water + sand + moss
#> <environment: 0x562308378510>
# as.matrix(spider[, 1:12]) ~ water + sand + moss

makeform(spider,1:3,13:15,FUN=sqrt)
#> sqrt(cbind(arct.lute, pard.lugu, zora.spin)) ~ water + sand + 
#>     moss
#> <environment: 0x5623083ffff0>
# sqrt(cbind(arct.lute, pard.lugu, zora.spin)) ~ water + sand + moss

makeform(spider,1:3,13:15,FUN=sqrt,extra="I(water^2)+")
#> sqrt(cbind(arct.lute, pard.lugu, zora.spin)) ~ I(water^2) + water + 
#>     sand + moss
#> <environment: 0x56230848f7c8>
# sqrt(cbind(arct.lute, pard.lugu, zora.spin)) ~ I(water^2) + water + 
# sand + moss
```
