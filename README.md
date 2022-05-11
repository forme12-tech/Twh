local VLib = loadstring(game:HttpGet("https://raw.githubusercontent.com/forme12-tech/Tower-of-hell/main/README.md"))()
 
local s = VLib:Window("Tower Of Hell Gui", "By Glodamord", "TOH")
 
local ss = s:Tab("General")
 
ss:Button("Bypass Anticheat",function()
    local reg = getreg()
 
    for i, Function in next, reg do
        if type(Function) == 'function' then
            local info = getinfo(Function)
 
            if info.name == 'kick' then
                if (hookfunction(info.func, function(...)end)) then
                    print'succesfully fuck that anticheat'
                else
                    print'failed to fuck the anticheat'
                end
            end
        end
    end
    local playerscripts = game:GetService'Players'.LocalPlayer.PlayerScripts
 
    local script1 = playerscripts.LocalScript
    local script2 = playerscripts.LocalScript2
 
    local script1signal = script1.Changed
    local script2signal = script2.Changed
 
    for i, connection in next, getconnections(script1signal) do
        connection:Disable()
    end
    for i, connection in next, getconnections(script2signal) do
        connection:Disable()
    end
 
    script1:Destroy()
    script2:Destroy()
end)
 
ss:Button("Go To End",function()
    local endzone = game.Workspace.tower.sections.finish.FinishGlow.CFrame
 
    local player = game.Players.LocalPlayer.Character
    player.HumanoidRootPart.CFrame = endzone
end)
 
ss:Button("Get All Items",function()
    for _,e in pairs(game.Players.LocalPlayer.Backpack:GetDescendants()) do
        if e:IsA("Tool") then
        e:Destroy()
        end
        end
        wait() 
        for _,v in pairs(game.ReplicatedStorage.Gear:GetDescendants()) do
        if v:IsA("Tool") then
        local CloneThings = v:Clone()
        wait()
        CloneThings.Parent = game.Players.LocalPlayer.Backpack
 
        end
        end
end)
 
ss:Button("Remove Kill Parts",function()
    for i,v in pairs(game:GetService("Workspace").tower:GetDescendants()) do
        if v:IsA("BoolValue") and v.Name == "kills" then
            v.Parent:Destroy()
        end
    end
end)
 
ss:Slider("WalkSpeed",0,500,16,function(t)
   game.Players.LocalPlayer.Character.Humanoid.WalkSpeed = t
end)
 
ss:Slider("JumpPower (Dont use it to high)",0,500,50,function(t)
    game.Players.LocalPlayer.Character.Humanoid.JumpPower = t
 end)
 
ss:Button("Reset Walk and Jump",function()
    game.Players.LocalPlayer.Character.Humanoid.WalkSpeed = 16
    game.Players.LocalPlayer.Character.Humanoid.JumpPower = 50
end)
 
ss:Button("Anti Lag",function()
    loadstring(game:HttpGet('https://pastebin.com/raw/eVHmQQvQ'))()
end)
 
local sss = s:Tab("Auto Farm")
 
-- Table
getgenv().Boolean = false
 
sss:Toggle("Auto Farm",function(v)
    getgenv().Boolean = v
 
    if v then -- if v == true then
    name()
    end
end)
 
-- function
function name()
spawn(function()
while getgenv().Boolean == true do
local endzone = game.Workspace.tower.sections.finish.FinishGlow.CFrame
 
local player = game.Players.LocalPlayer.Character
player.HumanoidRootPart.CFrame = endzone
wait()
end
end)
end
 
sss:Button("Anti Afk",function()
    local vu = game:GetService("VirtualUser")
    game:GetService("Players").LocalPlayer.Idled:connect(function()
       vu:Button2Down(Vector2.new(0,0),workspace.CurrentCamera.CFrame)
       wait(1)
       vu:Button2Up(Vector2.new(0,0),workspace.CurrentCamera.CFrame)
    end)
end)
 
 
local ssss = s:Tab("Credits")
 
ssss:Label("Gui By Glodamord/Adrik")
