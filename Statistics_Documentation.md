
# Statistics.lua - Explanatory Documentation

This module provides basic statistical functions for arrays of numbers.  
Recommended usage: server-side or client-side for data analysis or gameplay statistics.

# Functions

## Statistics.Mean(arr)
Computes the arithmetic mean (average) of an array.  
- **arr** : Table of numbers  
- Returns **mean as number or nil if empty**.

## Statistics.Median(arr)
Computes the median of an array.  
- **arr** : Table of numbers  
- Returns **median number or nil if empty**.

## Statistics.Mode(arr)
Computes the mode(s) of an array. Returns a table in case of multiple modes.  
- **arr** : Table of numbers  
- Returns **table of most frequent value(s)**.

## Statistics.Variance(arr, sample)
Computes variance.  
- **arr** : Table of numbers  
- **sample** : Boolean, true for sample variance (n-1 denominator)  
- Returns **variance or nil if empty**.

## Statistics.Std(arr, sample)
Computes standard deviation.  
- **arr** : Table of numbers  
- **sample** : Boolean, true for sample std deviation  
- Returns **number or nil**.

## Statistics.Quantile(arr, p)
Computes quantile / percentile of array (0..1).  
- **arr** : Table of numbers  
- **p** : Fraction between 0 and 1  
- Returns **number or nil if invalid**.

## Statistics.Covariance(x, y, sample)
Computes covariance between two arrays.  
- **x, y** : Arrays of numbers (same length)  
- **sample** : Boolean, use sample denominator (n-1)  
- Returns **covariance number or nil**.

## Statistics.Correlation(x, y)
Computes Pearson correlation coefficient between two arrays.  
- **x, y** : Arrays of numbers  
- Returns **correlation (-1..1) or nil**.

## Statistics.LinearRegression(xs, ys)
Performs simple linear regression.  
- **xs, ys** : Arrays of numbers (same length)  
- Returns **slope, intercept** or nil if not computable.

## Statistics.RunningMean(state, newValue)
Updates running mean online.  
- **state** : Table `{count = n, mean = m}`  
- **newValue** : New number to add  
- Returns **updated state table**.

# Example Usage
local stats = require(game.ReplicatedStorage.Lib.Statistics)

local arr = {1,2,2,3,4}
print("Mean:", stats.Mean(arr))
print("Median:", stats.Median(arr))
print("Mode:", table.concat(stats.Mode(arr), ","))
print("Variance:", stats.Variance(arr, true))
print("Std:", stats.Std(arr, true))
print("Quantile 0.5:", stats.Quantile(arr, 0.5))

local xs, ys = {1,2,3}, {2,4,6}
local slope, intercept = stats.LinearRegression(xs, ys)
print("Slope:", slope, "Intercept:", intercept)

local state = {}
state = stats.RunningMean(state, 10)
state = stats.RunningMean(state, 20)
print("Running mean:", state.mean)
