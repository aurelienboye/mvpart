# Soldering of Components on Printed-Circuit Boards

The `solder` data frame has 720 rows and 6 columns, representing a
balanced subset of a designed experiment varying 5 factors on the
soldering of components on printed-circuit boards.

## Usage

``` r
data(solder)
```

## Format

This data frame contains the following columns:

- `Opening`:

  a factor with levels `L` `M` `S` indicating the amount of clearance
  around the mounting pad.

- `Solder`:

  a factor with levels `Thick` `Thin` giving the thickness of the solder
  used.

- `Mask`:

  a factor with levels `A1.5` `A3` `B3` `B6` indicating the type and
  thickness of mask used.

- `PadType`:

  a factor with levels `D4` `D6` `D7` `L4` `L6` `L7` `L8` `L9` `W4` `W9`
  giving the size and geometry of the mounting pad.

- `Panel`:

  `1:3` indicating the panel on a board being tested.

- `skips`:

  a numeric vector giving the number of visible solder skips.

## Source

John M. Chambers and Trevor J. Hastie eds. (1992) *Statistical Models in
S*, Wadsworth and Brooks/Cole, Pacific Grove, CA 1992.

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
