Cheat Sheet
================
Modified cheatsheet orginally created by Ian Curtiss

The example code below is organized by textbook chapter. This cheat
sheet allows you to copy the relevant code and paste it into your own
file. It is important to update all portions of the example code that
start and end with an underscore.

For example, `_DATANAME_` should be replaced with the name of the
dataset and `_VARIABLE_` should be replaced with the variable of
interest. Keep in mind that R is case sensitive, so if a variable is
named `height` in a dataset then R will not recognize variables
specified as `Height` or `HEIGHT`.

## Chapter 2: Analysis of Categorical Data

### Frequency Table

``` r
tbl_1var(_DATANAME_, ~ _VARIABLE_)
```

### Bar Graph Using Percent

``` r
plot_bar(_DATANAME_, ~ _VARIABLE_, type = "percent")
```

Note: Specify `na_rm = TRUE` to remove missing values from plot.

### Bar Graph Using Counts

``` r
plot_bar(_DATANAME_, ~ _VARIABLE_, type = "count")
```

Note: Specify `na_rm = TRUE` to remove missing values from plot.

### Two-Way Table

``` r
tbl_2var(_DATANAME_, _RESPONSE_ ~ _EXPLANATORY_)
```

### Clustered Bar Graph

``` r
plot_bar(_DATANAME_, ~ _RESPONSE_, fill = ~ _EXPLANATORY_)
```

Note: Specify `na_rm = TRUE` to remove missing values from the plot.

## Chapter 3: Analysis of One Quantitative Variable

### Basic Numerical Summaries

``` r
tbl_num_sum(_DATANAME_, ~ _VARIABLE_, na_rm = TRUE)
```

### Percentile

``` r
tbl_pctile(_DATANAME_, ~ _VARIABLE_, probs = c(_PERCENTILES_))
```

Note: Replace `_PERCENTILES_` with the desired values separated by
commas. For example, specifying `probs = c(0.80, 0.90, 0.95)` will
provide the 80th, 90th, and 95th percentiles for `_VARIABLE_`.

### Boxplot

``` r
plot_box(_DATANAME_, ~ _VARIABLE_)
```

### Histogram

``` r
plot_hist(_DATANAME_, ~ _VARIABLE_)
```

Note: The `breaks` argument controls how many bars there are. For
example, specifying `breaks = seq(_START_, _END_, _BY_)`, `_START_` and
`_END_` specify the lower and upper limits of the x-axis, respectively,
and `_BY_` tells R how wide to make the bins along the axis. Basic
numerical summaries obtained using `tbl_num_sum()` for `_VARIABLE_` can
help to select start and end values that will not truncate data shown in
the histogram.

### Basic Numerical Summaries By Group

``` r
tbl_num_sum(_DATANAME_, _RESPONSE_ ~ _GROUPVARIABLE_, na_rm = TRUE)
```

### Percentiles By Group

``` r
tbl_pctile(_DATANAME_, _RESPONSE_ ~ _GROUPVARIABLE_)
```

### Boxplot By Group

``` r
plot_box(_DATANAME_, _RESPONSE_ ~ _GROUPVARIABLE_)
```

### Histogram By Group

``` r
plot_hist(_DATANAME_, ~ _VARIABLE_, group = ~ _GROUPVARIABLE_)
```

## Chapter 5: Estimating a Population Parameter

Note: Confidence levels default to 95% but can be overridden with
`conf_lvl = _DECIMAL_`. For example, specifying `conf_lvl = 0.90` will
provide a 90% confidence interval.

### Confidence Interval for $p$

``` r
infer_1prop_int(_DATANAME_, ~ _VARIABLE_, success = "_SUCCESSCATEGORY_", conf_lvl = _CONFIDENCELEVEL_)
```

### Confidence Interval for $\mu$

``` r
infer_1mean_int(_DATANAME_, ~ _VARIABLE_, conf_lvl = _CONFIDENCELEVEL_)
```

## Chapter 6: Analysis of Two Quantitative Variabes

### Scatterplot

``` r
plot_scatter(_DATANAME_, _RESPONSE_ ~ _EXPLANATORY_, axis_lines = "none", ls_line = "hide")
```

Note: Specify `axis_lines = "both"` to add grid lines to the plot. Note:
Specify `ls_line = "show"` to overlay the least squares regression line
on the plot.

### Linear Correlation

``` r
tbl_corr(_DATANAME_, _RESPONSE_ ~ _EXPLANATORY_, na_rm = TRUE)
```

### Linear Regression

``` r
infer_reg(_DATANAME_, _RESPONSE_ ~ _EXPLANATORY_, reduced = "yes")
```

Note: Specify `reduced = "no"` to also include the $t$-test statistic
and p-value.

### Scatterplot By Group

``` r
plot_scatter(_DATANAME_, _RESPONSE_ ~ _EXPLANATORY_, fill = ~ _GROUPVARIABLE_, legend_title = "_LEGENDTITLE_")
```

Note: Replace `_LEGENDTITLE_` with a title for the legend.

## Chapter 7: Introduction to Hypothesis Testing

### $\chi ^2$-test

#### Implement chi-squared test of independence

``` r
infer_chisq(_DATANAME_, _EXPLANATORY_ ~ _RESPONSE_, type = "test")
```

#### Calculate expected counts

``` r
infer_chisq(_DATANAME_, _EXPLANATORY_ ~ _RESPONSE_, type = "expected")
```

#### Calculate observed counts

``` r
infer_chisq(_DATANAME_, _EXPLANATORY_ ~ _RESPONSE_, type = "observed")
```

### Confidence Interval for $p_1 - p_2$

Note: Confidence levels default to 95% but can be overridden with
`conf_lvl = _DECIMAL_`. For example, specifying `conf_lvl = 0.9` will
provide a 90% confidence interval.

``` r
infer_2prop_int(_DATANAME_, _RESPONSE_ ~ _EXPLANATORY_, success = _SUCCESSCATEGORY_, conf_lvl = _CONFIDENCELEVEL_)
```

Note: For this code to work the explanatory variable `_EXPLANATORY_`
must have only two categories.

## Chapter 8: Testing for Differences

### Dependent Samples $t$-test

``` r
infer_1mean_test(_DATANAME_, ~ _DIFFERENCEVARIABLE_)
```

### Independent Samples $t$-test

``` r
infer_2mean_test(_DATANAME_, _VARIABLE_ ~ _GROUPVARIABLE_)
```

### Confidence Interval for $\mu_1 - \mu_2$

``` r
infer_2mean_int(_DATANAME_, _VARIABLE_ ~ _GROUPVARIABLE_, conf_lvl = _CONFIDENCELEVEL_)
```

### ANOVA

``` r
infer_anova(_DATANAME_, _VARIABLE_ ~ _GROUPVARIABLE_)
```
