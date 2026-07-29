
<!-- README.md is generated from README.Rmd. Please edit that file -->

# mvpart

![Version](https://img.shields.io/badge/version-1.6--4-blue)
![R](https://img.shields.io/badge/R-%3E%3D4.5.1-blue)
![Platform](https://img.shields.io/badge/platform-macOS%20%7C%20Windows-lightgrey)
![License](https://img.shields.io/badge/license-GPL--2%20%7C%20GPL--3-lightgrey)
![Last
commit](https://img.shields.io/github/last-commit/aurelienboye/mvpart)

mvpart fits multivariate regression trees (De’ath 2002). See Section
4.11 of Borcard et al. (2018) for a nice summary of MRTs.

This is a fork of
[richardjtelford/mvpart](https://github.com/richardjtelford/mvpart),
itself a fork of the last archived version of mvpart on
[CRAN](https://cran.r-project.org/src/contrib/Archive/mvpart/).

The original CRAN version (1.6-2) was archived in 2014, and
richardjtelford’s fork (version 1.6-3) patched the namespace so it would
install on R 3.6, but its C source still failed to compile on more
recent R versions. This fork adds those additional C source patches, and
has been confirmed working on:

- **macOS** (Sonoma 14.2.1) - R 4.6.1
- **Windows** - R 4.5.1 and R 4.6.1

No changes were made to the package’s actual statistical logic — only to
make the C code compile under R’s modern, stricter header rules.

## Installation

You can install mvpart from [GitHub](https://github.com/) with:

``` r
# install.packages("remotes")
remotes::install_github("aurelienboye/mvpart")
```

If you’re on an older version of R (≤ 4.1.3) and hit unrelated issues
with this fork, you may also want to try
[richardjtelford/mvpart](https://github.com/richardjtelford/mvpart) or
the [original CRAN
archive](https://cran.r-project.org/src/contrib/Archive/mvpart/)
directly.

## Companion package: MVPARTwrap

[MVPARTwrap](https://github.com/cran/MVPARTwrap) adds several tools for
interpreting and extending MRT models: identifying the discriminant
species at each node, partitioning the total species variance across the
tree and its splits, computing an adjusted R² for an MRT model, running
cascade MRT analyses, and producing an alternative graphical
representation of the tree (Ouellette et al. 2012). Unlike `mvpart`,
it’s a pure-R package (no C source), so it installs on modern R without
any of the patches above, as long as this fork of `mvpart` is installed
first:

``` r
# install mvpart first (see above), then:
remotes::install_github("cran/MVPARTwrap")
```

## References

Borcard, D., F. Gillet, and P. Legendre. 2018. Numerical Ecology with R.
2nd edition. Springer, New York, NY.

De’ath, G. 2002. Multivariate regression trees: a new technique for
modeling species-environment relationships. Ecology 83:1105-1117.

Ouellette, M.-H., P. Legendre, and D. Borcard. 2012. Cascade
multivariate regression tree: a novel approach for modelling nested
explanatory sets. Methods in Ecology and Evolution 3:234-244.
