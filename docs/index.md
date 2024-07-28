# Main

Welcome to Solodevs CustomNeckgrab Documentation!

## Setting Up 
**NOTE: This only needs to be done on the free version, if you use paid you can leave this part out!**
```lua title="CustomNeck Setup"
local CustomNeck = loadstring(game:HttpGet("https://please-suck.me/p/raw/7naxt0bcok"))() -- (with the getgenv().Settings over it!)
```

### Create Tool
**With this you can create a tool and assign it custom functions**
```lua title="Create Tool",linenums="1"
CustomNeck.CreateTool("Tool Name",function()
    --assigned function here
end)
```
‎  
#### AnimPlay & StopAnimation
**With this you can play Animations and Stop animations** 

```lua title="Play Animations",linenums="1"
CustomNeck.CreateTool("Play Animation",function()
    CustomNeck.AnimPlay({
        AnimationId = 1234567, 
        -- // This is all Optionial \\--
        Speed = 1, 
        Time = 0.5,
        Smoothing = 2 
    })
end)
```
```lua title="Stop Animation",linenums="1"
CustomNeck.CreateTool("Stop Animation",function()
    CustomNeck.StopAnimationId(id)
    -- to stop the grab animation you can do: CustomNeck.StopAnimationId("Grab")
end)
```
‎
#### GetBodyPosition & GetBodyGyro
**This just returns the BodyPosition & BodyGyro that is located in the Grabbed Player** (*Mostly used to just modify or remove*)
```lua title="GetBodyPosition",linenums="1"
CustomNeck.CreateTool("GetBodyPosition",function()
    local BodyPosition = CustomNeck.GetBodyPosition()
    print(BodyPosition.Position)
end)
```
```lua title="GetBodyGyro",linenums="1"
CustomNeck.CreateTool("GetBodyGyro",function()
    local BodyGyro = CustomNeck.GetBodyGyro()
    print(BodyGyro.CFrame)
end)
```
‎
#### Grab & Toggles
**This is used to e.g toggle specific things, and disable grabbing to make custom tools work** 


*Toggles:*

```
Paid: "Orbit","Turn Into Penis", "Demon Slayer", "Time Stop"
```

```
Free: "Get over here", "Punch smth idk", "Break Apart", "Rip Apart", "Make Player Invisible", "Move to Mouse", "Facing"
```
```lua title="Toggle",linenums="1"
CustomNeck.CreateTool("Example Toggles",function()
    CustomNeck.Toggle("Activated",false) -- disabling the Activated toggle so you dont loop grab the player
    CustomNeck.Grab(true) -- disable making the player teleport to your right hand, make sure to set to false at the end of your tool
end)
```
‎
#### Play & Stop
**With this you can play audios trough a boombox** (*If you dont have boombox the audios will still play but only clientsided*)

```lua title="Play Audio",linenums="1"
CustomNeck.CreateTool("Play Audio",function()
    CustomNeck.Play(audio id)
end)
```
```lua title="Stop Audio",linenums="1"
CustomNeck.CreateTool("Stop Audio",function()
    CustomNeck.StopAudio()
end)
```
‎
#### Move Body
**With this you can move the body of the grabbed character** (*For this you have 2 methods, tween or tp*)

```lua title="Move Body Tween",linenums="1"
CustomNeck.CreateTool("MoveBody tween",function()
    CustomNeck.Grab(true) -- make sure to always disable this after using tools so at the end of every tool of yours do: CustomNeck.Grab(false)
    CustomNeck.Toggle("Activated",false)
    CustomNeck.MoveBody("tween",{
        Speed = 1.2, -- in seconds (how long it takes to finish the tween)
        Position = game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.Position
    }) 
end)
```
```lua title="Move Body Tp",linenums="1"
CustomNeck.CreateTool("MoveBody Tp",function()
    CustomNeck.Grab(true) -- make sure to always disable this after using tools so at the end of every tool of yours do: CustomNeck.Grab(false)
    CustomNeck.Toggle("Activated",false)
    CustomNeck.MoveBody("tp",{
        Position = game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.Position
    }) 
end)
```
‎
#### Send to void
**This just sends the player into the void** 

```lua title="Send to void",linenums="1"
CustomNeck.CreateTool("Send to void",function()
    CustomNeck.Grab(true) -- make sure to always disable this after using tools so at the end of every tool of yours do: CustomNeck.Grab(false)
    CustomNeck.Toggle("Activated",false)

    CustomNeck.SendToVoid(10) -- 10 is the amount of time you'll wait before sending him to wait, customizable 
end)
```
‎
#### Grabbed
**Just returns the Character of the Grabbed player** 

```lua title="Grabbed",linenums="1"
CustomNeck.CreateTool("Grabbed",function()
    print(tostring(CustomNeck.Grabbed()))
end)
```
‎
#### Chat
**This just basically makes you say message in the chat** 

```lua title="Chat",linenums="1"
CustomNeck.CreateTool("Chat",function()
    CustomNeck.Chat("This is a test message")
end)
```
‎
#### Rip
**With this you rip parts of the player** ([Parts here](https://create.roblox.com/docs/reference/engine/enums/BodyPartR15))
```lua title="Rip",linenums="1"
CustomNeck.CreateTool("Rip",function()
    CustomNeck.Grab(true) -- make sure to always disable this after using tools so at the end of every tool of yours do: CustomNeck.Grab(false)
    CustomNeck.Toggle("Activated",false)

    CustomNeck.Rip("RightUpperLeg") -- Part Name
end)
```
