
# Math.lua - Explanatory Documentation

This module provides extended mathematical utilities for Roblox, including constants, wrappers, clamping, lerping, remapping, rounding, easing, random ranges, factorials, combinatorics, GCD/LCM, angles, approximate equality, linear regression, and vector helpers.

# Constants
- **Math.PI** : π  
- **Math.TAU** : 2π  
- **Math.EPSILON** : 1e-6

# Wrappers
- Standard math functions: `abs`, `acos`, `asin`, `atan`, `ceil`, `cos`, `deg`, `exp`, `floor`, `log`, `max`, `min`, `pow`, `rad`, `sin`, `sqrt`, `tan`, `atan2`

# Functions

## Math.sign(x)
Returns the sign of a number (-1, 0, 1).  

## Math.clamp(x, minVal, maxVal)
Clamps x between minVal and maxVal.

## Math.clamp01(x)
Clamps x to [0,1].

## Math.lerp(a, b, t)
Linear interpolation between a and b with t ∈ [0,1].

## Math.inverseLerp(a, b, value)
Returns t such that `lerp(a,b,t) = value`.

## Math.remap(value, inMin, inMax, outMin, outMax, doClamp)
Maps a value from one range to another, optionally clamped.

## Math.round(x, n)
Rounds x to n decimal places.

## Math.fract(x)
Returns fractional part of x.

## Math.repeatf(value, length)
Repeats/wraps value in [0,length].

## Math.wrap(value, minVal, maxVal)
Wraps value in [minVal, maxVal).

## Math.pingpong(value, length)
Returns a value that goes back and forth between 0 and length.

## Math.hypot(a, b)
Returns sqrt(a² + b²), supports optional b=0.

## Math.rsqrt(number)
Returns 1 / sqrt(number) using fast approximation.

## Math.distance(a, b)
Returns distance between numbers or Vector3s.

## Math.distanceSquared(a, b)
Returns squared distance.

## Math.map
Alias for remap.

## Math.smoothstep(edge0, edge1, x)
Performs smoothstep interpolation.

## Math.smootherstep(edge0, edge1, x)
Performs smootherstep interpolation.

## Easing Functions
- **Math.easeInQuad(t)**  
- **Math.easeOutQuad(t)**  
- **Math.easeInOutQuad(t)**  
- **Math.easeInCubic(t)**  
- **Math.easeOutCubic(t)**  
- **Math.easeInOutCubic(t)**  

## Math.randomRange(minVal, maxVal, integer)
Random float or inclusive integer if `integer=true`.

## Math.factorial(n)
Returns factorial of n.

## Math.binomial(n, k)
Returns n choose k.

## Math.gcd(a, b)
Returns greatest common divisor.

## Math.lcm(a, b)
Returns least common multiple.

## Math.normalizeAngleRad(theta)
Normalizes angle to [-π, π).

## Math.normalizeAngleDeg(d)
Normalizes angle to [-180,180).

## Math.approxEqual(a, b, tol)
Returns true if a ≈ b within tolerance.

## Math.linearRegression(xs, ys)
Performs simple linear regression, returns slope and intercept.

## Vector Helpers
- **Math.vectorLerp(a, b, t)** : Lerp between Vector3s.  
- **Math.vectorDistance(a, b)** : Distance between Vector3s.

# Example Usage
local MathUtil = require(game.ReplicatedStorage.Lib.Math)

print(MathUtil.clamp(5, 0, 10))          -- 5
print(MathUtil.lerp(0, 100, 0.25))      -- 25
print(MathUtil.remap(5, 0, 10, 0, 1))   -- 0.5
print(MathUtil.round(3.14159, 2))       -- 3.14
print(MathUtil.hypot(3,4))              -- 5
print(MathUtil.factorial(5))             -- 120
print(MathUtil.binomial(5,2))           -- 10
local slope, intercept = MathUtil.linearRegression({1,2,3}, {2,4,6})
print(slope, intercept)                  -- 2, 0
local lerpVec = MathUtil.vectorLerp(Vector3.new(0,0,0), Vector3.new(10,0,0), 0.5)
