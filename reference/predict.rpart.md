# Predictions from a Fitted Rpart Object

Returns a vector of predicted responses from a fitted `rpart` object.

## Usage

``` r
# S3 method for class 'rpart'
predict(object, newdata=list(),
       type=c("vector", "prob", "class", "matrix", "where"), ...)
```

## Arguments

- object:

  fitted model object of class `rpart`. This is assumed to be the result
  of some function that produces an object with the same named
  components as that returned by the `rpart` function.

- newdata:

  data frame containing the values at which predictions are required.
  The predictors referred to in the right side of `formula(object)` must
  be present by name in `newdata`. If missing, the fitted values are
  returned.

- type:

  character string denoting the type of predicted value returned. If the
  `rpart` object is a classification tree, then the default is to return
  `prob` predictions, a matrix whose columns are the probability of the
  first, second, etc. class. (This agrees with the default behavior of
  tree). Otherwise, a vector result is returned.

- ...:

  further arguments passed to or from other methods.

## Value

A new object is obtained by dropping `newdata` down the object. For
factor predictors, if an observation contains a level not used to grow
the tree, it is left at the deepest possible node and `frame$yval` at
the node is the prediction.

If `type="vector"`:  
vector of predicted responses. For regression trees this is the mean
response at the node, for Poisson trees it is the estimated response
rate, and for classification trees it is the predicted class.

If `type="prob"`:  
(for a classification tree) a matrix of class probabilities.

If `type="matrix"`:  
a matrix of the full responses (`frame$yval2` if this exists, otherwise
`frame$yval`). For regression trees, this is the mean response, for
Poisson trees it is the response rate and the number of events at that
node in the fitted tree, and for classification trees it is the
concatonation of the predicted class, the class counts at that node in
the fitted tree, and the class probabilities.

If `type="class"`:  
(for a classification tree) a factor of classifications based on the
responses.

## Details

This function is a method for the generic function predict for class
`rpart`. It can be invoked by calling `predict` for an object of the
appropriate class, or directly by calling `predict.rpart` regardless of
the class of the object.

## See also

[`predict`](https://rdrr.io/r/stats/predict.html),
[`rpart.object`](https://aurelienboye.github.io/mvpart/reference/rpart.object.md)

## Examples

``` r
data(car.test.frame)
z.auto <- rpart(Mileage ~ Weight, car.test.frame)
predict(z.auto)
#>                Eagle Summit 4               Ford Escort   4 
#>                      30.50000                      30.50000 
#>                Ford Festiva 4                 Honda Civic 4 
#>                      34.00000                      34.00000 
#>               Mazda Protege 4              Mercury Tracer 4 
#>                      30.50000                      25.66667 
#>               Nissan Sentra 4              Pontiac LeMans 4 
#>                      34.00000                      30.50000 
#>               Subaru Loyale 4                Subaru Justy 3 
#>                      25.66667                      34.00000 
#>              Toyota Corolla 4               Toyota Tercel 4 
#>                      30.50000                      34.00000 
#>            Volkswagen Jetta 4           Chevrolet Camaro V8 
#>                      25.66667                      21.06250 
#>                 Dodge Daytona               Ford Mustang V8 
#>                      23.80000                      21.06250 
#>                    Ford Probe          Honda Civic CRX Si 4 
#>                      27.00000                      34.00000 
#>        Honda Prelude Si 4WS 4                Nissan 240SX 4 
#>                      27.00000                      23.80000 
#>                Plymouth Laser                   Subaru XT 4 
#>                      23.80000                      30.50000 
#>                     Audi 80 4               Buick Skylark 4 
#>                      27.00000                      23.33333 
#>           Chevrolet Beretta 4          Chrysler Le Baron V6 
#>                      27.00000                      23.80000 
#>                  Ford Tempo 4                Honda Accord 4 
#>                      23.80000                      23.80000 
#>                   Mazda 626 4           Mitsubishi Galant 4 
#>                      23.80000                      27.00000 
#>           Mitsubishi Sigma V6               Nissan Stanza 4 
#>                      21.06250                      23.80000 
#>           Oldsmobile Calais 4                 Peugeot 405 4 
#>                      23.33333                      23.33333 
#>               Subaru Legacy 4                Toyota Camry 4 
#>                      23.80000                      23.80000 
#>                   Volvo 240 4               Acura Legend V6 
#>                      23.80000                      21.06250 
#>               Buick Century 4       Chrysler Le Baron Coupe 
#>                      23.80000                      23.80000 
#>        Chrysler New Yorker V6              Eagle Premier V6 
#>                      21.06250                      21.06250 
#>                Ford Taurus V6           Ford Thunderbird V6 
#>                      21.06250                      21.06250 
#>              Hyundai Sonata 4                  Mazda 929 V6 
#>                      23.80000                      21.06250 
#>              Nissan Maxima V6    Oldsmobile Cutlass Ciera 4 
#>                      21.06250                      23.80000 
#> Oldsmobile Cutlass Supreme V6             Toyota Cressida 6 
#>                      21.06250                      21.06250 
#>             Buick Le Sabre V6          Chevrolet Caprice V8 
#>                      21.06250                      18.66667 
#>    Ford LTD Crown Victoria V8       Chevrolet Lumina APV V6 
#>                      18.66667                      21.06250 
#>        Dodge Grand Caravan V6              Ford Aerostar V6 
#>                      18.66667                      18.66667 
#>                  Mazda MPV V6            Mitsubishi Wagon 4 
#>                      18.66667                      21.06250 
#>               Nissan Axxess 4                  Nissan Van 4 
#>                      21.06250                      18.66667 

data(kyphosis)
fit <- rpart(Kyphosis ~ Age + Number + Start, data=kyphosis)
predict(fit, type="prob")   # class probabilities (default)
#>       absent   present
#> 1  1.0000000 0.0000000
#> 2  0.8750000 0.1250000
#> 3  0.0000000 1.0000000
#> 4  1.0000000 0.0000000
#> 5  1.0000000 0.0000000
#> 6  1.0000000 0.0000000
#> 7  1.0000000 0.0000000
#> 8  1.0000000 0.0000000
#> 9  1.0000000 0.0000000
#> 10 0.2000000 0.8000000
#> 11 0.2000000 0.8000000
#> 12 1.0000000 0.0000000
#> 13 0.3333333 0.6666667
#> 14 1.0000000 0.0000000
#> 15 1.0000000 0.0000000
#> 16 1.0000000 0.0000000
#> 17 1.0000000 0.0000000
#> 18 0.8750000 0.1250000
#> 19 1.0000000 0.0000000
#> 20 1.0000000 0.0000000
#> 21 1.0000000 0.0000000
#> 22 0.0000000 1.0000000
#> 23 0.2000000 0.8000000
#> 24 1.0000000 0.0000000
#> 25 0.3333333 0.6666667
#> 26 1.0000000 0.0000000
#> 27 1.0000000 0.0000000
#> 28 0.8750000 0.1250000
#> 29 1.0000000 0.0000000
#> 30 1.0000000 0.0000000
#> 31 1.0000000 0.0000000
#> 32 0.8750000 0.1250000
#> 33 0.8750000 0.1250000
#> 34 1.0000000 0.0000000
#> 35 0.8750000 0.1250000
#> 36 1.0000000 0.0000000
#> 37 1.0000000 0.0000000
#> 38 0.0000000 1.0000000
#> 39 1.0000000 0.0000000
#> 40 0.2000000 0.8000000
#> 41 0.3333333 0.6666667
#> 42 1.0000000 0.0000000
#> 43 1.0000000 0.0000000
#> 44 1.0000000 0.0000000
#> 45 1.0000000 0.0000000
#> 46 0.8750000 0.1250000
#> 47 1.0000000 0.0000000
#> 48 0.8750000 0.1250000
#> 49 0.0000000 1.0000000
#> 50 0.8750000 0.1250000
#> 51 0.2000000 0.8000000
#> 52 1.0000000 0.0000000
#> 53 0.0000000 1.0000000
#> 54 1.0000000 0.0000000
#> 55 1.0000000 0.0000000
#> 56 1.0000000 0.0000000
#> 57 1.0000000 0.0000000
#> 58 0.0000000 1.0000000
#> 59 1.0000000 0.0000000
#> 60 0.8750000 0.1250000
#> 61 0.0000000 1.0000000
#> 62 0.0000000 1.0000000
#> 63 1.0000000 0.0000000
#> 64 1.0000000 0.0000000
#> 65 1.0000000 0.0000000
#> 66 1.0000000 0.0000000
#> 67 1.0000000 0.0000000
#> 68 0.8750000 0.1250000
#> 69 1.0000000 0.0000000
#> 70 1.0000000 0.0000000
#> 71 0.8750000 0.1250000
#> 72 0.8750000 0.1250000
#> 73 1.0000000 0.0000000
#> 74 0.8750000 0.1250000
#> 75 1.0000000 0.0000000
#> 76 1.0000000 0.0000000
#> 77 0.8750000 0.1250000
#> 78 1.0000000 0.0000000
#> 79 0.8750000 0.1250000
#> 80 0.0000000 1.0000000
#> 81 1.0000000 0.0000000
predict(fit, type="vector") # level numbers
#>  1  2  3  4  5  6  7  8  9 10 11 12 13 14 15 16 17 18 19 20 21 22 23 24 25 26 
#>  1  1  2  1  1  1  1  1  1  2  2  1  2  1  1  1  1  1  1  1  1  2  2  1  2  1 
#> 27 28 29 30 31 32 33 34 35 36 37 38 39 40 41 42 43 44 45 46 47 48 49 50 51 52 
#>  1  1  1  1  1  1  1  1  1  1  1  2  1  2  2  1  1  1  1  1  1  1  2  1  2  1 
#> 53 54 55 56 57 58 59 60 61 62 63 64 65 66 67 68 69 70 71 72 73 74 75 76 77 78 
#>  2  1  1  1  1  2  1  1  2  2  1  1  1  1  1  1  1  1  1  1  1  1  1  1  1  1 
#> 79 80 81 
#>  1  2  1 
predict(fit, type="class")  # factor
#>       1       2       3       4       5       6       7       8       9      10 
#>  absent  absent present  absent  absent  absent  absent  absent  absent present 
#>      11      12      13      14      15      16      17      18      19      20 
#> present  absent present  absent  absent  absent  absent  absent  absent  absent 
#>      21      22      23      24      25      26      27      28      29      30 
#>  absent present present  absent present  absent  absent  absent  absent  absent 
#>      31      32      33      34      35      36      37      38      39      40 
#>  absent  absent  absent  absent  absent  absent  absent present  absent present 
#>      41      42      43      44      45      46      47      48      49      50 
#> present  absent  absent  absent  absent  absent  absent  absent present  absent 
#>      51      52      53      54      55      56      57      58      59      60 
#> present  absent present  absent  absent  absent  absent present  absent  absent 
#>      61      62      63      64      65      66      67      68      69      70 
#> present present  absent  absent  absent  absent  absent  absent  absent  absent 
#>      71      72      73      74      75      76      77      78      79      80 
#>  absent  absent  absent  absent  absent  absent  absent  absent  absent present 
#>      81 
#>  absent 
#> Levels: absent present
predict(fit, type="matrix") # level number, class frequencies, probabilities
#>    [,1] [,2] [,3]      [,4]      [,5]
#> 1     1    3    0 1.0000000 0.0000000
#> 2     1   14    2 0.8750000 0.1250000
#> 3     2    0    4 0.0000000 1.0000000
#> 4     1    2    0 1.0000000 0.0000000
#> 5     1   29    0 1.0000000 0.0000000
#> 6     1   29    0 1.0000000 0.0000000
#> 7     1   29    0 1.0000000 0.0000000
#> 8     1   29    0 1.0000000 0.0000000
#> 9     1   29    0 1.0000000 0.0000000
#> 10    2    1    4 0.2000000 0.8000000
#> 11    2    1    4 0.2000000 0.8000000
#> 12    1   29    0 1.0000000 0.0000000
#> 13    2    1    2 0.3333333 0.6666667
#> 14    1   12    0 1.0000000 0.0000000
#> 15    1   29    0 1.0000000 0.0000000
#> 16    1   29    0 1.0000000 0.0000000
#> 17    1   29    0 1.0000000 0.0000000
#> 18    1   14    2 0.8750000 0.1250000
#> 19    1   29    0 1.0000000 0.0000000
#> 20    1   12    0 1.0000000 0.0000000
#> 21    1   29    0 1.0000000 0.0000000
#> 22    2    0    4 0.0000000 1.0000000
#> 23    2    1    4 0.2000000 0.8000000
#> 24    1    2    0 1.0000000 0.0000000
#> 25    2    1    2 0.3333333 0.6666667
#> 26    1   12    0 1.0000000 0.0000000
#> 27    1    2    0 1.0000000 0.0000000
#> 28    1   14    2 0.8750000 0.1250000
#> 29    1   29    0 1.0000000 0.0000000
#> 30    1   29    0 1.0000000 0.0000000
#> 31    1   29    0 1.0000000 0.0000000
#> 32    1   14    2 0.8750000 0.1250000
#> 33    1   14    2 0.8750000 0.1250000
#> 34    1   29    0 1.0000000 0.0000000
#> 35    1   14    2 0.8750000 0.1250000
#> 36    1   29    0 1.0000000 0.0000000
#> 37    1   12    0 1.0000000 0.0000000
#> 38    2    0    5 0.0000000 1.0000000
#> 39    1   12    0 1.0000000 0.0000000
#> 40    2    1    4 0.2000000 0.8000000
#> 41    2    1    2 0.3333333 0.6666667
#> 42    1   12    0 1.0000000 0.0000000
#> 43    1    2    0 1.0000000 0.0000000
#> 44    1    3    0 1.0000000 0.0000000
#> 45    1   29    0 1.0000000 0.0000000
#> 46    1   14    2 0.8750000 0.1250000
#> 47    1   29    0 1.0000000 0.0000000
#> 48    1   14    2 0.8750000 0.1250000
#> 49    2    0    4 0.0000000 1.0000000
#> 50    1   14    2 0.8750000 0.1250000
#> 51    2    1    4 0.2000000 0.8000000
#> 52    1   29    0 1.0000000 0.0000000
#> 53    2    0    5 0.0000000 1.0000000
#> 54    1   29    0 1.0000000 0.0000000
#> 55    1   29    0 1.0000000 0.0000000
#> 56    1   29    0 1.0000000 0.0000000
#> 57    1   12    0 1.0000000 0.0000000
#> 58    2    0    5 0.0000000 1.0000000
#> 59    1   12    0 1.0000000 0.0000000
#> 60    1   14    2 0.8750000 0.1250000
#> 61    2    0    4 0.0000000 1.0000000
#> 62    2    0    5 0.0000000 1.0000000
#> 63    1    3    0 1.0000000 0.0000000
#> 64    1   29    0 1.0000000 0.0000000
#> 65    1   29    0 1.0000000 0.0000000
#> 66    1   12    0 1.0000000 0.0000000
#> 67    1   29    0 1.0000000 0.0000000
#> 68    1   14    2 0.8750000 0.1250000
#> 69    1   12    0 1.0000000 0.0000000
#> 70    1   29    0 1.0000000 0.0000000
#> 71    1   14    2 0.8750000 0.1250000
#> 72    1   14    2 0.8750000 0.1250000
#> 73    1   29    0 1.0000000 0.0000000
#> 74    1   14    2 0.8750000 0.1250000
#> 75    1   29    0 1.0000000 0.0000000
#> 76    1   29    0 1.0000000 0.0000000
#> 77    1   14    2 0.8750000 0.1250000
#> 78    1   12    0 1.0000000 0.0000000
#> 79    1   14    2 0.8750000 0.1250000
#> 80    2    0    5 0.0000000 1.0000000
#> 81    1   12    0 1.0000000 0.0000000

data(iris)
sub <- c(sample(1:50, 25), sample(51:100, 25), sample(101:150, 25))
fit <- rpart(Species ~ ., data=iris, subset=sub)
fit
#> n= 75 
#> 
#> node), split, n, loss, yval, (yprob)
#>       * denotes terminal node
#> 
#>  1) root 75 50 setosa (0.33333333 0.33333333 0.33333333)  
#>    2) Petal.Length< 2.45 25  0 setosa (1.00000000 0.00000000 0.00000000) *
#>    3) Petal.Length>=2.45 50 25 versicolor (0.00000000 0.50000000 0.50000000)  
#>      6) Petal.Width< 1.75 27  3 versicolor (0.00000000 0.88888889 0.11111111)  
#>       12) Petal.Length< 5.35 25  1 versicolor (0.00000000 0.96000000 0.04000000) *
#>       13) Petal.Length>=5.35 2  0 virginica (0.00000000 0.00000000 1.00000000) *
#>      7) Petal.Width>=1.75 23  1 virginica (0.00000000 0.04347826 0.95652174) *
table(predict(fit, iris[-sub,], type="class"), iris[-sub, "Species"])
#>             
#>              setosa versicolor virginica
#>   setosa         25          0         0
#>   versicolor      0         25         2
#>   virginica       0          0        23
```
