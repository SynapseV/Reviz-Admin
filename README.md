---GUI By - Meow_Gang#8830 ---
---Script By - Cyclically#9215 ---
--Credits to dhruvil123 (Same method but uses tools)--

-- Objects

local FeKill = Instance.new("ScreenGui")
local Header = Instance.new("Frame")
local Body = Instance.new("Frame")
local Name = Instance.new("TextBox")
local Kill = Instance.new("TextButton")
local FEKill = Instance.new("TextLabel")
local Exit = Instance.new("TextButton")
local Minimize = Instance.new("TextButton")

-- Properties

FeKill.Name = "FeKill"
FeKill.Parent = game.CoreGui
FeKill.ZIndexBehavior = Enum.ZIndexBehavior.Sibling

Header.Name = "Header"
Header.Parent = FeKill
Header.BackgroundColor3 = Color3.new(1, 0.180392, 0.180392)
Header.BorderColor3 = Color3.new(1, 0.180392, 0.180392)
Header.BorderSizePixel = 0
Header.Position = UDim2.new(0.331454366, 0, 0.246315822, 0)
Header.Size = UDim2.new(0, 191, 0, 20)
Header.Active = true
Header.Draggable = true

Body.Name = "Body"
Body.Parent = Header
Body.BackgroundColor3 = Color3.new(0.317647, 0.317647, 0.317647)
Body.BorderSizePixel = 0
Body.Position = UDim2.new(-0.000720118987, 0, 0.998849511, 0)
Body.Size = UDim2.new(0, 191, 0, 70)

Name.Name = "Name"
Name.Parent = Body
Name.BackgroundColor3 = Color3.new(1, 1, 1)
Name.BorderColor3 = Color3.new(0.243137, 0.0431373, 0.0431373)
Name.BorderSizePixel = 3
Name.Position = UDim2.new(0.125654474, 0, 0.099999994, 0)
Name.Size = UDim2.new(0, 134, 0, 26)
Name.Font = Enum.Font.SourceSans
Name.Text = ""
Name.TextColor3 = Color3.new(0, 0, 0)
Name.TextSize = 14

Kill.Name = "Kill"
Kill.Parent = Body
Kill.BackgroundColor3 = Color3.new(1, 1, 1)
Kill.Position = UDim2.new(0.272251308, 0, 0.568443537, 0)
Kill.Size = UDim2.new(0, 73, 0, 24)
Kill.Style = Enum.ButtonStyle.RobloxRoundButton
Kill.Font = Enum.Font.Arcade
Kill.Text = "KILL"
Kill.TextColor3 = Color3.new(0, 0, 0)
Kill.TextSize = 14

FEKill.Name = "FEKill"
FEKill.Parent = Header
FEKill.BackgroundColor3 = Color3.new(1, 1, 1)
FEKill.BackgroundTransparency = 1
FEKill.BorderSizePixel = 0
FEKill.Position = UDim2.new(0.031413611, 0, 0, 0)
FEKill.Size = UDim2.new(0, 46, 0, 16)
FEKill.Font = Enum.Font.Arcade
FEKill.Text = "FE KILL"
FEKill.TextColor3 = Color3.new(0, 0, 0)
FEKill.TextSize = 14
FEKill.TextXAlignment = Enum.TextXAlignment.Left
FEKill.TextYAlignment = Enum.TextYAlignment.Top

Exit.Name = "Exit"
Exit.Parent = Header
Exit.BackgroundColor3 = Color3.new(1, 1, 1)
Exit.Position = UDim2.new(0.879580975, 0, 0, 0)
Exit.Size = UDim2.new(0, 23, 0, 20)
Exit.Style = Enum.ButtonStyle.RobloxRoundButton
Exit.Font = Enum.Font.Arcade
Exit.Text = "X"
Exit.TextColor3 = Color3.new(0, 0, 0)
Exit.TextSize = 14
Exit.MouseButton1Down:connect(function()
    FeKill:Destroy()
end)

Minimize.Name = "Minimize"
Minimize.Parent = Header
Minimize.BackgroundColor3 = Color3.new(1, 1, 1)
Minimize.Position = UDim2.new(0.759162128, 0, -0.0500000007, 0)
Minimize.Size = UDim2.new(0, 23, 0, 20)
Minimize.Style = Enum.ButtonStyle.RobloxRoundButton
Minimize.Font = Enum.Font.Arcade
Minimize.Text = "-"
Minimize.TextColor3 = Color3.new(0, 0, 0)
Minimize.TextSize = 14
Minimize.MouseButton1Down:connect(function()
    local Main = game.CoreGui.FeKill.Header.Body
    if Main.Visible == true then
    Main.Visible = false
    else
        Main.Visible = true
    end
end)

--kill--
Kill.MouseButton1Down:connect(function()
    local targetname = Name.Text

local LocalPlayer = game:GetService("Players").LocalPlayer
local target = game:GetService("Players")[targetname]
local torsoname = "Torso"
if LocalPlayer.Character:FindFirstChild("Humanoid").RigType == Enum.HumanoidRigType.R15 then
    torsoname = "UpperTorso"
end
if target.Character ~= nil then
    local savepos = LocalPlayer.Character:FindFirstChild("HumanoidRootPart").CFrame
    LocalPlayer.Character:FindFirstChild(torsoname).Anchored = true
    local tool = Instance.new("Tool", LocalPlayer.Backpack)
    local hat = LocalPlayer.Character:FindFirstChildOfClass("Accessory")
    local hathandle = hat.Handle
    hathandle.Parent = tool
    hathandle.Massless = true
    tool.GripPos = Vector3.new(0, 9e99, 0)
    tool.Parent = LocalPlayer.Character
    repeat wait() until LocalPlayer.Character:FindFirstChildOfClass("Tool") ~= nil
    tool.Grip = CFrame.new(Vector3.new(0, 0, 0))
    LocalPlayer.Character:FindFirstChild(torsoname).Anchored = false
    repeat
        LocalPlayer.Character:FindFirstChild("HumanoidRootPart").CFrame = target.Character:FindFirstChild("HumanoidRootPart").CFrame
        wait()
    until target.Character == nil or target.Character:FindFirstChild("Humanoid").Health <= 0 or LocalPlayer.Character == nil or LocalPlayer.Character:FindFirstChild("Humanoid").Health <= 0 or (target.Character:FindFirstChild("HumanoidRootPart").Velocity.magnitude - target.Character:FindFirstChild("Humanoid").WalkSpeed) > (target.Character:FindFirstChild("Humanoid").WalkSpeed + 20)
    LocalPlayer.Character:FindFirstChild("Humanoid"):UnequipTools()
    hathandle.Parent = hat
    hathandle.Massless = false
    tool:Destroy()
    LocalPlayer.Character:FindFirstChild("HumanoidRootPart").CFrame = savepos
end
    end)
