ShrankhlaPandey_k21103886_AdvBioinformaticsAssignment
================

## GitHub RMarkdown Document

This is an R Markdown format used for publishing markdown documents to
GitHub. When you click the **Knit** button all R code chunks are run and
a markdown file (.md) suitable for publishing to GitHub is generated.

## Code begins here

``` r
#install.packages("tidyverse") #run only the first time
#install.packages("ggplot2") #run only the first time
library(ggplot2)
```

    ## Warning in register(): Can't find generic `scale_type` in package ggplot2 to
    ## register S3 method.

``` r
library(tidyverse)
```

    ## ── Attaching packages ─────────────────────────────────────── tidyverse 1.3.1 ──

    ## ✓ tibble  3.1.6     ✓ dplyr   1.0.8
    ## ✓ tidyr   1.1.4     ✓ stringr 1.4.0
    ## ✓ readr   2.1.2     ✓ forcats 0.5.1
    ## ✓ purrr   0.3.4

    ## ── Conflicts ────────────────────────────────────────── tidyverse_conflicts() ──
    ## x dplyr::filter() masks stats::filter()
    ## x dplyr::lag()    masks stats::lag()

``` r
cat(paste0("Question 3.1. Using the sum() function and : operator, write an expression in the code snippet to evaluate the sum of all integers between 5 and 55. (5pt)"))
```

    ## Question 3.1. Using the sum() function and : operator, write an expression in the code snippet to evaluate the sum of all integers between 5 and 55. (5pt)

``` r
a = 5
b = 55
n = b - a +1 
res_3.1 <- (n * (sum(a:b))) /2
cat(paste0("\nAnswer 3.1. Sum of all integers between 5 and 55 is = ",res_3.1))
```

    ## 
    ## Answer 3.1. Sum of all integers between 5 and 55 is = 39015

``` r
cat(paste0("Question 3.2. Write a function called sumfun with one input parameter, called n, that calculates the sum of all integers between 5 and n. Use the function to do the calculation for n = 10, n = 20, and n = 100 and present the results. (5pt) \n"))
```

    ## Question 3.2. Write a function called sumfun with one input parameter, called n, that calculates the sum of all integers between 5 and n. Use the function to do the calculation for n = 10, n = 20, and n = 100 and present the results. (5pt)

``` r
sumfun <- function(input) {
  p = input - 4 
  output <- (p * (sum(5:input))) /2
  return(output)
}

cat(paste0("Answer 3.2:"))
```

    ## Answer 3.2:

``` r
cat(paste0("\n sum of all integers between 5 and 10 is ", sumfun(10)))
```

    ## 
    ##  sum of all integers between 5 and 10 is 135

``` r
cat(paste0("\n sum of all integers between 5 and 20 is ", sumfun(20)))
```

    ## 
    ##  sum of all integers between 5 and 20 is 1600

``` r
cat(paste0("\n sum of all integers between 5 and 100 is ", sumfun(100)))
```

    ## 
    ##  sum of all integers between 5 and 100 is 241920

``` r
cat(paste0("Question 3.3. The famous Fibonacci series is calculated as the sum of the two preceding members of the sequence, where the first two steps in the sequence are 1, 1. Write an R script using a for loop to calculate and print out the first 12 entries of the Fibonacci series. (5pt) \n"))
```

    ## Question 3.3. The famous Fibonacci series is calculated as the sum of the two preceding members of the sequence, where the first two steps in the sequence are 1, 1. Write an R script using a for loop to calculate and print out the first 12 entries of the Fibonacci series. (5pt)

``` r
Fibonacci = list(1,1)
n1 = 1
n2 = 1
count=1
for (count in 1:10){
  nth = n1 + n2
  Fibonacci = append(Fibonacci, nth)
  # update values
  n1 = n2
  n2 = nth
  count = count + 1
}

cat(paste0("Answer 3.3 First 12 entries of the Fibonacci series are "))
```

    ## Answer 3.3 First 12 entries of the Fibonacci series are

``` r
cat(paste0(Fibonacci))
```

    ## 1 1 2 3 5 8 13 21 34 55 89 144

    ## Question 3.4. With the mtcars dataset bundled with R, use ggplot to generate a box of miles per gallon (in the variable mpg) as a function of the number of gears (in the variable gear). Use the fill aesthetic to colour bars by number of gears. (5pt)

![](ShrankhlaPandey_k21103886_AdvBioinformaticsAssignment_files/figure-gfm/question%203.4-1.png)<!-- -->

``` r
cat(paste0("Question 3.5. Using the cars dataset and the function lm, fit a linear relationship between speed and breaking distance in the variable distance. What are the fitted slope and intercept of the line, and their standard errors? What are the units used for the variables in the dataset? (5pt) \n"))
```

    ## Question 3.5. Using the cars dataset and the function lm, fit a linear relationship between speed and breaking distance in the variable distance. What are the fitted slope and intercept of the line, and their standard errors? What are the units used for the variables in the dataset? (5pt)

``` r
cars_linear_model <- lm(dist ~ speed, data=cars)
results3.5 <- cars_linear_model$coefficients
fitted_intercept <- results3.5[[1]]
cat("Answer 3.5: \nThe intercept of the fitted model is ",fitted_intercept)
```

    ## Answer 3.5: 
    ## The intercept of the fitted model is  -17.57909

``` r
cat(paste0("Summary of the Linear Model (Contains details about residual errors and standard errors in slope and intercept): "))
```

    ## Summary of the Linear Model (Contains details about residual errors and standard errors in slope and intercept):

``` r
fitted_slope <- results3.5[[2]]
cat("\nThe slope of the fitted model is ",fitted_slope)
```

    ## 
    ## The slope of the fitted model is  3.932409

``` r
#cat(paste0("\nThe standard error in slope is ", summary[["coefficients"]][[4]]))

cat(paste0("\nThe resdiual standard error of the model is ",summary(cars_linear_model)$sigma)) 
```

    ## 
    ## The resdiual standard error of the model is 15.3795867488199

    ## Question 3.6. Use ggplot to plot the data points from Task 6 and the linear fit. (5pt)

![](ShrankhlaPandey_k21103886_AdvBioinformaticsAssignment_files/figure-gfm/question%203.6-1.png)<!-- -->

``` r
cat(paste0("Question 3.7. Again using the cars dataset, now use linear regression (lm) to estimate the average reaction time for the driver to start braking (in seconds). To simplify matters you may assume that once braking commences, braking distance is proportional to the square of the speed. Explain the steps in your analysis. Do you get reasonable results? Finally, use ggplot to plot the data points and the fitted relationship. (10pt)"))
```

    ## Question 3.7. Again using the cars dataset, now use linear regression (lm) to estimate the average reaction time for the driver to start braking (in seconds). To simplify matters you may assume that once braking commences, braking distance is proportional to the square of the speed. Explain the steps in your analysis. Do you get reasonable results? Finally, use ggplot to plot the data points and the fitted relationship. (10pt)
