# Dissimilarity Measures

The function computes useful dissimilarity indices which are known to
have a good rank-order relation with gradient separation and are thus
efficient in community ordination with multidimensional scaling.

## Usage

``` r
gdist(x, method="bray", keepdiag=FALSE, full=FALSE, sq=FALSE)
```

## Arguments

- x:

  Data matrix

- method:

  Dissimilarity index

- keepdiag:

  Compute amd keep diagonals

- full:

  Return the square dissimilarity matrix

- sq:

  Square the dissimilarities – useful for distance-based partitioning

## Details

The function knows the following dissimilarity indices:

|  |  |
|----|----|
| `euclidean` | \\d\_{jk} = \sqrt{\sum_i (x\_{ij}-x\_{ik})^2}\\ |
| `manhattan` | \\d\_{jk} = \sum_i \|x\_{ij} - x\_{ik}\|\\ |
| `gower` | \\d\_{jk} = \sum_i \frac{\|x\_{ij}-x\_{ik}\|}{\max_i-\min_i}\\ |
| `canberra` | \\d\_{jk}=\frac{1}{N-Z} \sum_i \frac{\|x\_{ij}-x\_{ik}\|}{x\_{ij}+x\_{ik}}\\ |
| `bray` | \\d\_{jk} = \frac{\sum_i \|x\_{ij}-x\_{ik}\|}{\sum_i (x\_{ij}+x\_{ik})}\\ |
| `kulczynski` | \\d\_{jk} = 1-0.5(\frac{\sum_i \min(x\_{ij},x\_{ik})}{\sum_i x\_{ij}} + \frac{\sum_i \min(x\_{ij},x\_{ik})}{\sum_i x\_{ik}} )\\ |
| `maximum` | \\d\_{jk} = \max_i \|x\_{ij} - x\_{ik}\|\\ |
| `binary` | \\d\_{jk} = \sum_i \|x\_{ij}\>0 - x\_{ik}\>0\|\\ |
| `chord` | \\d\_{jk} = \sqrt{\sum_i (x\_{ij}-x\_{ik})^2} / {\sum_i (x\_{ij}+x\_{ik})^2}\\ |

where \\N-Z\\ is the number of non-zero entries.

Infamous ”double zeros” are removed in Canberra dissimilarity.

Euclidean and Manhattan dissimilarities are not good in gradient
separation without proper standardization but are still included for
comparison and special needs.

Some of indices become identical or rank-order similar after some
standardizations.

## Value

Should be interchangeable with
[`dist`](https://rdrr.io/r/stats/dist.html) and returns a distance
object of the same type.

## References

Faith, D.P, Minchin, P.R. and Belbin, L. (1987) Compositional
dissimilarity as a robust measure of ecological distance. *Vegetatio*
69, 57-68.

## Author

Jari Oksanen – modified Glenn De'ath (Dec 03)

## Note

The function is an alternative to
[`dist`](https://rdrr.io/r/stats/dist.html) adding some ecologically
meaningful indices. Both methods should produce similar types of objects
which can be interchanged in any method accepting either. Manhattan and
Euclidean dissimilarities should be identical in both methods, and
Canberra dissimilary may be similar.

## Examples

``` r
data(spider)
spider.dist <- gdist(spider[1:12,])
```
