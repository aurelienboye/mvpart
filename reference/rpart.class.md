# Set up for \`class' Method for an Rpart Model

Set up for the `class` method for an `rpart` model.

## Usage

``` r
rpart.class(y, offset, parms, wt)
```

## Arguments

- y:

  the responses.

- offset:

  `NULL`: anything else is an error.

- parms:

  a named list of parameters.

- wt:

  case weights.

## Value

Returns a list consisting of

- y:

  `y` as factor codes,

- parms:

  a named list of parameters. This will have components `prior`, `loss`
  and `split` (and more if supplied).

- numresp:

  the number of responses (one plus the number of classes).

- counts:

  a vector of counts for each class.

- ylevels:

  the response levels corresponding to the codes given in `y`.

- summary:

  a function to be invoked by
  [`summary.rpart`](https://aurelienboye.github.io/mvpart/reference/summary.rpart.md),

- text:

  a function to be invoked by
  [`text.rpart`](https://aurelienboye.github.io/mvpart/reference/text.rpart.md).

## Details

`rpart.class` is to be used only by the function `rpart`. It validates
the input parameter list: if that is missing or `NULL` default values
are supplied.

## See also

[`rpart`](https://aurelienboye.github.io/mvpart/reference/rpart.md)
