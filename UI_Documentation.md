
# UI.lua - Explanatory Documentation

This module provides utility functions for creating and animating simple UI elements in Roblox.  
Recommended usage: client-side for GUI creation and effects.

# Configuration
- **UI.Theme** : Default colors for UI elements (Background, Panel, Accent, Text, SubText)  

# Functions

## UI.CreateFrame(parent, size, pos, opts)
Creates a Frame with optional size, position, and styling.  
- **parent** : GuiObject parent  
- **size** : UDim2 size (default 200x120)  
- **pos** : UDim2 position (default centered)  
- **opts** : Table `{bgColor, border, anchor}`  
- Returns **Frame instance**.

## UI.CreateLabel(text, parent, size, pos, opts)
Creates a TextLabel with optional styling.  
- **text** : String  
- **parent** : GuiObject parent  
- **size, pos** : UDim2 size and position  
- **opts** : Table `{color, font, textSize, wrapped, alignX}`  
- Returns **TextLabel instance**.

## UI.CreateButton(text, parent, size, pos, opts)
Creates a TextButton with optional styling.  
- **text** : String  
- **parent** : GuiObject parent  
- **size, pos** : UDim2 size and position  
- **opts** : Table `{bgColor, textColor, font, textSize}`  
- Returns **TextButton instance**.

## UI.MakeDraggable(frame, handle)
Makes a frame draggable using a handle (or the frame itself).  
- **frame** : Frame to drag  
- **handle** : Optional GuiObject handle  
- Returns **nil**.

## UI.Fade(uiObject, from, to, duration, callback)
Fades a GuiObject from one transparency to another.  
- **uiObject** : GuiObject (Frame/TextLabel/TextButton/TextBox)  
- **from, to** : Transparency values (0..1)  
- **duration** : Seconds (default 0.3)  
- **callback** : Function called after fade completes  
- Returns **Tween instance**.

## UI.Tween(uiObject, props, duration, style, direction, callback)
Tweens arbitrary properties of a GuiObject.  
- **uiObject** : GuiObject  
- **props** : Table of property values  
- **duration** : Seconds (default 0.3)  
- **style** : EasingStyle (default Quad)  
- **direction** : EasingDirection (default Out)  
- **callback** : Function called after tween completes  
- Returns **Tween instance**.

## UI.ClearChildren(gui)
Destroys all children of a GuiObject safely.  
- **gui** : GuiObject parent  
- Returns **nil**.

## UI.Notify(parent, text, duration)
Shows a simple notification Label that fades in/out.  
- **parent** : GuiObject parent  
- **text** : Notification text  
- **duration** : Seconds before fade-out (default 2)  
- Returns **Frame instance**.

## UI.Modal(parent, title, contentText)
Creates a modal dialog with title, content, and an OK button.  
- **parent** : GuiObject parent  
- **title** : Modal title text  
- **contentText** : Modal body text  
- Returns **Frame instance (modal background)**.

# Example Usage
local ui = require(game.ReplicatedStorage.Lib.UI)

local frame = ui.CreateFrame(workspace.CurrentCamera, UDim2.new(0,200,0,100))
local lbl = ui.CreateLabel("Hello World", frame)
local btn = ui.CreateButton("Click Me", frame)
ui.MakeDraggable(frame)
ui.Fade(frame, 1, 0, 0.5)
ui.Notify(workspace.CurrentCamera, "Notification!")
ui.Modal(workspace.CurrentCamera, "Title", "This is a modal")
