--[[
	SCRIPT DE VELOCIDADE E INFINITE JUMP PARA ROBLOX
	COM INTERFACE BONITA E FUNÇÕES DE ATIVAR/DESATIVAR
]]

-- Criando ScreenGui
local player = game.Players.LocalPlayer
local gui = Instance.new("ScreenGui")
gui.Name = "SpeedJumpGUI"
gui.ResetOnSpawn = false
gui.Parent = player.PlayerGui

-- Criando Frame Principal (fundo da interface)
local mainFrame = Instance.new("Frame")
mainFrame.Size = UDim2.new(0, 320, 0, 380)
mainFrame.Position = UDim2.new(0.5, -160, 0.5, -190)
mainFrame.BackgroundColor3 = Color3.fromRGB(25, 25, 35)
mainFrame.BackgroundTransparency = 0.15
mainFrame.BorderSizePixel = 0
mainFrame.ClipsDescendants = true
mainFrame.Parent = gui

-- Arredondamento e efeito de vidro (Glassmorphism)
local corner = Instance.new("UICorner")
corner.CornerRadius = UDim.new(0, 20)
corner.Parent = mainFrame

local shadow = Instance.new("ShadowEffect") -- Precisa de um plugin para sombra real, mas faremos manual
-- Criando uma borda sutil
local border = Instance.new("Frame")
border.Size = UDim2.new(1, 0, 1, 0)
border.Position = UDim2.new(0, 0, 0, 0)
border.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
border.BackgroundTransparency = 0.9
border.BorderSizePixel = 0
border.Parent = mainFrame
local borderCorner = Instance.new("UICorner")
borderCorner.CornerRadius = UDim.new(0, 20)
borderCorner.Parent = border

-- Título
local title = Instance.new("TextLabel")
title.Size = UDim2.new(1, 0, 0, 50)
title.Position = UDim2.new(0, 0, 0, 0)
title.BackgroundTransparency = 1
title.Text = "🚀 SPEED & JUMP"
title.TextColor3 = Color3.fromRGB(255, 255, 255)
title.TextScaled = true
title.Font = Enum.Font.GothamBold
title.Parent = mainFrame

-- Linha separadora
local line = Instance.new("Frame")
line.Size = UDim2.new(0.8, 0, 0, 2)
line.Position = UDim2.new(0.1, 0, 0, 55)
line.BackgroundColor3 = Color3.fromRGB(100, 100, 255)
line.BackgroundTransparency = 0.5
line.Parent = mainFrame

-- Botão Ativar/Desativar
local toggleBtn = Instance.new("TextButton")
toggleBtn.Size = UDim2.new(0.6, 0, 0, 40)
toggleBtn.Position = UDim2.new(0.2, 0, 0, 70)
toggleBtn.BackgroundColor3 = Color3.fromRGB(0, 200, 100)
toggleBtn.Text = "ATIVAR"
toggleBtn.TextColor3 = Color3.fromRGB(255, 255, 255)
toggleBtn.TextScaled = true
toggleBtn.Font = Enum.Font.GothamBold
toggleBtn.Parent = mainFrame

local btnCorner = Instance.new("UICorner")
btnCorner.CornerRadius = UDim.new(0, 10)
btnCorner.Parent = toggleBtn

-- Configurações de Velocidade
local speedLabel = Instance.new("TextLabel")
speedLabel.Size = UDim2.new(0.8, 0, 0, 30)
speedLabel.Position = UDim2.new(0.1, 0, 0, 125)
speedLabel.BackgroundTransparency = 1
speedLabel.Text = "⚡ VELOCIDADE"
speedLabel.TextColor3 = Color3.fromRGB(200, 200, 255)
speedLabel.TextScaled = true
speedLabel.Font = Enum.Font.Gotham
speedLabel.Parent = mainFrame

local speedSlider = Instance.new("Frame")
speedSlider.Size = UDim2.new(0.8, 0, 0, 8)
speedSlider.Position = UDim2.new(0.1, 0, 0, 160)
speedSlider.BackgroundColor3 = Color3.fromRGB(60, 60, 80)
speedSlider.Parent = mainFrame
local sliderCorner = Instance.new("UICorner")
sliderCorner.CornerRadius = UDim.new(0, 4)
sliderCorner.Parent = speedSlider

local speedFill = Instance.new("Frame")
speedFill.Size = UDim2.new(0.5, 0, 1, 0)
speedFill.BackgroundColor3 = Color3.fromRGB(100, 200, 255)
speedFill.Parent = speedSlider
local fillCorner = Instance.new("UICorner")
fillCorner.CornerRadius = UDim.new(0, 4)
fillCorner.Parent = speedFill

local speedValue = Instance.new("TextLabel")
speedValue.Size = UDim2.new(0.2, 0, 0, 30)
speedValue.Position = UDim2.new(0.78, 0, 0, 125)
speedValue.BackgroundTransparency = 1
speedValue.Text = "x1.5"
speedValue.TextColor3 = Color3.fromRGB(255, 255, 255)
speedValue.TextScaled = true
speedValue.Font = Enum.Font.Gotham
speedValue.Parent = mainFrame

-- Configurações de Pulo
local jumpLabel = Instance.new("TextLabel")
jumpLabel.Size = UDim2.new(0.8, 0, 0, 30)
jumpLabel.Position = UDim2.new(0.1, 0, 0, 185)
jumpLabel.BackgroundTransparency = 1
jumpLabel.Text = "🦘 PULO INFINITO"
jumpLabel.TextColor3 = Color3.fromRGB(200, 200, 255)
jumpLabel.TextScaled = true
jumpLabel.Font = Enum.Font.Gotham
jumpLabel.Parent = mainFrame

local jumpToggle = Instance.new("TextButton")
jumpToggle.Size = UDim2.new(0.3, 0, 0, 35)
jumpToggle.Position = UDim2.new(0.35, 0, 0, 220)
jumpToggle.BackgroundColor3 = Color3.fromRGB(0, 200, 100)
jumpToggle.Text = "ATIVO"
jumpToggle.TextColor3 = Color3.fromRGB(255, 255, 255)
jumpToggle.TextScaled = true
jumpToggle.Font = Enum.Font.GothamBold
jumpToggle.Parent = mainFrame
local jumpCorner = Instance.new("UICorner")
jumpCorner.CornerRadius = UDim.new(0, 10)
jumpCorner.Parent = jumpToggle

-- Botão Fechar
local closeBtn = Instance.new("TextButton")
closeBtn.Size = UDim2.new(0, 30, 0, 30)
closeBtn.Position = UDim2.new(1, -40, 0, 5)
closeBtn.BackgroundColor3 = Color3.fromRGB(255, 50, 50)
closeBtn.Text = "✕"
closeBtn.TextColor3 = Color3.fromRGB(255, 255, 255)
closeBtn.TextScaled = true
closeBtn.Font = Enum.Font.GothamBold
closeBtn.Parent = mainFrame
local closeCorner = Instance.new("UICorner")
closeCorner.CornerRadius = UDim.new(0, 15)
closeCorner.Parent = closeBtn

-- Botão Abrir (invisível inicialmente)
local openBtn = Instance.new("TextButton")
openBtn.Size = UDim2.new(0, 50, 0, 50)
openBtn.Position = UDim2.new(0, 10, 0.5, -25)
openBtn.BackgroundColor3 = Color3.fromRGB(25, 25, 35)
openBtn.BackgroundTransparency = 0.2
openBtn.Text = "⚡"
openBtn.TextColor3 = Color3.fromRGB(255, 255, 255)
openBtn.TextScaled = true
openBtn.Font = Enum.Font.GothamBold
openBtn.Visible = false
openBtn.Parent = gui
local openCorner = Instance.new("UICorner")
openCorner.CornerRadius = UDim.new(0, 25)
openCorner.Parent = openBtn

-- Variáveis de estado
local scriptEnabled = true
local infiniteJumpEnabled = true
local speedMultiplier = 1.5
local originalWalkSpeed = 16
local playerChar = player.Character or player.CharacterAdded:Wait()

-- Função para atualizar a velocidade
local function updateSpeed()
	if scriptEnabled and playerChar and playerChar:FindFirstChild("Humanoid") then
		local humanoid = playerChar.Humanoid
		originalWalkSpeed = humanoid.WalkSpeed / speedMultiplier
		humanoid.WalkSpeed = originalWalkSpeed * speedMultiplier
	end
end

-- Função para ativar/desativar pulo infinito
local function updateJump()
	if playerChar and playerChar:FindFirstChild("Humanoid") then
		local humanoid = playerChar.Humanoid
		if infiniteJumpEnabled and scriptEnabled then
			humanoid:SetStateEnabled(Enum.HumanoidStateType.Jumping, true)
		else
			humanoid:SetStateEnabled(Enum.HumanoidStateType.Jumping, true)
		end
	end
end

-- Evento de pulo (infinite jump)
local function onJumpRequest()
	if scriptEnabled and infiniteJumpEnabled and playerChar and playerChar:FindFirstChild("Humanoid") then
		local humanoid = playerChar.Humanoid
		if humanoid:GetState() == Enum.HumanoidStateType.Jumping then
			humanoid:ChangeState(Enum.HumanoidStateType.Jumping)
		end
	end
end

-- Conectar eventos
local function setupCharacter(character)
	playerChar = character
	if character:FindFirstChild("Humanoid") then
		updateSpeed()
		updateJump()
		character.Humanoid.StateChanged:Connect(function(oldState, newState)
			if newState == Enum.HumanoidStateType.Jumping then
				onJumpRequest()
			end
		end)
	end
end

-- Quando o personagem spawnar
player.CharacterAdded:Connect(setupCharacter)
if player.Character then setupCharacter(player.Character) end

-- Controles da interface
toggleBtn.MouseButton1Click:Connect(function()
	scriptEnabled = not scriptEnabled
	toggleBtn.Text = scriptEnabled and "ATIVADO" or "DESATIVADO"
	toggleBtn.BackgroundColor3 = scriptEnabled and Color3.fromRGB(0, 200, 100) or Color3.fromRGB(200, 50, 50)
	
	if scriptEnabled then
		updateSpeed()
		updateJump()
	else
		if playerChar and playerChar:FindFirstChild("Humanoid") then
			playerChar.Humanoid.WalkSpeed = originalWalkSpeed
		end
	end
end)

jumpToggle.MouseButton1Click:Connect(function()
	infiniteJumpEnabled = not infiniteJumpEnabled
	jumpToggle.Text = infiniteJumpEnabled and "ATIVO" or "DESATIVO"
	jumpToggle.BackgroundColor3 = infiniteJumpEnabled and Color3.fromRGB(0, 200, 100) or Color3.fromRGB(200, 50, 50)
	updateJump()
end)

-- Slider de velocidade (simplificado)
local dragging = false
speedSlider.InputBegan:Connect(function(input)
	if input.UserInputType == Enum.UserInputType.MouseButton1 then
		dragging = true
	end
end)

speedSlider.InputEnded:Connect(function(input)
	if input.UserInputType == Enum.UserInputType.MouseButton1 then
		dragging = false
	end
end)

game:GetService("RunService").RenderStepped:Connect(function()
	if dragging then
		local mouse = player:GetMouse()
		local framePos = speedSlider.AbsolutePosition.X
		local frameSize = speedSlider.AbsoluteSize.X
		local relativeX = math.clamp((mouse.X - framePos) / frameSize, 0, 1)
		speedFill.Size = UDim2.new(relativeX, 0, 1, 0)
		speedMultiplier = 1 + (relativeX * 4) -- De 1x a 5x
		speedValue.Text = "x" .. string.format("%.1f", speedMultiplier)
		if scriptEnabled then
			updateSpeed()
		end
	end
end)

-- Fechar e abrir
closeBtn.MouseButton1Click:Connect(function()
	mainFrame.Visible = false
	openBtn.Visible = true
end)

openBtn.MouseButton1Click:Connect(function()
	mainFrame.Visible = true
	openBtn.Visible = false
end)

-- Inicialização
toggleBtn.Text = "ATIVADO"
jumpToggle.Text = "ATIVO"
speedFill.Size = UDim2.new(0.125, 0, 1, 0) -- 1.5x

-- Animação suave de entrada
mainFrame.BackgroundTransparency = 0.15
mainFrame:TweenPosition(UDim2.new(0.5, -160, 0.5, -190), Enum.EasingDirection.Out, Enum.EasingStyle.Quad, 0.3, true)

print("🚀 Script Speed & Infinite Jump carregado com sucesso!")
