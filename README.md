local Rayfield = loadstring(game:HttpGet('https://sirius.menu/rayfield'))()
local Window = Rayfield:CreateWindow({
   Name = "LimeLuxe Bitcoin Miner",
   LoadingTitle = "Bitcoin Miner Script",
   LoadingSubtitle = "by Limeoyster",
   ConfigurationSaving = {
      Enabled = false,
      FolderName = "limeoyster's bitcoin miner", -- Create a custom folder for your hub/game
      FileName = "Bitcoin Miner"
   },
   Discord = {
      Enabled = false,
      Invite = "noinvitelink", -- The Discord invite code, do not include discord.gg/. E.g. discord.gg/ABCD would be ABCD
      RememberJoins = true -- Set this to false to make them join the discord every time they load it up
   },
   KeySystem = false, -- Set this to true to use our key system
   KeySettings = {
      Title = "Untitled",
      Subtitle = "Key System",
      Note = "No method of obtaining the key is provided",
      FileName = "Key", -- It is recommended to use something unique as other scripts using Rayfield may overwrite your key file
      SaveKey = true, -- The user's key will be saved, but if you change the key, they will be unable to use your script
      GrabKeyFromSite = false, -- If this is true, set Key below to the RAW site you would like Rayfield to get the key from
      Key = {"Hello"} -- List of keys that will be accepted by the system, can be RAW file links (pastebin, github etc) or simple strings ("hello","key22")
   }
})
local Tab = Window:CreateTab("Player", 4483362458) -- Title, Image
local Toggle = Tab:CreateToggle({
   Name = "Anti AFK",
   CurrentValue = false,
   Flag = "Toggle1", -- A flag is the identifier for the configuration file, make sure every element has a different flag if you're using configuration saving to ensure no overlaps
   Callback = function(Value)
       local vu = game:GetService("VirtualUser")
game:GetService("Players").LocalPlayer.Idled:connect(function()
vu:Button2Down(Vector2.new(0,0),workspace.CurrentCamera.CFrame)
wait(1)
vu:Button2Up(Vector2.new(0,0),workspace.CurrentCamera.CFrame)
end)
   -- The function that takes place when the toggle is pressed
   -- The variable (Value) is a boolean on whether the toggle is true or false
   end,
})
local Slider = Tab:CreateSlider({
   Name = "Walk Speed",
   Range = {0, 200},
   Increment = 1,
   Suffix = "Speed",
   CurrentValue = 16,
   Flag = "Slider1", -- A flag is the identifier for the configuration file, make sure every element has a different flag if you're using configuration saving to ensure no overlaps
   Callback = function(s)
       game.Players.LocalPlayer.Character.Humanoid.WalkSpeed = s
   -- The function that takes place when the slider changes
   -- The variable (Value) is a number which correlates to the value the slider is currently at
   end,
})

local Tab = Window:CreateTab("Game", 4483362458) -- Title, Image
local Section = Tab:CreateSection("Exchange")
local Button = Tab:CreateButton({
   Name = "Bitcoins",
   Callback = function()
   -- The function that takes place when the button is pressed
   end,
})
local Button = Tab:CreateButton({
   Name = "Solaris",
   Callback = function()
   -- The function that takes place when the button is pressed
   end,
})
local Button = Tab:CreateButton({
   Name = "Quasar",
   Callback = function()
local args = {
    [1] = "Qsr"
}

game:GetService("ReplicatedStorage"):WaitForChild("Events"):WaitForChild("ExchangeMoney"):FireServer(unpack(args))
   end,
})

local Section = Tab:CreateSection("Auto Exchange")
local Toggle = Tab:CreateToggle({
   Name = "Binance Auto",
   CurrentValue = false,
   Flag = "Binance1", -- A flag is the identifier for the configuration file, make sure every element has a different flag if you're using configuration saving to ensure no overlaps
   Callback = function(Value)
   -- The function that takes place when the toggle is pressed
   -- The variable (Value) is a boolean on whether the toggle is true or false
   end,
})
local Toggle = Tab:CreateToggle({
   Name = "Solaris Auto",
   CurrentValue = false,
   Flag = "Solaris1", -- A flag is the identifier for the configuration file, make sure every element has a different flag if you're using configuration saving to ensure no overlaps
   Callback = function(Value)
   -- The function that takes place when the toggle is pressed
   -- The variable (Value) is a boolean on whether the toggle is true or false
   end,
})

local function SendScriptContinuously()
    while ToggleOn do
        local args = {
            [1] = "Qsr"
        }
        game:GetService("ReplicatedStorage"):WaitForChild("Events"):WaitForChild("ExchangeMoney"):FireServer(unpack(args))
        wait(3)  -- Adjust the delay between each script execution as needed
    end
end

Toggle = Tab:CreateToggle({
    Name = "Quasar Auto",
    CurrentValue = false,
    Flag = "Quasar1", -- Unique flag for configuration
    Callback = function(Auto)
        ToggleOn = Auto  -- Update the toggle state

        if ToggleOn then
            -- Start sending the script continuously
            SendScriptContinuously()
        end
    end,
})

local Section = Tab:CreateSection("Automation")
local function SendScriptContinuously1()
    while ToggleOn do
        game:GetService("ReplicatedStorage"):WaitForChild("Events"):WaitForChild("ActivateOverclock"):FireServer()
        wait(300)  -- Adjust the delay between each script execution as needed
    end
end

Toggle = Tab:CreateToggle({
    Name = "Auto OverClock",
    CurrentValue = false,
    Flag = "Clock1", -- Unique flag for configuration
    Callback = function(Auto)
        ToggleOn = Auto  -- Update the toggle state

        if ToggleOn then
            -- Start sending the script continuously
            SendScriptContinuously1()
        end
    end,
})

local function SendScriptContinuously2()
    while ToggleOn do
        game:GetService("ReplicatedStorage"):WaitForChild("Events"):WaitForChild("ClaimFreeBoostStar"):FireServer()
        wait(420)  -- Adjust the delay between each script execution as needed
    end
end

Toggle = Tab:CreateToggle({
    Name = "Auto Claim Boost Star",
    CurrentValue = false,
    Flag = "Star1", -- Unique flag for configuration
    Callback = function(Auto)
        ToggleOn = Auto  -- Update the toggle state

        if ToggleOn then
            -- Start sending the script continuously
            SendScriptContinuously2()
        end
    end,
})

local function SendScriptContinuously3()
    while ToggleOn do
        local args = {
    [1] = 4
}

game:GetService("ReplicatedStorage"):WaitForChild("Events"):WaitForChild("AlgoChang"):FireServer(unpack(args))

        wait(3)  -- Adjust the delay between each script execution as needed
    end
end

Toggle = Tab:CreateToggle({
    Name = "Auto algorithms (test)",
    CurrentValue = false,
    Flag = "algo1", -- Unique flag for configuration
    Callback = function(Auto)
        ToggleOn = Auto  -- Update the toggle state

        if ToggleOn then
            -- Start sending the script continuously
            SendScriptContinuously3()
        end
    end,
})

