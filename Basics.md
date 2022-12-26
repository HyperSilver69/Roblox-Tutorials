"What is Lua? Lua is a powerful, efficient, lightweight, embeddable scripting language. It supports procedural programming, object-oriented programming, functional programming, data-driven programming, and data description"

play along! you can follow this part of the tutorial with the Lua demo environment. Link [Here](https://www.lua.org/cgi-bin/demo)
# Defining your variables
An example of a variable is:
```lua
local hello = "Hello"
```
Variables define things, so you can use them.

For example, lets say we want to put "Hello World" in the output:
```lua
-- you can put text in code without it messing it up with "--" before your text!
local hello = "Hello World" -- Defining the variable to have the string (A line of text) set to it. Whenever we provide `hello` as an argument, it will return Hello World.
print(hello) -- puts the argument (In this case hello) in the output.


--------------------------
Output:
Hello World!
```
Print can also work with the following:
```lua
print("Hello World12345") -- will print the string put inbetween parenthesis.

--------------------------
Output:
Hello World12345
```

Variables are used to shorten things up as well, let's take a look at the following code:
```lua
clickDetector.MouseClick:Connect(function()
  if game.Workspace.DeployROBLOXClone.RangeClones.DeployRangeClone.Transparency == 1 then
     game.Workspace.DeployROBLOXClone.RangeClones.DeployRangeClone.Transparency = .94
  elseif game.Workspace.DeployROBLOXClone.RangeClones.DeployRangeClone.Transparency < 1 then
    game.Workspace.DeployROBLOXClone.RangeClones.DeployRangeClone.Transparency = 1
  end
end)
```
Wow! what is going on there? See how the creator used the same `game.Workspace.DeployROBLOXClone.RangeClones.DeployRangeClone` 4 times? We can make that shorter! Let's use a variable:
```lua
local rangeClone = game.Workspace.DeployROBLOXClone.RangeClones.DeployRangeClone -- It's a variable, so we can access the RangeClones easier!

clickDetector.MouseClick:Connect(function()
  if rangeClone.Transparency == 1 then
     rangeClone.Transparency = .94
  elseif rangeClone.Transparency < 1 then
    rangeClone.Transparency = 1
  end
end)
```
I don't expect you to understand this code, but it's more easy to read right now.