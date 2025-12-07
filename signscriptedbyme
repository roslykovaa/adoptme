local Players = game:GetService("Players")
local player = Players.LocalPlayer
local playerGui = player:WaitForChild("PlayerGui")

-- Create ScreenGui
local screenGui = Instance.new("ScreenGui")
screenGui.Name = "DeltaGUI"
screenGui.ResetOnSpawn = false
screenGui.Parent = playerGui

-- Top Center Display Label
local topLabel = Instance.new("TextLabel")
topLabel.Name = "DisplayLabel"
topLabel.Size = UDim2.new(0.6, 0, 0.08, 0)
topLabel.Position = UDim2.new(0.2, 0, 0.02, 0)
topLabel.BackgroundColor3 = Color3.fromRGB(0, 0, 0)
topLabel.BackgroundTransparency = 0.3
topLabel.BorderSizePixel = 0
topLabel.Text = ""
topLabel.TextColor3 = Color3.fromRGB(255, 255, 255)
topLabel.TextScaled = true
topLabel.Font = Enum.Font.GothamBold
topLabel.Parent = screenGui

local topCorner = Instance.new("UICorner")
topCorner.CornerRadius = UDim.new(0, 12)
topCorner.Parent = topLabel

-- Right Side Main Frame
local mainFrame = Instance.new("Frame")
mainFrame.Name = "MainFrame"
mainFrame.Size = UDim2.new(0, 250, 0, 120)
mainFrame.Position = UDim2.new(1, -270, 0.5, -70)
mainFrame.BackgroundColor3 = Color3.fromRGB(35, 35, 45)
mainFrame.BorderSizePixel = 0
mainFrame.Parent = screenGui

local mainCorner = Instance.new("UICorner")
mainCorner.CornerRadius = UDim.new(0, 12)
mainCorner.Parent = mainFrame

-- Close X Button (top left of frame)
local xButton = Instance.new("TextButton")
xButton.Name = "CloseButton"
xButton.Size = UDim2.new(0, 32, 0, 32)
xButton.Position = UDim2.new(0, 8, 0, 8)
xButton.BackgroundColor3 = Color3.fromRGB(220, 50, 50)
xButton.BorderSizePixel = 0
xButton.Text = "✕"
xButton.TextColor3 = Color3.fromRGB(255, 255, 255)
xButton.TextScaled = true
xButton.Font = Enum.Font.GothamBold
xButton.Parent = mainFrame

local xCorner = Instance.new("UICorner")
xCorner.CornerRadius = UDim.new(0, 8)
xCorner.Parent = xButton

-- Input TextBox (middle of frame)
local textBox = Instance.new("TextBox")
textBox.Name = "InputBox"
textBox.Size = UDim2.new(0.88, 0, 0.65, 0)
textBox.Position = UDim2.new(0.06, 0, 0.25, 0)
textBox.BackgroundColor3 = Color3.fromRGB(50, 50, 60)
textBox.BorderSizePixel = 0
textBox.Text = ""
textBox.TextColor3 = Color3.fromRGB(255, 255, 255)
textBox.PlaceholderText = "Type here..."
textBox.PlaceholderColor3 = Color3.fromRGB(150, 150, 150)
textBox.TextScaled = true
textBox.Font = Enum.Font.Gotham
textBox.ClearTextOnFocus = false
textBox.MultiLine = false
textBox.TextXAlignment = Enum.TextXAlignment.Left
textBox.TextYAlignment = Enum.TextYAlignment.Center
textBox.Parent = mainFrame

local tbCorner = Instance.new("UICorner")
tbCorner.CornerRadius = UDim.new(0, 8)
tbCorner.Parent = textBox

-- Update display label live as you type
local function updateDisplay()
    topLabel.Text = textBox.Text
    topLabel.TextTransparency = textBox.Text ~= "" and 0 or 1
end

textBox:GetPropertyChangedSignal("Text"):Connect(updateDisplay)

-- Close button functionality
xButton.MouseButton1Click:Connect(function()
    screenGui:Destroy()
end)

-- Optional: Make main frame draggable
local dragging = false
local dragStart = nil
local startPos = nil

mainFrame.InputBegan:Connect(function(input)
    if input.UserInputType == Enum.UserInputType.MouseButton1 then
        dragging = true
        dragStart = input.Position
        startPos = mainFrame.Position
    end
end)

mainFrame.InputChanged:Connect(function(input)
    if dragging and input.UserInputType == Enum.UserInputType.MouseMovement then
        local delta = input.Position - dragStart
        mainFrame.Position = UDim2.new(startPos.X.Scale, startPos.X.Offset + delta.X, startPos.Y.Scale, startPos.Y.Offset + delta.Y)
    end
end)

mainFrame.InputEnded:Connect(function(input)
    if input.UserInputType == Enum.UserInputType.MouseButton1 then
        dragging = false
    end
end)
