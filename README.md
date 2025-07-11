-- Highlight Script para Zeus FPS Troca de Tiro RJ (apenas inimigos)
local Players = game:GetService("Players")
local LocalPlayer = Players.LocalPlayer

local function highlightEnemies()
    for _, player in pairs(Players:GetPlayers()) do
        if player ~= LocalPlayer and player.Team ~= LocalPlayer.Team and player.Character and player.Character:FindFirstChild("HumanoidRootPart") then
            if not player.Character:FindFirstChild("Highlight") then
                local highlight = Instance.new("Highlight")
                highlight.Parent = player.Character
                highlight.FillColor = Color3.fromRGB(255, 0, 0)      -- Vermelho para inimigos
                highlight.OutlineColor = Color3.fromRGB(255, 255, 0) -- Amarelo
                highlight.FillTransparency = 0.5
                highlight.OutlineTransparency = 0
                highlight.DepthMode = Enum.HighlightDepthMode.AlwaysOnTop
            end
        else
            -- Remove highlight de aliados, se existir
            if player.Character and player.Character:FindFirstChild("Highlight") then
                player.Character.Highlight:Destroy()
            end
        end
    end
end

-- Atualiza highlights a cada 1 segundo
while true do
    pcall(highlightEnemies)
    wait(1)
end
