# Control for Rpart Models

Various parameters that control aspects of the `rpart` fit.

## Usage

``` r
rpart.control(minsplit=5, minbucket=round(minsplit/3), cp=0.01, 
              maxcompete=4, maxsurrogate=0, usesurrogate=2, xval=10,
          surrogatestyle=0, maxdepth=30, ...)
```

## Arguments

- minsplit:

  the minimum number of observations that must exist in a node, in order
  for a split to be attempted.

- minbucket:

  the minimum number of observations in any terminal `<leaf>` node. If
  only one of `minbucket` or `minsplit` is specified, the code either
  sets `minsplit` to `minbucket*3` or `minbucket` to `minsplit/3`, as
  appropriate.

- cp:

  complexity parameter. Any split that does not decrease the overall
  lack of fit by a factor of `cp` is not attempted. For instance, with
  `anova` splitting, this means that the overall Rsquare must increase
  by `cp` at each step. The main role of this parameter is to save
  computing time by pruning off splits that are obviously not
  worthwhile. Essentially,the user informs the program that any split
  which does not improve the fit by `cp` will likely be pruned off by
  cross-validation, and that hence the program need not pursue it.

- maxcompete:

  the number of competitor splits retained in the output. It is useful
  to know not just which split was chosen, but which variable came in
  second, third, etc.

- maxsurrogate:

  the number of surrogate splits retained in the output. If this is set
  to zero the compute time will be shortened, since approximately half
  of the computational time (other than setup) is used in the search for
  surrogate splits.

- usesurrogate:

  how to use surrogates in the splitting process. 0= display only; an
  observation with a missing value for the primary split rule is not
  sent further down the tree. 1= use surrogates, in order, to split
  subjects missing the primary variable; if all surrogates are missing
  the observation is not split. 2= if all surrogates are missing, then
  send the observation in the majority direction. A value of 0
  corresponds to the action of tree, and 2 to the recommendations of
  Breiman, et.al.

- xval:

  number of cross-validations

- surrogatestyle:

  controls the selection of a best surrogate. If set to 0 (default) the
  program uses the total number of correct classification for a
  potential surrogate variable, if set to 1 it uses the percent correct,
  calculated over the non-missing values of the surrogate. The first
  option more severely penalizes covariates with a large number of
  missing values.

- maxdepth:

  Set the maximum depth of any node of the final tree, with the root
  node counted as depth 0 (past 30 `rpart` will give nonsense results on
  32-bit machines).

- ...:

  mop up other arguments.

## Value

a list containing the options.

## See also

[`rpart`](https://aurelienboye.github.io/mvpart/reference/rpart.md)
