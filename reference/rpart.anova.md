# Set up for \`anova' Method for an Rpart Model

Set up for `anova` method for an `rpart` model.

## Usage

``` r
rpart.anova(y, offset, parms, wt)
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

  the number of responses, here `1`,

- summary:

  a function to be invoked by
  [`summary.rpart`](https://aurelienboye.github.io/mvpart/reference/summary.rpart.md),

- text:

  a function to be invoked by
  [`text.rpart`](https://aurelienboye.github.io/mvpart/reference/text.rpart.md).

## Details

`rpart.anova` is to be used only by the function `rpart`.
