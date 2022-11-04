# Reco
This is a purely functional recursive alternative to Lua's built in for loop system. It allows you to recursively call a function on every iteration through a table.
Reco is really strong when used with an immutable data library as it allows you to loop through tables and only return the final result. Without creating variables along the way. See the examples below.

## API
The API is simple and it has only one function as of now.

`Reco.each(table, function, parameters [optional])`

`each` has 3 parameters, 1 of which is optional. The first parameter is the table that you want to loop through. The second is the function you would like to call upon every iteration. The third are is any number of parameters that you would like to pass on to the function.

NOTE: The function gets called by default with its first two parameters being (key, value). Any passed parameters will be after these.

## Examples
### Print Example
```lua
local testTable = {"hello", "world", 4, 5, 6}

local function iterator(key, value, word)
    print(key, value, word)
end

Reco.each(testTable, iterator, "RECO!!!")

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

local combinedTable = Reco.each(testTable, iterator, mergeTable)
print(combinedTable)
--[[
    Prints:
    {foo = "bar", hello = "world"}
]]
```
This works because in Reco anything returned gets passed as the parameters for the next function call. Allowing you keep track of the changed variables from the previous function call without having to create a variable for them.

## Installation
Check the Releases section for the raw .lua file or the .rbxm file for use in Roblox. I also have a published version on the Roblox Marketplace that can be found here. https://www.roblox.com/library/11465670869/Reco
