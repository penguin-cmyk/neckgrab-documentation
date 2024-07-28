# Paid
**In general you have some variables defined (only in paid)**


**Defined Varibales here**

```
LocalPlayer,RunService,ReplicatedStorage,Players
```

```lua
-- Example of how to use it:
-- Instead of needing to do
game:GetService("Players").LocalPlayer.Character
-- You can just do and wont be needing to define players before it
LocalPlayer.Character
```

‎
## Move Forward
**This will make the grabbed Character MoveForward with a specific distance**
```lua title="Moveforward Tween",linenums="1"
CustomNeck.CreateTool("Move forward test Tween",function()
    CustomNeck.Grab(true)
    CustomNeck.Toggle("Activated",false)
    CustomNeck.MoveForward({
        Method = "tween",
        Distance = 10, -- in studs
        Duration = 3, -- how long you want it to take to make the player go to the desired distance, needs to be removed when using normal tp
    })
    task.wait(Duration here) -- recommended to make it fit with the tween duration
    CustomNeck.Grab(false)
end)
```
```lua title="Moveforward Teleport",linenums="1"
CustomNeck.CreateTool("Move forward test Teleport",function()
    CustomNeck.Grab(true)
    CustomNeck.Toggle("Activated",false)
    CustomNeck.MoveForward({
        Distance = 10, -- in studs
    })
    CustomNeck.Grab(false)
end)
```
‎
## Move Part
**This moves a specific part of the grabbed character**
```lua title="MovePart",linenums="1"
local Loop;
CustomNeck.CreateTool("MovePart test",function()
    CustomNeck.Grab(true)
    CustomNeck.Toggle("Activated",false)

    Loop = RunService.Heartbeat:Connect(function()
        CustomNeck.MovePart({
            Part = "RightUpperArm",
            Position = LocalPlayer.Character:FindFirstChild("HumanoidRootPart").Position
        })
    end)
    task.wait(1)
    Loop:Disconnect()
    CustomNeck.Grab(false)
end)
```
‎
## Spin
**This will make the player spin around in a specific Radius, and so on**

```lua title="Spin",linenums="1"
CustomNeck.CreateTool("Spin test",function()
  CustomNeck.Grab(true) -- make sure to always disable this after using tools so at the end of every tool of yours do: CustomNeck.Grab(false)
  CustomNeck.Toggle("Activated",false)
  CustomNeck.Spin({
    Radius = 5, -- in studs, distance around you
    rotationTime = 2, -- time (in seconds) to complete one full rotation around you
    Duration = 4, -- time (in seconds) of how long you want it to be spinning in general!
  })
end)  
```