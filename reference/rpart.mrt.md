# Set up for \`mrt' Method for an Rpart Model

Set up for `mrt` method for an `rpart` model.

## Usage

``` r
rpart.mrt(y, offset, parms, wt)
```

## Arguments

- y:

  the responses.

- offset:

  an offset, or `NULL`.

- parms:

  a list of parameters, usually empty.

- wt:

  case weights.

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

- bar:

  a function to be invoked by
  [`text.rpart`](https://aurelienboye.github.io/mvpart/reference/text.rpart.md).

## Details

`rpart.mrt` is to be used only by the function `rpart`.
