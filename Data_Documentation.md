
# Data.lua - Explanatory Documentation

This script is a robust wrapper for Roblox's DataStoreService.  
It is designed to be used as a ModuleScript **on the server side only**.

# Services Used
- **DataStoreService** : For persistent data storage.  
- **Players** : To manage player-specific data.

# Configuration
- **Data.StorePrefix** : Prefix for DataStore names (default "DevHelper_").  
- **Data.DefaultRetry** : Number of retry attempts on error (default 3).  
- **Data.BackoffBase** : Initial backoff time in seconds for retries (default 0.5).  
- **Data.SessionCache** : In-memory cache for active sessions.

# Functions

## Data.GetStore(name)
Gets a DataStore by name, using the configured prefix.  
- **name** : Name of the DataStore.  
Returns the DataStore object.

## safeCall(func, retries)
Helper function to safely call a function with retries and exponential backoff.  
- **func** : Function to call.  
- **retries** : Number of retry attempts (optional).  
Returns success (true/false) and result or error message.

## playerKey(player, key)
Generates a standardized key for a player.  
- **player** : Player object.  
- **key** : Key name.  
Returns a string like "UserId:key".

## Data.SaveKey(storeName, key, value)
Saves a generic value to a DataStore.  
- **storeName** : Name of the DataStore.  
- **key** : Key to store the value under.  
- **value** : Any serializable value.  
Returns success (true/false) and result or error.

## Data.LoadKey(storeName, key, default)
Loads a value from a DataStore.  
- **storeName** : Name of the DataStore.  
- **key** : Key to load.  
- **default** : Default value if none exists.  
Returns the stored value or default.

## Data.SavePlayer(player, dataTable)
Saves the entire player data table under key "player".  
- **player** : Player object.  
- **dataTable** : Table to save.  
Updates in-memory session cache.  
Returns success (true/false) and result or error.

## Data.LoadPlayer(player, default)
Loads player data. Prioritizes session cache.  
- **player** : Player object.  
- **default** : Default table if no data exists.  
Returns the data table.

## Data.ClearPlayerCache(player)
Removes a player's session cache (e.g., on leave).  
- **player** : Player object.

## Data.SaveAll()
Saves the cache of all active players. Useful for shutdown or dev purposes.

## Data.UpdateKey(storeName, key, transform)
Wrapper for DataStore:UpdateAsync to safely update a value.  
- **storeName** : Name of the DataStore.  
- **key** : Key to update.  
- **transform** : Function that receives the old value and returns the new one.  
Returns success (true/false) and result or error.

# Automatic Hooks
- **Players.PlayerRemoving** : Automatically saves player data when they leave the game.

# Notes / Best Practices
- Always use **SaveKey/LoadKey** or **SavePlayer/LoadPlayer** instead of accessing DataStore directly.  
- Use **SessionCache** to reduce DataStore calls and improve performance.  
- **safeCall** ensures retries with exponential backoff to avoid DataStore throttling.  
- **SaveAll** is useful before server shutdown or for manual backups.  
- **UpdateKey** allows atomic updates without overwriting concurrent changes.  

# Example Usage
local playerData = Data.LoadPlayer(player, {coins = 0, level = 1})
playerData.coins = playerData.coins + 10
Data.SavePlayer(player, playerData)

Data.SaveKey("GlobalStore", "Leaderboard", {player1 = 100, player2 = 90})
local leaderboard = Data.LoadKey("GlobalStore", "Leaderboard", {})

Data.UpdateKey("GlobalStore", "Leaderboard", function(old)
    old = old or {}
    old["player3"] = 50
    return old
end)

Data.SaveAll() -- save all sessions
