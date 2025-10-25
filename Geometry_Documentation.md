
# Geometry.lua - Explanatory Documentation

This script provides geometric utilities for Roblox, including intersections, areas, barycentric coordinates, convex hull, projections, etc.  
It is designed to be used as a ModuleScript.

# Functions

## Geometry.PointToSegmentDistance(p, a, b)
Computes the distance from a point to a segment (2D or 3D).  
- **p** : Point (Vector2 or Vector3)  
- **a, b** : Segment endpoints (Vector2 or Vector3)  
Returns **distance** and **closest point on segment**.

## Geometry.SegmentIntersect2D(a1, a2, b1, b2)
Checks if two 2D segments intersect.  
- **a1, a2, b1, b2** : Vector2 endpoints  
Returns **boolean** and **intersection point if exists**.

## Geometry.PointInTriangle2D(p, a, b, c)
Checks if a 2D point lies inside a triangle using barycentric coordinates.  
- **p** : Point (Vector2)  
- **a, b, c** : Triangle vertices (Vector2)  
Returns **true/false**.

## Geometry.TriangleArea2D(a, b, c)
Calculates the area of a 2D triangle using cross product.  
- **a, b, c** : Vector2 vertices  
Returns **area**.

## Geometry.PolygonArea2D(points)
Calculates signed area of a 2D polygon.  
- **points** : Table of Vector2 points  
Returns **signed area**.

## Geometry.PointInPolygon2D(pt, polygon)
Checks if a 2D point is inside a polygon using the winding/raycast method.  
- **pt** : Vector2 point  
- **polygon** : Table of Vector2 points  
Returns **true/false**.

## Geometry.CircleIntersection2D(c1, r1, c2, r2)
Finds intersection points of two 2D circles.  
- **c1, c2** : Circle centers (Vector2)  
- **r1, r2** : Circle radii  
Returns a **table of 0,1,2 Vector2 points**.

## Geometry.RaycastPlane(origin, dir, planePoint, planeNormal)
Computes intersection of a ray with a plane.  
- **origin** : Ray origin (Vector3)  
- **dir** : Ray direction (Vector3)  
- **planePoint** : Point on plane (Vector3)  
- **planeNormal** : Plane normal (Vector3)  
Returns **intersection point** or nil.

## Geometry.Barycentric(a, b, c, p)
Computes barycentric coordinates for a point projected on a triangle.  
- **a, b, c** : Triangle vertices (Vector3)  
- **p** : Point (Vector3)  
Returns **u, v, w** or nil if degenerate.

## Geometry.ConvexHull2D(points)
Computes the convex hull of a set of 2D points using Graham scan.  
- **points** : Table of Vector2 points  
Returns **table of points in counter-clockwise order**.

# Notes / Best Practices
- Functions support both **Vector2 and Vector3** where applicable.  
- Degenerate cases (zero-area triangles, colinear points) are handled safely.  
- Use **PointToSegmentDistance** and **Barycentric** for precise geometric calculations.  
- **ConvexHull2D** sorts points and constructs the hull efficiently in O(n log n).  
- Functions can be combined for collision detection, hit tests, or physics calculations.

# Example Usage
local dist, closest = Geometry.PointToSegmentDistance(Vector3.new(1,2,0), Vector3.new(0,0,0), Vector3.new(5,0,0))
local inside = Geometry.PointInTriangle2D(Vector2.new(1,1), Vector2.new(0,0), Vector2.new(2,0), Vector2.new(1,2))
local area = Geometry.TriangleArea2D(Vector2.new(0,0), Vector2.new(1,0), Vector2.new(0,1))
local hull = Geometry.ConvexHull2D({Vector2.new(0,0), Vector2.new(1,1), Vector2.new(0,1)})
local bary = {Geometry.Barycentric(Vector3.new(0,0,0), Vector3.new(1,0,0), Vector3.new(0,1,0), Vector3.new(0.3,0.3,0))}
