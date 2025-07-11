-- Highlight Script para Zeus FPS Troca de Tiro RJ
local Players = game:GetService("Players")
local LocalPlayer = Players.LocalPlayer

-- Função para adicionar highlight em todos jogadores exceto o local
local function highlightPlayers()
    for _, player in pairs(Players:GetPlayers()) do
        if player ~= LocalPlayer and player.Character and player.Character:FindFirstChild("HumanoidRootPart") then
            -- Verifica se já existe um highlight
            if not player.Character:FindFirstChild("Highlight") then
                local highlight = Instance.new("Highlight")
                highlight.Parent = player.Character
                highlight.FillColor = Color3.fromRGB(255, 0, 0)      -- Vermelho (inimigo)
                highlight.OutlineColor = Color3.fromRGB(255, 255, 0) -- Amarelo
                highlight.FillTransparency = 0.5
                highlight.OutlineTransparency = 0
                highlight.DepthMode = Enum.HighlightDepthMode.AlwaysOnTop
            end
        end
    end
end

-- Atualiza highlights a cada 1 segundo
while true do
    pcall(highlightPlayers)
    wait(1)
end
