
# Camera.lua - Explanatory Documentation

This script manages the camera in a simplified way in Roblox. It is designed to be used as a ModuleScript.

# Service Imports
- **Players** : To get the local player.  
- **RunService** : To run code every frame (useful for following an object or making effects).  
- **TweenService** : To animate the camera and its properties smoothly.

# Main Variables
- **player** : The local player (Players.LocalPlayer).  
- **cam** : The main workspace camera (workspace.CurrentCamera).  

# Default Settings
- **Camera.DefaultFOV** : Stores the camera's initial field of view.  
- **Camera.DefaultCFrame** : Stores the camera's initial position and orientation.  
- **Camera.ShakeMagnitude** : Initial value of shake intensity.

# Functions

## TweenTo(cframe, duration, easingStyle, easingDirection, callback)
Animates the camera to a target CFrame.  
- **cframe** : Target position and rotation of the camera.  
- **duration** : Duration of the animation (default 0.5 seconds).  
- **easingStyle** : Animation style (default Quad).  
- **easingDirection** : Animation direction (default Out).  
- **callback** : Function to execute when the animation is complete.  
Returns the created Tween.

## SetFOV(fov, duration)
Animates the camera's field of view.  
- **fov** : New field of view value.  
- **duration** : Duration of the animation (default 0.3 seconds).  
Returns the created Tween.

## Shake(magnitude, duration)
Applies a camera shake effect.  
- **magnitude** : Shake intensity (default 1).  
- **duration** : Shake duration in seconds (default 0.5).  
- The camera returns to its initial position after the shake.

## Follow(target, offset)
Makes the camera follow a target (usually HumanoidRootPart).  
- **target** : Object to follow.  
- **offset** : Offset from the target (default Vector3(0,5,10)).  
- Updates the camera every frame.

## StopFollow()
Stops the camera from following.

## LookAt(position)
Orients the camera to look at a specific position.  
- **position** : Position to look at.

## Reset()
Resets the camera to its default position and field of view.

# Example Usage
Camera.TweenTo(CFrame.new(0,10,0), 1) -- Animate camera to point (0,10,0) in 1 second
Camera.SetFOV(70, 0.5) -- Change FOV to 70 in 0.5 seconds
Camera.Shake(2, 0.3) -- Shake with magnitude 2 for 0.3 seconds
Camera.Follow(player.Character.HumanoidRootPart) -- Follow the player
Camera.StopFollow() -- Stop following
Camera.LookAt(Vector3.new(0,0,0)) -- Look at point (0,0,0)
Camera.Reset() -- Reset camera to default
