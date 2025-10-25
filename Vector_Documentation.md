
# Vector.lua - Explanatory Documentation

This module provides helper functions for Vector2 and Vector3 operations in Roblox,  
including normalization, angles, projections, reflections, magnitude clamping, and closest points.

# Functions

## Vector.SafeNormalize(v)
Safely normalizes a Vector2 or Vector3. Returns zero vector if magnitude is 0.  
- **v** : Vector2 or Vector3  
- Returns **normalized vector**.

## Vector.AngleBetween(a, b)
Computes the angle in radians between two vectors.  
- **a, b** : Vector2 or Vector3  
- Returns **angle in radians**.

## Vector.Project(a, b)
Projects vector **a** onto vector **b**.  
- **a, b** : Vector2 or Vector3  
- Returns **projected vector**.

## Vector.Reflect(v, n)
Reflects vector **v** around normal **n**.  
- **v, n** : Vector2 or Vector3  
- Returns **reflected vector**.

## Vector.ClampMagnitude(v, maxMag)
Clamps the magnitude of a vector to a maximum value.  
- **v** : Vector2 or Vector3  
- **maxMag** : Maximum magnitude  
- Returns **vector with clamped magnitude**.

## Vector.ClosestPointOnLine(a, b, p)
Finds the closest point on a line (defined by points A->B) to point P.  
- **a, b, p** : Vector3 points  
- Returns **Vector3 point**.

## Vector.ClosestPointOnSegment(a, b, p)
Finds the closest point on a line segment (A->B) to point P.  
- **a, b, p** : Vector3 points  
- Returns **Vector3 point**.

## Vector.Rotate2(v2, angle)
Rotates a Vector2 by a given angle in radians.  
- **v2** : Vector2  
- **angle** : Angle in radians  
- Returns **rotated Vector2**.

## Vector.ToPolar(v2)
Converts a Vector2 to polar coordinates (r, θ).  
- **v2** : Vector2  
- Returns **r, theta**.

## Vector.FromPolar(r, theta)
Converts polar coordinates to a Vector2.  
- **r** : Radius  
- **theta** : Angle in radians  
- Returns **Vector2**.

## Vector.RandomUnit3()
Generates a random unit Vector3 with uniform distribution on the sphere.  
- Returns **Vector3**.

## Vector.Flatten(v3, dropAxis)
Flattens a Vector3 into Vector2 by dropping one axis.  
- **v3** : Vector3  
- **dropAxis** : "X", "Y" (default), or "Z"  
- Returns **Vector2**.

# Example Usage
local vecUtil = require(game.ReplicatedStorage.Lib.Vector)

local v1 = Vector3.new(1,2,3)
local v2 = Vector3.new(4,5,6)
print(vecUtil.SafeNormalize(v1))
print(vecUtil.AngleBetween(v1, v2))
print(vecUtil.Project(v1, v2))
print(vecUtil.Reflect(v1, Vector3.new(0,1,0)))
print(vecUtil.ClampMagnitude(v1, 2))
local closest = vecUtil.ClosestPointOnSegment(v1, v2, Vector3.new(3,3,3))
local r, theta = vecUtil.ToPolar(Vector2.new(1,1))
local v2FromPolar = vecUtil.FromPolar(r, theta)
local randomVec = vecUtil.RandomUnit3()
local flat = vecUtil.Flatten(v1, "Y")
