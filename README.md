
<!-- README.md is generated from README.Rmd. Please edit that file -->

# saeHB.spatial

<!-- badges: start -->
<!-- badges: end -->

Provides several functions and datasets for area level of Small Area
Estimation under Spatial Model using Hierarchical Bayesian (HB) Method.
Model-based estimators include the HB estimators based on a Spatial
Fay-Herriot model with univariate normal distribution for variable of
interest.The ‘rjags’ package is employed to obtain parameter estimates.
For the reference, see Rao and Molina (2015)
<doi:10.1002/9781118735855>.

## Author

Arina Mana Sikana, Azka Ubaidillah

## Maintaner

Arina Mana Sikana <sikanaradrianan@gmail.com>

## Function

- `sar.normal()` This function gives small area estimator under Spatial
  SAR Model and is implemented to variable of interest (y) that assumed
  to be a Normal Distribution. The range of data is (-∞ \< y \< ∞)

## Installation

You can install the development version of `saeHB.spatial` from
[GitHub](https://github.com/) with:

``` r
# install.packages("devtools")
devtools::install_github("arinams/saeHB.spatial")
```

## Example

This is a basic example of using `sar.normal()` function to make an
estimate based on synthetic data in this package

``` r
library(saeHB.spatial)

## For data without any non-sampled area
data(sp.norm)       # Load dataset
data(prox.mat)      # Load proximity Matrix

## For data with non-sampled area use sp.normNs

## Fitting model
result <- sar.normal(y ~ x1 + x2, "vardir", prox.mat, data = sp.norm)
#> Compiling model graph
#>    Resolving undeclared variables
#>    Allocating nodes
#> Graph information:
#>    Observed stochastic nodes: 64
#>    Unobserved stochastic nodes: 6
#>    Total graph size: 8989
#> 
#> Initializing model
#> 
#> Compiling model graph
#>    Resolving undeclared variables
#>    Allocating nodes
#> Graph information:
#>    Observed stochastic nodes: 64
#>    Unobserved stochastic nodes: 6
#>    Total graph size: 8989
#> 
#> Initializing model
#> 
#> Compiling model graph
#>    Resolving undeclared variables
#>    Allocating nodes
#> Graph information:
#>    Observed stochastic nodes: 64
#>    Unobserved stochastic nodes: 6
#>    Total graph size: 8989
#> 
#> Initializing model
```

Small Area mean Estimates

``` r
result$Est
```

Estimated model coefficient

``` r
result$coefficient
#>           Mean         SD       2.5%        25%       50%       75%     97.5%
#> b[0] 0.1700130 0.74079233 -1.3348037 -0.2860765 0.2121135 0.7049094 1.4542826
#> b[1] 1.4196559 0.40454428  0.6013067  1.1724748 1.4341555 1.6957986 2.1986285
#> b[2] 1.1204738 0.05961372  0.9999717  1.0827609 1.1224242 1.1628727 1.2381436
#> rho  0.8166122 0.09833086  0.5842319  0.7573845 0.8349576 0.8915150 0.9572931
```

Estimated random effect variances

``` r
result$refVar
#>  [1] 8.248286 8.064647 7.659618 7.500457 7.500457 7.659618 8.064647 8.248286
#>  [9] 8.064647 7.777176 7.417112 7.278729 7.278729 7.417112 7.777176 8.064647
#> [17] 7.659618 7.417112 7.118359 7.005280 7.005280 7.118359 7.417112 7.659618
#> [25] 7.500457 7.278729 7.005280 6.904393 6.904393 7.005280 7.278729 7.500457
#> [33] 7.500457 7.278729 7.005280 6.904393 6.904393 7.005280 7.278729 7.500457
#> [41] 7.659618 7.417112 7.118359 7.005280 7.005280 7.118359 7.417112 7.659618
#> [49] 8.064647 7.777176 7.417112 7.278729 7.278729 7.417112 7.777176 8.064647
#> [57] 8.248286 8.064647 7.659618 7.500457 7.500457 7.659618 8.064647 8.248286
```

## References

- Rao, J.N.K & Molina. (2015). Small Area Estimation 2nd Edition. New
  Jersey: John Wiley and Sons, Inc. <doi:10.1002/9781118735855>.
- J. Kubacki and A. Jedrzejczak. (2016). Small Area Estimation of Income
  Under Spatial SAR Model. Statistics in Transition New Series, Vol. 17,
  No. 3, pp. 365–390. \<doi: 10.21307/stattrans-2016-028\>.
- H. C. Chung and G. S. Datta. (2020). Bayesian Hierarchical Spatial
  Models for Small Area Estimation. Research Report Series. Washington,
  D.C.: U.S. Census Bureau.
