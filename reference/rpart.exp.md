# Set up for \`exp' Method for an Rpart Model

Set up for the `exp` method for an `rpart` model.

## Usage

``` r
rpart.exp(y, offset, parms, wt)
```

## Arguments

- y:

  the responses, a vector or a two-column matrix.

- offset:

  an offset, or `NULL`.

- parms:

  a list of parameters.

- wt:

  case weights.

## Value

Returns a list consisting of

- y:

  a matrix giving the observation times and number of events,

- parms:

  a named list of parameters, with components `shrink` and `method` (1
  for `"deviance"`, 2 for `"sqrt"`),

- numresp:

  the number of responses, here `2`,

- numy:

  the number of columns in `y`, here `2`,

- summary:

  a function to be invoked by
  [`summary.rpart`](https://aurelienboye.github.io/mvpart/reference/summary.rpart.md),

- text:

  a function to be invoked by
  [`text.rpart`](https://aurelienboye.github.io/mvpart/reference/text.rpart.md).

## Details

`rpart.exp` is to be used only by the function `rpart`. It transforms
the data to look like a unit-rate Poisson process so that the
`rpart.exp` method can be used.
