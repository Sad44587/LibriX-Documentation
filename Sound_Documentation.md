
# Sound.lua - Explanatory Documentation

This module provides simplified sound management for Roblox, including playing, stopping, fading, and 3D positioning.  
Recommended usage: server-side or client-side for sound effects in games.

# Configuration
- **Sound.GlobalVolume** : Global volume multiplier (default 1)  
- **Sound.SetGlobalVolume(volume)** : Sets global volume for all sounds  

# Functions

## Sound.Play(sound, volume, pitch, looped)
Plays a Sound object with optional volume, pitch, and looping.  
- **sound** : Sound object  
- **volume** : Number 0-1 (default 1)  
- **pitch** : Playback speed 0.5-2 (default 1)  
- **looped** : Boolean, loop the sound (default false)  
- Returns **Sound object playing**.

## Sound.Stop(sound)
Stops a Sound object if currently playing.  
- **sound** : Sound object  
- Returns **nil**.

## Sound.FadeIn(sound, duration, targetVolume)
Gradually increases volume from 0 to targetVolume.  
- **sound** : Sound object  
- **duration** : Fade-in duration in seconds (default 0.5)  
- **targetVolume** : Volume after fade (default 1)  
- Returns **Tween object**.

## Sound.FadeOut(sound, duration)
Gradually decreases volume to 0 and stops the sound.  
- **sound** : Sound object  
- **duration** : Fade-out duration in seconds (default 0.5)  
- Returns **Tween object**.

## Sound.Play3D(soundTemplate, position, volume, pitch, looped, parent)
Plays a 3D sound at a given position.  
- **soundTemplate** : Sound object to clone  
- **position** : Vector3 world position  
- **volume** : Number 0-1 (optional)  
- **pitch** : Playback speed (optional)  
- **looped** : Boolean (optional)  
- **parent** : BasePart or workspace (default workspace)  
- Returns **cloned Sound object** that is automatically cleaned up.

# Example Usage
local soundModule = require(game.ReplicatedStorage.Lib.Sound)

-- Play a sound normally
soundModule.Play(mySound, 0.8, 1, false)

-- Fade in a sound
soundModule.FadeIn(mySound, 1, 0.5)

-- Play a 3D sound at a position
soundModule.Play3D(mySound, Vector3.new(0,10,0), 1, 1, false)

-- Adjust global volume
soundModule.SetGlobalVolume(0.5)
