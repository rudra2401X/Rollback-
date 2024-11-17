local Library = {}

function Library:CreateWindow(title)
    local ScreenGui = Instance.new("ScreenGui")
    local Frame = Instance.new("Frame")
    local Title = Instance.new("TextLabel")
    local MinimizeButton = Instance.new("TextButton")

    ScreenGui.Parent = game.CoreGui
    Frame.Parent = ScreenGui
    Frame.BackgroundColor3 = Color3.new(0.2, 0.2, 0.2)
    Frame.Size = UDim2.new(0, 400, 0, 300)
    Frame.Position = UDim2.new(0.5, -200, 0.5, -150)
    Frame.Active = true
    Frame.Draggable = true

    Title.Parent = Frame
    Title.Text = title
    Title.Size = UDim2.new(1, 0, 0, 50)
    Title.BackgroundColor3 = Color3.new(0.1, 0.1, 0.1)
    Title.TextColor3 = Color3.new(1, 1, 1)
    Title.Font = Enum.Font.SourceSans
    Title.TextSize = 24

    MinimizeButton.Parent = Frame
    MinimizeButton.Text = "-"
    MinimizeButton.Size = UDim2.new(0, 50, 0, 50)
    MinimizeButton.Position = UDim2.new(1, -50, 0, 0)
    MinimizeButton.BackgroundColor3 = Color3.new(0.1, 0.1, 0.1)
    MinimizeButton.TextColor3 = Color3.new(1, 1, 1)
    MinimizeButton.Font = Enum.Font.SourceSans
    MinimizeButton.TextSize = 24
    MinimizeButton.MouseButton1Click:Connect(function()
        Frame.Visible = not Frame.Visible
    end)

    return Frame
end

function Library:CreateCheckbox(parent, text, callback)
    local Checkbox = Instance.new("TextButton")
    Checkbox.Parent = parent
    Checkbox.Text = text
    Checkbox.Size = UDim2.new(0, 150, 0, 30)
    Checkbox.BackgroundColor3 = Color3.new(0.3, 0.3, 0.3)
    Checkbox.TextColor3 = Color3.new(1, 1, 1)
    Checkbox.Font = Enum.Font.SourceSans
    Checkbox.TextSize = 18
    Checkbox.MouseButton1Click:Connect(function()
        callback()
    end)
    return Checkbox
end

function Library:CreateDropdown(parent, text, options, callback)
    local Dropdown = Instance.new("TextButton")
    Dropdown.Parent = parent
    Dropdown.Text = text
    Dropdown.Size = UDim2.new(0, 150, 0, 30)
    Dropdown.BackgroundColor3 = Color3.new(0.3, 0.3, 0.3)
    Dropdown.TextColor3 = Color3.new(1, 1, 1)
    Dropdown.Font = Enum.Font.SourceSans
    Dropdown.TextSize = 18
    Dropdown.MouseButton1Click:Connect(function()
        local currentIndex = table.find(options, Dropdown.Text) or 1
        local nextIndex = (currentIndex % #options) + 1
        Dropdown.Text = options[nextIndex]
        callback(options[nextIndex])
    end)
    return Dropdown
end

function Library:CreateToggle(parent, text, callback)
    local Toggle = Instance.new("TextButton")
    Toggle.Parent = parent
    Toggle.Text = text
    Toggle.Size = UDim2.new(0, 150, 0, 30)
    Toggle.BackgroundColor3 = Color3.new(1, 0, 0)  -- Inicialmente vermelho
    Toggle.TextColor3 = Color3.new(1, 1, 1)
    Toggle.Font = Enum.Font.SourceSans
    Toggle.TextSize = 18
    Toggle.MouseButton1Click:Connect(function()
        local isActive = Toggle.BackgroundColor3 == Color3.new(0, 1, 0)
        Toggle.BackgroundColor3 = isActive and Color3.new(1, 0, 0) or Color3.new(0, 1, 0)  -- Alterna entre verde e vermelho
        callback(not isActive)
    end)
    return Toggle
end

-- Script para Anime Vanguards no Roblox
local Rollback = {
    Enable = false,
    Method = "Trait", -- Opções: "Trait", "Gem"
}

-- Função para realizar o rollback
local function performRollback(method)
    if method == "Trait" then
        -- Código para girar passiva e dar rollback
        print("Realizando rollback para Trait...")
        -- Adicione aqui o código específico para rollback de Trait
    elseif method == "Gem" then
        -- Código para dar rollback ao girar no banner
        print("Realizando rollback para Gem...")
        -- Adicione aqui o código específico para rollback de Gem
    end
end

-- Função para reentrar no servidor
local function rejoinServer()
    print("Reentrando no servidor para realizar rollback...")
    game:GetService("TeleportService"):Teleport(game.PlaceId, game.Players.LocalPlayer)
end

-- Função para congelar/descongelar os dados do jogador
local function freezePlayerData(freeze)
    if freeze then
        -- Código para congelar os dados do jogador
        print("Dados do jogador congelados.")
    else
        -- Código para descongelar os dados do jogador
        print("Dados do jogador descongelados.")
    end
end

-- Toggle para ativar/desativar o rollback
local function toggleRollback(enable)
    Rollback.Enable = enable
    freezePlayerData(enable)
    if enable then
        performRollback(Rollback.Method)
    end
end

-- Exemplo de uso da UI Library
local RollbackUI = Library:CreateWindow("Rollback")

local EnableToggle = Library:CreateToggle(RollbackUI, "Enable Rollback", function(isActive)
    Rollback.Enable = isActive
    freezePlayerData(isActive)
    if isActive then
        print("Rollback ativado. Dados do jogador não serão salvos.")
    else
        print("Rollback desativado. Dados do jogador serão salvos.")
    end
end)
EnableToggle.Position = UDim2.new(0, 50, 0, 60)

local MethodDropdown = Library:CreateDropdown(RollbackUI, "Method: Trait", {"Trait", "Gem"}, function(selected)
    Rollback.Method = selected
end)
MethodDropdown.Position = UDim2.new(0, 50, 0, 120)

-- Adicionando a opção "Rejoin Server"
local RejoinButton = Instance.new("TextButton")
RejoinButton.Parent = RollbackUI
RejoinButton.Text = "Rejoin Server"
RejoinButton.Size = UDim2.new(0, 150, 0, 30)
RejoinButton.Position = UDim2.new(0, 50, 0, 180)
RejoinButton.BackgroundColor3 = Color3.new(0.3, 0.3, 0.3)
RejoinButton.TextColor3 = Color3.new(1, 1, 1)
RejoinButton.Font = Enum.Font.SourceSans
RejoinButton.TextSize = 18
RejoinButton.MouseButton1Click:Connect(function()
    if Rollback.Enable then
        print("Rollback está ativado. Reentrando no servidor sem salvar dados.")
    else
        print("Rollback está desativado. Reentrando no servidor e salvando dados.")
    end
    rejoinServer()
end)

-- Loop principal
spawn(function()
    while true do
        if Rollback.Enable then
            performRollback(Rollback.Method)
        end
        wait(1) -- Aguarda 1 segundo antes de verificar novamente
    end
end)
