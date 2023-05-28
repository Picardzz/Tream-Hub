local Window = Rayfield:CreateWindow({
    Name = "Test",
    LoadingTitle = "Rayfield Interface Suite",
    LoadingSubtitle = "Beta",
    ConfigurationSaving = {
       Enabled = true,
       FolderName = nil, -- Create a custom folder for your hub/game
       FileName = "Beta"
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


 Rayfield:Notify({
    Title = "Successfully loaded",
    Content = "",
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

 local Tab = Window:CreateTab("Catch", 4483362458) -- Title, Image


 local Toggle = Tab:CreateToggle({
    Name = "Regular Mags",
    CurrentValue = false,
    Flag = "Toggle1",
    Callback = function(Value)
       if Value then
        local player = game.Players.LocalPlayer
        local rs = game:GetService("RunService")
        function magBall(ball)
           if ball and player.Character then
               firetouchinterest(player.Character["Left Arm"], ball, 0)
               firetouchinterest(player.Character["Right Arm"], ball, 0)
               task.wait()
               firetouchinterest(player.Character["Left Arm"], ball, 1)
               firetouchinterest(player.Character["Right Arm"], ball, 1)
           end
        end
        --Mag Toggle
        w2:CreateToggle("Mags", function(bool)
        shared.Mags = bool
            rs.Stepped:Connect(function()
            if shared.Mags then
               for i,v in pairs(workspace:GetChildren()) do
                   if v.Name == "Football" and v:IsA("BasePart") then
                       wait()
                       local mag = (player.Character.Torso.Position - v.Position).Magnitude
                       magBall(v)
        
                   end
                en
       end
    end,
 })

 local Slider = Tab:CreateSlider({
    Name = "Slider Example",
    Range = {10, 100},
    Increment = 10,
    Suffix = "Mags",
    CurrentValue = 10,
    Flag = "Slider1", -- A flag is the identifier for the configuration file, make sure every element has a different flag if you're using configuration saving to ensure no overlaps
    Callback = function(Value)
    -- The function that takes place when the slider changes
    -- The variable (Value) is a number which correlates to the value the slider is currently at
    end,
 })
 
 local DataStoreService = game:GetService("DataStoreService")
local ConfigurationDataStore = DataStoreService:GetDataStore("Configuration")

local Input = Tab:CreateInput({
   Name = "Input Example",
   PlaceholderText = "Input Placeholder",
   RemoveTextAfterFocusLost = false,
   Callback = function(Text)
      -- The function that takes place when the input is changed
      -- The variable (Text) is a string for the value in the text box
      ConfigurationDataStore:SetAsync("InputExample", Text)
   end,
})

-- Load the saved value from the data store
local SavedValue = ConfigurationDataStore:GetAsync("InputExample")
if SavedValue then
   Input:SetText(SavedValue)
end

local Rayfield = require(game:GetService("ReplicatedStorage").Rayfield)

local RayfieldUI = Rayfield:CreateUI({
   Name = "Example UI",
   LayoutOrder = 1,
})

local Frame = RayfieldUI:AddFrame({
   Name = "Example Frame",
   Size = UDim2.new(0, 200, 0, 200),
})

local Open = false

game:GetService("UserInputService").InputBegan:Connect(function(Input)
   if Input.KeyCode == Enum.KeyCode.LeftControl then
      Open = not Open
      Frame.Visible = Open
   end
end)
