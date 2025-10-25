# Physics.lua - Explanatory Documentation

This module provides physics utilities such as ballistic trajectories, projectile prediction, applied forces, and explosion impulses in Roblox.

# Configuration
- **Physics.Gravity** : Gravity value (default workspace.Gravity or 196.2 studs/s²)

# Functions

## Physics.PredictPosition(initialPos, initialVel, t, gravity)
Predicts the position of a projectile at time `t`.  
- **initialPos** : Vector3, starting position  
- **initialVel** : Vector3, initial velocity  
- **t** : time in seconds  
- **gravity** : optional gravity (default Physics.Gravity)  
- Returns **Vector3**, predicted position.

## Physics.SolveBallistic(sourcePos, targetPos, speed, gravity)
Calculates initial velocity vectors to hit a target in 3D.  
- **sourcePos** : Vector3  
- **targetPos** : Vector3  
- **speed** : magnitude of initial velocity  
- **gravity** : optional gravity (default Physics.Gravity)  
- Returns **table of Vector3 velocities** or `nil` + error string if no solution.

## Physics.Raycast(origin, direction, range, ignoreList, whitelist)
Wrapper around workspace:Raycast with filtering.  
- **origin** : Vector3  
- **direction** : Vector3  
- **range** : number (optional, default 1000)  
- **ignoreList** : table of instances to ignore  
- **whitelist** : boolean, if true uses whitelist filter instead of blacklist  
- Returns **RaycastResult** or nil.

## Physics.SphereCast(origin, radius, direction, maxDistance, ignoreList)
Approximate sphere cast using GetPartBoundsInRadius.  
- Returns **table of hits**, each `{Part, Position}`.

## Physics.ApplyExplosion(origin, radius, force, ignoreList)
Applies explosion force to nearby BaseParts.  
- **origin** : Vector3  
- **radius** : studs  
- **force** : magnitude of impulse  
- **ignoreList** : table of parts to ignore  
- Temporarily adds BodyVelocity to affected parts.

## Physics.ApplyImpulse(part, impulseVec, duration)
Applies a single impulse to a BasePart.  
- **part** : BasePart  
- **impulseVec** : Vector3  
- **duration** : seconds (optional, default 0.2)  
- Returns **true** if applied successfully.

## Physics.TimeToGround(initialY, vy, gravity)
Predicts time for a projectile to hit the ground (y=0).  
- **initialY** : number, starting Y position  
- **vy** : initial vertical velocity  
- **gravity** : optional gravity  
- Returns **time in seconds** or nil if no solution.

# Example Usage

```lua
local angles = Physics.SolveBallistic(origin.Position, target.Position, 50)
if angles then
    for _, vel in ipairs(angles) do
        local proj = Instance.new("Part")
        proj.Position = origin.Position
        proj.Velocity = vel
        proj.Parent = workspace
    end
end

local pos = Physics.PredictPosition(Vector3.new(0,10,0), Vector3.new(0,20,0), 1)