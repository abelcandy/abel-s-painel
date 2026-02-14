-- ============================================
-- ROBLOX EXPLOIT PANEL - Created by Abel
-- Compatible with: Delta, Xeno, and more
-- Keybind: B
-- ============================================

local UserInputService = game:GetService("UserInputService")
local Players = game:GetService("Players")
local RunService = game:GetService("RunService")
local Camera = workspace.CurrentCamera

local Player = Players.LocalPlayer
local Mouse = Player:GetMouse()

-- ============================================
-- CONFIGURAÇÕES DO PAINEL
-- ============================================

local Config = {
    PanelOpen = false,
    KeyBind = Enum.KeyCode.B,
    ESPEnabled = false,
    AimbotEnabled = false,
    SilentAimbotEnabled = false,
    AimbotFOV = 100,
    BoxESP = false,
    NameESP = false,
    HealthESP = true
}

-- ============================================
-- CRIAÇÃO DO GUI
-- ============================================

local function createUI()
    local ScreenGui = Instance.new("ScreenGui")
    ScreenGui.Name = "AbelPanelGui"
    ScreenGui.ResetOnSpawn = false
    ScreenGui.DisplayOrder = 999
    
    if game:GetService("CoreGui"):FindFirstChild("AbelPanelGui") then
        game:GetService("CoreGui"):FindFirstChild("AbelPanelGui"):Destroy()
    end
    
    ScreenGui.Parent = game:GetService("CoreGui")
    
    -- MAIN PANEL
    local MainPanel = Instance.new("Frame")
    MainPanel.Name = "MainPanel"
    MainPanel.Size = UDim2.new(0, 450, 0, 500)
    MainPanel.Position = UDim2.new(0.5, -225, 0.5, -250)
    MainPanel.BackgroundColor3 = Color3.fromRGB(30, 30, 35)
    MainPanel.BorderSizePixel = 0
    MainPanel.Visible = false
    MainPanel.Parent = ScreenGui
    
    -- Corner Radius
    local corner = Instance.new("UICorner")
    corner.CornerRadius = UDim.new(0, 10)
    corner.Parent = MainPanel
    
    -- TITLE BAR
    local TitleBar = Instance.new("Frame")
    TitleBar.Name = "TitleBar"
    TitleBar.Size = UDim2.new(1, 0, 0, 40)
    TitleBar.BackgroundColor3 = Color3.fromRGB(20, 20, 25)
    TitleBar.BorderSizePixel = 0
    TitleBar.Parent = MainPanel
    
    local titleCorner = Instance.new("UICorner")
    titleCorner.CornerRadius = UDim.new(0, 10)
    titleCorner.Parent = TitleBar
    
    local TitleText = Instance.new("TextLabel")
    TitleText.Name = "TitleText"
    TitleText.Size = UDim2.new(1, -10, 1, 0)
    TitleText.Position = UDim2.new(0, 5, 0, 0)
    TitleText.BackgroundTransparency = 1
    TitleText.Text = "ABEL PANEL | Key: B"
    TitleText.TextColor3 = Color3.fromRGB(255, 100, 150)
    TitleText.TextSize = 16
    TitleText.Font = Enum.Font.GothamBold
    TitleText.TextXAlignment = Enum.TextXAlignment.Left
    TitleText.Parent = TitleBar
    
    -- Close Button
    local CloseButton = Instance.new("TextButton")
    CloseButton.Name = "CloseButton"
    CloseButton.Size = UDim2.new(0, 30, 0, 30)
    CloseButton.Position = UDim2.new(1, -35, 0, 5)
    CloseButton.BackgroundColor3 = Color3.fromRGB(255, 50, 50)
    CloseButton.Text = "X"
    CloseButton.TextColor3 = Color3.fromRGB(255, 255, 255)
    CloseButton.TextSize = 14
    CloseButton.Font = Enum.Font.GothamBold
    CloseButton.BorderSizePixel = 0
    CloseButton.Parent = TitleBar
    
    local closeCorner = Instance.new("UICorner")
    closeCorner.CornerRadius = UDim.new(0, 5)
    closeCorner.Parent = CloseButton
    
    CloseButton.MouseButton1Click:Connect(function()
        Config.PanelOpen = false
        MainPanel.Visible = false
    end)
    
    -- TABS CONTAINER
    local TabsContainer = Instance.new("Frame")
    TabsContainer.Name = "TabsContainer"
    TabsContainer.Size = UDim2.new(1, 0, 0, 50)
    TabsContainer.Position = UDim2.new(0, 0, 0, 40)
    TabsContainer.BackgroundColor3 = Color3.fromRGB(40, 40, 45)
    TabsContainer.BorderSizePixel = 0
    TabsContainer.Parent = MainPanel
    
    local listLayout = Instance.new("UIListLayout")
    listLayout.FillDirection = Enum.FillDirection.Horizontal
    listLayout.HorizontalAlignment = Enum.HorizontalAlignment.Left
    listLayout.VerticalAlignment = Enum.VerticalAlignment.Center
    listLayout.Padding = UDim.new(0, 2)
    listLayout.Parent = TabsContainer
    
    -- CONTENT AREA
    local ContentArea = Instance.new("Frame")
    ContentArea.Name = "ContentArea"
    ContentArea.Size = UDim2.new(1, 0, 1, -90)
    ContentArea.Position = UDim2.new(0, 0, 0, 90)
    ContentArea.BackgroundColor3 = Color3.fromRGB(35, 35, 40)
    ContentArea.BorderSizePixel = 0
    ContentArea.Parent = MainPanel
    
    -- Scroll Frame para conteúdo
    local ScrollFrame = Instance.new("ScrollingFrame")
    ScrollFrame.Name = "ScrollFrame"
    ScrollFrame.Size = UDim2.new(1, -20, 1, 0)
    ScrollFrame.Position = UDim2.new(0, 10, 0, 0)
    ScrollFrame.BackgroundTransparency = 1
    ScrollFrame.BorderSizePixel = 0
    ScrollFrame.ScrollBarThickness = 8
    ScrollFrame.ScrollBarImageColor3 = Color3.fromRGB(100, 100, 110)
    ScrollFrame.Parent = ContentArea
    
    local scrollLayout = Instance.new("UIListLayout")
    scrollLayout.FillDirection = Enum.FillDirection.Vertical
    scrollLayout.HorizontalAlignment = Enum.HorizontalAlignment.Left
    scrollLayout.VerticalAlignment = Enum.VerticalAlignment.Top
    scrollLayout.Padding = UDim.new(0, 10)
    scrollLayout.Parent = ScrollFrame
    
    local scrollPadding = Instance.new("UIPadding")
    scrollPadding.PaddingTop = UDim.new(0, 10)
    scrollPadding.PaddingBottom = UDim.new(0, 10)
    scrollPadding.PaddingLeft = UDim.new(0, 0)
    scrollPadding.PaddingRight = UDim.new(0, 0)
    scrollPadding.Parent = ScrollFrame
    
    -- ============================================
    -- FUNÇÕES DE CRIAÇÃO DE ELEMENTOS UI
    -- ============================================
    
    local function createTab(tabName)
        local tab = Instance.new("TextButton")
        tab.Name = tabName .. "Tab"
        tab.Size = UDim2.new(0, 100, 1, 0)
        tab.BackgroundColor3 = Color3.fromRGB(50, 50, 60)
        tab.Text = tabName
        tab.TextColor3 = Color3.fromRGB(255, 255, 255)
        tab.TextSize = 12
        tab.Font = Enum.Font.Gotham
        tab.BorderSizePixel = 0
        tab.Parent = TabsContainer
        
        local tabCorner = Instance.new("UICorner")
        tabCorner.CornerRadius = UDim.new(0, 5)
        tabCorner.Parent = tab
        
        return tab
    end
    
    local function createToggle(parent, name, callback)
        local toggleContainer = Instance.new("Frame")
        toggleContainer.Name = name .. "Container"
        toggleContainer.Size = UDim2.new(1, 0, 0, 40)
        toggleContainer.BackgroundColor3 = Color3.fromRGB(45, 45, 50)
        toggleContainer.BorderSizePixel = 0
        toggleContainer.Parent = parent
        
        local toggleCorner = Instance.new("UICorner")
        toggleCorner.CornerRadius = UDim.new(0, 5)
        toggleCorner.Parent = toggleContainer
        
        local label = Instance.new("TextLabel")
        label.Name = "Label"
        label.Size = UDim2.new(1, -50, 1, 0)
        label.Position = UDim2.new(0, 10, 0, 0)
        label.BackgroundTransparency = 1
        label.Text = name
        label.TextColor3 = Color3.fromRGB(255, 255, 255)
        label.TextSize = 12
        label.Font = Enum.Font.Gotham
        label.TextXAlignment = Enum.TextXAlignment.Left
        label.Parent = toggleContainer
        
        local toggleButton = Instance.new("TextButton")
        toggleButton.Name = "ToggleButton"
        toggleButton.Size = UDim2.new(0, 40, 0, 25)
        toggleButton.Position = UDim2.new(1, -45, 0.5, -12)
        toggleButton.BackgroundColor3 = Color3.fromRGB(100, 100, 110)
        toggleButton.Text = "OFF"
        toggleButton.TextColor3 = Color3.fromRGB(255, 255, 255)
        toggleButton.TextSize = 10
        toggleButton.Font = Enum.Font.GothamBold
        toggleButton.BorderSizePixel = 0
        toggleButton.Parent = toggleContainer
        
        local toggleCorner2 = Instance.new("UICorner")
        toggleCorner2.CornerRadius = UDim.new(0, 3)
        toggleCorner2.Parent = toggleButton
        
        local toggleState = false
        
        toggleButton.MouseButton1Click:Connect(function()
            toggleState = not toggleState
            toggleButton.BackgroundColor3 = toggleState and Color3.fromRGB(100, 200, 100) or Color3.fromRGB(100, 100, 110)
            toggleButton.Text = toggleState and "ON" or "OFF"
            if callback then
                callback(toggleState)
            end
        end)
        
        return toggleButton, toggleState
    end
    
    local function createSlider(parent, name, min, max, default, callback)
        local sliderContainer = Instance.new("Frame")
        sliderContainer.Name = name .. "Container"
        sliderContainer.Size = UDim2.new(1, 0, 0, 60)
        sliderContainer.BackgroundColor3 = Color3.fromRGB(45, 45, 50)
        sliderContainer.BorderSizePixel = 0
        sliderContainer.Parent = parent
        
        local sliderCorner = Instance.new("UICorner")
        sliderCorner.CornerRadius = UDim.new(0, 5)
        sliderCorner.Parent = sliderContainer
        
        local label = Instance.new("TextLabel")
        label.Name = "Label"
        label.Size = UDim2.new(1, -20, 0, 20)
        label.Position = UDim2.new(0, 10, 0, 5)
        label.BackgroundTransparency = 1
        label.Text = name .. ": " .. default
        label.TextColor3 = Color3.fromRGB(255, 255, 255)
        label.TextSize = 12
        label.Font = Enum.Font.Gotham
        label.TextXAlignment = Enum.TextXAlignment.Left
        label.Parent = sliderContainer
        
        local sliderBg = Instance.new("Frame")
        sliderBg.Name = "SliderBg"
        sliderBg.Size = UDim2.new(1, -20, 0, 8)
        sliderBg.Position = UDim2.new(0, 10, 0, 30)
        sliderBg.BackgroundColor3 = Color3.fromRGB(60, 60, 70)
        sliderBg.BorderSizePixel = 0
        sliderBg.Parent = sliderContainer
        
        local sliderBgCorner = Instance.new("UICorner")
        sliderBgCorner.CornerRadius = UDim.new(0, 4)
        sliderBgCorner.Parent = sliderBg
        
        local sliderButton = Instance.new("TextButton")
        sliderButton.Name = "SliderButton"
        sliderButton.Size = UDim2.new(0, 15, 0, 20)
        sliderButton.Position = UDim2.new(0, 0, 0.5, -10)
        sliderButton.BackgroundColor3 = Color3.fromRGB(255, 100, 150)
        sliderButton.Text = ""
        sliderButton.BorderSizePixel = 0
        sliderButton.Parent = sliderBg
        
        local sliderButtonCorner = Instance.new("UICorner")
        sliderButtonCorner.CornerRadius = UDim.new(0, 3)
        sliderButtonCorner.Parent = sliderButton
        
        local currentValue = default
        local dragging = false
        
        local function updateSlider(input)
            local sliderSize = sliderBg.AbsoluteSize.X
            local mouseX = input.Position.X - sliderBg.AbsolutePosition.X
            local percentage = math.clamp(mouseX / sliderSize, 0, 1)
            currentValue = math.floor(min + (max - min) * percentage)
            
            sliderButton.Position = UDim2.new(percentage, -7.5, 0.5, -10)
            label.Text = name .. ": " .. currentValue
            
            if callback then
                callback(currentValue)
            end
        end
        
        sliderButton.MouseButton1Down:Connect(function()
            dragging = true
        end)
        
        UserInputService.InputEnded:Connect(function(input)
            if input.UserInputType == Enum.UserInputType.MouseButton1 then
                dragging = false
            end
        end)
        
        UserInputService.InputChanged:Connect(function(input)
            if dragging and input.UserInputType == Enum.UserInputType.MouseMovement then
                updateSlider(input)
            end
        end)
        
        return sliderButton, currentValue
    end
    
    local function createTextLabel(parent, text, textColor)
        local label = Instance.new("TextLabel")
        label.Size = UDim2.new(1, 0, 0, 30)
        label.BackgroundColor3 = Color3.fromRGB(45, 45, 50)
        label.Text = text
        label.TextColor3 = textColor or Color3.fromRGB(200, 200, 200)
        label.TextSize = 11
        label.Font = Enum.Font.Gotham
        label.TextWrapped = true
        label.BorderSizePixel = 0
        label.Parent = parent
        
        local labelCorner = Instance.new("UICorner")
        labelCorner.CornerRadius = UDim.new(0, 5)
        labelCorner.Parent = label
        
        return label
    end
    
    -- ============================================
    -- HOME TAB
    -- ============================================
    
    local homeContent = Instance.new("Frame")
    homeContent.Name = "HomeContent"
    homeContent.Size = UDim2.new(1, 0, 1, 0)
    homeContent.BackgroundTransparency = 1
    homeContent.Parent = ScrollFrame
    
    local homeLayout = Instance.new("UIListLayout")
    homeLayout.FillDirection = Enum.FillDirection.Vertical
    homeLayout.HorizontalAlignment = Enum.HorizontalAlignment.Left
    homeLayout.VerticalAlignment = Enum.VerticalAlignment.Top
    homeLayout.Padding = UDim.new(0, 10)
    homeLayout.Parent = homeContent
    
    local homePadding = Instance.new("UIPadding")
    homePadding.PaddingTop = UDim.new(0, 10)
    homePadding.PaddingBottom = UDim.new(0, 10)
    homePadding.PaddingLeft = UDim.new(0, 0)
    homePadding.PaddingRight = UDim.new(0, 0)
    homePadding.Parent = homeContent
    
    createTextLabel(homeContent, "Welcome to ABEL PANEL", Color3.fromRGB(255, 100, 150))
    createTextLabel(homeContent, "Created by: abel", Color3.fromRGB(255, 200, 100))
    createTextLabel(homeContent, "Version: 1.0", Color3.fromRGB(150, 150, 200))
    createTextLabel(homeContent, "Keybind: B", Color3.fromRGB(200, 100, 255))
    
    -- ============================================
    -- GAME TAB
    -- ============================================
    
    local gameContent = Instance.new("Frame")
    gameContent.Name = "GameContent"
    gameContent.Size = UDim2.new(1, 0, 1, 0)
    gameContent.BackgroundTransparency = 1
    gameContent.Visible = false
    gameContent.Parent = ScrollFrame
    
    local gameLayout = Instance.new("UIListLayout")
    gameLayout.FillDirection = Enum.FillDirection.Vertical
    gameLayout.HorizontalAlignment = Enum.HorizontalAlignment.Left
    gameLayout.VerticalAlignment = Enum.VerticalAlignment.Top
    gameLayout.Padding = UDim.new(0, 10)
    gameLayout.Parent = gameContent
    
    local gamePadding = Instance.new("UIPadding")
    gamePadding.PaddingTop = UDim.new(0, 10)
    gamePadding.PaddingBottom = UDim.new(0, 10)
    gamePadding.PaddingLeft = UDim.new(0, 0)
    gamePadding.PaddingRight = UDim.new(0, 0)
    gamePadding.Parent = gameContent
    
    -- ESP Toggle
    local espToggle, _ = createToggle(gameContent, "ESP", function(state)
        Config.ESPEnabled = state
    end)
    
    -- Silent Aimbot + Aimbot Toggle
    local aimbotToggle, _ = createToggle(gameContent, "Silent Aimbot + Aimbot", function(state)
        Config.AimbotEnabled = state
        Config.SilentAimbotEnabled = state
    end)
    
    -- FOV Slider
    local fovSlider, _ = createSlider(gameContent, "Aimbot FOV", 10, 500, 100, function(value)
        Config.AimbotFOV = value
    end)
    
    -- ============================================
    -- TAB SWITCHING
    -- ============================================
    
    local homeTab = createTab("Home")
    local gameTab = createTab("Game")
    
    homeTab.MouseButton1Click:Connect(function()
        homeContent.Visible = true
        gameContent.Visible = false
        homeTab.BackgroundColor3 = Color3.fromRGB(100, 150, 255)
        gameTab.BackgroundColor3 = Color3.fromRGB(50, 50, 60)
    end)
    
    gameTab.MouseButton1Click:Connect(function()
        gameContent.Visible = false
        homeContent.Visible = true
        gameContent.Visible = true
        homeTab.BackgroundColor3 = Color3.fromRGB(50, 50, 60)
        gameTab.BackgroundColor3 = Color3.fromRGB(100, 150, 255)
    end)
    
    -- Set Home as default
    homeTab.BackgroundColor3 = Color3.fromRGB(100, 150, 255)
    
    return MainPanel
end

-- ============================================
-- SISTEMA DE ESP
-- ============================================

local espInstances = {}

local function removeESP()
    for _, instance in ipairs(espInstances) do
        if instance and instance.Parent then
            instance:Destroy()
        end
    end
    espInstances = {}
end

local function createESP(character)
    if not Config.ESPEnabled or not character:FindFirstChild("HumanoidRootPart") then
        return
    end
    
    local humanoidRootPart = character.HumanoidRootPart
    local humanoid = character:FindFirstChild("Humanoid")
    
    -- Box ESP
    local boxGui = Instance.new("BillboardGui")
    boxGui.Size = UDim2.new(4, 0, 5, 0)
    boxGui.MaxDistance = 500
    boxGui.Parent = humanoidRootPart
    
    local boxFrame = Instance.new("Frame")
    boxFrame.Size = UDim2.new(1, 0, 1, 0)
    boxFrame.BackgroundTransparency = 0.7
    boxFrame.BackgroundColor3 = Color3.fromRGB(255, 0, 0)
    boxFrame.BorderColor3 = Color3.fromRGB(255, 100, 100)
    boxFrame.BorderSizePixel = 2
    boxFrame.Parent = boxGui
    
    table.insert(espInstances, boxGui)
    
    -- Name ESP
    local nameGui = Instance.new("BillboardGui")
    nameGui.Size = UDim2.new(4, 0, 1, 0)
    nameGui.MaxDistance = 500
    nameGui.Parent = humanoidRootPart
    
    local nameLabel = Instance.new("TextLabel")
    nameLabel.Size = UDim2.new(1, 0, 1, 0)
    nameLabel.BackgroundTransparency = 1
    nameLabel.Text = character.Name
    nameLabel.TextColor3 = Color3.fromRGB(255, 255, 0)
    nameLabel.TextSize = 14
    nameLabel.Font = Enum.Font.GothamBold
    nameLabel.Parent = nameGui
    
    table.insert(espInstances, nameGui)
end

-- ============================================
-- SISTEMA DE AIMBOT
-- ============================================

local function getClosestPlayer()
    local closestPlayer = nil
    local closestDistance = Config.AimbotFOV
    
    for _, player in ipairs(Players:GetPlayers()) do
        if player ~= Player and player.Character and player.Character:FindFirstChild("HumanoidRootPart") then
            local targetPos = player.Character.HumanoidRootPart.Position
            local screenPos = Camera:WorldToScreenPoint(targetPos)
            local mousePos = Mouse.X - screenPos.X
            local mousePos2 = Mouse.Y - screenPos.Y
            local distance = math.sqrt(mousePos^2 + mousePos2^2)
            
            if distance < closestDistance then
                closestDistance = distance
                closestPlayer = player
            end
        end
    end
    
    return closestPlayer
end

local function aimAtPlayer(targetPlayer)
    if not targetPlayer or not targetPlayer.Character or not targetPlayer.Character:FindFirstChild("HumanoidRootPart") then
        return
    end
    
    local targetPos = targetPlayer.Character.HumanoidRootPart.Position
    Camera.CFrame = CFrame.new(Camera.CFrame.Position, targetPos)
end

-- ============================================
-- KEYBIND LISTENER
-- ============================================

local MainPanel = createUI()

UserInputService.InputBegan:Connect(function(input, gameProcessed)
    if gameProcessed then return end
    
    if input.KeyCode == Config.KeyBind then
        Config.PanelOpen = not Config.PanelOpen
        MainPanel.Visible = Config.PanelOpen
    end
end)

-- ============================================
-- UPDATE LOOP
-- ============================================

RunService.RenderStepped:Connect(function()
    -- ESP Updates
    if Config.ESPEnabled then
        for _, player in ipairs(Players:GetPlayers()) do
            if player ~= Player and player.Character then
                local found = false
                for _, esp in ipairs(espInstances) do
                    if esp and esp.Parent == player.Character:FindFirstChild("HumanoidRootPart") then
                        found = true
                        break
                    end
                end
                if not found then
                    createESP(player.Character)
                end
            end
        end
    else
        removeESP()
    end
    
    -- Aimbot Updates
    if Config.AimbotEnabled then
        local target = getClosestPlayer()
        if target then
            aimAtPlayer(target)
        end
    end
end)

-- Handle new players
Players.PlayerAdded:Connect(function(player)
    player.CharacterAdded:Connect(function(character)
        if Config.ESPEnabled then
            wait(0.1)
            createESP(character)
        end
    end)
end)

print("Abel Panel Loaded! Press B to toggle | Compatible with Delta, Xeno, etc.")
