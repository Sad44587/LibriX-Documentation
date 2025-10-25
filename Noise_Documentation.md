
# Noise.lua - Explanatory Documentation

This module provides simple Value Noise, Perlin-like gradient noise, and 2D Fractal Brownian Motion (FBM).  
Useful for terrain generation, procedural variations, and random patterns.  

# Functions

## Noise.ValueNoise1D(x, seed)
Generates 1D value noise.  
- **x** : Input coordinate (number)  
- **seed** : Optional seed for deterministic output  
- Returns **noise value between 0 and 1**.

## Noise.ValueNoise2D(x, y, seed)
Generates 2D value noise.  
- **x, y** : Input coordinates (numbers)  
- **seed** : Optional seed  
- Returns **noise value between 0 and 1**.

## Noise.FBM2D(x, y, octaves, lacunarity, gain, seed)
Generates Fractal Brownian Motion in 2D using value noise.  
- **x, y** : Coordinates  
- **octaves** : Number of layers (default 4)  
- **lacunarity** : Frequency multiplier per octave (default 2)  
- **gain** : Amplitude multiplier per octave (default 0.5)  
- **seed** : Optional seed  
- Returns **FBM noise value normalized between 0 and 1**.

## Noise.Perlin2D(x, y, seed)
Generates simple Perlin-like gradient noise in 2D.  
- **x, y** : Coordinates  
- **seed** : Optional seed  
- Returns **gradient noise value** (can be normalized if needed).

## Noise.Normalize01(value, minV, maxV)
Normalizes a noise value to the [0,1] range.  
- If **minV** and **maxV** are provided, uses them; otherwise assumes input range [-1,1].  
- Returns normalized value.

# Internal Helpers
- **hashInt(n, seed)** : Deterministic integer hash for reproducible noise  
- **smooth(t)** : Smoothstep interpolation function  
- **gradHash(ix, iy, seed)** : Generates pseudo-random gradient for Perlin2D  

# Example Usage
local val = Noise.ValueNoise1D(5.3, 42)
local val2D = Noise.ValueNoise2D(3.2, 7.1, 123)
local fbm = Noise.FBM2D(10, 15, 5, 2, 0.5, 99)
local perlin = Noise.Perlin2D(2.5, 4.7, 77)
local normalized = Noise.Normalize01(perlin)
