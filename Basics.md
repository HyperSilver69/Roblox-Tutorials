"What is Lua? Lua is a powerful, efficient, lightweight, embeddable scripting language. It supports procedural programming, object-oriented programming, functional programming, data-driven programming, and data description"

play along! you can follow this part of the tutorial with the Lua demo environment. Link [Here](https://www.lua.org/cgi-bin/demo)
## Defining your variables
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

local variables are bound to their scope, that means that if I define a variable with `local` in front of it anywhere that isn't in the root of the script, it won't be accessible by the root, to explain:
```lua
-- First script, we define it in the root and we can use it anywhere
local value = true
print(value) -- prints true

local function test()
    print(value) -- prints true, but only if `test()` is ran somewhere else.
end
```
Okay cool, so then lets look at this:
```lua
local function test()
    local value = true -- We decalred it inside of something, in this case the test function. This means that the variable is only accessible inside this function
    print(value) -- will print true
end

print(value) -- will return an error! it is in the root and the value variable can't be used here!
```



## Tables

Tables store things, just like in real life! Take a look at the following code:
```lua
local tableWithAnEpicName = {} -- "{}" is used to let the language know that we're creating a table!
```
Congrats, you just created an empty table. Let's fill it up!
```lua
local tableWithAnEpicName = { -- opening the table with the open curly bracker
      "tom","scott","peter","arnold" -- each string requires it's own set of parenthesis, you can't put undefined things (not made variables) in a table without parenthesis.
} -- closing the table
```
Now that we have a table with those things, let's try to retrieve Scott out of there
```lua
local tableWithAnEpicName = {
      "tom","scott","peter","arnold" 
}
print(tableWithAnEpicName[2])

--------------------------
Ouput:
scott
```
Each element of a table (thing we store in it that's divided by a comma) has it's own numerical value inbetween the brackets, [2] calls the second one in the list. Look at the table, which one is the second? does that match the output? Play around with it.

We'll get to this part in a bit but we can also get tables with things that we don't define outselves (with parenthesis or values):
```lua
local playersService = game:GetService("Players") -- get the players service, we'll get to this in a bit.
local playerList = playersService:GetPlayers() -- Returns a table with all the players

print(playerList[2]) -- Prints the 2nd player stored under the players tab in Studio

--------------------------
Output:
player2
```


## The use of the math library

the `math` library contains a lot of useful functions.
In this tutorial we're gonna be looking at `math.random()`, `math.floor()`, and `math.ceil()`, the three most widely used.

`math.random` allows you to find a random number, whether this is in a table, just numbers, or between values.
```lua
local table1 = {
  "Hello!", "Bye!", "G'day!"
}
local table2 = {
 "Rage.","Happinness","Love"
}

local var = math.random() -- math.random() without any given argument will return a value between 0 and 1, with decimals.
local var1 = math.random(1, 65) -- math.random() with number arguments will return a value between min(first number) and max(last number), math.random allows up to 2 arguments.
local var2 = math.random(-5, 15) -- math.random() takes negative values. Remember to always put the smallest number as `min` and the largest number as `max`

local var3 = table1[math.random(#table1)] -- first, we use `table1[]` to make it obvious that we're refering to a table, then we call math.random(#table1), by doing so, we're applying math.random to `#table1`. Putting "#" before a table, will make it so we're getting a value, since "#" makes it numbered.
```
Now lets take a look at the outputs!
```lua
print(var)
print(var1)
print(var2)
print(var3)


----------------------------------------
0.91847161 -- print(var)
32 -- print(var1)
-3 -- print(var2)
Hello! -- print(var3)
```






Math.floor

Math.floor returns whatever value provided and lowers it to the nearest integer. Let's take a look!
```lua
local number = 4.9999999999 -- number with decimals
print(math.floor(number))


----------------------------------------
4 -- print(math.floor(number))
```
See how the name corrolates to the actual word "Floor"? and a floor is on the ground so we're going DOWN to the ground



Math.ceil

math.ceil returns whatever value provided and rouds it up to the nearest integer, let's take a look!
```lua
local number = 4.0000000001 -- number with decimals
print(math.ceil(number))

----------------------------------------
5 -- print(math.ceil(number))
```
See how the name corrolates to the actual word "Ceiling"? and a ceiling is above you, so we're going UP!
