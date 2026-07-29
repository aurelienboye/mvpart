# Follow Paths to Selected Nodes of an Rpart Object

Returns a names list where each element contains the splits on the path
from the root to the selected nodes.

## Usage

``` r
path.rpart(tree, nodes, pretty=0, print.it=TRUE)
```

## Arguments

- tree:

  fitted model object of class `rpart`. This is assumed to be the result
  of some function that produces an object with the same named
  components as that returned by the `rpart` function.

- nodes:

  an integer vector containing indices (node numbers) of all nodes for
  which paths are desired. If missing, user selects nodes as described
  below.

- pretty:

  an integer denoting the extent to which factor levels in split labels
  will be abbreviated. A value of (0) signifies no abbreviation. A
  `NULL`, the default, signifies using elements of letters to represent
  the different factor levels.

- print.it:

  Logical. Denotes whether paths will be printed out as nodes are
  interactively selected. Irrelevant if `nodes` argument is supplied.

## Value

A named (by node) list, each element of which contains all the splits on
the path from the root to the specified or selected nodes.

## Graphical Interaction

A dendrogram of the `rpart` object is expected to be visible on the
graphics device, and a graphics input device (eg a mouse) is required.
Clicking (the selection button) on a node selects that node. This
process may be repeated any number of times. Clicking the exit button
will stop the selection process and return the list of paths.

## Details

The function has a required argument as an `rpart` object and a list of
nodes as optional arguments. Omitting a list of nodes will cause the
function to wait for the user to select nodes from the dendogram. It
will return a list, with one component for each node specified or
selected. The component contains the sequence of splits leading to that
node. In the graphical interation, the individual paths are printed out
as nodes are selected.

## References

This function was modified from `path.tree` in S.

## See also

[`rpart`](https://aurelienboye.github.io/mvpart/reference/rpart.md)

## Examples

``` r
data(kyphosis)
fit <- rpart(Kyphosis ~ Age + Number + Start, data=kyphosis)
summary(fit)
#> Call:
#> rpart(formula = Kyphosis ~ Age + Number + Start, data = kyphosis)
#>   n= 81 
#> 
#>           CP nsplit rel error   xerror      xstd
#> 1 0.17647059      0 1.0000000 1.000000 0.2155872
#> 2 0.11764706      1 0.8235294 1.352941 0.2387187
#> 3 0.07843137      2 0.7058824 1.235294 0.2320031
#> 4 0.05882353      5 0.4705882 1.235294 0.2320031
#> 5 0.01000000      9 0.2352941 1.176471 0.2282908
#> 
#> Node number 1: 81 observations,    complexity param=0.1764706
#>   predicted class=absent   expected loss=0.2098765
#>     class counts:    64    17
#>    probabilities: 0.790 0.210 
#>   left son=2 (62 obs) right son=3 (19 obs)
#>   Primary splits:
#>       Start  < 8.5   to the right, improve=6.762330, (0 missing)
#>       Number < 5.5   to the left,  improve=2.866795, (0 missing)
#>       Age    < 39.5  to the left,  improve=2.250212, (0 missing)
#> 
#> Node number 2: 62 observations,    complexity param=0.05882353
#>   predicted class=absent   expected loss=0.09677419
#>     class counts:    56     6
#>    probabilities: 0.903 0.097 
#>   left son=4 (29 obs) right son=5 (33 obs)
#>   Primary splits:
#>       Start  < 14.5  to the right, improve=1.0205280, (0 missing)
#>       Age    < 55    to the left,  improve=0.6848635, (0 missing)
#>       Number < 4.5   to the left,  improve=0.2975332, (0 missing)
#> 
#> Node number 3: 19 observations,    complexity param=0.1176471
#>   predicted class=present  expected loss=0.4210526
#>     class counts:     8    11
#>    probabilities: 0.421 0.579 
#>   left son=6 (2 obs) right son=7 (17 obs)
#>   Primary splits:
#>       Age    < 11.5  to the left,  improve=1.498452, (0 missing)
#>       Start  < 4     to the left,  improve=1.352047, (0 missing)
#>       Number < 4.5   to the left,  improve=1.149522, (0 missing)
#> 
#> Node number 4: 29 observations
#>   predicted class=absent   expected loss=0
#>     class counts:    29     0
#>    probabilities: 1.000 0.000 
#> 
#> Node number 5: 33 observations,    complexity param=0.05882353
#>   predicted class=absent   expected loss=0.1818182
#>     class counts:    27     6
#>    probabilities: 0.818 0.182 
#>   left son=10 (12 obs) right son=11 (21 obs)
#>   Primary splits:
#>       Age    < 55    to the left,  improve=1.2467530, (0 missing)
#>       Start  < 9.5   to the left,  improve=0.3009404, (0 missing)
#>       Number < 2.5   to the left,  improve=0.2181818, (0 missing)
#> 
#> Node number 6: 2 observations
#>   predicted class=absent   expected loss=0
#>     class counts:     2     0
#>    probabilities: 1.000 0.000 
#> 
#> Node number 7: 17 observations,    complexity param=0.07843137
#>   predicted class=present  expected loss=0.3529412
#>     class counts:     6    11
#>    probabilities: 0.353 0.647 
#>   left son=14 (12 obs) right son=15 (5 obs)
#>   Primary splits:
#>       Start  < 5.5   to the left,  improve=1.7647060, (0 missing)
#>       Number < 4.5   to the left,  improve=1.1361340, (0 missing)
#>       Age    < 130.5 to the right, improve=0.7170868, (0 missing)
#> 
#> Node number 10: 12 observations
#>   predicted class=absent   expected loss=0
#>     class counts:    12     0
#>    probabilities: 1.000 0.000 
#> 
#> Node number 11: 21 observations,    complexity param=0.05882353
#>   predicted class=absent   expected loss=0.2857143
#>     class counts:    15     6
#>    probabilities: 0.714 0.286 
#>   left son=22 (16 obs) right son=23 (5 obs)
#>   Primary splits:
#>       Age    < 98    to the right, improve=3.4714290, (0 missing)
#>       Start  < 12.5  to the right, improve=0.7936508, (0 missing)
#>       Number < 2.5   to the left,  improve=0.5714286, (0 missing)
#> 
#> Node number 14: 12 observations,    complexity param=0.07843137
#>   predicted class=absent   expected loss=0.5
#>     class counts:     6     6
#>    probabilities: 0.500 0.500 
#>   left son=28 (2 obs) right son=29 (10 obs)
#>   Primary splits:
#>       Age    < 130.5 to the right, improve=1.2000000, (0 missing)
#>       Number < 3.5   to the left,  improve=0.2222222, (0 missing)
#>       Start  < 4     to the left,  improve=0.2222222, (0 missing)
#> 
#> Node number 15: 5 observations
#>   predicted class=present  expected loss=0
#>     class counts:     0     5
#>    probabilities: 0.000 1.000 
#> 
#> Node number 22: 16 observations
#>   predicted class=absent   expected loss=0.125
#>     class counts:    14     2
#>    probabilities: 0.875 0.125 
#> 
#> Node number 23: 5 observations
#>   predicted class=present  expected loss=0.2
#>     class counts:     1     4
#>    probabilities: 0.200 0.800 
#> 
#> Node number 28: 2 observations
#>   predicted class=absent   expected loss=0
#>     class counts:     2     0
#>    probabilities: 1.000 0.000 
#> 
#> Node number 29: 10 observations,    complexity param=0.07843137
#>   predicted class=present  expected loss=0.4
#>     class counts:     4     6
#>    probabilities: 0.400 0.600 
#>   left son=58 (6 obs) right son=59 (4 obs)
#>   Primary splits:
#>       Age    < 93    to the left,  improve=2.133333, (0 missing)
#>       Number < 5.5   to the left,  improve=0.800000, (0 missing)
#>       Start  < 2.5   to the left,  improve=0.300000, (0 missing)
#> 
#> Node number 58: 6 observations,    complexity param=0.05882353
#>   predicted class=absent   expected loss=0.3333333
#>     class counts:     4     2
#>    probabilities: 0.667 0.333 
#>   left son=116 (3 obs) right son=117 (3 obs)
#>   Primary splits:
#>       Number < 4.5   to the left,  improve=1.3333330, (0 missing)
#>       Age    < 39.5  to the right, improve=0.1666667, (0 missing)
#> 
#> Node number 59: 4 observations
#>   predicted class=present  expected loss=0
#>     class counts:     0     4
#>    probabilities: 0.000 1.000 
#> 
#> Node number 116: 3 observations
#>   predicted class=absent   expected loss=0
#>     class counts:     3     0
#>    probabilities: 1.000 0.000 
#> 
#> Node number 117: 3 observations
#>   predicted class=present  expected loss=0.3333333
#>     class counts:     1     2
#>    probabilities: 0.333 0.667 
#> 
path.rpart(fit, node=c(11, 22))
#> 
#>  node number: 11 
#>    root
#>    Start>=8.5
#>    Start< 14.5
#>    Age>=55
#> 
#>  node number: 22 
#>    root
#>    Start>=8.5
#>    Start< 14.5
#>    Age>=55
#>    Age>=98
```
