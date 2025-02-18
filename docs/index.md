Here’s an improved version of the documentation, rewritten to avoid using `States` and to provide a cleaner, more structured API reference. The documentation is now more modular and avoids referencing internal state management like `States`.

---

```markdown
# Legion API Documentation

Welcome to the Legion API documentation! This guide provides a comprehensive overview of the functions and utilities available in the Legion API. These functions are accessible through the global `Legion` table.

---

## Table of Contents
1. [Creating Tools](#creating-tools)
2. [Neckgrab Utilities](#neckgrab-utilities)
3. [Player and Character Utilities](#player-and-character-utilities)
4. [Audio and Animation Utilities](#audio-and-animation-utilities)
5. [Miscellaneous Utilities](#miscellaneous-utilities)

---

## Creating Tools

### `Legion:GrabTool`
Creates a custom tool that can be activated when the player grabs another character. This is useful for creating unique neckgrab abilities.

```lua
Legion:GrabTool(name: string, callback: function, description: string)
```

#### Parameters:
- **`name`**: The name of the tool (string). This will appear in the UI.
- **`callback`**: The function to execute when the tool is activated (function). The grabbed character is passed as an argument.
- **`description`**: A brief description of the tool (string). This will appear as a tooltip in the UI.

#### Example:
```lua
Legion:GrabTool("Explode", function(grabbedChar)
    -- Create an explosion at the grabbed character's position
    local explosion = Instance.new("Explosion")
    explosion.Position = grabbedChar.HumanoidRootPart.Position
    explosion.Parent = workspace

    -- Remove the grabbed character
    Legion:Remove(grabbedChar, "all")
end, "Causes the grabbed player to explode.")
```

---

## Neckgrab Utilities

### `Legion:GetForwardPosition`
Calculates a position a specified distance in front of the local player's character. Useful for positioning effects or teleporting the grabbed player.

```lua
Legion:GetForwardPosition(distance: number) -> Vector3
```

#### Parameters:
- **`distance`**: The distance in studs to calculate the position in front of the character (number).

#### Returns:
- A `Vector3` representing the calculated position.

#### Example:
```lua
local forwardPosition = Legion:GetForwardPosition(10)
print("Forward position:", forwardPosition)
```

---

## Player and Character Utilities

### `Legion:Find`
Searches for a descendant within a parent object based on a name (case-insensitive). Useful for locating specific items or players.

```lua
Legion:Find(parent: Instance, name: string) -> Instance?
```

#### Parameters:
- **`parent`**: The object to search within (Instance).
- **`name`**: The name (or part of the name) of the object to find (string).

#### Returns:
- The found object (Instance) or `nil` if not found.

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
- **`option`**: (Optional) The name of a child object to find within the character (string). If omitted, returns the character model itself.

#### Returns:
- The character model (Model) or the found child object (Instance), or `nil` if the child is not found.

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
- **`character`**: The character model to remove the limb from (Model).
- **`part`**: The name of the limb to remove (string), or `"all"` to remove all limbs.

#### Example:
```lua
Legion:Remove(grabbedChar, "all")
```

---

## Audio and Animation Utilities

### `Legion:PlayAudio`
Plays an audio file using its asset ID.

```lua
Legion:PlayAudio(id: number)
```

#### Parameters:
-
