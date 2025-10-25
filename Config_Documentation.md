
# Config.lua - Explanatory Documentation

This script is a centralized configuration module for Roblox. It is designed to be used as a ModuleScript.

# Main Table
- **Config._data** : Stores all configuration values.

# Default Example Values
- **GameName** : "MonJeu"  
- **MaxPlayers** : 16  
- **DebugMode** : false  
- **SpawnRadius** : 50  
- **DefaultCurrency** : "Honey"  

# Functions

## Config.Get(key)
Returns the value associated with the given key.  
- **key** : The configuration key.  
Returns the value.

## Config.Set(key, value)
Sets a configuration value and updates the exported folder if active.  
- **key** : The configuration key.  
- **value** : The new value to set.  
Returns the updated value.

## Config.Merge(tbl)
Merges another table into the current configuration.  
- **tbl** : Table containing key-value pairs to merge.

## Config.GetAll()
Returns a copy of the complete configuration table.

## Config.ExportToReplicatedStorage(folderName)
Creates or updates a Folder in ReplicatedStorage with Attributes for clients to read.  
- **folderName** : Optional name of the folder (default "DevHelperConfig").  
Returns the created or updated folder.

## Config.ImportFromFolder(folder)
Imports configuration values from a folder's Attributes.  
- **folder** : Folder to read Attributes from.  
Returns true if successful, false and an error message otherwise.

## Config.Listen(callback)
Registers a callback for when attributes change (requires ExportToReplicatedStorage).  
- **callback** : Function to call when an attribute changes.  
Returns a function to stop listening.

## Config.Setup(defaults, export)
Initializes the configuration with optional defaults and exports.  
- **defaults** : Table of default values to merge.  
- **export** : Optional folder name to export configuration.

# Example Usage
Config.Setup({GameName = "TestGame", MaxPlayers = 10}, "MyConfigFolder") -- Setup defaults and export
Config.Set("DebugMode", true) -- Set a single config value
local max = Config.Get("MaxPlayers") -- Get a config value
local all = Config.GetAll() -- Get a copy of all config
Config.ExportToReplicatedStorage() -- Export to ReplicatedStorage
Config.ImportFromFolder(folder) -- Import values from a folder
