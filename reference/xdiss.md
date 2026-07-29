# Extendend Dissimilarity Measures

The function computes extended dissimilarity indices which are for long
gradients have better good rank-order relation with gradient separation
and are thus efficient in community ordination with multidimensional
scaling.

## Usage

``` r
xdiss(data, dcrit = 1, dauto = TRUE, dinf = 0.5, method = "man", 
    use.min = TRUE, eps = 1e-04, replace.neg = TRUE, big = 10000,
    sumry = TRUE, full = FALSE, sq = FALSE)
```

## Arguments

- data:

  Data matrix

- dcrit:

  Dissimilarities \< `dcrit` are considered to have no species in common
  and are recalculated.

- dauto:

  Automatically select tuning parameters – recommended.

- method:

  Dissimilarity index

- use.min:

  Minimum dissimilarity of pairs of distances used – recommended.

- dinf, eps, replace.neg, big:

  Internal parameters – leave as is usually.

- sumry:

  Print summary of extended dissimilarities?

- full:

  Return the square dissimilarity matrix.

- sq:

  Square the dissimilarities – useful for distance-based partitionong.

## Details

The function knows the same dissimilarity indices as
[`gdist`](https://aurelienboye.github.io/mvpart/reference/gdist.md).

## Value

Returns an object of class distance with attributes "Size" and "ok".
"ok" is TRUE if rows are not disconnected (De'ath 1999).

## References

De'ath, G. (1999) Extended dissimilarity: a method of robust estimation
of ecological distances from high beta diversity data. *Plant Ecology*
144(2):191-199.

Faith, D.P, Minchin, P.R. and Belbin, L. (1987) Compositional
dissimilarity as a robust measure of ecological distance. *Vegetatio*
69, 57-68.

## Author

Glenn De'ath

## Examples

``` r
data(spider)
spider.dist <- xdiss(spider)
#> Using Extended Dissimilarity : Manhattan (Site Standardised by Mean)
#> Maximum distance =  0.9655 
#> Critical distance =  0.6474 
#> % Distances > Crit Dist =  29.89 
#> Summary of Extended Dissimilarities
#>    Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
#> 0.05587 0.33476 0.51946 0.54686 0.74297 1.27757 
```
