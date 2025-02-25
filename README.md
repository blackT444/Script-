# Script-local toggle = true -- Começa com os nomes ativados

local function toggleNameTags()
    toggle = not toggle

    for _, player in pairs(game:GetService("Players"):GetPlayers()) do
        if player.Character and player.Character:FindFirstChild("Head") then
            for _, v in pairs(player.Character.Head:GetChildren()) do
                if v:IsA("BillboardGui") then
                    v.Enabled = toggle
                end
            end
        end
    end

    if toggle then
        game.StarterGui:SetCore("SendNotification", {
            Title = "Marretão Script";
            Text = "Nomes ativados!";
            Duration = 2;
        })
    else
        game.StarterGui:SetCore("SendNotification", {
            Title = "Marretão Script";
            Text = "Nomes desativados!";
            Duration = 2;
        })
    end
end

-- Criar um comando no chat para ativar/desativar
game:GetService("Players").LocalPlayer.Chatted:Connect(function(msg)
    if msg:lower() == "!nomes" then
        toggleNameTags()
    end
end)

game.StarterGui:SetCore("SendNotification", {
    Title = "Marretão Script";
    Text = "Digite !nomes no chat para ativar/desativar os nomes.";
    Duration = 5;
})
