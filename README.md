-- Subscribe to ProjectCoxelizo, i make bypasses.
-- You can mostly see me on Dollhouse Roleplay.
-- My Username is ProjectCoxelizo.
-- Version: 2.82
-- Instances:
local ScreenGui = Instance.new("ScreenGui")
local Frame = Instance.new("Frame")
local TextBox = Instance.new("TextBox")
local TextButton = Instance.new("TextButton")
local TextButton_2 = Instance.new("TextButton")
local TextLabel = Instance.new("TextLabel")
--Properties:
ScreenGui.Parent = game.Players.LocalPlayer:WaitForChild("PlayerGui")
ScreenGui.ZIndexBehavior = Enum.ZIndexBehavior.Sibling

Frame.Parent = ScreenGui
Frame.BackgroundColor3 = Color3.new(0.364706, 0.364706, 0.364706)
Frame.Position = UDim2.new(0, 0, 0.416461915, 0)
Frame.Size = UDim2.new(0, 157, 0, 125)

TextBox.Parent = Frame
TextBox.BackgroundColor3 = Color3.new(0.4, 0.4, 0.4)
TextBox.Position = UDim2.new(0.0617061071, 0, 0.32585302, 0)
TextBox.Size = UDim2.new(0, 136, 0, 30)
TextBox.Font = Enum.Font.SourceSans
TextBox.Text = ""
TextBox.TextColor3 = Color3.new(0.937255, 0.937255, 0.937255)
TextBox.TextSize = 19

TextButton.Parent = Frame
TextButton.BackgroundColor3 = Color3.new(0.203922, 0.203922, 0.203922)
TextButton.Position = UDim2.new(0.0501454361, 0, 0.688206077, 0)
TextButton.Size = UDim2.new(0, 140, 0, 31)
TextButton.Font = Enum.Font.SciFi
TextButton.Text = "Kill Player"
TextButton.TextColor3 = Color3.new(0.678431, 0.678431, 0.678431)
TextButton.TextSize = 24

TextButton_2.Parent = Frame
TextButton_2.BackgroundColor3 = Color3.new(0.364706, 0.364706, 0.364706)
TextButton_2.Position = UDim2.new(0.847133756, 0, 0, 0)
TextButton_2.Size = UDim2.new(0, 24, 0, 24)
TextButton_2.Font = Enum.Font.SciFi
TextButton_2.Text = "X"
TextButton_2.TextColor3 = Color3.new(0, 0, 0)
TextButton_2.TextSize = 18
TextButton_2.MouseButton1Click:connect(function()
	Frame.Visible = false
end)

TextLabel.Parent = Frame
TextLabel.BackgroundColor3 = Color3.new(0.364706, 0.364706, 0.364706)
TextLabel.Size = UDim2.new(0, 133, 0, 24)
TextLabel.Font = Enum.Font.SourceSans
TextLabel.Text = "Dirt? :3 By: Sten"
TextLabel.TextColor3 = Color3.new(0, 0, 0)
TextLabel.TextSize = 18
-- Scripts:
local Players = game:GetService("Players")
local LocalPlayer = Players.LocalPlayer
local function RemoveSpaces(String)
	return String:gsub("%s+", "") or String
end
--Made By StenHisDirt :)
local function FindPlayer(String)
	String = RemoveSpaces(String)
	for _, _Player in pairs(Players:GetPlayers()) do
		if _Player.Name:lower():match('^'.. String:lower()) then
			return _Player
		end
	end
	return nil
end

TextButton.MouseButton1Click:Connect(function()
	local Target = FindPlayer(TextBox.Text)
	if Target and Target.Character then
		local Character = LocalPlayer.Character or LocalPlayer.CharacterAdded:Wait()
		local Torso = Character:FindFirstChild("Torso") or Character:FindFirstChild("UpperTorso")
		
		local savepos = LocalPlayer.Character:FindFirstChild("HumanoidRootPart").CFrame
	    Torso.Anchored = true
	    local tool = Instance.new("Tool", LocalPlayer.Backpack)
	    local hat = LocalPlayer.Character:FindFirstChildOfClass("Accessory")
	    local hathandle = hat.Handle
	    hathandle.Parent = tool
	    hathandle.Massless = true
	    tool.GripPos = Vector3.new(0, 9e99, 0)
	    tool.Parent = LocalPlayer.Character
	    repeat wait() until LocalPlayer.Character:FindFirstChildOfClass("Tool") ~= nil
	    tool.Grip = CFrame.new(Vector3.new(0, 0, 0))
		Torso.Anchored = false
	    repeat LocalPlayer.Character:FindFirstChild("HumanoidRootPart").CFrame = Target.Character:FindFirstChild("HumanoidRootPart").CFrame wait()
	    until Target.Character == nil or Target.Character:FindFirstChild("Humanoid").Health <= 0 or LocalPlayer.Character == nil or LocalPlayer.Character:FindFirstChild("Humanoid").Health <= 0 or (Target.Character:FindFirstChild("HumanoidRootPart").Velocity.magnitude - Target.Character:FindFirstChild("Humanoid").WalkSpeed) > (Target.Character:FindFirstChild("Humanoid").WalkSpeed + 20)
	    LocalPlayer.Character:FindFirstChild("Humanoid"):UnequipTools()
	    hathandle.Parent = hat
	    hathandle.Massless = false
	    tool:Destroy()
	    LocalPlayer.Character:FindFirstChild("HumanoidRootPart").CFrame = savepos
	else
		warn'no player found named like that or he has no char'
	end
end)
