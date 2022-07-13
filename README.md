local Library = loadstring(game:HttpGet("https://raw.githubusercontent.com/xHeptc/Kavo-UI-Library/main/source.lua"))()
local Window = Library.CreateLib("Welcome To Pylwt Hub", "DarkTheme")

local Main = Window:NewTab("Main")
local MainSection = Main:NewSection("Tracking")
MainSection:NewButton("ESP", "Click to get tool", function()
    loadstring(game:HttpGet("https://cdn.wearedevs.net/scripts/WRD ESP.txt"))()
end)
MainSection:NewButton("Charms", "Click to get tool", function()
    pcall(loadstring(game:HttpGet("https://pastebin.com/raw/eH39iKSg")))
end)
local MainSection = Main:NewSection("B-Tools")
MainSection:NewButton("Btools V1", "Click to get tool", function()
    loadstring(game:HttpGet('https://raw.githubusercontent.com/TrixAde/scripts/main/Btools.lua', true))() 
end)
MainSection:NewButton("Btools V2", "Click to get tool", function()
    Instance.new("HopperBin", game.Players.LocalPlayer.Backpack).BinType = 2
Instance.new("HopperBin", game.Players.LocalPlayer.Backpack).BinType = 3
Instance.new("HopperBin", game.Players.LocalPlayer.Backpack).BinType = 4 
end)
local MainSection = Main:NewSection("Studio Editor")
MainSection:NewButton("DarkDexV3", "Click to get tool", function()
    loadstring(game:HttpGet("https://raw.githubusercontent.com/TrixAde/scripts/main/DarkDexV3.lua"))(); 
end)
local Player = Window:NewTab("Player")
local PlayerSection = Player:NewSection("Player Section")
PlayerSection:NewButton("Fly", "Press C", function()
    pcall(loadstring(game:HttpGet("https://pastebin.com/raw/ReJ0TXqg")))
end)
PlayerSection:NewButton("No Clip", "Press B", function()
    pcall(loadstring(game:HttpGet("https://pastebin.com/raw/kt3Nxzw1")))
end)
local PlayerSection = Player:NewSection("Teleportation")
PlayerSection:NewButton("Click TP", "Click to get tool", function()
    pcall(loadstring(game:HttpGet("https://pastebin.com/raw/njMw0Bke")))
end)
PlayerSection:NewButton("Player TP", "Click to get tool", function()
    loadstring(game:HttpGet("https://pastebin.com/raw/EBhdqeWb", true))()
end)
local PlayerSection = Player:NewSection("Movement")
PlayerSection:NewButton("Shift Run", "Press Shift", function()
    repeat wait() until game.Players.LocalPlayer 
m = game.Players.LocalPlayer:GetMouse() 
m.KeyDown:connect(function(key)
 if key == "0" then --"Shift to run" 0 == shift
  print("Running")
  game.Players.LocalPlayer.Character.Humanoid.WalkSpeed = 60
 end
end) 
m.KeyUp:connect(function(key)
 if key == "0" then
  game.Players.LocalPlayer.Character.Humanoid.WalkSpeed = 16
 end
end)
end)
PlayerSection:NewButton("High Jump", "Click to get tool", function()
    pcall(loadstring(game:HttpGet("https://pastebin.com/raw/0JgQ1hJy")))
end)
PlayerSection:NewButton("Infinite Jump", "Press V", function()
    pcall(loadstring(game:HttpGet("https://pastebin.com/raw/2wgbZ6Xd"))) 
end)
local PlayerSection = Player:NewSection("Visuals")
PlayerSection:NewButton("Korblox", "Click to get korblox leg", function()
    local char = game:GetService("Players").LocalPlayer.Character
-- RIGHT LEG
char.RightFoot.MeshId = "http://www.roblox.com/asset/?id=902942089"
char.RightFoot.Transparency = 1
char.RightLowerLeg.MeshId = "http://www.roblox.com/asset/?id=902942093"
char.RightLowerLeg.Transparency = 1
char.RightUpperLeg.MeshId = "http://www.roblox.com/asset/?id=902942096"
char.RightUpperLeg.TextureID = "http://roblox.com/asset/?id=902843398"
end)
PlayerSection:NewButton("Force Field", "Click to get force field", function()
end)
local Admin = Window:NewTab("Admin")
local AdminSection = Admin:NewSection("OP Stuff")
AdminSection:NewButton("CMD-X Admin Commands", "Click to get tool", function()
    loadstring(game:HttpGet('https://raw.githubusercontent.com/CMD-X/CMD-X/master/Source', true))()
end)
AdminSection:NewButton("Infinite Yield Admin Commands", "Click to get tool", function()
    loadstring(game:HttpGet(('https://raw.githubusercontent.com/EdgeIY/infiniteyield/master/source'),true))()
end)
AdminSection:NewButton("Fates Admin Commands", "Click to get tool", function()
    loadstring(game:HttpGet("https://raw.githubusercontent.com/fatesc/fates-admin/main/main.lua"))()
end)
AdminSection:NewButton("God Mode", "Click to get tool", function()
    loadstring(game:HttpGet("https://pastebin.com/raw/FwfNEqYz", true))() 
end)
AdminSection:NewButton("Invisible God Mode", "Click to get tool", function()
    loadstring(game:HttpGet("https://pastebin.com/raw/HMcCQbpk", true))()
end)
AdminSection:NewButton("Studio Editor", "Click to get tool", function()
    loadstring(game:HttpGet("https://raw.githubusercontent.com/TrixAde/scripts/main/DarkDexV3.lua"))();
end)
local Games = Window:NewTab("Games")
local GamesSection = Games:NewSection("Join the game you want & click the buttons below")

GamesSection:NewButton("Prison Life", "You must be in the game for it to work", function()
    loadstring(game:HttpGet("https://pastebin.com/raw/wMagw9Cn", true))()
end)
GamesSection:NewButton("Gun Simulator", "You must be in the game for it to work", function()
    loadstring(game:HttpGet("https://paste.ee/r/KOoZW", true))()
end)
GamesSection:NewButton("Tower Of Hell", "You must be in the game for it to work", function()
    loadstring(game:HttpGet("https://raw.githubusercontent.com/iiProductionz/Floater-Scripts/main/WaifuEdition/Tower%20Of%20Hell"))()
end)
GamesSection:NewButton("Legends Of Speed", "You must be in the game for it to work", function()
    loadstring(game:HttpGet("https://raw.githubusercontent.com/TrixAde/Proxima-Hub/main/Main.lua"))()
end)
GamesSection:NewButton("Ninja Legends", "You must be in the game for it to work", function()
    loadstring(game:HttpGet("https://raw.githubusercontent.com/TrixAde/Proxima-Hub/main/Main.lua"))()
end)
GamesSection:NewButton("Saber Simulator", "You must be in the game for it to work", function()
    loadstring(game:HttpGet("https://raw.githubusercontent.com/TrixAde/Proxima-Hub/main/Main.lua"))()
end)
GamesSection:NewButton("BIG Paintball", "You must be in the game for it to work", function()
    pcall(loadstring(game:HttpGet("https://raw.githubusercontent.com/TrixAde/scripts/main/paintball.lua")))
loadstring(game:HttpGet('https://pastebin.com/raw/GVvyGhpx'))()
end)
GamesSection:NewButton("Adopt Me", "You must be in the game for it to work", function()
    loadstring(game:HttpGet("https://raw.githubusercontent.com/1201for/V.G-Hub/main/V.Ghub"))()
end)
GamesSection:NewButton("Roblox Talent Show", "You must be in the game for it to work", function()
    loadstring(game:HttpGet("https://raw.githubusercontent.com/liloskiller/Scripts/main/TalentShowObbyAutoFarm", true))()
end)
GamesSection:NewButton("Da Hood", "You must be in the game for it to work", function()
    loadstring(game:HttpGet('https://raw.githubusercontent.com/TrixAde/scripts/main/DaHood-DoomWare.lua', true))()
end)
GamesSection:NewButton("Squid Games Obby", "You must be in the game for it to work", function()
    --// Services \\--
local Workspace = game:GetService("Workspace")
local Players = game:GetService("Players")

--// Variables \\--
local Player = Players.LocalPlayer
local Tiles = Workspace:WaitForChild("Map"):WaitForChild("Game"):WaitForChild("Tiles")
local Original = Color3.fromRGB(198, 237, 255)

--// Remember Broken Glass \\--
Tiles.DescendantAdded:Connect(function(A_1)
    if A_1.Name == "GlassShatter" then
        -- Set Color
        A_1.Parent.Color = Color3.new(1, 0, 0)
        -- Get Lane
        local Lane = A_1.Parent.Parent.Name
        if Lane == "Right" then
            Lane = "Left"
        else
            Lane = "Right"
        end
        -- Set Sibling Color
        local Number = A_1.Parent.Name:match("%d+")
        Tiles[Lane]["Tile" .. Number].Color = Color3.new(0, 1, 0)
    end
end)

--// Remember Stepped Glass \\--
for _, A_1 in next, Tiles:GetDescendants() do
    if A_1:IsA("TouchTransmitter") then
        local Part = A_1.Parent
        Part.Touched:Connect(function(A_2)
            -- Check if already broken
            if A_2.Transparency == 1 then
                return
            end
            -- Timer
            local Timer = tick() + 0.5
            repeat
                task.wait()
            until tick() - Timer > 0 or Part.Transparency == 1
            -- Get Lane
            local Lane = A_1.Parent.Parent.Name
            if Lane == "Right" then
                Lane = "Left"
            else
                Lane = "Right"
            end
            -- Check if broke
            if Part.Transparency == 1 then
                -- Set Glass Color
                Part.Color = Color3.new(1, 0, 0)
                -- Set Sibling Color
                local Number = A_1.Parent.Name:match("%d+")
                Tiles[Lane]["Tile" .. Number].Color = Color3.new(0, 1, 0)
            elseif A_2.Parent.Humanoid.Health == 100 then
                -- Set Glass Color
                Part.Color = Color3.new(0, 1, 0)
                -- Set Sibling Color
                local Number = A_1.Parent.Name:match("%d+")
                Tiles[Lane]["Tile" .. Number].Color = Color3.new(1, 0, 0)
            end
        end)
    end
end

--// UI Library \\--
local Library = loadstring(game:HttpGetAsync('https://raw.githubusercontent.com/Just-Egg-Salad/roblox-scripts/main/uwuware'))()
local Window = Library:CreateWindow("Memory by Ezpi")
Window:AddButton({
    text = "Clear Colors",
    callback = function()
        for _, A_1 in next, Tiles:GetDescendants() do
            if A_1:IsA("BasePart") then
                A_1.Color = Original
            end
        end
    end
})
Library:Init()
end)
local GamesSection = Games:NewSection("None of the scripts above are mine!")
local Credits = Window:NewTab("Credits")
local CreditsSection = Credits:NewSection("Made By Tim")
local CreditsSection = Credits:NewSection("Discord: @Pylwt#6567")
local CreditsSection = Credits:NewSection("Stapchat: @tfr.p")
local CreditsSection = Credits:NewSection("Server: .gg/QnbxmxMrJG")
local CreditsSection = Credits:NewSection("Thank you for choosing Pylwt Hub!")
