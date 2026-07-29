# Set up for \`dist' Method for an Rpart Model

Set up for `dist` method for an `rpart` model.

## Usage

``` r
rpart.dist(y, offset, parms, wt)
```

## Arguments

- y:

  the responses.

- offset:

  an offset, or `NULL`.

- parms:

  a list of parameters, usually empty.

- wt:

  case weights – ignored.

## Value

Returns a list consisting of

- y:

  (subtracting `offset` if necessary),

- parms:

  as input,

- numresp:

  the number of responses,

- summary:

  a function to be invoked by
  [`summary.rpart`](https://aurelienboye.github.io/mvpart/reference/summary.rpart.md),

- text:

  a function to be invoked by
  [`text.rpart`](https://aurelienboye.github.io/mvpart/reference/text.rpart.md).

## Details

`rpart.dist` is to be used only by the function `rpart`.
