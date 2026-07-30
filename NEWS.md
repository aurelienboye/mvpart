# mvpart 1.6-4

## This fork (aurelienboye/mvpart)

* Patched the C source so the package compiles on modern R, confirmed working on:
  - macOS, R 4.6.1
  - Windows, R 4.5.1 and R 4.6.1 (Rtools45/46)
  - Linux (Ubuntu, via GitHub Actions)
* Root cause: several old C constructs (empty-parameter function pointer declarations, K&R-style function definitions, removed S-compatibility macros/types) that R's headers used to tolerate are rejected under the C23 standard R 4.5+ selects by default on Windows. Fixes were prototype/declaration additions or macro renames; two genuine latent type-mismatch bugs were also found and fixed (`s_xpred.c`, `xval.c`), confirmed to have zero effect on results.
* No changes were made to the package's statistical logic.
* Updated `Maintainer`, `URL`, and `Bugs` fields to point to this fork.
* Moved `MVPARTwrap` from `Imports` to `Suggests` (it was creating a circular dependency, since `MVPARTwrap` itself depends on `mvpart`).
* Added a worked-example vignette (`mrt-worked-example`), using the Doubs fish dataset, demonstrating a full MRT workflow together with `MVPARTwrap`.

# mvpart 1.6-3

* richardjtelford's fork patched the package namespace so it would install on R 3.6.
* See <https://github.com/richardjtelford/mvpart> for details.

# mvpart 1.6.1

* Removed use of `assign` and passed parameters by name (2013-04-15).

# mvpart 1.6-0

* Fixed up a splitting error in `mrt.c` (2012-02-18).

# mvpart 1.4-0

* Investigated a reported problem with Mac versions; turned out to be a false alarm (2011-03-11).

# mvpart 1.3-1

* Fixed `format.g`, required for `summary()` of `rpart.dist` objects (2010-02-28).

# mvpart 1.3-0

* Fixed documentation to pass R checks and warnings (2009-12).

# mvpart 1.2-1

* Fixed `cmds.diss` to correctly pass arguments to the `xdiss` and `gdist` functions (2006-08-23).

# mvpart 1.0-1

* Modified extension of `rpart` (2004-11-11).

## About MVPART

The `mvpart` package is a modification of `rpart`:

* Authors of the original `rpart`: Terry M. Therneau and Beth Atkinson (<atkinson@mayo.edu>).
* R port of `rpart`: Brian Ripley (<ripley@stats.ox.ac.uk>).
* Modifications from `rpart` to `mvpart`: Glenn De'ath (<g.death@aims.gov.au>).

`mvpart` includes partitioning based on (1) multivariate numeric responses and (2) dissimilarity matrices. It was not possible to build a separate package depending on `rpart`, owing to the modifications needed in `rpart`'s C code to support these two new partitioning methods — as few changes as possible were made to `rpart` itself.

In addition to the C-code changes, the following changes and additions were made to the R functions:

1. A wrapper function for `rpart`, called `mvpart`, supporting selection of trees by cross-validation, interactive display, printing of results, etc.
2. Multivariate methods for representing and interpreting multivariate partitioning objects, including PCA plots and tree-cluster comparisons.
3. Methods for calculating additional forms of dissimilarities and for scaling matrices, designed in particular for community ecology.
4. `text.rpart` was modified to include graphical annotation of nodes.
