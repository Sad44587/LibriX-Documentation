
# Path.lua - Explanatory Documentation

This module wraps Roblox's PathfindingService with retries, waypoint smoothing, and utilities to follow paths.  
Recommended usage: server-side, for NPC or AI movement.

# Configuration
- **Path.MaxRetries** : Maximum attempts to compute a path (default 3)  
- **Path.AcceptableRadius** : Distance threshold to consider a waypoint reached (default 2)  
- **Path.RepathDelay** : Delay before recomputing a path if blocked (default 0.5 seconds)  

# Functions

## Path.CreatePath(params)
Creates a Path object with optional parameters.  
- **params.agentRadius** : NPC radius (default 2)  
- **params.agentHeight** : NPC height (default 5)  
- **params.agentMaxSlope** : Maximum slope angle (default 45)  
- **params.agentCanJump** : Allow jumping (default true)  
- Returns **Path object**.

## Path.Compute(origin, destination, params)
Computes a path between two points with retries.  
- **origin, destination** : Vector3 positions  
- **params** : Optional overrides for Path.CreatePath  
- Returns **success (bool), path object or error string**.

## Path.GetWaypoints(path)
Converts a Path object to a table of waypoints.  
- **path** : Path object  
- Returns **table of {Position = Vector3, Action = Enum.PathWaypointAction}**.

## Path.SmoothWaypoints(waypoints, tolerance)
Removes almost-collinear waypoints to smooth movement.  
- **waypoints** : Table of waypoints  
- **tolerance** : Maximum distance from line to remove waypoint (default 0.5)  
- Returns **smoothed waypoints table**.

## Path.FollowPath(model, pathObj, options)
Moves a Model along a path. Works best for Humanoids.  
- **model** : NPC or character model with Humanoid & HumanoidRootPart  
- **pathObj** : Path object  
- **options.speed** : Movement speed (default humanoid.WalkSpeed or 16)  
- **options.arriveRadius** : Optional waypoint radius (default AcceptableRadius)  
- **options.onStep(idx, pos)** : Callback on each waypoint  
- **options.onComplete()** : Callback when path complete  
- **options.onStuck()** : Callback if NPC gets stuck  
- Returns **true on start**; actual movement runs asynchronously.

## Path.ClosestWaypointIndex(waypoints, position)
Finds the nearest waypoint to a given position.  
- **waypoints** : Table of waypoints  
- **position** : Vector3 position  
- Returns **index of nearest waypoint, waypoint position**.

# Example Usage
local pathObj = Path.Compute(npc.Position, target.Position)
if pathObj then
    Path.FollowPath(npc.Model, pathObj, {speed=16, onComplete=function() print("Done") end})
end
