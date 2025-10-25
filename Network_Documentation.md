
# Network.lua - Explanatory Documentation

This module provides simplified management of RemoteEvents and RemoteFunctions in Roblox.  
It is designed to be used as a ModuleScript.

# Central Folder
- **LibriXNetwork** : All RemoteEvents and RemoteFunctions are stored under this folder in ReplicatedStorage.

# Internal Helper
- **ensureRemote(name, className)** : Creates or replaces a RemoteEvent/RemoteFunction if it doesn’t exist.

# Functions

## Network.CreateEvent(name)
Creates a RemoteEvent under the central folder.  
- **name** : Event name  
Returns **RemoteEvent instance**.

## Network.OnEvent(name, callback)
Binds a callback for a RemoteEvent.  
- On the **server**: triggers when a client fires the event (OnServerEvent)  
- On the **client**: triggers when the server fires the event (OnClientEvent)  
- **callback** : Function to handle the event

## Network.FireClient(name, player, ...)
Server sends a RemoteEvent to a specific client.  
- **player** : Player instance  
- Additional arguments passed to the event.

## Network.FireAllClients(name, ...)
Server sends a RemoteEvent to all clients.

## Network.FireServer(name, ...)
Client sends a RemoteEvent to the server.

## Network.CreateFunction(name)
Creates a RemoteFunction under the central folder.  
- **name** : Function name  
Returns **RemoteFunction instance**.

## Network.OnInvoke(name, callback)
Server sets the behavior when a client calls the RemoteFunction.  
- **callback** : Function(player, ...) -> return value

## Network.InvokeServer(name, ...)
Client calls the RemoteFunction on the server and returns the result.

## Network.Exists(name)
Checks if a RemoteEvent or RemoteFunction exists under the central folder.  
- Returns **true/false**.

## Network.Remove(name)
Removes a RemoteEvent or RemoteFunction from the central folder.

# Notes / Best Practices
- All events and functions are stored under **LibriXNetwork** in ReplicatedStorage.  
- Always use **OnEvent** or **OnInvoke** to bind callbacks instead of directly connecting.  
- Fire events/functions only on the correct side (server/client) to avoid errors.  
- Use **Remove** for cleanup or debugging.

# Example Usage
-- Server: Create event
Network.CreateEvent("HitEvent")
Network.OnEvent("HitEvent", function(player, damage) print(player.Name, damage) end)
Network.FireClient("HitEvent", somePlayer, 10)
Network.FireAllClients("HitEvent", 5)

-- Client: Receive event
Network.OnEvent("HitEvent", function(damage) print("Received damage:", damage) end)
Network.FireServer("HitEvent", 7)

-- RemoteFunction
Network.CreateFunction("GetHealth")
Network.OnInvoke("GetHealth", function(player) return 100 end)
local health = Network.InvokeServer("GetHealth")
