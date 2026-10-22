--[[
    ═══════════════════════════════════════════════════════════
    Zexart V1 — Universal Roblox GUI (Loadstring Edition)
    Theme: Black + Neon Purple
    ═══════════════════════════════════════════════════════════
]]

if _G.ZexartV1Loaded then
    pcall(function() if _G.ZexartV1GUI then _G.ZexartV1GUI:Destroy() end end)
end
_G.ZexartV1Loaded = true

if not game:IsLoaded() then game.Loaded:Wait() end

local Players = game:GetService("Players")
local RunService = game:GetService("RunService")
local TweenService = game:GetService("TweenService")
local UserInputService = game:GetService("UserInputService")
local Lighting = game:GetService("Lighting")
local Workspace = game:GetService("Workspace")
local HttpService = game:GetService("HttpService")
local Debris = game:GetService("Debris")
local TeleportService = game:GetService("TeleportService")

local LP = Players.LocalPlayer
print("[Zexart V1] Loading...")

local Lang = {
    en = { title="Zexart V1", tab_combat="Combat", tab_troll="Troll", tab_player="Player", tab_visual="Visual", tab_misc="Misc", tab_settings="Settings", speed="Speed Hack", jump="Jump Power", noclip="Noclip", infjump="Infinite Jump", antiafk="Anti AFK", esp="Player ESP", fling="Fling All", dolphin="Dolphin Attach", partspam="Particle Spam", chatspam="Chat Spammer", orbit="Orbit Chaos", bringall="Bring All", partrain="Part Rain", fullbright="Full Bright", fov="FOV", skybox="Rainbow Skybox", aura="Purple Aura", serverhop="Server Hop", rejoin="Rejoin", gameid="Copy Game ID", fps="FPS Unlocker", unload="Unload Script", language="Language", on="ON", off="OFF" },
    id = { title="Zexart V1", tab_combat="Combat", tab_troll="Troll", tab_player="Player", tab_visual="Visual", tab_misc="Misc", tab_settings="Pengaturan", speed="Speed Hack", jump="Jump Power", noclip="Noclip", infjump="Lompat Tanpa Batas", antiafk="Anti AFK", esp="ESP Player", fling="Fling Semua", dolphin="Tempel Lumba-lumba", partspam="Spam Partikel", chatspam="Spam Chat", orbit="Orbit Chaos", bringall="Tarik Semua", partrain="Hujan Part", fullbright="Terang Total", fov="FOV", skybox="Skybox Pelangi", aura="Aura Ungu", serverhop="Pindah Server", rejoin="Masuk Ulang", gameid="Salin Game ID", fps="Unlock FPS", unload="Unload Script", language="Bahasa", on="ON", off="OFF" }
}
local currentLang = "en"
local T = function(k) return Lang[currentLang][k] or Lang.en[k] or k end

local OrigSky = Lighting:FindFirstChildOfClass("Sky")
local OrigFogEnd = Lighting.FogEnd
local OrigBrightness = Lighting.Brightness
local OrigFOV = Workspace.CurrentCamera.FieldOfView

local ScreenGui = Instance.new("ScreenGui")
ScreenGui.Name = "ZexartV1"
ScreenGui.ResetOnSpawn = false
ScreenGui.Parent = LP:WaitForChild("PlayerGui")
_G.ZexartV1GUI = ScreenGui

local Toggle = Instance.new("TextButton")
Toggle.Size = UDim2.new(0, 50, 0, 50)
Toggle.Position = UDim2.new(0, 20, 0.5, -25)
Toggle.BackgroundColor3 = Color3.fromRGB(10, 10, 10)
Toggle.Text = "Z"
Toggle.TextColor3 = Color3.fromRGB(160, 32, 240)
Toggle.TextSize = 24
Toggle.Font = Enum.Font.GothamBold
Toggle.Parent = ScreenGui
Instance.new("UICorner", Toggle).CornerRadius = UDim.new(0, 12)
local tStroke = Instance.new("UIStroke", Toggle)
tStroke.Color = Color3.fromRGB(139, 0, 255)
tStroke.Thickness = 2

local Main = Instance.new("Frame")
Main.Size = UDim2.new(0, 500, 0, 350)
Main.Position = UDim2.new(0.5, -250, 0.5, -175)
Main.BackgroundColor3 = Color3.fromRGB(10, 10, 10)
Main.Visible = false
Main.Parent = ScreenGui
Instance.new("UICorner", Main).CornerRadius = UDim.new(0, 12)

local TitleBar = Instance.new("Frame")
TitleBar.Size = UDim2.new(1, 0, 0, 40)
TitleBar.BackgroundColor3 = Color3.fromRGB(20, 10, 30)
TitleBar.Parent = Main
Instance.new("UICorner", TitleBar).CornerRadius = UDim.new(0, 12)

local Title = Instance.new("TextLabel")
Title.Size = UDim2.new(1, -80, 1, 0)
Title.Position = UDim2.new(0, 15, 0, 0)
Title.BackgroundTransparency = 1
Title.Text = "Zexart V1"
Title.TextColor3 = Color3.fromRGB(160, 32, 240)
Title.TextSize = 20
Title.Font = Enum.Font.GothamBold
Title.TextXAlignment = Enum.TextXAlignment.Left
Title.Parent = TitleBar

local CloseBtn = Instance.new("TextButton")
CloseBtn.Size = UDim2.new(0, 30, 0, 30)
CloseBtn.Position = UDim2.new(1, -40, 0, 5)
CloseBtn.BackgroundColor3 = Color3.fromRGB(60, 0, 60)
CloseBtn.Text = "X"
CloseBtn.TextColor3 = Color3.new(1, 1, 1)
CloseBtn.Parent = TitleBar
Instance.new("UICorner", CloseBtn).CornerRadius = UDim.new(0, 8)

local Sidebar = Instance.new("Frame")
Sidebar.Size = UDim2.new(0, 120, 1, -50)
Sidebar.Position = UDim2.new(0, 5, 0, 45)
Sidebar.BackgroundColor3 = Color3.fromRGB(15, 10, 20)
Sidebar.Parent = Main
Instance.new("UICorner", Sidebar).CornerRadius = UDim.new(0, 8)

local Content = Instance.new("Frame")
Content.Size = UDim2.new(1, -135, 1, -50)
Content.Position = UDim2.new(0, 130, 0, 45)
Content.BackgroundColor3 = Color3.fromRGB(15, 10, 20)
Content.Parent = Main
Instance.new("UICorner", Content).CornerRadius = UDim.new(0, 8)

local tabs = { "combat", "troll", "player", "visual", "misc", "settings" }
local tabFrames, tabButtons = {}, {}

for i, name in ipairs(tabs) do
    local btn = Instance.new("TextButton")
    btn.Size = UDim2.new(1, -10, 0, 32)
    btn.Position = UDim2.new(0, 5, 0, 5 + (i-1)*36)
    btn.BackgroundColor3 = Color3.fromRGB(20, 10, 30)
    btn.Text = T("tab_"..name)
    btn.TextColor3 = Color3.fromRGB(200, 200, 200)
    btn.Font = Enum.Font.Gotham
    btn.TextSize = 13
    btn.Parent = Sidebar
    Instance.new("UICorner", btn).CornerRadius = UDim.new(0, 6)
    tabButtons[name] = btn

    local sf = Instance.new("ScrollingFrame")
    sf.Size = UDim2.new(1, -10, 1, -10)
    sf.Position = UDim2.new(0, 5, 0, 5)
    sf.BackgroundTransparency = 1
    sf.ScrollBarThickness = 4
    sf.CanvasSize = UDim2.new(0, 0, 0, 0)
    sf.Visible = (i == 1)
    sf.Parent = Content
    tabFrames[name] = sf

    btn.MouseButton1Click:Connect(function()
        for n, f in pairs(tabFrames) do f.Visible = (n == name) end
        for n, b in pairs(tabButtons) do
            b.BackgroundColor3 = (n == name) and Color3.fromRGB(60, 20, 90) or Color3.fromRGB(20, 10, 30)
        end
    end)
end
tabButtons["combat"].BackgroundColor3 = Color3.fromRGB(60, 20, 90)

local yPos = { combat=0, troll=0, player=0, visual=0, misc=0, settings=0 }

local function addButton(tab, text, callback)
    local b = Instance.new("TextButton")
    b.Size = UDim2.new(1, -10, 0, 32)
    b.Position = UDim2.new(0, 5, 0, yPos[tab])
    b.BackgroundColor3 = Color3.fromRGB(25, 15, 35)
    b.Text = text
    b.TextColor3 = Color3.fromRGB(230, 230, 230)
    b.Font = Enum.Font.Gotham
    b.TextSize = 13
    b.Parent = tabFrames[tab]
    Instance.new("UICorner", b).CornerRadius = UDim.new(0, 6)
    b.MouseButton1Click:Connect(function() pcall(callback) end)
    yPos[tab] = yPos[tab] + 38
    tabFrames[tab].CanvasSize = UDim2.new(0, 0, 0, yPos[tab] + 10)
    return b
end

local function addToggle(tab, text, callback)
    local state = false
    local b = addButton(tab, text.." [OFF]", function()
        state = not state
        b.Text = text.." ["..(state and T("on") or T("off")).."]"
        b.BackgroundColor3 = state and Color3.fromRGB(60, 20, 90) or Color3.fromRGB(25, 15, 35)
        pcall(callback, state)
    end)
    return b
end

local function addSlider(tab, text, min, max, default, callback)
    local frame = Instance.new("Frame")
    frame.Size = UDim2.new(1, -10, 0, 50)
    frame.Position = UDim2.new(0, 5, 0, yPos[tab])
    frame.BackgroundColor3 = Color3.fromRGB(25, 15, 35)
    frame.Parent = tabFrames[tab]
    Instance.new("UICorner", frame).CornerRadius = UDim.new(0, 6)

    local label = Instance.new("TextLabel")
    label.Size = UDim2.new(1, -10, 0, 20)
    label.Position = UDim2.new(0, 8, 0, 3)
    label.BackgroundTransparency = 1
    label.Text = text..": "..default
    label.TextColor3 = Color3.fromRGB(230, 230, 230)
    label.TextSize = 12
    label.Font = Enum.Font.Gotham
    label.TextXAlignment = Enum.TextXAlignment.Left
    label.Parent = frame

    local bar = Instance.new("Frame")
    bar.Size = UDim2.new(1, -20, 0, 8)
    bar.Position = UDim2.new(0, 10, 0, 30)
    bar.BackgroundColor3 = Color3.fromRGB(40, 20, 50)
    bar.Parent = frame
    Instance.new("UICorner", bar).CornerRadius = UDim.new(0, 4)

    local fill = Instance.new("Frame")
    fill.Size = UDim2.new((default-min)/(max-min), 0, 1, 0)
    fill.BackgroundColor3 = Color3.fromRGB(139, 0, 255)
    fill.Parent = bar
    Instance.new("UICorner", fill).CornerRadius = UDim.new(0, 4)

    local dragging = false
    bar.InputBegan:Connect(function(input)
        if input.UserInputType == Enum.UserInputType.MouseButton1 or input.UserInputType == Enum.UserInputType.Touch then dragging = true end
    end)
    UserInputService.InputEnded:Connect(function(input)
        if input.UserInputType == Enum.UserInputType.MouseButton1 or input.UserInputType == Enum.UserInputType.Touch then dragging = false end
    end)
    UserInputService.InputChanged:Connect(function(input)
        if dragging and (input.UserInputType == Enum.UserInputType.MouseMovement or input.UserInputType == Enum.UserInputType.Touch) then
            local rel = math.clamp((input.Position.X - bar.AbsolutePosition.X) / bar.AbsoluteSize.X, 0, 1)
            local val = math.floor(min + (max-min) * rel)
            fill.Size = UDim2.new(rel, 0, 1, 0)
            label.Text = text..": "..val
            pcall(callback, val)
        end
    end)
    yPos[tab] = yPos[tab] + 56
    tabFrames[tab].CanvasSize = UDim2.new(0, 0, 0, yPos[tab] + 10)
end

-- FITUR COMBAT
addSlider("combat", T("speed"), 16, 500, 16, function(v)
    if LP.Character and LP.Character:FindFirstChildOfClass("Humanoid") then LP.Character:FindFirstChildOfClass("Humanoid").WalkSpeed = v end
end)
addSlider("combat", T("jump"), 50, 500, 50, function(v)
    local h = LP.Character and LP.Character:FindFirstChildOfClass("Humanoid")
    if h then h.JumpPower = v h.UseJumpPower = true end
end)
addButton("combat", T("fling").." (All)", function()
    for _, p in ipairs(Players:GetPlayers()) do
        if p ~= LP and p.Character and p.Character:FindFirstChild("HumanoidRootPart") then
            pcall(function()
                local bv = Instance.new("BodyVelocity")
                bv.Velocity = Vector3.new(math.random(-500,500), 500, math.random(-500,500))
                bv.MaxForce = Vector3.new(1e5, 1e5, 1e5)
                bv.Parent = p.Character.HumanoidRootPart
                Debris:AddItem(bv, 0.5)
            end)
        end
    end
end)

-- FITUR TROLL
local dolphinConn
addToggle("troll", T("dolphin"), function(state)
    if dolphinConn then dolphinConn:Disconnect() dolphinConn = nil end
    if not state then return end
    local target
    for _, p in ipairs(Players:GetPlayers()) do
        if p ~= LP and p.Character and p.Character:FindFirstChild("HumanoidRootPart") then target = p break end
    end
    if not target then return end
    dolphinConn = RunService.Heartbeat:Connect(function()
        pcall(function()
            if target.Character and target.Character:FindFirstChild("HumanoidRootPart") and LP.Character and LP.Character:FindFirstChild("HumanoidRootPart") then
                LP.Character.HumanoidRootPart.CFrame = target.Character.HumanoidRootPart.CFrame * CFrame.new(0, 0, 3)
            end
        end)
    end)
end)

addToggle("troll", T("partspam"), function(state)
    if not state then return end
    task.spawn(function()
        while _G.ZexartV1Loaded do
            pcall(function()
                for _, p in ipairs(Players:GetPlayers()) do
                    if p ~= LP and p.Character and p.Character:FindFirstChild("HumanoidRootPart") then
                        local part = Instance.new("Part")
                        part.Size = Vector3.new(1,1,1) part.Color = Color3.fromRGB(160, 32, 240)
                        part.Material = Enum.Material.Neon part.CanCollide = false
                        part.CFrame = p.Character.HumanoidRootPart.CFrame * CFrame.new(math.random(-5,5), math.random(0,5), math.random(-5,5))
                        part.Parent = Workspace
                        Debris:AddItem(part, 3)
                    end
                end
            end)
            task.wait(0.5)
        end
    end)
end)

addButton("troll", T("bringall"), function()
    if not LP.Character or not LP.Character:FindFirstChild("HumanoidRootPart") then return end
    for _, p in ipairs(Players:GetPlayers()) do
        if p ~= LP and p.Character and p.Character:FindFirstChild("HumanoidRootPart") then
            pcall(function() p.Character.HumanoidRootPart.CFrame = LP.Character.HumanoidRootPart.CFrame * CFrame.new(math.random(-3,3), 0, math.random(-3,3)) end)
        end
    end
end)

-- FITUR PLAYER
local noclipConn
addToggle("player", T("noclip"), function(state)
    if noclipConn then noclipConn:Disconnect() noclipConn = nil end
    if state then
        noclipConn = RunService.Stepped:Connect(function()
            pcall(function()
                if LP.Character then for _, p in ipairs(LP.Character:GetDescendants()) do if p:IsA("BasePart") then p.CanCollide = false end end end
            end)
        end)
    end
end)

addToggle("player", T("esp"), function(state)
    for _, p in ipairs(Players:GetPlayers()) do
        if p ~= LP and p.Character then
            pcall(function()
                local hl = p.Character:FindFirstChild("ZexartESP")
                if state and not hl then
                    local h = Instance.new("Highlight")
                    h.Name = "ZexartESP" h.FillColor = Color3.fromRGB(160, 32, 240)
                    h.Parent = p.Character
                elseif not state and hl then hl:Destroy() end
            end)
        end
    end
end)

-- FITUR VISUAL
addToggle("visual", T("fullbright"), function(state)
    Lighting.Brightness = state and 2 or OrigBrightness
    Lighting.FogEnd = state and 1e6 or OrigFogEnd
end)

-- MISC
addButton("misc", T("rejoin"), function()
    pcall(function() TeleportService:Teleport(game.PlaceId, LP) end)
end)

addButton("misc", T("unload"), function()
    _G.ZexartV1Loaded = false
    pcall(function()
        if OrigSky then OrigSky.Parent = Lighting end
        Lighting.FogEnd = OrigFogEnd
        Lighting.Brightness = OrigBrightness
        Workspace.CurrentCamera.FieldOfView = OrigFOV
        ScreenGui:Destroy()
    end)
    print("[Zexart V1] Unloaded")
end)

-- SETTINGS (Ganti Bahasa)
for _, code in ipairs({"en", "id"}) do
    addButton("settings", T("language")..": "..code:upper(), function()
        currentLang = code
        Title.Text = T("title")
        for _, name in ipairs(tabs) do tabButtons[name].Text = T("tab_"..name) end
    end)
end

-- TOGGLE
local function toggleUI()
    Main.Visible = not Main.Visible
    if Main.Visible then
        Main.Size = UDim2.new(0, 0, 0, 0)
        TweenService:Create(Main, TweenInfo.new(0.3), {Size = UDim2.new(0, 500, 0, 350)}):Play()
    end
end

Toggle.MouseButton1Click:Connect(toggleUI)
CloseBtn.MouseButton1Click:Connect(toggleUI)
UserInputService.InputBegan:Connect(function(input, gp)
    if gp then return end
    if input.KeyCode == Enum.KeyCode.RightShift then toggleUI() end
end)

-- DRAG
local dragging, startPos, startInput
TitleBar.InputBegan:Connect(function(input)
    if input.UserInputType == Enum.UserInputType.MouseButton1 or input.UserInputType == Enum.UserInputType.Touch then
        dragging = true startPos = Main.Position startInput = input.Position
    end
end)
UserInputService.InputChanged:Connect(function(input)
    if dragging and (input.UserInputType == Enum.UserInputType.MouseMovement or input.UserInputType == Enum.UserInputType.Touch) then
        local delta = input.Position - startInput
        Main.Position = UDim2.new(startPos.X.Scale, startPos.X.Offset + delta.X, startPos.Y.Scale, startPos.Y.Offset + delta.Y)
    end
end)
UserInputService.InputEnded:Connect(function(input)
    if input.UserInputType == Enum.UserInputType.MouseButton1 or input.UserInputType == Enum.UserInputType.Touch then dragging = false end
end)

print("[Zexart V1] Loaded ✓")