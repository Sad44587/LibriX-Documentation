
# Table.lua - Explanatory Documentation

This module provides utility functions for manipulating tables in Roblox.  
Recommended usage: server-side or client-side for data handling and table operations.

# Functions

## Table.ShallowCopy(t)
Creates a shallow copy of a table.  
- **t** : Input table  
- Returns **new table with same keys/values**.

## Table.DeepCopy(t)
Creates a deep (recursive) copy of a table.  
- **t** : Input table  
- Returns **new table with nested copies**.

## Table.Merge(t1, t2)
Merges two tables; values from t2 overwrite t1.  
- **t1, t2** : Tables to merge  
- Returns **merged table**.

## Table.Count(t)
Counts the number of keys in a table.  
- **t** : Table  
- Returns **integer count**.

## Table.Contains(t, val)
Checks if table contains a value.  
- **t** : Table  
- **val** : Value to search  
- Returns **boolean**.

## Table.FindKey(t, val)
Finds a key by its value.  
- **t** : Table  
- **val** : Value to search  
- Returns **key or nil**.

## Table.Filter(t, func)
Filters table elements using a callback function.  
- **t** : Table  
- **func(v, k)** : Callback returning true to keep element  
- Returns **new filtered table**.

## Table.Map(t, func)
Maps table values using a callback function.  
- **t** : Table  
- **func(v, k)** : Callback returning transformed value  
- Returns **new table**.

## Table.Reverse(t)
Reverses an array-style table.  
- **t** : Array table  
- Returns **reversed array**.

## Table.Shuffle(t)
Shuffles an array-style table using Fisher-Yates algorithm.  
- **t** : Array table  
- Returns **shuffled array**.

## Table.ConcatArrays(...)
Concatenates multiple array-style tables.  
- **...** : Tables to concatenate  
- Returns **new array table**.

## Table.First(t)
Returns the first element of an array-style table.  
- **t** : Array table  
- Returns **element or nil**.

## Table.Last(t)
Returns the last element of an array-style table.  
- **t** : Array table  
- Returns **element or nil**.

## Table.Clear(t)
Clears all keys from a table.  
- **t** : Table  
- Returns **nil**.

## Table.IsEmpty(t)
Checks if a table is empty.  
- **t** : Table  
- Returns **boolean**.

## Table.Slice(t, startIdx, endIdx)
Returns a slice of an array-style table.  
- **t** : Array table  
- **startIdx** : Start index (default 1)  
- **endIdx** : End index (default #t)  
- Returns **new array table**.

# Example Usage
local tblUtil = require(game.ReplicatedStorage.Lib.Table)

local arr = {1,2,3,4,5}
local copy = tblUtil.ShallowCopy(arr)
local reversed = tblUtil.Reverse(arr)
local slice = tblUtil.Slice(arr, 2, 4)
local shuffled = tblUtil.Shuffle(arr)
print(tblUtil.First(arr), tblUtil.Last(arr))
