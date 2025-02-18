# Legion API Documentation

Welcome to the Legion API documentation! This guide provides a comprehensive overview of the functions and utilities available in the Legion API. These functions are accessible through the global `Legion` table.

## Table of Contents

1.  [Creating Tools](#creating-tools)
2.  [Neckgrab Utilities](#neckgrab-utilities)
3.  [Player and Character Utilities](#player-and-character-utilities)
4.  [Audio and Animation Utilities](#audio-and-animation-utilities)
5.  [Miscellaneous Utilities](#miscellaneous-utilities)

## Creating Tools

### `Legion:GrabTool`

Creates a custom tool that can be activated when the player grabs another character. This is useful for creating unique neckgrab abilities.

```lua
Legion:GrabTool({
    Name = "Tool Name",
    Description = "Tool Description",
    StopAnimation = true, -- Stops all grabbing animations when the the tool is activated
    Callback = function()
        
    end,
})
```

#### Parameters:

*   **`name`**: The name of the tool (string). This will appear in the UI.
*   **`callback`**: The function to execute when the tool is activated (function). The grabbed character is passed as an argument.
*   **`description`**: A brief description of the tool (string). This will appear as a tooltip in the UI.

#### Example:

```lua
Legion:GrabTool({
    Name = "Explode",
    Description = "Causes the grabbed player to explode.",
    StopAnimation = true, -- Stops all grabbing animations when the the tool is activated
    Callback = function(grabbedChar)
        -- Create an explosion at the grabbed character's position
        local explosion = Instance.new("Explosion")
        explosion.Position = grabbedChar.HumanoidRootPart.Position
        explosion.Parent = workspace
    
        -- Remove the grabbed characters bodyparts
        Legion:Remove(grabbedChar, "all")
    end,
})
```

## Neckgrab Utilities

### `Legion:GetForwardPosition`

Calculates a position a specified distance in front of the local player's character. Useful for positioning effects or teleporting the grabbed player.

```lua
Legion:GetForwardPosition(distance: number) -> Vector3
```

#### Parameters:

*   **`distance`**: The distance in studs to calculate the position in front of the character (number).

#### Returns:

*   A `Vector3` representing the calculated position.

#### Example:

```lua
local forwardPosition = Legion:GetForwardPosition(10)
print("Forward position:", forwardPosition)
```

## Player and Character Utilities

### `Legion:Find`

Searches for a descendant within a parent object based on a name (case-insensitive). Useful for locating specific items or players.

```lua
Legion:Find(parent: Instance, name: string) -> Instance?
```

#### Parameters:

*   **`parent`**: The object to search within (Instance).
*   **`name`**: The name (or part of the name) of the object to find (string).

#### Returns:

*   The found object (Instance) or `nil` if not found.

#### Example:

```lua
local lmgAmmo = Legion:Find(workspace.Ignored.Shop, "lmg ammo")
if lmgAmmo then
    Legion:BuyItem(lmgAmmo)
end
```

### `Legion:GetCharacter`

Returns the local player's character or a specific child of the character.

```lua
Legion:GetChar(option: string?) -> Instance?
```

#### Parameters:

*   **`option`**: (Optional) The name of a child object to find within the character (string). If omitted, returns the character model itself.

#### Returns:

*   The character model (Model) or the found child object (Instance), or `nil` if the child is not found.

#### Example:

```lua
local character = Legion:GetChar()
local rootPart = Legion:GetChar("HumanoidRootPart")
```

### `Legion:Remove`

Removes a limb or all limbs from a character.

```lua
Legion:Remove(character: Model, part: string)
```

#### Parameters:

*   **`character`**: The character model to remove the limb from (Model).
*   **`part`**: The name of the limb to remove (string), or `"all"` to remove all limbs.

#### Example:

```lua
Legion:Remove(grabbedChar, "all")
```

## Audio and Animation Utilities

### `Legion:PlayAudio`

Plays an audio file using its asset ID.

```lua
Legion:PlayAudio(id: number)
```

#### Parameters:

*   **`id`**: The asset ID of the audio file (number).

#### Example:

```lua
Legion:PlayAudio(1234567890)
```

### `Legion:StopAudio`

Stops the currently playing audio.

```lua
Legion:StopAudio()
```

#### Example:

```lua
Legion:StopAudio()
```

### `Legion:AddConnection`

Adds a script connection to a table for later disconnection.

```lua
Legion:AddConnection(name: string, connection: RBXScriptConnection)
```

#### Parameters:

*   **`name`**: The name of the connection (string).
*   **`connection`**: The `RBXScriptConnection` object (RBXScriptConnection).

#### Example:

```lua
local connection = RunService.Heartbeat:Connect(function() print("Heartbeat") end)
Legion:AddConnection("Heartbeat", connection)
```

### `Legion:RemoveConnection`

Removes and disconnects a script connection.

```lua
Legion:RemoveConnection(name: string)
```

#### Parameters:

*   **`name`**: The name of the connection to remove (string).

#### Example:

```lua
Legion:RemoveConnection("Heartbeat")
```

## Miscellaneous Utilities

### `Legion:GetGrabbed`

Returns the character currently being grabbed by the local player.

```lua
Legion:GetGrabbed() -> Instance?
```

#### Returns:

*   The grabbed character model (Model) or `nil` if no character is currently grabbed.

#### Example:

```lua
local grabbedChar = Legion:GetGrabbed()
if grabbedChar then
    print("Grabbed character:", grabbedChar.Name)
end
```

### `Legion:PlayAnimation`

Plays an animation on a character using its asset ID.

```lua
Legion:PlayAnimation(character: Model, id: number, speed: number?, time: number?, smoothing: number?)
```

#### Parameters:

*   **`character`**: The character model to play the animation on (Model).
*   **`id`**: The asset ID of the animation (number).
*   **`speed`**: (Optional) The speed of the animation (number).
*   **`time`**: (Optional) The starting time position of the animation (number).
*   **`smoothing`**: (Optional) The fade-in time for the animation (number).

#### Example:

```lua
local character = Legion:GetChar()
Legion:PlayAnimation(character, 9876543210, 1, 0, 0.1)
```

### `Legion:StopAnimation`

Stops a specific animation on a character.

```lua
Legion:StopAnimation(character: Model, id: number)
```

#### Parameters:

*   **`character`**: The character model to stop the animation on (Model).
*   **`id`**: The asset ID of the animation to stop (number).

#### Example:

```lua
local character = Legion:GetChar()
Legion:StopAnimation(character, 9876543210)
```

## Miscellaneous Utilities

### `Legion:BuyItem`

Simulates buying an item from a shop by clicking its `ClickDetector`.

```lua
Legion:BuyItem(item: Instance, option: string?)
```

#### Parameters:

*   **`item`**: The item instance in the workspace (Instance).
*   **`option`**: (Optional) Specifies if the item is related to armor ("normal" or "fire") (string).

#### Example:

```lua
local lmgAmmo = Legion:Find(workspace.Ignored.Shop, "lmg ammo")
if lmgAmmo then
    Legion:BuyItem(lmgAmmo)
end
```

### `Legion:Chat`

Sends a chat message to the in-game chat.

```lua
Legion:Chat(message: string)
```

#### Parameters:

*   **`message`**: The message to send (string).

#### Example:

```lua
Legion:Chat("Hello, world!")
```

### `Legion:Create`

Creates a new instance of a specified class with given properties.

```lua
Legion:Create(className: string, properties: table) -> Instance
```

#### Parameters:

*   **`className`**: The class name of the instance to create (string).
*   **`properties`**: A table of properties to apply to the instance (table).

#### Returns:

*   The created instance (Instance).

#### Example:

```lua
local bodyPosition = Legion:Create("BodyPosition", {
    Parent = character.HumanoidRootPart,
    MaxForce = Vector3.new(9e9, 9e9, 9e9),
    Position = character.HumanoidRootPart.Position
})
```

### `Legion:Delete`

Destroys specified descendants within a parent object.

```lua
Legion:Delete(parent: Instance, options: table)
```

#### Parameters:

*   **`parent`**: The object to search within (Instance).
*   **`options`**: A table of names of the objects to destroy (table).

#### Example:

```lua
Legion:Delete(workspace.PartFolder, {"Part1", "Part2"})
```

### `Legion:Shoot`

Simulates shooting a gun at a target.

```lua
Legion:Shoot(targetName: string, gun: Tool)
```

#### Parameters:

*   **`targetName`**: The name of the target player (string).
*   **`gun`**: The gun tool to use (Tool).

#### Example:

```lua
local targetName = "Player2"
local gun = game.Players.LocalPlayer.Character:FindFirstChild("[LMG]")
if gun then
    Legion:Shoot(targetName, gun)
end
```

### `Legion:Tween`

Creates and plays a tween on a given object.

```lua
Legion:Tween(instance: Instance, duration: number, properties: table)
```

#### Parameters:

*   **`instance`**: The instance to tween (Instance).
*   **`duration`**: The duration of the tween in seconds (number).
*   **`properties`**: A table of properties to tween (table).

#### Example:

```lua
Legion:Tween(lighting, 1, {FogEnd = 1000})
```

### `Legion:Void`

Applies a strong downward `BodyVelocity` to a character, effectively making them fall into the void.

```lua
Legion:Void(character: Model, partName: string?)
```

#### Parameters:

*   **`character`**: The character model to apply the effect to (Model).
*   **`partName`**: (Optional) The name of the part to attach the `BodyVelocity` to (string). If omitted, defaults to `UpperTorso`.

#### Example:

```lua
Legion:Void(grabbedChar)
```

# Services 
#### How to access services?
```lua
Services.ServiceName --(e.g Services.Workspace)
```

#### What Services are in there?
- Players 
- LocalPlayer
- ReplicatedStorage
- MainEvent
- RunService
- Workspace
- Lighting
- TweenService
- HttpService
- UserInputService
- VirtualInputManager
