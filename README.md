# Tream-Hub
A test
local Rayfield = loadstring(game:HttpGet('https://sirius.menu/rayfield'))()
THIS IS A TEST

local Window = Rayfield:CreateWindow({
    Name = "Tream Hub",
    LoadingTitle = "LOADING Interface Suite",
    LoadingSubtitle = "by Picard",
    ConfigurationSaving = {
       Enabled = true,
       FolderName = nil, -- Create a custom folder for your hub/game
       FileName = "Tream Interface"
    },
    Discord = {
       Enabled = true,
       Invite = "Y5G5EtUz", -- The Discord invite code, do not include discord.gg/. E.g. discord.gg/ABCD would be ABCD
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

 local Tab = Window:CreateTab("Physics", 4483362458) -- Title, Image

 Rayfield:Notify({
    Title = "Succesfully Loaded Hub",
    Content = "Notification Content",
    Duration = 6.5,
    Image = 4483362458,
    Actions = { -- Notification Buttons
       Ignore = {
          Name = "Okay!",
          Callback = function()
          print("The user tapped Okay!")
       end
    },
 },
 })

 local Toggle = MainTab:CreateToggle({
    Name = "Infinite Jump",
    CurrentValue = false,
    Flag = "Toggle1", -- A flag is the identifier for the configuration file, make sure every element has a different flag if you're using configuration saving to ensure no overlaps
    Callback = function(InfiniteJumpEnabled)
        local InfiniteJumpEnabled = true
        game:GetService("UserInputService").JumpRequest:connect(function()
            if InfiniteJumpEnabled then
                game:GetService"Players".LocalPlayer.Character:FindFirstChildOfClass'Humanoid':ChangeState("Jumping")
            end
        end)
    end,
 })
 

 local Slider = MainTab:CreateSlider({
    Name = "Walkspeed",
    Range = {16, 200},
    Increment = 10,
    Suffix = "Walkspeed",
    CurrentValue = 10,
    Flag = "Slider1", -- A flag is the identifier for the configuration file, make sure every element has a different flag if you're using configuration saving to ensure no overlaps
    Callback = function(v)
        game.Players.LocalPlayer.Character.Humanoid.WalkSpeed = v
    end,
 })



 local Slider = MainTab:CreateSlider({
    Name = "JumpPower",
    Range = {50, 450},
    Increment = 10,
    Suffix = "JumpPower",
    CurrentValue = 10,
    Flag = "Slider1", -- A flag is the identifier for the configuration file, make sure every element has a different flag if you're using configuration saving to ensure no overlaps
    Callback = function(v)
        game.Players.LocalPlayer.Character.Humanoid.JumpPower = v
    end,
 })

 local Toggle = Tab:CreateToggle({
    Name = "Auto Click",
    CurrentValue = false,
    Flag = "Auto Click", -- A flag is the identifier for the configuration file, make sure every element has a different flag if you're using configuration saving to ensure no overlaps
    Callback = function(Value)
    shared.["Auto Click"] = x
    while shared["Auto Click"] do
        task.wait()
        if not shared["Auto Click"] then
             } -- List of keys that will be accepted by the system, can be RAW file links (pastebin, github etc) or simple strings (
       end
       Click()
    end,
 })

 local ColorPicker = Tab:CreateColorPicker({
    Name = "Colorize",
    Color = Color3.fromRGB(255,255,255),
    Flag = "Colorize", -- A flag is the identifier for the configuration file, make sure every element has a different flag if you're using configuration saving to ensure no overlaps
    Callback = function(Value)
        -- The function that takes place every time the color picker is moved/changed
        -- The variable (Value) is a Color3fromRGB value based on which color is selected
    end
})
