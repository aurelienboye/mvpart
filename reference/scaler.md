# Row and Column Scaling of a Data Matrix

The function provides some popular (and effective) standardization
methods for community ecologists.

## Usage

``` r
scaler(x, col = c("mean1", "max1", "min0", "ssq1", "range01",
  "zsc", "pa", "rank")[2], row = c("mean1", "max1", "min0",
  "ssq1", "range01", "zsc", "pa", "rank")[1])
```

## Arguments

- x:

  Data matrix.

- col:

  Character vector of column standardizations.

- row:

  Character vector of row standardizations.

## Details

The function offers following data matrix standardizations:

- `mean1 `: scale to mean of 1.

- `max1 `: scale to maximum of 1.

- `ssq1 `: scale to sums of sqaures equal 1.

- `range01 `: scale range to 0-1.

- `zsc `: standardize to z-scores (mean=0, sd=1).

- `pa `: scale to presence/absence scale (0/1).

- `rank `: scale to rank order (1=lowest).

Standardizations are performed first on columns then on rows. "pa"
applies to the whole matrix and can be specied using row or col.

## Value

Returns the standardized matrix.

## Author

Jari Oksanen – modified Glenn De'ath (Dec 03)

## Note

Common transformations can be made with standard R functions.

## Examples

``` r
data(spider)
spid.data <- scaler(spider, col = "max", row="mean1")
```
