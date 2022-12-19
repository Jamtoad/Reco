# Reco
This is a purely functional recursive alternative to Lua's built in for loop system. It allows you to recursively call a function on every iteration through a table.
Reco is really strong when used with an immutable data library as it allows you to loop through tables and only return the final result. Without creating variables along the way. See the examples below.

## Usage
`each` has 3 parameters, 1 of which is optional. The first parameter is the table that you want to loop through. The second is the function you would like to call upon every iteration. The third are is any number of parameters that you would like to pass on to the function.

NOTE: The function gets called by default with its first two parameters being (key, value). Any passed parameters will be after these.

## Examples
### Print Example
```lua
local testTable = {"hello", "world", 4, 5, 6}

local function iterator(key, value, word)
    print(key, value, word)
end

Reco(testTable, iterator, "RECO!!!")

--[[
    Prints:
    1, hello, RECO!!!
    2, world, RECO!!!
    
    and so on.
]]
```
### Returning Example
```lua
local testTable = {hello = "world"}
local mergeTable = {foo = "bar"}

local function iterator(key, value, combinedTable)
    return combinedTable[key] = value
end

local combinedTable = Reco(testTable, iterator, mergeTable)
print(combinedTable)
--[[
    Prints:
    {foo = "bar", hello = "world"}
]]
```
This works because in Reco anything returned gets passed as the parameters for the next function call. Allowing you keep track of the changed variables from the previous function call without having to create a variable for them.

## Install
### Roblox Workflow
You can get Reco off the Roblox Marketplace here.
https://www.roblox.com/library/11821595200/Reco

### Rojo Workflow
Get the `.rbxm` file from the releases page. This file can be used to sync to Studio when using Rojo.

### Raw Files
You can find both the `.lua` and the `.rbxm` files here in the releases section.
