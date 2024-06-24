
<!-- README.md is generated from README.Rmd. Please edit that file -->

# saeHB.spatial

<!-- badges: start -->
<!-- badges: end -->

Provides several functions and datasets for area level of Small Area
Estimation under Spatial SAR Model using Hierarchical Bayesian (HB)
Method. Model-based estimators include the HB estimators based on a
Spatial Fay-Herriot model with univariate normal distribution for
variable of interest.The ‘rjags’ package is employed to obtain parameter
estimates. For the reference, see Rao and Molina (2015)
<doi:10.1002/9781118735855>.

## Author

Arina Mana Sikana, Azka Ubaidillah

## Maintaner

Arina Mana Sikana <sikanaradrianan@gmail.com>

## Function

-   `spatial.normal()` This function gives small area estimator under
    Spatial SAR Model and is implemented to variable of interest (y)
    that assumed to be a Normal Distribution. The range of data is (-∞
    \< y \< ∞)

## Installation

You can install the development version of `saeHB.spatial` from
[GitHub](https://github.com/) with:

``` r
# install.packages("devtools")
devtools::install_github("arinams/saeHB.spatial")
```

## Example

This is a basic example of using `spatial.normal()` function to make an
estimate based on synthetic data in this package

``` r
library(saeHB.spatial)

## For data without any non-sampled area
data(sp.norm)       # Load dataset
data(prox.mat)      # Load proximity Matrix

## For data with non-sampled area use sp.normNs

## Fitting model
result <- spatial.normal(y ~ x1 + x2, "vardir", prox.mat, data = sp.norm)
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
```

Estimated random effect variances

``` r
result$refVar
#>  [1] 3.374605 3.210616 2.883059 2.772039 2.772039 2.883059 3.210616 3.374605
#>  [9] 3.210616 2.944840 2.664411 2.571676 2.571676 2.664411 2.944840 3.210616
#> [17] 2.883059 2.664411 2.434569 2.360292 2.360292 2.434569 2.664411 2.883059
#> [25] 2.772039 2.571676 2.360292 2.294087 2.294087 2.360292 2.571676 2.772039
#> [33] 2.772039 2.571676 2.360292 2.294087 2.294087 2.360292 2.571676 2.772039
#> [41] 2.883059 2.664411 2.434569 2.360292 2.360292 2.434569 2.664411 2.883059
#> [49] 3.210616 2.944840 2.664411 2.571676 2.571676 2.664411 2.944840 3.210616
#> [57] 3.374605 3.210616 2.883059 2.772039 2.772039 2.883059 3.210616 3.374605
```

## References

-   Rao, J.N.K & Molina. (2015). Small Area Estimation 2nd Edition. New
    Jersey: John Wiley and Sons, Inc. <doi:10.1002/9781118735855>.
-   J. Kubacki and A. Jedrzejczak. (2016). Small Area Estimation of
    Income Under Spatial SAR Model. Statistics in Transition New Series,
    Vol. 17, No. 3, pp. 365–390. \<doi: 10.21307/stattrans-2016-028>.
-   H. C. Chung and G. S. Datta. (2020). Bayesian Hierarchical Spatial
    Models for Small Area Estimation. Research Report Series.
    Washington, D.C.: U.S. Census Bureau.
