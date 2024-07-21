local Material = loadstring(game:HttpGet("https://raw.githubusercontent.com/Kinlei/MaterialLua/master/Module.lua"))()
repeat wait() until game:IsLoaded()
game:GetService("Players").LocalPlayer.Idled:connect(function()
game:GetService("VirtualUser"):ClickButton2(Vector2.new())
end)
local X = Material.Load({
Title = "💪 Get Huge Simulator 🔥",
Style = 2,
SizeX = 320,
SizeY = 320,
Theme = "Dark",
ColorOverrides = {
MainFrame = Color3.fromRGB(0,9,55)
}
})
local Y = X.New({
Title = "Main"
})
Y.Toggle({
Text = "Auto Lift",
Callback = function(Value)
_G.Lift = Value
while _G.Lift do
task.wait()
game:GetService("ReplicatedStorage"):WaitForChild("Remotes"):WaitForChild("LiftWeight"):FireServer()
end
end,
Enabled = false
})
Y.Toggle({
    Text = "Auto Sell",
    Callback = function(Value)
    _G.Sell = Value
    while _G.Sell do
    task.wait(1)
    game:GetService("ReplicatedStorage"):WaitForChild("Remotes"):WaitForChild("SellStrengthRequest"):FireServer()
    end
    end,
    Enabled = false
})
Y.Toggle({
    Text = "Auto Collect [Gems,Coin]",
    Callback = function(Value)
    _G.Collect = Value
    while _G.Collect do
    task.wait(1)
    for _,v in pairs(workspace.ConsumableSpawns:GetDescendants()) do
        if v:IsA("TouchTransmitter") then
        firetouchinterest(game.Players.LocalPlayer.Character.HumanoidRootPart, v.Parent, 0) --0 is touch
        firetouchinterest(game.Players.LocalPlayer.Character.HumanoidRootPart, v.Parent, 1) -- 1 is untouch
    end
    end
    end
    end,
    Enabled = false
})
Y.Toggle({
    Text = "Auto King - [Gems]",
    Callback = function(Value)
    _G.King = Value
    while _G.King do
    task.wait(1)
    game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(207.045685, 360.756317, -1191.72351, -0.834650397, -1.27868223e-08, 0.550780058, -5.92018523e-08, 1, -6.64984654e-08, -0.550780058, -8.81101698e-08, -0.834650397)
    end
    end,
    Enabled = false
})
local S = X.New({
    Title = "Shop"
    })
S.Toggle({
    Text = "Buy Weights [All]",
    Callback = function(Value)
    _G.Weights = Value
    while _G.Weights do
    task.wait(1)
    game:GetService("ReplicatedStorage"):WaitForChild("Remotes"):WaitForChild("Shop"):WaitForChild("RequestBuyAll"):InvokeServer("Weight", "Islands")    
    end
    end,
    Enabled = false
})
S.Toggle({
    Text = "Auto Upgrade DNA",
    Callback = function(Value)
    _G.DNA = Value
    while _G.DNA do
    task.wait(0.1)
    Dna = {1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15, 16, 17, 18, 19, 20, 21, 22, 23, 24, 25, 26, 27, 28, 29, 30, 31, 32, 33, 34, 35, 36, 37, 38, 39, 40, 41, 42, 43, 44, 45, 46, 47, 48, 49, 50, 51, 52, 53, 54, 55, 56, 57, 58, 59, 60, 61, 62, 63, 64, 65, 66, 67, 68, 69, 70, 71, 72, 73, 74, 75, 76, 77, 78, 79, 80, 81, 82, 83, 84, 85, 86, 87, 88, 89, 90, 91, 92, 93, 94, 95, 96, 97, 98, 99, 100}
    for i, v in next, Dna do
        if v then
    local args = {
        [1] = v,
        [2] = "DNA",
        [3] = "Islands"
    }
    
    game:GetService("ReplicatedStorage"):WaitForChild("Remotes"):WaitForChild("Shop"):WaitForChild("RequestPurchase"):InvokeServer(unpack(args))
    wait(0.1)
    end
    end    
    end
    end,
    Enabled = false
})
