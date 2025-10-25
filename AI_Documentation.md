
# AI.lua - Explanatory Documentation

This script provides a modular AI system for Roblox, including a state machine and behaviors such as Patrol, Follow, Wander, Seek.  
It is designed to be used server-side for decision calculations; movement can be handled via Humanoid.MoveTo or custom controls.

# AI Entity Structure
- **Model** : The AI model  
- **Humanoid** : Humanoid object  
- **Root** : RootPart (HumanoidRootPart)  
- **state** : Current state (string)  
- **data** : Custom data storage  
- **_tasks** : Internal list of running tasks  
- **_running** : Whether entity is active  

# Functions

## AI.CreateEntity(model)
Creates an AI entity from a model.  
- **model** : Model containing a Humanoid and HumanoidRootPart  
Returns **entity table** or nil with error string.

## AI.SetState(entity, newState, onEnterData)
Sets the AI entity state. Cancels running tasks.  
- **entity** : AI entity  
- **newState** : State name (string)  
- **onEnterData** : Optional data to store on state entry

## AI.Patrol(entity, points, opts)
Makes the entity patrol a series of points.  
- **points** : Table of Vector3 points  
- **opts.loop** : Loop patrol (default true)  
- **opts.speed** : WalkSpeed (default Humanoid.WalkSpeed or 16)

## AI.Follow(entity, targetModel, opts)
Makes the entity follow a target while maintaining a distance.  
- **targetModel** : Model to follow  
- **opts.distance** : Desired distance (default 6)  
- **opts.speed** : WalkSpeed

## AI.Seek(entity, position, opts)
Moves the entity to a single position and triggers optional callback on arrival.  
- **position** : Vector3 target  
- **opts.speed** : WalkSpeed  
- **opts.onComplete** : Function called when target reached

## AI.Wander(entity, center, radius, opts)
Random movement around a center within a radius.  
- **center** : Vector3 center  
- **radius** : Maximum wandering radius  
- **opts.speed** : WalkSpeed  
- **opts.interval** : Time between target changes (default random 2–5s)

## AI.PathTo(entity, destPos, opts)
Follows a path to a destination using Path module.  
- **destPos** : Vector3 target  
- **opts.pathParams** : Optional pathfinding parameters  
- **opts.smooth** : Boolean for waypoint smoothing  
- **opts.onComplete** / **onFail** : Callbacks

## AI.Stop(entity)
Stops all running tasks for the entity.

## AI.RunStateMachine(entity, states, initialState)
Runs a simple user-defined state machine.  
- **states** : Table of state definitions `{enter, update, exit}`  
- **initialState** : Optional initial state (default entity.state or "idle")

# Notes / Best Practices
- Each behavior uses **RunService.Heartbeat** for updates.  
- Store custom entity data in **entity.data**.  
- Ensure Humanoid and HumanoidRootPart exist before creating an entity.  
- Use **Stop** before destroying an entity to prevent lingering tasks.  
- State machine allows smooth transitions and modular AI behavior.  

# Example Usage
local ent = AI.CreateEntity(npcModel)
AI.Patrol(ent, {Vector3.new(0,0,0), Vector3.new(10,0,0)}, {loop=true, speed=16})
AI.Follow(ent, player.Character, {distance=5})
AI.Seek(ent, Vector3.new(5,0,5), {onComplete=function(reached) print(reached) end})
AI.Wander(ent, Vector3.new(0,0,0), 10)
AI.PathTo(ent, Vector3.new(10,0,10), {smooth=true, speed=12})
AI.SetState(ent, "alert")
AI.Stop(ent)
AI.RunStateMachine(ent, {
    idle = {enter=function(e) print("idle") end, update=function(e,dt) end}
})
