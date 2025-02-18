# Documentation
## Creating Tools
```lua
Legion:GrabTool("Name",function()
    --callback
end,"Description")
```
## Find
```lua
Legion:Find(Parent,Name)
--(so e.g)
local LmgAmmo = Legion:Find(Services.Workspace.Ignored.Shop,"lmg ammo"))
```
## Shoot
```lua
Legion:Shoot(targetname,gunParent)
```
```lua
local Character = Legion:GetChar("") -- Legion:GetChar("") returns the character, but if you want to find something in the character you can do Legion:GetChar("BodyEffects") e.g
local Gun = Character:FindFirstChild("[LMG]")
Legion:Shoot("FullPlayerUserName",Gun)
```
## Delete
```lua
Legion:Delete(Parent,{classes})
--(so e.g)
Legion:Delete(Legion:GetChar(""),{"BodyVelocity","BodyGyro",...}))
```
