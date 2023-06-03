# Style Guide
This style guide aims to unify projects as much as possible under the same style and conventions.

The purpose of this guide is to keep consistent and clean code. This guide values & promotes readability. The era of focusing on performance over readability is slowly coming to an end.

# Principles
* The purpose of this style guide is to avoid arguments.
	* There is no one right answer how to style your code, but consistency, readability, and performance is important. We want to spend more time writing code, and less time reading code.

* Optimize code for reading, not writing.
	* You will write your code once. Many people will need to read it, from reviewers, and to anyone who wishes to use the code - even you.
	* Consider what diffs will look like. It's much easier to read a diff that doesn't involve moving things between lines. Clean diffs means your code will be reviewed easier & faster.

* Avoid magic.
	* Avoid using deprecated features or writing code that does not make much sense. Magical code is nice to use, until something goes wrong - no one knows why it broke or how to fix it.
	* Metatables are a good example of a powerful feature that should be used with caution.

# Guide
Finally, you made it! This is where the style guide begins.

## File Structure
Files should consist of these things in order.

* Block comment that mentions basic information about the file.
```lua
--[[
	File.server.lua
	Nicklaus_s
	25 September 2022

	File that handles essentials for the game to run.
	Initializes all modules in a specific order.
--]]
```

* Services used by the file
  * All services should be received by using `DataModel:GetService()`

* Module imports

* Assets
  * Define all assets using `WaitForChild` (if applicable)

* Variables
  * Define all non-constant variables that will be modified
  * Tables should go last (if applicable)

* Constants
  * Define all constants using `LOUD_SNAKE_CASE`
  * Tables should go last

I'll show an example below.

```lua
--[[
	File.server.lua
	Nicklaus_s
	25 September 2022

	File that handles essentials for the game to run.
	Initializes all modules in a specific order.
--]]

local Workspace = game:GetService('Workspace')
local Players = game:GetService('Players')
local ReplicatedStorage = game:GetService('ReplicatedStorage')

local Modules = ReplicatedStorage.Modules
local Data = require(Modules.Data)

local Player = Players.LocalPlayer
local PlayerGui = Player:WaitForChild('PlayerGui')

local Asset = Workspace:WaitForChild('Asset')
```

## Comments
Comments should be kept to a minimum. You should document your code well when needed - such as describing a series of semantics used to achieve something and when your code doesn't express those semantics clearly.

Libraries follow different rules, you should be documenting each function well. Someone shouldn't have to read your functions just to figure out how to use them.

Comments shouldn't be placed inside scopes (don't follow this heavily, it's just a basic guideline). Comments should not be hidden. An example of this is if you're documenting a function. You should put the comment before the function is declared (code example provided below).

```lua
--[[
	Used to test our library.

	@param Statement string
	The statement which is echoed back.

	@return nil
	This function does not return anything.
--]]

	function Library.Test(Statement: string): nil
		print(Statement)
	end
```

## Variables

# Attributions
Formal attributions are provided here.

## Design
* [Roblox's Lua Style Guide](https://roblox.github.io/lua-style-guide/)
* [4thAxis's Luau Style Guide](https://hackmd.io/@4thAxis/4thAxis-Luau-Style-Guide)
* [Google's C++ Style Guide](https://google.github.io/styleguide/cppguide.html)
