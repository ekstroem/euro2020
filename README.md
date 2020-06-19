# euro2020 (make that 2021)

Prediction competition for the Euro 2020 football winners from eRum 2020. 

The slides from the talk can be [found here](https://biostatistics.dk/talks/eRum2020/pred.pdf).

## Competition rules

To participate in the competition you need to upload a $7 \times 24$
prediction matrix. The 24 columns represent the 24 teams and the 7
rows represent the 7 different ranks that can be determined from the
tournament: 1st, 2nd, 3rd, 4th, 5th-8th, 9th-16th, 17th-24th.

The prediction matrix should be uploaded here as a PULL REQUEST of an
R matrix object that can be read by `load()` on R v4.0.0 or higher.

The **order** of the columns (the 24 teams) will be provided here
after the final play-off match in November 2020. Then we know the
names of all the 24 teams.

The **elements** of the prediction matrix should be the probabilities
that the given country (column) will obtain a specific
rank. Consequently, all columns must sum to 1.

The rows of the prediction matrix must sum to `c(1, 1, 1, 1, 4, 8,
8)`, respectively. These numbers represent the number of teams that
can be part of each rank.

The **deadline** for submission i Sunday June 6th, 2021 at midnight CET.


## Determining the winner

We will use the Tournament Rank Probability Score (TRPS) to determine
the best tournament prediction.

The TRPS is defined in [this paper](https://arxiv.org/abs/1912.07364) and implemented in the `socceR` package which can be installed from CRAN:



```r
install.packages("socceR")
```

Smaller numbers represents better predictions.


```r
library("socceR")
m1 <- matrix(c(1, 0, 0, 0, 0, 1, 0, 0, 0, 0, .5, .5, 0, 0, .5, .5), 4)
m1 # Prediction where certain on the top 2 ranks
```

```
##      [,1] [,2] [,3] [,4]
## [1,]    1    0  0.0  0.0
## [2,]    0    1  0.0  0.0
## [3,]    0    0  0.5  0.5
## [4,]    0    0  0.5  0.5
```

```r
trps(m1, c(1, 2, 3, 4))
```

```
## [1] 0.04166667
```


## How to model the tournament results

You are free to model the tournament results in any way you want. You
can even conjure them up. Run a complicated random forest model. Or
make educated armchair guesses. All that counts is the 7 x 24 matrix.


## Summarizing

Hopefully we can summarize some of the approaches on eRum 2022. In any case we will have updates and the winner listed here on GitHub.
