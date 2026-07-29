# Set up for \`poisson' Method for an Rpart Model

Set up for `poisson` method for an `rpart` model.

## Usage

``` r
rpart.poisson(y, offset, parms, wt)
```

## Arguments

- y:

  the responses, a vector or a two-column matrix. If a matrix the first
  column is the observation times and the second is the counts.

- offset:

  an offset, or `NULL`. The offset is interpreted as a log observation
  time.

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

`rpart.poisson` is to be used only by the function `rpart`.
