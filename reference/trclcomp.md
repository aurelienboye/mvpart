# Tree-Clustering Comparison

This function compares the within-group variation for groups formed by
tree partitioning and unconstrained clustering. The results are plotted
and returned invisibly.

## Usage

``` r
trclcomp(x, method = "com", km = TRUE, mrt = TRUE)
```

## Arguments

- x:

  Rpart object with method "mrt" – see
  [`rpart`](https://aurelienboye.github.io/mvpart/reference/rpart.md)

- method:

  The clustering method for the unconstrained clustering

.

- km:

  If `TRUE` a K-Means clustering is compared with the multivariate tree
  partitioning.

- mrt:

  If `TRUE` an additional K-Means clustering with a starting
  configuration based on the multivariate tree partitioning is
  generated.

## Details

The within-group variation for groups formed by multivariate tree
partitioning and unconstrained clusterings are compared for all sizes of
the hierarchy of tree partitions.

## Value

Returns a list (invisibly) of the within-tree and within-cluster
variation for all tree sizes.

## References

De'ath G. (2002) Multivariate Regression Trees : A New Technique for
Constrained Classification Analysis. Ecology 83(4):1103-1117.

## Examples

``` r
data(spider)
fit <- mvpart(data.matrix(spider[,1:12])~herbs+reft+moss+sand+twigs+water,spider)

trclcomp(fit)
#> 1 2 3 

#> MRT error                :  1 0.481 0.336 
#> MRT.Cluster error        :  1 0.436 0.3 
#> Cluster error            :  1 0.436 0.341 
```
