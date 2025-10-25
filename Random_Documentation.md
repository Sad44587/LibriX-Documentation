
# Random.lua - Explanatory Documentation

This module provides utility functions for randomization, weighted choices, shuffling, and seeded RNGs.  
Recommended usage: server-side or client-side for DevHelper or game utilities.

# Configuration
- **Random.Chance(prob)** : Probability check, returns true with given chance (default 0.5)  
- **Random.SeededRNG** : Class for seeded random numbers, useful for reproducibility  

# Functions

## Random.Chance(prob)
Returns a boolean based on a probability.  
- **prob** : Number between 0 and 1 (default 0.5)  
- Returns **true or false**.

## Random.Choice(arr)
Selects a random element from an array-style table.  
- **arr** : Table of items  
- Returns **one random element or nil** if table is empty.

## Random.WeightedChoice(items)
Selects an item with weighted probability.  
- **items** : Table of `{item=..., weight=number}`  
- Returns **selected item or nil** if all weights are zero.

## Random.Shuffle(arr)
Shuffles an array using Fisher-Yates algorithm.  
- **arr** : Table to shuffle  
- Returns **new shuffled table**.

## Random.Range(min, max)
Returns a random float between min and max.  
- **min, max** : Numbers  
- Returns **float**.

## Random.Int(min, max)
Returns a random integer inclusively between min and max.  
- **min, max** : Numbers  
- Returns **integer**.

## Random.Vector3(xMin, xMax, yMin, yMax, zMin, zMax)  
Generates a random Vector3 within given ranges, or via table `{x={min,max},y=...,z=...}`.  
- Returns **Vector3**.

## Random.Color3()
Returns a random Color3.  
- Returns **Color3 object**.

## Random.Gaussian(mu, sigma)
Returns a random number following Gaussian distribution.  
- **mu** : Mean (default 0)  
- **sigma** : Standard deviation (default 1)  
- Returns **float**.

## Random.SeededRNG.new(seed)
Creates a seeded RNG instance.  
- **seed** : Optional number  
- Returns **SeededRNG object**.

### SeededRNG:next()
Returns a float [0,1).  

### SeededRNG:int(min, max)
Returns a random integer using the seeded generator.  

### SeededRNG:range(min, max)
Returns a random float in [min, max) using seeded generator.  

## Random.ValueNoise1D(x, seed)
Generates 1D value noise based on seeded RNG.  
- **x** : Input coordinate  
- **seed** : Optional seed  
- Returns **float** between 0 and 1.

## Random.SplitInt(total, parts, minEach)
Splits an integer `total` into `parts` random integers, optionally with a minimum for each.  
- **total** : Total sum  
- **parts** : Number of parts (default 1)  
- **minEach** : Minimum value per part (default 0)  
- Returns **table of integers summing to total**.

# Example Usage
local rnd = Random.SeededRNG.new(123)
print(Random.Chance(0.7))
print(Random.Choice({"apple","banana","cherry"}))
local pathNoise = Random.ValueNoise1D(5.2, 42)
local splits = Random.SplitInt(10, 3, 1)
