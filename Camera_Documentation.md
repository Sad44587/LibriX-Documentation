
# Camera.lua - Explanatory Documentation

This module provides simplified camera management in Roblox, including tweening, shake, follow, and look-at functions.  
Recommended usage: client-side for camera control.

# Configuration
- **Camera.DefaultFOV** : Default camera FieldOfView  
- **Camera.DefaultCFrame** : Default camera CFrame  
- **Camera.ShakeMagnitude** : Default shake magnitude  

# Functions

## Camera.TweenTo(cframe, duration, easingStyle, easingDirection, callback)
Tweens the camera to a given CFrame.  
- **cframe** : Target CFrame  
- **duration** : Seconds (default 0.5)  
- **easingStyle** : Enum.EasingStyle (default Quad)  
- **easingDirection** : Enum.EasingDirection (default Out)  
- **callback** : Function called when tween completes  
- Returns **Tween instance**.

## Camera.SetFOV(fov, duration)
Tweens the camera FieldOfView.  
- **fov** : FieldOfView value  
- **duration** : Seconds (default 0.3)  
- Returns **Tween instance**.

## Camera.Shake(magnitude, duration)
Applies a camera shake effect.  
- **magnitude** : Shake strength (default 1)  
- **duration** : Duration in seconds (default 0.5)  
- Returns **nil**.

## Camera.Follow(target, offset)
Follows a target (HumanoidRootPart) with an optional offset.  
- **target** : Instance to follow  
- **offset** : Vector3 offset from target (default {0,5,10})  
- Returns **nil**.

## Camera.StopFollow()
Stops any active follow behavior.  
- Returns **nil**.

## Camera.LookAt(position)
Orients the camera to look at a specific position.  
- **position** : Vector3 target position  
- Returns **nil**.

## Camera.Reset()
Resets camera to default CFrame and FieldOfView.  
- Returns **nil**.

# Example Usage
local camUtil = require(game.ReplicatedStorage.Lib.Camera)

camUtil.TweenTo(CFrame.new(0,10,20), 1)
camUtil.SetFOV(70, 0.5)
camUtil.Shake(2, 0.3)
camUtil.Follow(workspace.NPC.HumanoidRootPart, Vector3.new(0,5,10))
camUtil.StopFollow()
camUtil.LookAt(Vector3.new(0,0,0))
camUtil.Reset()
