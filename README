-- FLY GUI MOBILE 📱🪽
-- Para Delta Executor

local player = game.Players.LocalPlayer
local char = player.Character or player.CharacterAdded:Wait()
local hrp = char:WaitForChild("HumanoidRootPart")
local humanoid = char:WaitForChild("Humanoid")

local flying = false
local speed = 60

local bv
local bg

-- GUI
local gui = Instance.new("ScreenGui")
gui.Parent = game.CoreGui

local frame = Instance.new("Frame")
frame.Parent = gui
frame.Size = UDim2.new(0,200,0,120)
frame.Position = UDim2.new(0.05,0,0.4,0)
frame.BackgroundTransparency = 0.2
frame.Active = true
frame.Draggable = true

local flyButton = Instance.new("TextButton")
flyButton.Parent = frame
flyButton.Size = UDim2.new(0,180,0,40)
flyButton.Position = UDim2.new(0,10,0,10)
flyButton.Text = "FLY: OFF"

local speedBox = Instance.new("TextBox")
speedBox.Parent = frame
speedBox.Size = UDim2.new(0,180,0,40)
speedBox.Position = UDim2.new(0,10,0,60)
speedBox.Text = tostring(speed)
speedBox.PlaceholderText = "Velocidad"

speedBox.FocusLost:Connect(function()
	local num = tonumber(speedBox.Text)
	if num then
		speed = num
	end
end)

local function startFly()
	flying = true

	bv = Instance.new("BodyVelocity")
	bv.MaxForce = Vector3.new(9e9,9e9,9e9)
	bv.Parent = hrp

	bg = Instance.new("BodyGyro")
	bg.MaxTorque = Vector3.new(9e9,9e9,9e9)
	bg.CFrame = hrp.CFrame
	bg.Parent = hrp

	game:GetService("RunService").RenderStepped:Connect(function()
		if flying then
			local cam = workspace.CurrentCamera
			bg.CFrame = cam.CFrame
			bv.Velocity = humanoid.MoveDirection * speed
		end
	end)
end

local function stopFly()
	flying = false

	if bv then bv:Destroy() end
	if bg then bg:Destroy() end
end

flyButton.MouseButton1Click:Connect(function()
	if flying then
		stopFly()
		flyButton.Text = "FLY: OFF"
	else
		startFly()
		flyButton.Text = "FLY: ON"
	end
end)
