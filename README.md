# Script
local CoreGui = game:GetService("CoreGui")
local ScreenGui = Instance.new("ScreenGui")
ScreenGui.Name = "G_Logo_UI"
ScreenGui.ResetOnSpawn = false
ScreenGui.Parent = CoreGui

local LogoButton = Instance.new("TextButton")
LogoButton.Name = "GLogo"
LogoButton.Size = UDim2.new(0, 60, 0, 60)
LogoButton.Position = UDim2.new(0, 20, 0, 200)
LogoButton.BackgroundColor3 = Color3.fromRGB(25, 25, 25)
LogoButton.BorderSizePixel = 0
LogoButton.Text = "G"
LogoButton.Font = Enum.Font.GothamBold
LogoButton.TextSize = 32
LogoButton.TextColor3 = Color3.fromRGB(0, 255, 0)
LogoButton.AutoButtonColor = true
LogoButton.ZIndex = 2
LogoButton.Parent = ScreenGui

local UICornerLogo = Instance.new("UICorner")
UICornerLogo.CornerRadius = UDim.new(0, 
UICornerLogo.Parent = LogoButton


local FuncFrame = Instance.new("Frame")
FuncFrame.Name = "G_FunctionMenu"
FuncFrame.Size = UDim2.new(0, 220, 0, 260)
FuncFrame.Position = UDim2.new(0, 90, 0, 170)
FuncFrame.BackgroundColor3 = Color3.fromRGB(15, 15, 15)
FuncFrame.BorderSizePixel = 0
FuncFrame.Visible = false
FuncFrame.ZIndex = 1
FuncFrame.Parent = ScreenGui

local UICornerFrame = Instance.new("UICorner")
UICornerFrame.CornerRadius = UDim.new(0, 10)
UICornerFrame.Parent = FuncFrame

local UIStrokeFrame = Instance.new("UIStroke")
UIStrokeFrame.Thickness = 1.5
UIStrokeFrame.Color = Color3.fromRGB(0, 255, 0)
UIStrokeFrame.Parent = FuncFrame


local Title = Instance.new("TextLabel")
Title.Size = UDim2.new(1, -10, 0, 30)
Title.Position = UDim2.new(0, 5, 0, 5)
Title.BackgroundTransparency = 1
Title.Text = "G Functions"
Title.Font = Enum.Font.GothamBold
Title.TextSize = 18
Title.TextColor3 = Color3.fromRGB(0, 255, 0)
Title.TextXAlignment = Enum.TextXAlignment.Left
Title.Parent = FuncFrame


local ButtonsHolder = Instance.new("Frame")
ButtonsHolder.Size = UDim2.new(1, -10, 1, -40)
ButtonsHolder.Position = UDim2.new(0, 5, 0, 35)
ButtonsHolder.BackgroundTransparency = 1
ButtonsHolder.Parent = FuncFrame

local UIList2 = Instance.new("UIListLayout")
UIList2.Padding = UDim.new(0, 4)
UIList2.FillDirection = Enum.FillDirection.Vertical
UIList2.HorizontalAlignment = Enum.HorizontalAlignment.Center
UIList2.SortOrder = Enum.SortOrder.LayoutOrder
UIList2.Parent = ButtonsHolder


local function CreateFuncButton(text, callback)
    local btn = Instance.new("TextButton")
    btn.Size = UDim2.new(1, 0, 0, 26)
    btn.BackgroundColor3 = Color3.fromRGB(30, 30, 30)
    btn.BorderSizePixel = 0
    btn.Text = text
    btn.Font = Enum.Font.Gotham
    btn.TextSize = 14
    btn.TextColor3 = Color3.fromRGB(220, 220, 220)
    btn.AutoButtonColor = true
    btn.Parent = ButtonsHolder

    local corner = Instance.new("UICorner")
    corner.CornerRadius = UDim.new(0, 6)
    corner.Parent = btn

    btn.MouseButton1Click:Connect(function()
        pcall(callback)
    end)
end


LogoButton.MouseButton1Click:Connect(function()
    FuncFrame.Visible = not FuncFrame.Visible
end)


-- script içinde _G.Auto_Farm_Level, _G.Auto_AllBoss, _G.Auto_SwanGG vb. zaten var

CreateFuncButton("Toggle Auto Farm", function()
    _G.Auto_Farm_Level = not _G.Auto_Farm_Level
end)

CreateFuncButton("Toggle All Boss", function()
    _G.Auto_AllBoss = not _G.Auto_AllBoss
end)

CreateFuncButton("Toggle Ken Haki", function()
    _G.Auto_Ken = not _G.Auto_Ken
end)

CreateFuncButton("Toggle Swan Glasses", function()
    _G.Auto_SwanGG = not _G.Auto_SwanGG
end)
