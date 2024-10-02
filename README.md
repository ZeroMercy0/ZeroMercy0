-- // Mythril Hub ♦️ \\ -- | (Version 1.01) [ Made by ThroughTheFireAndFlames#9925 :3 ] Any attempts to make profit off this project are pathetic and will be laughed at.
------------------------------------------------------------------------------------------------------------------------------------------------------------------------
repeat task.wait(0.25) until game:IsLoaded();local BoredLibrary = loadstring(game:HttpGet("https://raw.githubusercontent.com/Lvl9999/Bored/main/Backup"))();
getgenv().CurrentVersion = "1.02";

-- // Anti AFK \\ --
task.spawn(function()
    if not getgenv().AntiAfk == true then getgenv().AntiAfk = true;
        while true do task.wait(1100);
            pcall(function()
                game:GetService("VirtualInputManager"):SendKeyEvent(true,"RightBracket",false,game);
            end)
        end
    end
end)

-- // Loaded Notification \\ --
task.spawn(function()BoredLibrary.prompt("Mythril Hub  ♦️","Welcome To Mythril Hub :3",1.5);end)
-----------------------------------[[ Main Ui Libs ]]------------------------------------------------------------------
local DarkraiX = loadstring(game:HttpGet("https://raw.githubusercontent.com/Lvl9999/Darkrai/main/Backup",true))();
local Library = DarkraiX:Window("               Mythril Hub ♦️   ","  A Universal Time  [Version "..tostring(getgenv().CurrentVersion).."]","rbxassetid://18853503513",Enum.KeyCode[getgenv().ToggleUI]);
-----------------------------------[[ Main Ui Libs ]]------------------------------------------------------------------
-- // UI Icon Mobile \\ --
task.spawn(function()
    if not getgenv().LoadedMobileUI == true then getgenv().LoadedMobileUI = true
        local OpenUI = Instance.new("ScreenGui");
        local ImageButton = Instance.new("ImageButton");
        local UICorner = Instance.new("UICorner");
        OpenUI.Name = "OpenUI";
        OpenUI.Parent = game:GetService("CoreGui");
        OpenUI.ZIndexBehavior = Enum.ZIndexBehavior.Sibling;
        ImageButton.Parent = OpenUI;
        ImageButton.BackgroundColor3 = Color3.fromRGB(105,105,105);
        ImageButton.BackgroundTransparency = 0.8
        ImageButton.Position = UDim2.new(0.9,0,0.1,0);
        ImageButton.Size = UDim2.new(0,50,0,50);
        ImageButton.Image = "rbxassetid://18853503513";
        ImageButton.Draggable = true;
        ImageButton.Transparency = 1;
        UICorner.CornerRadius = UDim.new(0,200);
        UICorner.Parent = ImageButton;
        ImageButton.MouseButton1Click:Connect(function()
            game:GetService("VirtualInputManager"):SendKeyEvent(true,getgenv().ToggleUI,false,game);
        end)
    end
end)

BoredLibrary.prompt("Mythril Hub  ♦️","Current Version: "..getgenv().CurrentVersion,1.5);
Home = Library:Tab("Home");
Fighting = Library:Tab("Fighting");
Farming = Library:Tab("Farming");
Quests = Library:Tab("Quests");
Teleports = Library:Tab("Teleports");
---------------------------------[[ Main Source Code 💞 ]]------------------------------------------------------------
Home:Seperator("Bypass Menu Stuff")
Home:Button("Open Inventory Menu",function()
    game:GetService("Players").LocalPlayer.PlayerGui.UI.Menus.Visible = true;
    game:GetService("Players").LocalPlayer.PlayerGui.UI.Menus.Inventory.Visible = true;
end)

Home:Button("Open Ability Menu",function()
    game:GetService("Players").LocalPlayer.PlayerGui.UI.Menus.Visible = true;
    game:GetService("Players").LocalPlayer.PlayerGui.UI.Menus.Ability.Visible = true;
end)

Home:Button("Open Shop Menu",function()
    game:GetService("Players").LocalPlayer.PlayerGui.UI.Menus.Visible = true;
    game:GetService("Players").LocalPlayer.PlayerGui.UI.Menus.Products.Visible = true;
end)

Home:Button("Open Quest Menu",function()
    game:GetService("Players").LocalPlayer.PlayerGui.UI.Menus.Visible = true;
    game:GetService("Players").LocalPlayer.PlayerGui.UI.Menus.Quests.Visible = true;
end)

Home:Seperator("Local Player Stuff");
Home:Toggle("Super Walkspeed",false,function(Value)
    getgenv().WalkspeedBypass = Value

    -- Got From https://raw.githubusercontent.com/EdgeIY/infiniteyield/master/source
    task.spawn(function()
        while getgenv().WalkspeedBypass == true and game:GetService("Players").LocalPlayer do
            pcall(function()
                local chr = game:GetService("Players").LocalPlayer.Character
                if chr then
                   local hum = chr:FindFirstChildWhichIsA("Humanoid");
                    if hum and hum.Parent then
                        local hb = game:GetService("RunService").Heartbeat
                        local delta = hb:Wait()
                        if hum.MoveDirection.Magnitude > 0 then
                            chr:TranslateBy(hum.MoveDirection * 10 * delta * 10);
                        else
                            chr:TranslateBy(hum.MoveDirection * delta * 10);
                        end
                    end
                end
            end)
            task.wait(0.0015);
        end
    end)
end)

Home:Toggle("Super Jumppower",false,function(Value)
    getgenv().JumpPowerBypass = Value;

    task.spawn(function()
        while getgenv().JumpPowerBypass == true do
            pcall(function()
                if game.Players.LocalPlayer.Character:FindFirstChildOfClass("Humanoid"):GetState() == Enum.HumanoidStateType.Jumping then
                    game.Players.LocalPlayer.Character.Humanoid.RootPart.CFrame = game.Players.LocalPlayer.Character.Humanoid.RootPart.CFrame * CFrame.new(0,110,0);
                end
            end)
            task.wait(0.0015);
        end
    end)
end)

Home:Button("Reset Character",function()
	game.Players.LocalPlayer.Character.Humanoid.Health = 0;
end)

Home:Seperator("Visual Scripts");
Home:Toggle("Esp Players",false,function(Value)
    getgenv().EspPlayers = Value;

    local Folder = workspace.Living

    local function CreateBilboard(X)
        local Head = X:FindFirstChild("Head");
        if not Head then return end

        local BillboardGui = Instance.new("BillboardGui");
        local TextLabel = Instance.new("TextLabel");

        BillboardGui.Parent = Head
        BillboardGui.AlwaysOnTop = true
        BillboardGui.Size = UDim2.new(0,100,0,50);
        BillboardGui.StudsOffset = Vector3.new(0,2,0);

        TextLabel.Parent = BillboardGui
        TextLabel.BackgroundColor3 = Color3.new(1,1,1);
        TextLabel.BackgroundTransparency = 1
        TextLabel.Size = UDim2.new(1,0,1,0);
        TextLabel.Text = X.Name
        TextLabel.TextColor3 = Color3.fromRGB(255,255,0);
        TextLabel.TextScaled = true
        TextLabel.Font = Enum.Font.GothamBold
        TextLabel.TextStrokeTransparency = 0
        TextLabel.TextStrokeColor3 = Color3.fromRGB(0,0,0);
        TextLabel.Visible = false

        return BillboardGui,TextLabel
    end

    local function UseESP(X)
        local Head = X:FindFirstChild("Head");
        if not Head then return end

        local BillboardGui,TextLabel = CreateBilboard(X)
        local RenderSteppedCon

        local function DisconnectCons()
            if BillboardGui then
                BillboardGui:Destroy();
            end
            if RenderSteppedCon then
                RenderSteppedCon:Disconnect();
                RenderSteppedCon = nil
            end
        end

        RenderSteppedCon = game:GetService("RunService").RenderStepped:Connect(function()
            local HeadPosition,HeadOnScreen = workspace.CurrentCamera:WorldToViewportPoint(Head.Position);
            if HeadOnScreen then
                TextLabel.Visible = getgenv().EspPlayers
            else
                TextLabel.Visible = false
            end
        end)

        X.AncestryChanged:Connect(function(_,b)
            if not b then
                DisconnectCons();
            end
        end)
    end

    local function isPlayer(X)
        return game.Players:GetPlayerFromCharacter(X) ~= nil
    end

    local function XAdded(X)
        if isPlayer(X) and X:IsA("Model") and X:FindFirstChild("Head") then
            UseESP(X);
        end
        X.ChildAdded:Connect(function(v)
            if isPlayer(v) and v:IsA("Model") and v:FindFirstChild("Head") then
                UseESP(v);
            end
        end)
    end

    for _,X in ipairs(Folder:GetChildren()) do
        if isPlayer(X) and X:IsA("Model") and X:FindFirstChild("Head") then
            XAdded(X);
        end
    end

    Folder.ChildAdded:Connect(function(v)
        task.wait(0.5);XAdded(v);
    end)
end)

Home:Toggle("Esp Entities",false,function(Value)
	getgenv().EspEntities = Value;

    local Folder = workspace.Living

    local function CreateBilboard(X)
        local Head = X:FindFirstChild("Head");
        if not Head then return end

        local BillboardGui = Instance.new("BillboardGui");
        local TextLabel = Instance.new("TextLabel");

        BillboardGui.Parent = Head
        BillboardGui.AlwaysOnTop = true
        BillboardGui.Size = UDim2.new(0,100,0,50);
        BillboardGui.StudsOffset = Vector3.new(0,2,0);

        TextLabel.Parent = BillboardGui
        TextLabel.BackgroundColor3 = Color3.new(1,1,1);
        TextLabel.BackgroundTransparency = 1
        TextLabel.Size = UDim2.new(1,0,1,0);
        TextLabel.Text = X.Name
        TextLabel.TextColor3 = Color3.fromRGB(255,0,0);
        TextLabel.TextScaled = true
        TextLabel.Font = Enum.Font.GothamBold
        TextLabel.TextStrokeTransparency = 0
        TextLabel.TextStrokeColor3 = Color3.fromRGB(0,0,0);
        TextLabel.Visible = false

        return BillboardGui,TextLabel
    end

    local function UseESP(X)
        local Head = X:FindFirstChild("Head");
        if not Head then return end

        local BillboardGui,TextLabel = CreateBilboard(X)
        local RenderSteppedCon

        local function DisconnectCons()
            if BillboardGui then
                BillboardGui:Destroy();
            end
            if RenderSteppedCon then
                RenderSteppedCon:Disconnect();
                RenderSteppedCon = nil
            end
        end

        RenderSteppedCon = game:GetService("RunService").RenderStepped:Connect(function()
            local HeadPosition,HeadOnScreen = workspace.CurrentCamera:WorldToViewportPoint(Head.Position);
            if HeadOnScreen then
                TextLabel.Visible = getgenv().EspEntities
            else
                TextLabel.Visible = false
            end
        end)

        X.AncestryChanged:Connect(function(_,b)
            if not b then
                DisconnectCons();
            end
        end)
    end

    local function isPlayer(X)
        for _,k in pairs(game.Players:GetPlayers()) do
            if X.Name == k.Name then
                return true
            end
        end
        return false
    end

    local function XAdded(X)
        if not isPlayer(X) and X:IsA("Model") and X:FindFirstChild("Head") then
            UseESP(X);
        end
        X.ChildAdded:Connect(function(v)
            if not isPlayer(v) and v:IsA("Model") and v:FindFirstChild("Head") then
                UseESP(v);
            end
        end)
    end

    for _,X in ipairs(Folder:GetChildren()) do
        if not isPlayer(X) and X:IsA("Model") and X:FindFirstChild("Head") then
            XAdded(X);
        end
    end

    Folder.ChildAdded:Connect(function(v)
        task.wait(0.5);XAdded(v);
    end)
end)

Home:Button("Jumpscare",function()
    task.spawn(function()
        local ScreenGui = Instance.new("ScreenGui");
        ScreenGui.Parent = game.Players.LocalPlayer:WaitForChild("PlayerGui");
        local ImageLabel = Instance.new("ImageLabel");
        ImageLabel.Parent = ScreenGui
        ImageLabel.BackgroundColor3 = Color3.fromRGB(255,255,255);
        ImageLabel.BorderColor3 = Color3.fromRGB(0,0,0);
        ImageLabel.BorderSizePixel = 0;
        ImageLabel.Position = UDim2.new(0,0,0,0);
        ImageLabel.Size = UDim2.new(1,0,1,0);
        ImageLabel.Image = "http://www.roblox.com/asset/?id=7307744965";
        ImageLabel.ImageTransparency = 0;
        ImageLabel.DisplayOrder = 999999;
    end)
    task.spawn(function()
        local Screams = "http://www.roblox.com/asset/?id=6863021504";
        local Sound = Instance.new("Sound");
        Sound.Name = "Sound";
        Sound.SoundId = Screams;
        Sound.Volume = 10;
        Sound.Looped = true;
        Sound.Archivable = false;
        Sound.Parent = game.Workspace
        Sound:Play();
    end)
end)

Fighting:Seperator("Fighting Scripts");
Fighting:Toggle("Auto Ctrl Click M1ing Combo",false,function(Value)
    getgenv().AutoTeleportPunching = Value;

    getgenv().DetectionDistance = 55
    getgenv().TeleportDistance = 5

    local LPlayer = game.Players.LocalPlayer
    local CRoot

    local function UpdateCRoot()
        local LChar = LPlayer.Character
        if LChar then
            CRoot = LChar:FindFirstChild("HumanoidRootPart");
            if not CRoot then
                LChar.ChildAdded:Wait();
                CRoot = LChar:WaitForChild("HumanoidRootPart");
            end
        end
    end

    local function FindNearest()
        local Dist = getgenv().DetectionDistance
        local NearestPlr = nil

        for _,v in pairs(game.Workspace.Living:GetChildren()) do
            local Humanoid = v:FindFirstChildOfClass("Humanoid");
            local HumanoidRoot = v:FindFirstChild("HumanoidRootPart");

            if Humanoid and HumanoidRoot and v ~= LPlayer.Character then
                if Humanoid.Health > 0 then
                    local Mag = (CRoot.Position - HumanoidRoot.Position).magnitude
                    if Mag < Dist then
                        Dist = Mag
                        NearestPlr = HumanoidRoot
                    end
                end
            end
        end

        return NearestPlr
    end

    game:GetService("UserInputService").InputBegan:Connect(function(t,j)
        if not j and t.UserInputType == Enum.UserInputType.MouseButton1 then
            if game:GetService("UserInputService"):IsKeyDown(Enum.KeyCode.LeftControl) then
                if getgenv().AutoTeleportPunching == true then
                    pcall(function()UpdateCRoot();
                        if CRoot then
                            local Found = FindNearest();
                            if Found then
                                local Target = Found.Position + -Found.CFrame.LookVector * getgenv().TeleportDistance
                                LPlayer.Character:SetPrimaryPartCFrame(CFrame.new(Target,Target + (Found.Position - Target).unit));
                            end
                        end
                    end)
                end
            end
        end
    end)

    LPlayer.CharacterAdded:Connect(function()
        task.wait(3);UpdateCRoot();
    end)
end)

Fighting:Toggle("Auto Dodge Players / Mobs  [BETA]",false,function(Value)
    getgenv().AutoDodging = Value;

    task.spawn(function()
        local connection
        connection = game:GetService("RunService").RenderStepped:Connect(function()
            if getgenv().AutoDodging == true then
                pcall(function()
                    for _,k in ipairs(workspace.Living:GetChildren()) do
                        if k:IsA("Model") and k:FindFirstChild("Head") and k.Head:IsA("Part") and k.Head.Name == "Head" and k.Head ~= game.Players.LocalPlayer.Character.Head then
                            if (k.Head.Position - game.Players.LocalPlayer.Character.Head.Position).magnitude <= 15 then
                                if k:FindFirstChildOfClass("Humanoid") and k:FindFirstChildOfClass("Humanoid").Health > 0 then
                                    if k:FindFirstChild("Stand"):FindFirstChild("StandHumanoidRootPart") then
                                        for _,v in ipairs(k:FindFirstChild("Stand").StandHumanoidRootPart:GetChildren()) do
                                            if v:IsA("Sound") and v.Playing == true then
                                                game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = k.HumanoidRootPart.CFrame * CFrame.new(0,0,15);
                                                break
                                            end
                                        end
                                    end
                                end
                            end
                        end
                    end
                end)
            else
                connection:Disconnect();
            end
        end)
    end)
end)

Fighting:Seperator("More Coming Soon!");

Farming:Seperator("Auto Farming Features");
Farming:Dropdown("Select Attacks",{"E","R","T","G","Y","V","H"},function(Value)
    getgenv().ExecuteMoves = Value;
end)

Farming:Toggle("Auto Complete Zoro Quest",false,function(Value)
    getgenv().AutoCompleteZoroQuest = Value;

    task.spawn(function()
        while getgenv().AutoCompleteZoroQuest == true do
            pcall(function()
                game:GetService("ReplicatedStorage"):WaitForChild("ReplicatedModules"):WaitForChild("KnitPackage"):WaitForChild("Knit"):WaitForChild("Services"):WaitForChild("AdventureService"):WaitForChild("RF"):WaitForChild("PickedUpSword"):InvokeServer();
                local args = {[1] = "Zoros_Swords_Adventure"};
                game:GetService("ReplicatedStorage"):WaitForChild("ReplicatedModules"):WaitForChild("KnitPackage"):WaitForChild("Knit"):WaitForChild("Services"):WaitForChild("DialogueService"):WaitForChild("RF"):WaitForChild("CheckDialogue"):InvokeServer(unpack(args));
                game:GetService("ReplicatedStorage"):WaitForChild("ReplicatedModules"):WaitForChild("KnitPackage"):WaitForChild("Knit"):WaitForChild("Services"):WaitForChild("AdventureService"):WaitForChild("RF"):WaitForChild("PickedUpSword"):InvokeServer();
                local args = {[1] = "Zoros_Swords_Adventure"};
                game:GetService("ReplicatedStorage"):WaitForChild("ReplicatedModules"):WaitForChild("KnitPackage"):WaitForChild("Knit"):WaitForChild("Services"):WaitForChild("DialogueService"):WaitForChild("RF"):WaitForChild("CheckDialogue"):InvokeServer(unpack(args));
                game:GetService("ReplicatedStorage"):WaitForChild("ReplicatedModules"):WaitForChild("KnitPackage"):WaitForChild("Knit"):WaitForChild("Services"):WaitForChild("AdventureService"):WaitForChild("RF"):WaitForChild("PickedUpSword"):InvokeServer();
            end)
            task.wait(0.095);
        end
    end)
end)

Farming:Toggle("Auto One Shot Npcs (Optional)",false,function(Value)
    getgenv().AutoOneShotting = Value;

    task.spawn(function()
        local connection
        connection = game:GetService("RunService").RenderStepped:Connect(function()
            if getgenv().AutoOneShotting == true then
                pcall(function()
                    for _,k in ipairs(workspace.Living:GetChildren()) do
                        if k:IsA("Model") and k:FindFirstChild("Head") and k.Head ~= game.Players.LocalPlayer.Character.Head then
                            if (k.Head.Position - game.Players.LocalPlayer.Character.Head.Position).magnitude <= 35 then
                                if k:FindFirstChildOfClass("Humanoid").Health ~= k:FindFirstChildOfClass("Humanoid").MaxHealth then k:FindFirstChildOfClass("Humanoid").Health = 0;end
                            end
                        end
                    end
                end)
            else
                connection:Disconnect();
            end
        end)
    end)
end)

Farming:Toggle("Auto Ascend Current Abillity",false,function(Value)
    getgenv().AutoAscending = Value;

    task.spawn(function()
        while getgenv().AutoAscending == true do
            pcall(function()
                if game:GetService("Players").LocalPlayer:WaitForChild("Data"):WaitForChild("Ability"):GetAttribute("AbilityLevel") == 200 then
                    local args = {[1] = game:GetService("Players").LocalPlayer:WaitForChild("Data"):WaitForChild("Ability").Value};
                    game:GetService("ReplicatedStorage"):WaitForChild("ReplicatedModules"):WaitForChild("KnitPackage"):WaitForChild("Knit"):WaitForChild("Services"):WaitForChild("LevelService"):WaitForChild("RF"):WaitForChild("AscendAbility"):InvokeServer(unpack(args));
                end
            end)
            task.wait(0.35);
        end
    end)
end)

Farming:Toggle("Auto Kill Fleeing Prisoners",false,function(Value)
    getgenv().AutoFastestFarm = Value;

    local FloatPart = Instance.new("Part",game.Workspace);
    FloatPart.Name = "FloatPart"
    FloatPart.Size = Vector3.new(6,0.1,6);
    FloatPart.Anchored = true
    FloatPart.Transparency = 1

    task.spawn(function()
        if getgenv().AutoFastestFarm == false then
            pcall(function()
                game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(2588.35009765625,918.5690307617188,5582.02685546875);
            end)
        end
    end)

    task.spawn(function()
        while getgenv().AutoFastestFarm == true do
            pcall(function()
                FloatPart.CFrame = game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame + Vector3.new(0,-3.05,0);
            end)
            task.wait(0.01);
        end
    end)

    task.spawn(function()
        while getgenv().AutoFastestFarm == true do
            pcall(function()
                if not workspace.Living[game.Players.LocalPlayer.Name].StatesFolder.StandOn.Value == true then
                    local args = {[1] = "Q"};
                    game:GetService("ReplicatedStorage"):WaitForChild("ReplicatedModules"):WaitForChild("KnitPackage"):WaitForChild("Knit"):WaitForChild("Services"):WaitForChild("MoveInputService"):WaitForChild("RF"):WaitForChild("FireInput"):InvokeServer(unpack(args)); 
                end
            end)
            task.wait(0.45);
        end
    end)
    
    task.spawn(function()
        while getgenv().AutoFastestFarm == true do
            pcall(function()
                for _,j in pairs(game:GetService("Players"):GetPlayers()) do
                    local Char = j.Character
                    if Char then
                        for _,n in pairs(Char:GetDescendants()) do
                            if n:IsA("BasePart") then
                                n.CanCollide = false
                            end
                        end
                    end
                end
            end)
            task.wait(0.15);
        end
    end)
  
    task.spawn(function()
        while getgenv().AutoFastestFarm == true do
            pcall(function()
                getgenv().Target = nil;getgenv().FoundAnything = false
                for i,v in ipairs({"Prisoner"}) do
                    for _,x in ipairs(workspace.Living:GetChildren()) do
                        if x:FindFirstChild("Head") and x.Name:lower():find(v:lower()) then
                            getgenv().Target = x getgenv().FoundAnything = true;
                            break;
                        end
                    end
                end
            end)
            task.wait(0.45);
        end
    end)

    task.spawn(function()
        while getgenv().AutoFastestFarm == true do
            pcall(function()
                if getgenv().FoundAnything == true and not game.Players[game.Players.LocalPlayer.Name].Cooldowns:FindFirstChild("Rush Attack") and game.Players.LocalPlayer.Character.Humanoid.Health ~= 0 then
                    local TryToGet = {workspace.ItemSpawns.StandardItems,workspace.ItemSpawns.DevilFruits};
                    local Table = {}
                
                    for _,x in ipairs(TryToGet) do
                        for _,v in ipairs(x:GetDescendants()) do
                            if v:IsA("BasePart") and v.Name ~= "SpawnLocation" then
                                table.insert(Table,v);
                            end
                        end
                    end

                    if #Table == 0 then
                        game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(getgenv().Target.HumanoidRootPart.Position - Vector3.new(0,6.5,0),getgenv().Target.HumanoidRootPart.Position);
                        task.spawn(function()
                            local args = {[1] = "MouseButton1"};
                            game:GetService("ReplicatedStorage"):WaitForChild("ReplicatedModules"):WaitForChild("KnitPackage"):WaitForChild("Knit"):WaitForChild("Services"):WaitForChild("MoveInputService"):WaitForChild("RF"):WaitForChild("FireInput"):InvokeServer(unpack(args));
                            task.wait(0.25);
                        end)
                    else
                        game.Players.LocalPlayer.Character:SetPrimaryPartCFrame(Table[math.random(#Table)].CFrame * CFrame.new(0,0.2,0));
                        for _,x in ipairs(TryToGet) do
                            for _,v in ipairs(x:GetDescendants()) do
                                if v:IsA("ProximityPrompt") then
                                    v.HoldDuration = 0;v:InputHoldBegin();v:InputHoldEnd();task.wait(0.15);
                                end
                            end
                        end
                    end
                else
                    game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(2588.402099609375,898.4298095703125,5582.00439453125);
                end
            end)
            task.wait(0.0000000000015);
        end
    end)
end)

Farming:Toggle("Auto Kill Dio Fushigoro",false,function(Value)
    getgenv().AutoFarmDioBoss = Value;

    task.spawn(function()
        if getgenv().AutoFarmDioBoss == true then
            pcall(function()
                game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(2806.075927734375,1023.2745361328125,-744.5523681640625);
            end)
        end
    end)

    task.spawn(function()
        if getgenv().AutoFarmDioBoss == false then
            pcall(function()
                game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(2806.075927734375,1023.2745361328125,-744.5523681640625);
            end)
        end
    end)

    task.spawn(function()
        while getgenv().AutoFarmDioBoss == true do
            pcall(function()
                if not workspace.Living[game.Players.LocalPlayer.Name].StatesFolder.StandOn.Value == true then
                    local args = {[1] = "Q"};
                    game:GetService("ReplicatedStorage"):WaitForChild("ReplicatedModules"):WaitForChild("KnitPackage"):WaitForChild("Knit"):WaitForChild("Services"):WaitForChild("MoveInputService"):WaitForChild("RF"):WaitForChild("FireInput"):InvokeServer(unpack(args)); 
                end
            end)
            task.wait(0.45);
        end
    end)
    
    task.spawn(function()
        while getgenv().AutoFarmDioBoss == true do
            pcall(function()
                local args = {[1] = "Spawn Boss Altar",[2] = "Dio",[3] = workspace:WaitForChild("NPCSpawns"):WaitForChild("Boss Altar"):WaitForChild("Spawn"):WaitForChild("Part")};
                game:GetService("ReplicatedStorage"):WaitForChild("Remotes"):WaitForChild("NpcFunc"):InvokeServer(unpack(args));
                local args = {[1] = "Spawn Boss Altar",[2] = "Dio",[3] = workspace:WaitForChild("NPCSpawns"):WaitForChild("Boss Altar"):WaitForChild("Spawn"):WaitForChild("Part")};
                game:GetService("ReplicatedStorage"):WaitForChild("Remotes"):WaitForChild("NpcFunc"):InvokeServer(unpack(args));
            end)
            task.wait(0.15);
        end
    end)

    task.spawn(function()
        while getgenv().AutoFarmDioBoss == true do
            pcall(function()
                for _,v in pairs(workspace.Effects:GetChildren()) do
                    if v.Name == "Hold up, aint you Dio?" then
                        v:Destroy();
                    end
                end
            end)
            task.wait(0.45);
        end
    end)
    
    task.spawn(function()
        while getgenv().AutoFarmDioBoss == true do
            pcall(function()
                getgenv().Target = nil;getgenv().FoundAnything = false;
                for i,v in ipairs({"Dio"}) do
                    for _,x in ipairs(workspace.Living:GetChildren()) do
                        if x:FindFirstChild("Head") and x.Name:lower():find(v:lower()) then
                            if x:FindFirstChildOfClass("Humanoid").Health ~= 0 then
                                getgenv().Target = x;getgenv().FoundAnything = true;
                                break;
                            end
                        end
                    end
                end
            end)
            task.wait(0.15);
        end
    end)
    
    task.spawn(function()
        while getgenv().AutoFarmDioBoss == true do
            pcall(function()
                local TryToGet = {workspace.ItemSpawns.StandardItems,workspace.ItemSpawns.DevilFruits};
                local Table = {}
                
                for _,x in ipairs(TryToGet) do
                    for _,v in ipairs(x:GetDescendants()) do
                        if v:IsA("BasePart") and v.Name ~= "SpawnLocation" then
                            table.insert(Table,v);
                        end
                    end
                end

                if #Table == 0 then
                    if getgenv().Target and game.Players.LocalPlayer.Character.Humanoid.Health ~= 0 then
                        game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(getgenv().Target.HumanoidRootPart.Position - Vector3.new(0,0,-5),getgenv().Target.HumanoidRootPart.Position);
                        task.spawn(function()
                            local args = {[1] = "MouseButton1"};
                            game:GetService("ReplicatedStorage"):WaitForChild("ReplicatedModules"):WaitForChild("KnitPackage"):WaitForChild("Knit"):WaitForChild("Services"):WaitForChild("MoveInputService"):WaitForChild("RF"):WaitForChild("FireInput"):InvokeServer(unpack(args));
                            if getgenv().ExecuteMoves then
                                for _,x in ipairs(getgenv().ExecuteMoves) do
                                    local args = {[1] = x};
                                    game:GetService("ReplicatedStorage"):WaitForChild("ReplicatedModules"):WaitForChild("KnitPackage"):WaitForChild("Knit"):WaitForChild("Services"):WaitForChild("MoveInputService"):WaitForChild("RF"):WaitForChild("FireInput"):InvokeServer(unpack(args));    
                                end
                            end
                            task.wait(0.25);
                        end)
                    end
                else
                    game.Players.LocalPlayer.Character:SetPrimaryPartCFrame(Table[math.random(#Table)].CFrame * CFrame.new(0,0.2,0));
                    for _,x in ipairs(TryToGet) do
                        for _,v in ipairs(x:GetDescendants()) do
                            if v:IsA("ProximityPrompt") then
                                v.HoldDuration = 0;v:InputHoldBegin();v:InputHoldEnd();task.wait(0.15);
                            end
                        end
                    end
                end
            end)
            task.wait(0.0000000000015);
        end
    end)
end)

Farming:Seperator("Auto Use Stats");
Farming:Dropdown("Select Stats",{"Special","Defense","Health","Attack"},function(Value)
    getgenv().WantedStats = Value;
end)

Farming:Toggle("Auto Apply Stats",false,function(Value)
    getgenv().AutoUsingStats = Value;

    task.spawn(function()
        while getgenv().AutoUsingStats == true do
            pcall(function()
                local Stats = {Special = 0,Defense = 0,Health = 0,Attack = 0};
                for _,x in ipairs(getgenv().WantedStats or {}) do
                    Stats[x] = 1;
                end
                local args = {[1] = 1,[2] = Stats};
                game:GetService("ReplicatedStorage"):WaitForChild("ReplicatedModules"):WaitForChild("KnitPackage"):WaitForChild("Knit"):WaitForChild("Services"):WaitForChild("StatService"):WaitForChild("RF"):WaitForChild("ApplyStats"):InvokeServer(unpack(args));
            end)
            task.wait(0.35);
        end
    end)
end)

Farming:Seperator("Auto Farming Mobs");
Farming:Toggle("Auto Kill Curses",false,function(Value)
    getgenv().AutofarmingCursedMobs = Value;

    task.spawn(function()
        while getgenv().AutofarmingCursedMobs == true do
            pcall(function()
                if game.Players.LocalPlayer.Character.Humanoid.Health ~= 0 then
                    game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(1980.7568359375,935.0916748046875,-1499.26416015625);task.wait(0.45);
                else
                    task.wait(6.5);
                end
            end)
        end
    end)

    task.spawn(function()
        while getgenv().AutofarmingCursedMobs == true do
            pcall(function()
                if not workspace.Living[game.Players.LocalPlayer.Name].StatesFolder.StandOn.Value == true then
                    local args = {[1] = "Q"};
                    game:GetService("ReplicatedStorage"):WaitForChild("ReplicatedModules"):WaitForChild("KnitPackage"):WaitForChild("Knit"):WaitForChild("Services"):WaitForChild("MoveInputService"):WaitForChild("RF"):WaitForChild("FireInput"):InvokeServer(unpack(args)); 
                end
            end)
            task.wait(0.45);
        end
    end)
   
    task.spawn(function()
        while getgenv().AutofarmingCursedMobs == true do
            pcall(function()
                getgenv().Targetz = nil;getgenv().FoundAnythingz = false
                for i,v in ipairs({"Ropp","Juju","Mantis","Fly"}) do
                    for _,x in ipairs(workspace.Living:GetChildren()) do
                        if x:FindFirstChild("Head") and x.Name:lower():find(v:lower()) then
                            getgenv().Targetz = x getgenv().FoundAnythingz = true;
                            break;
                        end
                    end
                end
            end)
            task.wait(0.45);
        end
    end)

    task.spawn(function()
        local connection
        connection = game:GetService("RunService").Heartbeat:Connect(function()
            if getgenv().AutofarmingCursedMobs == true then
                pcall(function()
                    local TryToGet = {workspace.ItemSpawns.StandardItems,workspace.ItemSpawns.DevilFruits};
                    local Table = {}
                    
                    for _,x in ipairs(TryToGet) do
                        for _,v in ipairs(x:GetDescendants()) do
                            if v:IsA("BasePart") and v.Name ~= "SpawnLocation" then
                                table.insert(Table,v);
                            end
                        end
                    end

                    if #Table == 0 then
                        if getgenv().FoundAnythingz == true and not game.Players[game.Players.LocalPlayer.Name].Cooldowns:FindFirstChild("Rush Attack") and game.Players.LocalPlayer.Character.Humanoid.Health ~= 0 then
                            game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(getgenv().Targetz.Head.Position - Vector3.new(0,-4,0),getgenv().Targetz.Head.Position);
                            task.spawn(function()
                                local args = {[1] = "MouseButton1"};
                                game:GetService("ReplicatedStorage"):WaitForChild("ReplicatedModules"):WaitForChild("KnitPackage"):WaitForChild("Knit"):WaitForChild("Services"):WaitForChild("MoveInputService"):WaitForChild("RF"):WaitForChild("FireInput"):InvokeServer(unpack(args));
                                if getgenv().ExecuteMoves then
                                    for _,x in ipairs(getgenv().ExecuteMoves) do
                                        local args = {[1] = x};
                                        game:GetService("ReplicatedStorage"):WaitForChild("ReplicatedModules"):WaitForChild("KnitPackage"):WaitForChild("Knit"):WaitForChild("Services"):WaitForChild("MoveInputService"):WaitForChild("RF"):WaitForChild("FireInput"):InvokeServer(unpack(args));    
                                    end
                                end
                            end)
                        else
                            task.wait(7.15);
                        end
                    else
                        game.Players.LocalPlayer.Character:SetPrimaryPartCFrame(Table[math.random(#Table)].CFrame * CFrame.new(0,0.2,0));
                        for _,x in ipairs(TryToGet) do
                            for _,v in ipairs(x:GetDescendants()) do
                                if v:IsA("ProximityPrompt") then
                                    v.HoldDuration = 0;v:InputHoldBegin();v:InputHoldEnd();task.wait(0.15);
                                end
                            end
                        end
                    end
                end)
            else
                connection:Disconnect();
            end
            task.wait(1);
        end)
    end)
end)

Farming:Dropdown("Select Chest",{"Common","Epic","Rare","Legendary"},function(Value)
    getgenv().TryToFind = Value;
end)

Farming:Toggle("Auto Collect Chests",false,function(Value)
    getgenv().AutoCollectChests = Value;

    task.spawn(function()
        while getgenv().AutoCollectChests == true do
            pcall(function()
                game:GetService("Players").LocalPlayer.PlayerGui.UI.Gameplay.ChestRoll.Visible = false;
            end)
            task.wait(0.015);
        end
    end)

    task.spawn(function()
        local connection
        connection = game:GetService("RunService").Heartbeat:Connect(function()
            if getgenv().AutoCollectChests == true then
                pcall(function()
                    if getgenv().AutofarmingCursedMobs == true and game.Players[game.Players.LocalPlayer.Name].Cooldowns:FindFirstChild("Rush Attack") and game.Players.LocalPlayer.Character.Humanoid.Health ~= 0 or getgenv().AutofarmingCursedMobs ~= true and game.Players.LocalPlayer.Character.Humanoid.Health ~= 0 then
                        local InRange = {}
                        for i,v in ipairs(workspace:GetChildren()) do
                            for _,x in ipairs(getgenv().TryToFind) do
                                if v.Name:match(x) then
                                    local Chest = v:FindFirstChild("RootPart");
                                    if Chest and (Chest.Position - game.Players.LocalPlayer.Character:WaitForChild("HumanoidRootPart").Position).magnitude <= 370 then
                                        table.insert(InRange,Chest);
                                    end
                                end
                            end
                        end
        
                        if #InRange > 0 then
                            local Selected = InRange[math.random(#InRange)];
                            local Prompt = Selected.ProximityAttachment:FindFirstChildOfClass("ProximityPrompt");
                        
                            game.Players.LocalPlayer.Character:WaitForChild("HumanoidRootPart").CFrame = Selected.CFrame - Vector3.new(0,-1.65,5) ;
                            task.wait(0.15);Prompt.HoldDuration = 0;Prompt:InputHoldBegin();Prompt:InputHoldEnd();
                        end
                    else
                        task.wait(7.15);
                    end
                end)
            else
                connection:Disconnect();
            end
            task.wait(1);
        end)
    end)
end)

Farming:Seperator("Auto Selling Items");
Farming:Slider("Sell Delay",15,50,25,function(Value)
    getgenv().DelaySelling = Value;
end)

Farming:Toggle("Auto Sell Inventory",false,function(Value)
    getgenv().AutoSellingItems = Value;

    task.spawn(function()
        while getgenv().AutoSellingItems == true do
            pcall(function()
                local LongAssRemote = game:GetService("ReplicatedStorage")
                :WaitForChild("ReplicatedModules"):WaitForChild("KnitPackage"):WaitForChild("Knit")
                :WaitForChild("Services"):WaitForChild("ShopService"):WaitForChild("RE"):WaitForChild("Signal");
                local args = {[1] = "BlackMarketBulkSellItems",[2] = {}};
                for _,x in ipairs(game:GetService("Players").LocalPlayer.Backpack:GetChildren()) do 
                    if x:IsA("Tool") then
                        table.insert(args[2],{x:GetAttribute("ItemId"),x:GetAttribute("UUID"),1});
                    end
                end
                LongAssRemote:FireServer(unpack(args));                
            end)
            task.wait(getgenv().DelaySelling);
        end
    end)

    task.spawn(function()
        while getgenv().AutoSellingItems == true do
            pcall(function()
                for _,x in pairs(game.Players.LocalPlayer.Backpack:GetChildren()) do task.wait(0.15);
                    if x:IsA("Tool") and x.Name == "Sanji's Cookbook" then 
                        x:Destroy();
                    end
                end           
            end)
            task.wait(1.45);
        end
    end)
end)

Farming:Seperator("Auto Storing Items");
Farming:Dropdown("Select Wanted Items",{"Pumpkin","Bone","Watch","Tales of the Universe","Azakana Mask","Ancient Sword","Dragon Ball","Cursed Orb","Monochromatic Orb","Kinetic Orb","Mysterious Fragment","Bisento","Ope Devil Fruit","Mero Devil Fruit","Bouquet Of Flowers","Law's Cap","Golden Hook","Suna Devil Fruit","Gojo's Blindfold","Sukuna's Finger","Slime Energy","Knight's Sword"},function(Value)
    getgenv().WantedItems = Value;
end)

Farming:Toggle("Auto Store Items",false,function(Value)
    getgenv().AutoStoreItems = Value;

    task.spawn(function()
        while getgenv().AutoStoreItems == true do
            pcall(function()
                for _,x in ipairs(game:GetService("Players").LocalPlayer.Backpack:GetChildren()) do
                    for _,k in ipairs(getgenv().WantedItems) do
                        if x.Name == k then
                            game:GetService("Players").LocalPlayer.Character:FindFirstChild("Humanoid"):EquipTool(x);
                            local args = {[1] = {["AddItems"] = true}};
                            game:GetService("ReplicatedStorage"):WaitForChild("ReplicatedModules"):WaitForChild("KnitPackage"):WaitForChild("Knit"):WaitForChild("Services"):WaitForChild("InventoryService"):WaitForChild("RE"):WaitForChild("ItemInventory"):FireServer(unpack(args));
                            task.wait(0.15);game:GetService("Players").LocalPlayer.Character:FindFirstChild("Humanoid"):UnequipTools();
                        end
                    end
                end
            end)
            task.wait(0.25);
        end
    end)
end)

Farming:Seperator("Auto Pick Traits");
Farming:Dropdown("Select Wanted Traits",{"Prime","Overconfident Prime","Solar","Icarus Solar","Cursed","Undying Cursed","Vampiric","Ancient Vampiric","Gluttonous","Festering Gluttonous","Voided","Abyssal Voided","Gambler","Idle Death Gambler","Overflowing","Torrential Overflowing","Deferred","Fractured Deferred","True","Vitriolic True","Cultivation","Soul Reaping Cultivation","Economic","Greedy Economic","Angelic","Fallen Angelic","Godly","Egotistic Godly","Temporal","FTL Temporal","Spiritual","Psychotic Spiritual","Ryoiki","Heavenly Restricted Ryoiki","RCT","Automatic RCT"},function(Value)
    getgenv().WantedThoseTraits = Value;
end)

Farming:Toggle("Auto Collect Traits",false,function(Value)
    getgenv().AutoPickingTraits = Value;

    task.spawn(function()
        while getgenv().AutoPickingTraits == true do 
            if game:GetService("Players").LocalPlayer.PlayerGui.UI.Gameplay.TraitHandPrompt.Visible == true then
                local OpenTraitMenu = game:GetService("Players").LocalPlayer.PlayerGui.UI.Gameplay.MoveHandPrompt.TextLabel;
                game:GetService("VirtualInputManager"):SendMouseButtonEvent(OpenTraitMenu.AbsolutePosition.X+OpenTraitMenu.AbsoluteSize.X/1.5,OpenTraitMenu.AbsolutePosition.Y+35,0,true,OpenTraitMenu,1.5);
                game:GetService("VirtualInputManager"):SendMouseButtonEvent(OpenTraitMenu.AbsolutePosition.X+OpenTraitMenu.AbsoluteSize.X/1.5,OpenTraitMenu.AbsolutePosition.Y+35,0,false,OpenTraitMenu,1.5);
            end
            task.wait(1.35);
            if game:GetService("Players").LocalPlayer.PlayerGui.UI.Gameplay.TraitHands.Visible == true and game:GetService("Players").LocalPlayer.PlayerGui.UI.Gameplay.TraitHands.ShowAll.Visible == true then
                local RevealEverything = game:GetService("Players").LocalPlayer.PlayerGui.UI.Gameplay.TraitHands.ShowAll.TextLabel;
                game:GetService("VirtualInputManager"):SendMouseButtonEvent(RevealEverything.AbsolutePosition.X+RevealEverything.AbsoluteSize.X/3.5,RevealEverything.AbsolutePosition.Y+35,0,true,RevealEverything,3,5);
                game:GetService("VirtualInputManager"):SendMouseButtonEvent(RevealEverything.AbsolutePosition.X+RevealEverything.AbsoluteSize.X/3.5,RevealEverything.AbsolutePosition.Y+35,0,false,RevealEverything,3.5);
            end
        end
        task.wait(0.45);
    end)

    task.spawn(function()
        while getgenv().AutoPickingTraits == true do
            pcall(function()
                local TraitHolder = game:GetService("Players").LocalPlayer.PlayerGui.UI.Gameplay.TraitHands.Holder;            
                local TraitHolders = {TraitHolder["1"].Content.Title.Label,TraitHolder["2"].Content.Title.Label,TraitHolder["3"].Content.Title.Label};
                local DiscardTrait = game:GetService("Players").LocalPlayer.PlayerGui.UI.Gameplay.TraitHands.Discard.TextLabel;

                if game:GetService("Players").LocalPlayer.PlayerGui.UI.Gameplay.TraitHands.Visible == true then local FoundTrait = false;
                    for _,v in ipairs(TraitHolders) do
                        for _,x in ipairs(getgenv().WantedThoseTraits) do
                            if v.Text:match(x) then FoundTrait = true;
                                game:GetService("VirtualInputManager"):SendMouseButtonEvent(v.AbsolutePosition.X + v.AbsoluteSize.X/3.5,v.AbsolutePosition.Y + 35,0,true,v,3.5);
                                game:GetService("VirtualInputManager"):SendMouseButtonEvent(v.AbsolutePosition.X + v.AbsoluteSize.X/3.5,v.AbsolutePosition.Y + 35,0,false,v,3.5);
                                task.wait(0.51);for _,x in ipairs(game:GetService("Players").LocalPlayer.PlayerGui.UI.Prompt.Frame.Buttons:GetChildren()) do
                                    if x:IsA("TextButton") then
                                        if x:FindFirstChildOfClass("TextLabel").Text == "Yes" then
                                            game:GetService("VirtualInputManager"):SendMouseButtonEvent(x.AbsolutePosition.X + x.AbsoluteSize.X/4.5,x.AbsolutePosition.Y + 45,0,true,x,4.5);
                                            game:GetService("VirtualInputManager"):SendMouseButtonEvent(x.AbsolutePosition.X + x.AbsoluteSize.X/4.5,x.AbsolutePosition.Y + 45,0,false,x,4.5);
                                        end
                                    end
                                    task.spawn(function()task.wait(5.15);
                                        getgenv().AutoPickingTraits = false;
                                    end)
                                end
                            end
                        end
                    end
                    if not FoundTrait then
                        game:GetService("VirtualInputManager"):SendMouseButtonEvent(DiscardTrait.AbsolutePosition.X+DiscardTrait.AbsoluteSize.X/3.5,DiscardTrait.AbsolutePosition.Y+35,0,true,DiscardTrait,3.5);
                        game:GetService("VirtualInputManager"):SendMouseButtonEvent(DiscardTrait.AbsolutePosition.X+DiscardTrait.AbsoluteSize.X/3.5,DiscardTrait.AbsolutePosition.Y+35,0,false,DiscardTrait,3.5);
                        task.wait(0.51);for _,x in ipairs(game:GetService("Players").LocalPlayer.PlayerGui.UI.Prompt.Frame.Buttons:GetChildren()) do
                            if x:IsA("TextButton") then
                                if x:FindFirstChildOfClass("TextLabel").Text == "Yes" then
                                    game:GetService("VirtualInputManager"):SendMouseButtonEvent(x.AbsolutePosition.X + x.AbsoluteSize.X/4.5,x.AbsolutePosition.Y + 45,0,true,x,4.5);
                                    game:GetService("VirtualInputManager"):SendMouseButtonEvent(x.AbsolutePosition.X + x.AbsoluteSize.X/4.5,x.AbsolutePosition.Y + 45,0,false,x,4.5);
                                end
                            end
                        end
                    end
                end
            end)
            task.wait(1.25);
        end
    end)
end)

Farming:Seperator("Auto Managing Skins");
Farming:Toggle("Auto Open Skin Crates",false,function(Value)
    getgenv().AutoOpenSkinCrate = Value;

    task.spawn(function()
        if getgenv().AutoOpenSkinCrate == true then
            pcall(function()
                BoredLibrary.prompt("Mythril Hub  ♦️","Resseting Every 35 Seconds Oke?",3.5);
                BoredLibrary.prompt("Mythril Hub  ♦️","To Get Rid Of Combat to Open Crates!",3.5);
            end)
        end
    end)

    task.spawn(function()
        while getgenv().AutoOpenSkinCrate == true do
            pcall(function()
                for i = 1,35 do task.wait(0.15);
                    game.Players.LocalPlayer.Character.Humanoid.Health = 0;
                end                               
            end)
            task.wait(35);
        end
    end)

    task.spawn(function()
        while getgenv().AutoOpenSkinCrate == true do
            pcall(function()
                game:GetService("Players").LocalPlayer.PlayerGui.UI.Prompt.Visible = false;
            end)
            task.wait(0.0015);
        end
    end)

    task.spawn(function()
        while getgenv().AutoOpenSkinCrate == true do
            pcall(function()
                local args = {[1] = "ItemInventory"};
                local Items = game:GetService("ReplicatedStorage").ReplicatedModules.KnitPackage.Knit.Services.InventoryService.RF.GetItems:InvokeServer(unpack(args));

                for _,x in pairs(Items) do
                    if x._DisplayName == "5x Skin Crate" then
                        local args = {[1] = {["UUID"] = x._UUID,["ItemId"] = x._ItemId}};
                        game:GetService("ReplicatedStorage"):WaitForChild("ReplicatedModules"):WaitForChild("KnitPackage"):WaitForChild("Knit"):WaitForChild("Services"):WaitForChild("InventoryService"):WaitForChild("RE"):WaitForChild("ItemInventory"):FireServer(unpack(args));
                    end
                end
            end)
            task.wait(0.45);
        end
    end)
end)

Farming:Toggle("Auto Buy Skin Crates",false,function(Value)
    getgenv().AutoBuySkinCrate = Value;

    task.spawn(function()
        while getgenv().AutoBuySkinCrate == true do
            pcall(function()
                local args = {[1] = "Skin_Crate",[2] = "UShards",[3] = 1};
                game:GetService("ReplicatedStorage"):WaitForChild("ReplicatedModules"):WaitForChild("KnitPackage"):WaitForChild("Knit"):WaitForChild("Services"):WaitForChild("ShopService"):WaitForChild("RF"):WaitForChild("BuySkinCrate"):InvokeServer(unpack(args));                
            end)
            task.wait(0.35);
        end
    end)
end)

Farming:Toggle("Auto Buy Event Skin Crates",false,function(Value)
    getgenv().AutoBuyEventSkinCrate = Value;

    task.spawn(function()
        while getgenv().AutoBuyEventSkinCrate == true do
            pcall(function()
                local args = {[1] = "Event_Crate_2",[2] = "PoolPoints",[3] = 1};
                game:GetService("ReplicatedStorage"):WaitForChild("ReplicatedModules"):WaitForChild("KnitPackage"):WaitForChild("Knit"):WaitForChild("Services"):WaitForChild("ShopService"):WaitForChild("RF"):WaitForChild("BuySkinCrate"):InvokeServer(unpack(args));
            end)
            task.wait(0.35);
        end
    end)
end)

Farming:Toggle("Auto Delete Leg Skins",false,function(Value)
    getgenv().AutoDeleteLegendary = Value;

    task.spawn(function()
        while getgenv().AutoDeleteLegendary == true do
            pcall(function()
                local Inventory = game:GetService("Players").LocalPlayer.PlayerGui.UI.Menus.Inventory.Tabs.Items;

                for _,k in pairs(Inventory:GetChildren()) do
                    if k:FindFirstChild("Button") and k.Button:FindFirstChild("UIStroke") and k.Button.UIStroke.Color == Color3.fromRGB(255,150,75)  then
                        local args = {[1] = "SkinInventory"};
                        local Skins = game:GetService("ReplicatedStorage").ReplicatedModules.KnitPackage.Knit.Services.InventoryService.RF.GetItems:InvokeServer(unpack(args));
                        
                        for _, x in pairs(Skins) do
                            if k.Button:FindFirstChild("Label") and x._DisplayName == k.Button.Label.Text then
                                local args = {[1] = {["UUID"] = x._UUID,["Remove"] = true}};
                                game:GetService("ReplicatedStorage"):WaitForChild("ReplicatedModules"):WaitForChild("KnitPackage"):WaitForChild("Knit"):WaitForChild("Services"):WaitForChild("InventoryService"):WaitForChild("RE"):WaitForChild("SkinInventory"):FireServer(unpack(args));
                            end
                        end
                    end
                end
            end)
            task.wait(1.15);
        end
    end)
end)

Farming:Toggle("Auto Delete Epic Skins",false,function(Value)
    getgenv().AutoDeleteEpic = Value;

    task.spawn(function()
        while getgenv().AutoDeleteEpic == true do
            pcall(function()
                local Inventory = game:GetService("Players").LocalPlayer.PlayerGui.UI.Menus.Inventory.Tabs.Items;

                for _,k in pairs(Inventory:GetChildren()) do
                    if k:FindFirstChild("Button") and k.Button:FindFirstChild("UIStroke") and k.Button.UIStroke.Color == Color3.fromRGB(175,90,255)  then
                        local args = {[1] = "SkinInventory"};
                        local Skins = game:GetService("ReplicatedStorage").ReplicatedModules.KnitPackage.Knit.Services.InventoryService.RF.GetItems:InvokeServer(unpack(args));
                        
                        for _, x in pairs(Skins) do
                            if k.Button:FindFirstChild("Label") and x._DisplayName == k.Button.Label.Text then
                                local args = {[1] = {["UUID"] = x._UUID,["Remove"] = true}};
                                game:GetService("ReplicatedStorage"):WaitForChild("ReplicatedModules"):WaitForChild("KnitPackage"):WaitForChild("Knit"):WaitForChild("Services"):WaitForChild("InventoryService"):WaitForChild("RE"):WaitForChild("SkinInventory"):FireServer(unpack(args));
                            end
                        end
                    end
                end
            end)
            task.wait(1.15);
        end
    end)
end)

Farming:Toggle("Auto Delete Rare Skins",false,function(Value)
    getgenv().AutoDeleteRare = Value;

    task.spawn(function()
        while getgenv().AutoDeleteRare == true do
            pcall(function()
                local Inventory = game:GetService("Players").LocalPlayer.PlayerGui.UI.Menus.Inventory.Tabs.Items;

                for _,k in pairs(Inventory:GetChildren()) do
                    if k:FindFirstChild("Button") and k.Button:FindFirstChild("UIStroke") and k.Button.UIStroke.Color == Color3.fromRGB(75,150,255)  then
                        local args = {[1] = "SkinInventory"};
                        local Skins = game:GetService("ReplicatedStorage").ReplicatedModules.KnitPackage.Knit.Services.InventoryService.RF.GetItems:InvokeServer(unpack(args));
                        
                        for _, x in pairs(Skins) do
                            if k.Button:FindFirstChild("Label") and x._DisplayName == k.Button.Label.Text then
                                local args = {[1] = {["UUID"] = x._UUID,["Remove"] = true}};
                                game:GetService("ReplicatedStorage"):WaitForChild("ReplicatedModules"):WaitForChild("KnitPackage"):WaitForChild("Knit"):WaitForChild("Services"):WaitForChild("InventoryService"):WaitForChild("RE"):WaitForChild("SkinInventory"):FireServer(unpack(args));
                            end
                        end
                    end
                end
            end)
            task.wait(1.15);
        end
    end)
end)

Quests:Seperator("Coming Soon!");

Teleports:Seperator("Coming Soon!");
