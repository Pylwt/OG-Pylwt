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
MainSection:NewButton("X-Ray", "Press X", function()
    loadstring(game:HttpGet("https://pastebin.com/raw/vNpnSDCz", true))()
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
PlayerSection:NewButton("Front/Back Flips", "Press Z,X,C", function()
    wait(5)
local ver = "2.00"
local scriptname = "feFlip"
local FrontflipKey = Enum.KeyCode.Z
local BackflipKey = Enum.KeyCode.X
local AirjumpKey = Enum.KeyCode.C
local ca = game:GetService("ContextActionService")
local zeezy = game:GetService("Players").LocalPlayer
local h = 0.0174533
local antigrav
function zeezyFrontflip(act,inp,obj)
	if inp == Enum.UserInputState.Begin then
		zeezy.Character.Humanoid:ChangeState("Jumping")
		wait()
		zeezy.Character.Humanoid.Sit = true
		for i = 1,360 do 
			delay(i/720,function()
			zeezy.Character.Humanoid.Sit = true
				zeezy.Character.HumanoidRootPart.CFrame = zeezy.Character.HumanoidRootPart.CFrame * CFrame.Angles(-h,0,0)
			end)
		end
		wait(0.55)
		zeezy.Character.Humanoid.Sit = false
	end
end
function zeezyBackflip(act,inp,obj)
	if inp == Enum.UserInputState.Begin then
		zeezy.Character.Humanoid:ChangeState("Jumping")
		wait()
		zeezy.Character.Humanoid.Sit = true
		for i = 1,360 do
			delay(i/720,function()
			zeezy.Character.Humanoid.Sit = true
				zeezy.Character.HumanoidRootPart.CFrame = zeezy.Character.HumanoidRootPart.CFrame * CFrame.Angles(h,0,0)
			end)
		end
		wait(0.55)
		zeezy.Character.Humanoid.Sit = false
	end
end
function zeezyAirjump(act,inp,obj)
	if inp == Enum.UserInputState.Begin then
		zeezy.Character:FindFirstChildOfClass'Humanoid':ChangeState("Seated")
		wait()
		zeezy.Character:FindFirstChildOfClass'Humanoid':ChangeState("Jumping")	
	end
end
ca:BindAction("zeezyFrontflip",zeezyFrontflip,false,FrontflipKey)
ca:BindAction("zeezyBackflip",zeezyBackflip,false,BackflipKey)
ca:BindAction("zeezyAirjump",zeezyAirjump,false,AirjumpKey)
print(scriptname .. " " .. ver .. " loaded successfully")
print("made by Zeezy#7203")
local notifSound = Instance.new("Sound",workspace)
notifSound.PlaybackSpeed = 1.5
notifSound.Volume = 0.15
notifSound.SoundId = "rbxassetid://170765130"
notifSound.PlayOnRemove = true
notifSound:Destroy()
game.StarterGui:SetCore("SendNotification", {Title = "feFlip", Text = "feFlip loaded successfully!", Icon = "rbxassetid://505845268", Duration = 5, Button1 = "Okay"})
end)
PlayerSection:NewSlider("Walk Speed", "Choose your walk speed", 500, 16, function(s) -- 500 (MaxValue) | 0 (MinValue)
    game.Players.LocalPlayer.Character.Humanoid.WalkSpeed = s
end)
PlayerSection:NewSlider("Jump Power", "Choose your jump power", 500, 50, function(s) -- 500 (MaxValue) | 0 (MinValue)
    game.Players.LocalPlayer.Character.Humanoid.JumpPower = s
end)
local PlayerSection = Player:NewSection("Visuals")
PlayerSection:NewButton("Headless", "Click to get force field", function()
    local lp = game:GetService "Players".LocalPlayer
if lp.Character:FindFirstChild "Head" then
    local char = lp.Character
    char.Archivable = true
    local new = char:Clone()
    new.Parent = workspace
    lp.Character = new
    wait(2)
    local oldhum = char:FindFirstChildWhichIsA "Humanoid"
    local newhum = oldhum:Clone()
    newhum.Parent = char
    newhum.RequiresNeck = false
    oldhum.Parent = nil
    wait(2)
    lp.Character = char
    new:Destroy()
    wait(1)
    newhum:GetPropertyChangedSignal("Health"):Connect(
        function()
            if newhum.Health <= 0 then
                oldhum.Parent = lp.Character
                wait(1)
                oldhum:Destroy()
            end
        end)
    workspace.CurrentCamera.CameraSubject = char
    if char:FindFirstChild "Animate" then
        char.Animate.Disabled = true
        wait(.1)
        char.Animate.Disabled = false
    end
    lp.Character:FindFirstChild "Head":Destroy()
end
end)
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
local Tools = Window:NewTab("All Tools")
local ToolsSection = Tools:NewSection("Here are all the tools we have.")
local ToolsSection = Tools:NewSection("Some might not work!")
ToolsSection:NewButton("Charms", "Click to get tool", function()
    pcall(loadstring(game:HttpGet("https://pastebin.com/raw/eH39iKSg")))
end)
ToolsSection:NewButton("Ctrl Delete", "Click to get tool", function()
    pcall(loadstring(game:HttpGet("https://pastebin.com/raw/KGYKmYtW")))
end)
ToolsSection:NewButton("ESP", "Click to get tool", function()
    loadstring(game:HttpGet("https://cdn.wearedevs.net/scripts/WRD ESP.txt"))()
end)
ToolsSection:NewButton("Fly V1", "Press C", function()
    pcall(loadstring(game:HttpGet("https://pastebin.com/raw/ReJ0TXqg")))
end)
ToolsSection:NewButton("Fly V2", "Press E", function()
    loadstring(game:HttpGet("https://pastebin.com/raw/jebnPDXh", true))()
end)
ToolsSection:NewButton("FOV", "Click to get tool", function()
    pcall(loadstring(game:HttpGet("https://pastebin.com/raw/PRw16c2Y")))
end)
ToolsSection:NewButton("God Mode", "Click to get tool", function()
    loadstring(game:HttpGet("https://pastebin.com/raw/FwfNEqYz", true))()
end)
ToolsSection:NewButton("Gravity", "Click to get tool", function()
    pcall(loadstring(game:HttpGet("https://pastebin.com/raw/0JgQ1hJy")))
end)
ToolsSection:NewButton("Infinite Jump", "Press V", function()
    pcall(loadstring(game:HttpGet("https://pastebin.com/raw/2wgbZ6Xd")))
end)
ToolsSection:NewButton("Invisible God Mode", "Click to get tool", function()
    loadstring(game:HttpGet("https://pastebin.com/raw/HMcCQbpk", true))()
end)
ToolsSection:NewButton("Less Lag", "Click to get tool", function()
    loadstring(game:HttpGet("https://pastebin.com/raw/eHEfAR8z", true))()
end)
ToolsSection:NewButton("No Clip", "Press B", function()
    pcall(loadstring(game:HttpGet("https://pastebin.com/raw/kt3Nxzw1")))
end)
ToolsSection:NewButton("Reset", "Click to get tool", function()
    game.Players.LocalPlayer:GetMouse().KeyUp:connect(function(key)
    if key == "r"  then
        game.Players.LocalPlayer.character:WaitForChild("Humanoid").Health = 0
    end  
end)
end)
ToolsSection:NewButton("Shift Run", "Click to get tool", function()
    repeat wait() until game.Players.LocalPlayer
m = game.Players.LocalPlayer:GetMouse()
m.KeyDown:connect(function(key)
 if key == "0" then --"Shift to run" 0 == shift
  print("Running")
  game.Players.LocalPlayer.Character.Humanoid.WalkSpeed = 70
 end
end)
m.KeyUp:connect(function(key)
 if key == "0" then
  game.Players.LocalPlayer.Character.Humanoid.WalkSpeed = 16
 end
end)
end)
ToolsSection:NewButton("TP tool", "Click to get tool", function()
    pcall(loadstring(game:HttpGet("https://pastebin.com/raw/njMw0Bke")))
end)
ToolsSection:NewButton("X-Ray", "Press X", function()
    loadstring(game:HttpGet("https://pastebin.com/raw/vNpnSDCz", true))()
end)
ToolsSection:NewButton("Anti AFK", "Click to get tool", function()
    pcall(loadstring(game:HttpGet("https://pastebin.com/raw/dnwYtGCQ")))
end)
ToolsSection:NewButton("B-Tools V1", "Click to get tool", function()
    loadstring(game:HttpGet('https://raw.githubusercontent.com/TrixAde/scripts/main/Btools.lua', true))()
end)
ToolsSection:NewButton("B-Tools V2", "Click to get tool", function()
    Instance.new("HopperBin", game.Players.LocalPlayer.Backpack).BinType = 2
Instance.new("HopperBin", game.Players.LocalPlayer.Backpack).BinType = 3
Instance.new("HopperBin", game.Players.LocalPlayer.Backpack).BinType = 4
end)
ToolsSection:NewButton("RTX", "Click to get tool", function()
    loadstring(game:HttpGet("https://pastebin.com/raw/zxV27xHc", true))()
end)
ToolsSection:NewButton("Spectate", "Click to get tool", function()
    loadstring(game:HttpGet("https://pastebin.com/raw/WgpJfMGS", true))()
end)
ToolsSection:NewButton("TP Gui", "Click to get tool", function()
    loadstring(game:HttpGet("https://pastebin.com/raw/EBhdqeWb", true))()
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
local Trolling = Window:NewTab("Trolling")
local TrollingSection = Trolling:NewSection("Guns")
TrollingSection:NewButton("Pistol", "Click to get tool", function()
    loadstring(game:HttpGet("https://pastebin.com/raw/SeRxrgci", true))()
end)
TrollingSection:NewButton("AK-47", "Click to get tool", function()
    game:GetObjects("rbxassetid://149948769")[1].Parent=game.Players.LocalPlayer.Backpack
end)
TrollingSection:NewButton("Telekinisis Gun", "Click to get tool", function()
    loadstring(game:HttpGet("https://pastebin.com/raw/fauftxLe", true))()
end)
local TrollingSection = Trolling:NewSection("Broken Stuff")
TrollingSection:NewButton("Rocket Spin", "Click to get tool", function()
power = 1000 -- change this to make it more or less powerful
game:GetService('RunService').Stepped:connect(function()
game.Players.LocalPlayer.Character.Head.CanCollide = false
game.Players.LocalPlayer.Character.UpperTorso.CanCollide = false
game.Players.LocalPlayer.Character.LowerTorso.CanCollide = false
game.Players.LocalPlayer.Character.HumanoidRootPart.CanCollide = false
end)
wait(.1)
local bambam = Instance.new("BodyThrust")
bambam.Parent = game.Players.LocalPlayer.Character.HumanoidRootPart
bambam.Force = Vector3.new(power,0,power)
bambam.Location = game.Players.LocalPlayer.Character.HumanoidRootPart.Position
end)
TrollingSection:NewButton("Chat Spoofer", "Click to get tool", function()
    loadstring(game:HttpGet(('https://pastebin.com/raw/djBfk8Li'),true))()
end)
TrollingSection:NewButton("Server Message", "Send a fake server message", function()
    player =  "Server"
fakemsg = "Welcome Admin (c00lkidd) joined"
message = "Hi                                                                                                                                                            ["..tostring(player).."]: "..tostring(fakemsg)
game:GetService("ReplicatedStorage").DefaultChatSystemChatEvents.SayMessageRequest:FireServer(message, "All")
end)
TrollingSection:NewButton("Insult Bypass", "Click to get tool", function()
    loadstring(game:HttpGet("https://the-shed.xyz/roblox/scripts/ChatBypass", true))()
end)
TrollingSection:NewButton("Clones", "Click to get tool", function()
    loadstring(game:GetObjects('rbxassetid://7339698872')[1].Source)() 
end)
TrollingSection:NewButton("Huge Sword", "Click to get tool", function()
    game:GetObjects("rbxassetid://169934427")[1].Parent=game.Players.LocalPlayer.Backpack
end)
TrollingSection:NewButton("Swords", "Click to get tool", function()
    loadstring(game:HttpGet("https://pastebin.com/raw/80juE2kw", true))()
end)
local TrollingSection = Trolling:NewSection("Avatar Forms")
TrollingSection:NewButton("Titan Form", "Click to get tool", function()
    loadstring(game:HttpGet("https://pastebin.com/raw/ZmySaMrb", true))()
end)
TrollingSection:NewButton("Assasin Form", "Click to get tool", function()
    loadstring(game:HttpGet("https://pastebin.com/raw/bKu2GuzN", true))()
end)
TrollingSection:NewButton("Beerus Form", "Click to get tool", function()
    loadstring(game:HttpGet("https://pastebin.com/raw/c1TGDAKC", true))()
end)
TrollingSection:NewButton("Omega Form", "Click to get tool", function()
    loadstring(game:HttpGet("https://pastebin.com/raw/VSerZV3e", true))()
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
GamesSection:NewButton("AimBlox", "You must be in the game for it to work", function()
    loadstring(game:HttpGet(('https://raw.githubusercontent.com/Straden/Scripts/main/stronccMain.lua'),true))()
end)
GamesSection:NewButton("Assasins", "You must be in the game for it to work", function()
    loadstring(game:HttpGet("https://raw.githubusercontent.com/1201for/V.G-Hub/main/V.Ghub"))()
end)
GamesSection:NewButton("Bloxburg", "You must be in the game for it to work", function()
    pcall(loadstring(game:HttpGet("https://pastebin.com/raw/Wcd0ajFS")))
end)
GamesSection:NewButton("Bubble Gum", "You must be in the game for it to work", function()
    loadstring(game:HttpGet("https://raw.githubusercontent.com/TrixAde/scripts/main/BubbleGumQoucxHub.lua"))()
end)
GamesSection:NewButton("Bed Wars", "You must be in the game for it to work", function()
    loadstring(game:HttpGet("https://raw.githubusercontent.com/7GrandDadPGN/VapeV4ForRoblox/main/NewMainScript.lua", true))()
end)
GamesSection:NewButton("Doomspire", "You must be in the game for it to work", function()
    loadstring(game:HttpGet("https://raw.githubusercontent.com/2dgeneralspam1/scripts-and-stuff/master/scripts/garfield%20hub", true))()
end)
GamesSection:NewButton("Islands", "You must be in the game for it to work", function()
    loadstring(game:HttpGet("http://void-scripts.com/Scripts/islands_new.lua"))()
end)
GamesSection:NewButton("KAT", "You must be in the game for it to work", function()
    loadstring(game:HttpGet("https://pastebin.com/raw/78kG7trR", true))()
end)
GamesSection:NewButton("Murder Mystery 2", "You must be in the game for it to work", function()
    loadstring(game:HttpGet("https://pastebin.com/raw/34KnyYvi", true))()
end)
GamesSection:NewButton("Mad City", "You must be in the game for it to work", function()
    pcall(loadstring(game:HttpGet("https://raw.githubusercontent.com/TrixAde/scripts/main/mad.lua")))
end)
GamesSection:NewButton("Pet Sim X", "You must be in the game for it to work", function()
    loadstring(game:HttpGet("https://pastebin.com/raw/BdvUGb2q"))()
end)
GamesSection:NewButton("Work At A Pizza Place", "You must be in the game for it to work", function()
    loadstring(game:HttpGet("https://raw.githubusercontent.com/TrixAde/scripts/main/work-a-pizza-place.lua",true))()
end)
GamesSection:NewButton("RagDoll Engine", "You must be in the game for it to work", function()
    loadstring(game:HttpGet("https://raw.githubusercontent.com/RegularVynixu/Scripts/master/Vynixius%20Ragdoll%20Engine"))()
end)
GamesSection:NewButton("SCP 3008", "You must be in the game for it to work", function()
    loadstring(game:HttpGet'https://raw.githubusercontent.com/RunDTM/scripts/main/3008.lua')()
end)
GamesSection:NewButton("Mega Easy Obby", "You must be in the game for it to work", function()
    loadstring(game:HttpGet("https://pastebin.com/raw/X361rzKq"))()
end)
GamesSection:NewButton("Blox Fruits", "You must be in the game for it to work", function()
    loadstring(game:HttpGet('https://raw.githubusercontent.com/Cve-Hub/LnHub/main/README.md'))()
end)
GamesSection:NewButton("Funky Friday", "You must be in the game for it to work", function()
    loadstring(game:HttpGet("https://raw.githubusercontent.com/ZoinkyPoinkie/FunkyFridayDevTools/main/Un-Obfuscated",true))()
end)
local GamesSection = Games:NewSection("None of the scripts above are mine!")
local Hubs = Window:NewTab("Hubs")
local HubsSection = Hubs:NewSection("These Are Hubs From Other People!")
HubsSection:NewButton("Alpha X Hub", "Click to open hub", function()
    loadstring(game:HttpGet("https://pastebin.com/raw/bUmX44UN", true))()
end)
HubsSection:NewButton("Bolts Hub", "Click to open hub", function()
    loadstring(game:HttpGet(('https://raw.githubusercontent.com/fusiongreg/BoltsHubV5/main/BoltsHubV5'), true))()
end)
HubsSection:NewButton("Bruh Hub", "Click to open hub", function()
    loadstring(game:HttpGet("https://bruh.keshsenpai.com/.lua"))()
end)
HubsSection:NewButton("Dark Hub", "Click to open hub", function()
    loadstring(game:HttpGet("https://raw.githubusercontent.com/RandomAdamYT/DarkHub/master/Init", true))()
end)
HubsSection:NewButton("Eclipse Hub", "Click to open hub", function()
    loadstring(game:HttpGet("https://pastebin.com/raw/34KnyYvi", true))()
end)
HubsSection:NewButton("Extreme Hub", "Click to open hub", function()
    loadstring(game:HttpGet("https://raw.githubusercontent.com/ExtremeAntonis/KeySystemUI/main/KeySystemUI-Obfuscated.lua"))()
end)
HubsSection:NewButton("EZ Hub", "Click to open hub", function()
    loadstring(game:HttpGet(('https://raw.githubusercontent.com/debug420/Ez-Industries-Launcher-Data/master/Launcher.lua'),true))()
end)
HubsSection:NewButton("Sorky Hub", "Click to open hub", function()
    loadstring(game:HttpGet(('https://pastebin.com/raw/MHx8q6xP'),true))()
end)
HubsSection:NewButton("Owl Hub", "Click to open hub", function()
    loadstring(game:HttpGet("https://raw.githubusercontent.com/CriShoux/OwlHub/master/OwlHub.txt"))();
end)
HubsSection:NewButton("VG Hub", "Click to open hub", function()
    loadstring(game:HttpGet("https://raw.githubusercontent.com/1201for/V.G-Hub/main/V.Ghub"))()
end)
local HubsSection = Hubs:NewSection("None of the scripts above are mine!")
local Credits = Window:NewTab("Credits")
local CreditsSection = Credits:NewSection("Made By Tim")
local CreditsSection = Credits:NewSection("Discord: @Pylwt#6567")
local CreditsSection = Credits:NewSection("Stapchat: @tfr.p")
local CreditsSection = Credits:NewSection("Server: .gg/QnbxmxMrJG")
local CreditsSection = Credits:NewSection("Thank you for choosing Pylwt Hub!")
