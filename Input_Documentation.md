
# Input.lua - Explanatory Documentation

This module provides utilities for handling user inputs in Roblox, including keyboard, mouse, and click detection.  
It is designed to be used as a ModuleScript.

# Services Used
- **UserInputService** : Detects keyboard and mouse input  
- **RunService** : Heartbeat for key hold detection

# Internal Tables
- **keyDownCallbacks** : Stores callbacks for key down events  
- **keyUpCallbacks** : Stores callbacks for key up events  
- **holdCallbacks** : Stores callbacks for key hold events with thresholds  
- **boundClicks** : Stores click connections for GUI or BasePart instances

# Functions

## Input.OnKeyDown(keyName, callback)
Registers a callback for key down.  
- **keyName** : Name of the key (string)  
- **callback** : Function to call  
Returns a **function to unbind**.

## Input.OnKeyUp(keyName, callback)
Registers a callback for key up.  
- **keyName** : Key name  
- **callback** : Function to call  
Returns a **function to unbind**.

## Input.OnKeyHold(keyName, threshold, callback)
Registers a callback once a key is held for a threshold duration.  
- **threshold** : Time in seconds (default 0.5)  
Returns a **function to unbind**.

## Input.IsKeyDown(keyName)
Checks if a key is currently pressed.  
- Returns **true/false**.

## Input.OnClick(instance, callback)
Registers a click callback on a GUI object or BasePart.  
- **instance** : GUI object (TextButton, ImageButton) or BasePart  
- **callback** : Function to call on click  
Returns a **function to unbind**.

## Input.UnbindAll()
Clears all key and click bindings. Useful for cleanup when scripts are reloaded.

# Notes / Best Practices
- Key hold detection uses **RunService.Heartbeat** for timing.  
- Click detection works on GUI objects, BaseParts, and globally via Mouse raycast fallback.  
- Always store returned unbind functions to remove callbacks when needed.  
- Use **UnbindAll** to prevent lingering connections on script reload.

# Example Usage
-- Key down
local unbindE = Input.OnKeyDown("E", function() print("E pressed") end)

-- Key up
local unbindQ = Input.OnKeyUp("Q", function() print("Q released") end)

-- Key hold
local cancelHold = Input.OnKeyHold("F", 1.0, function() print("F held for 1s") end)

-- Check if key is down
if Input.IsKeyDown("E") then print("E is down") end

-- Click on a GUI button
local button = script.Parent:WaitForChild("TextButton")
local unbindClick = Input.OnClick(button, function() print("Button clicked") end)

-- Cleanup
Input.UnbindAll()
