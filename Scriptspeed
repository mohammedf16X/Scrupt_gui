local Players = game:GetService("Players")
local StarterGui = game:GetService("StarterGui")
local UserInputService = game:GetService("UserInputService")
local RunService = game:GetService("RunService")
local player = Players.LocalPlayer
local character = player.Character or player.CharacterAdded:Wait()
local humanoid = character:FindFirstChildOfClass("Humanoid")

if not humanoid then
    warn("⚠️ لا يوجد Humanoid في الشخصية!")
    return
end

-- إرسال إشعار عند بدء التشغيل
StarterGui:SetCore("SendNotification", {
    Title = "🚀 بدء التشغيل!",
    Text = "تم تشغيل السكربت بنجاح! 🎉",
    Duration = 5
})

-- إنشاء واجهة المستخدم
local ScreenGui = Instance.new("ScreenGui")
local MainFrame = Instance.new("Frame")
local LeftFrame = Instance.new("Frame")
local SpeedFrame = Instance.new("Frame")
local JumpFrame = Instance.new("Frame")
local CommandsFrame = Instance.new("Frame")
local HideButton = Instance.new("TextButton")
local ShowButton = Instance.new("TextButton")
local DeleteButton = Instance.new("TextButton")
local PlayerImage = Instance.new("ImageLabel")
local UserLabel = Instance.new("TextLabel")
local CreditLabel = Instance.new("TextLabel")

ScreenGui.Parent = game.CoreGui

-- إعداد التصميم الرئيسي
MainFrame.Size = UDim2.new(0, 600, 0, 400) -- حجم أكبر
MainFrame.Position = UDim2.new(0.5, -300, 0.5, -200)
MainFrame.BackgroundColor3 = Color3.fromRGB(20, 20, 20) -- لون أسود غامق
MainFrame.BackgroundTransparency = 0.2
MainFrame.BorderSizePixel = 2
MainFrame.Parent = ScreenGui

-- إطار القوائم على اليسار
LeftFrame.Size = UDim2.new(0, 120, 0, 400)
LeftFrame.Position = UDim2.new(0, 0, 0, 0)
LeftFrame.BackgroundColor3 = Color3.fromRGB(30, 30, 30) -- لون داكن
LeftFrame.Parent = MainFrame

-- صورة المستخدم
PlayerImage.Size = UDim2.new(0, 60, 0, 60)
PlayerImage.Position = UDim2.new(0, 10, 0, 10) -- أعلى الواجهة
PlayerImage.Image = "rbxthumb://type=AvatarHeadShot&id=" .. player.UserId .. "&w=420&h=420"
PlayerImage.Parent = MainFrame

-- تسمية المستخدم
UserLabel.Size = UDim2.new(0, 300, 0, 30)
UserLabel.Position = UDim2.new(0, 80, 0, 20) -- أعلى الواجهة
UserLabel.Text = "✨ مرحبًا, " .. player.Name .. " ✨"
UserLabel.TextColor3 = Color3.fromRGB(255, 255, 255)
UserLabel.BackgroundTransparency = 1
UserLabel.Parent = MainFrame

-- إطار السرعة
SpeedFrame.Size = UDim2.new(0, 450, 0, 120)
SpeedFrame.Position = UDim2.new(0, 130, 0, 80) -- تحت صورة المستخدم
SpeedFrame.BackgroundColor3 = Color3.fromRGB(40, 40, 40) -- لون داكن
SpeedFrame.Visible = false
SpeedFrame.Parent = MainFrame

local SpeedInput = Instance.new("TextBox")
SpeedInput.Size = UDim2.new(0, 400, 0, 40)
SpeedInput.Position = UDim2.new(0, 25, 0, 10) -- تم تعديل الموضع ليكون في الأعلى
SpeedInput.PlaceholderText = "🚀 أدخل السرعة"
SpeedInput.BackgroundColor3 = Color3.fromRGB(50, 50, 50) -- لون داكن
SpeedInput.TextColor3 = Color3.fromRGB(255, 255, 255)
SpeedInput.Parent = SpeedFrame

local SpeedButton = Instance.new("TextButton")
SpeedButton.Size = UDim2.new(0, 400, 0, 40)
SpeedButton.Position = UDim2.new(0, 25, 0, 60) -- تم تعديل الموضع ليكون تحت TextBox
SpeedButton.Text = "تعيين السرعة"
SpeedButton.BackgroundColor3 = Color3.fromRGB(0, 100, 0) -- لون أخضر داكن
SpeedButton.TextColor3 = Color3.fromRGB(255, 255, 255)
SpeedButton.Parent = SpeedFrame

-- إطار القفز
JumpFrame.Size = UDim2.new(0, 450, 0, 120)
JumpFrame.Position = UDim2.new(0, 130, 0, 80) -- تم تعديل الموضع ليكون في الأعلى
JumpFrame.BackgroundColor3 = Color3.fromRGB(40, 40, 40) -- لون داكن
JumpFrame.Visible = false
JumpFrame.Parent = MainFrame

local JumpInput = Instance.new("TextBox")
JumpInput.Size = UDim2.new(0, 400, 0, 40)
JumpInput.Position = UDim2.new(0, 25, 0, 10) -- تم تعديل الموضع ليكون في الأعلى
JumpInput.PlaceholderText = "🦘 أدخل القفز"
JumpInput.BackgroundColor3 = Color3.fromRGB(50, 50, 50) -- لون داكن
JumpInput.TextColor3 = Color3.fromRGB(255, 255, 255)
JumpInput.Parent = JumpFrame

local JumpButton = Instance.new("TextButton")
JumpButton.Size = UDim2.new(0, 400, 0, 40)
JumpButton.Position = UDim2.new(0, 25, 0, 60) -- تم تعديل الموضع ليكون تحت TextBox
JumpButton.Text = "تعيين القفز"
JumpButton.BackgroundColor3 = Color3.fromRGB(150, 75, 0) -- لون برتقالي داكن
JumpButton.TextColor3 = Color3.fromRGB(255, 255, 255)
JumpButton.Parent = JumpFrame

-- إطار الأوامر
CommandsFrame.Size = UDim2.new(0, 450, 0, 180)
CommandsFrame.Position = UDim2.new(0, 130, 0, 80) -- تم تعديل الموضع ليكون في الأعلى
CommandsFrame.BackgroundColor3 = Color3.fromRGB(40, 40, 40) -- لون داكن
CommandsFrame.Visible = false
CommandsFrame.Parent = MainFrame

local DetectPlayersButton = Instance.new("TextButton")
DetectPlayersButton.Size = UDim2.new(0, 400, 0, 40)
DetectPlayersButton.Position = UDim2.new(0, 25, 0, 10) -- تم تعديل الموضع ليكون في الأعلى
DetectPlayersButton.Text = "👥 كشف اللاعبين"
DetectPlayersButton.BackgroundColor3 = Color3.fromRGB(0, 75, 150) -- لون أزرق داكن
DetectPlayersButton.TextColor3 = Color3.fromRGB(255, 255, 255)
DetectPlayersButton.Parent = CommandsFrame

local FlyButtonMobile = Instance.new("TextButton")
FlyButtonMobile.Size = UDim2.new(0, 400, 0, 40)
FlyButtonMobile.Position = UDim2.new(0, 25, 0, 60) -- تم تعديل الموضع ليكون تحت الزر السابق
FlyButtonMobile.Text = "🕊️ طيران للجوال"
FlyButtonMobile.BackgroundColor3 = Color3.fromRGB(150, 0, 0) -- لون أحمر داكن
FlyButtonMobile.TextColor3 = Color3.fromRGB(255, 255, 255)
FlyButtonMobile.Parent = CommandsFrame

local FlyButtonPC = Instance.new("TextButton")
FlyButtonPC.Size = UDim2.new(0, 400, 0, 40)
FlyButtonPC.Position = UDim2.new(0, 25, 0, 110) -- تم تعديل الموضع ليكون تحت الزر السابق
FlyButtonPC.Text = "🕊️ طيران للكمبيوتر (G)"
FlyButtonPC.BackgroundColor3 = Color3.fromRGB(150, 0, 0) -- لون أحمر داكن
FlyButtonPC.TextColor3 = Color3.fromRGB(255, 255, 255)
FlyButtonPC.Parent = CommandsFrame

-- زر الإخفاء
HideButton.Size = UDim2.new(0, 100, 0, 40)
HideButton.Position = UDim2.new(0, 10, 0, 80) -- تحت صورة المستخدم
HideButton.Text = "🔽 إخفاء"
HideButton.BackgroundColor3 = Color3.fromRGB(255, 165, 0) -- لون برتقالي
HideButton.TextColor3 = Color3.fromRGB(255, 255, 255)
HideButton.Parent = LeftFrame

-- زر الإظهار (بدلاً من العين الضاحكة)
ShowButton.Size = UDim2.new(0, 100, 0, 40)
ShowButton.Position = UDim2.new(0, 10, 0, 130) -- تحت زر الإخفاء
ShowButton.Text = "Open"
ShowButton.BackgroundColor3 = Color3.fromRGB(0, 50, 100) -- لون أزرق غامق
ShowButton.TextColor3 = Color3.fromRGB(255, 255, 255)
ShowButton.Visible = false
ShowButton.Parent = ScreenGui

-- زر الحذف
DeleteButton.Size = UDim2.new(0, 100, 0, 40)
DeleteButton.Position = UDim2.new(0, 10, 0, 180) -- تحت زر الإظهار
DeleteButton.Text = "❌ حذف"
DeleteButton.BackgroundColor3 = Color3.fromRGB(255, 0, 0) -- لون أحمر
DeleteButton.TextColor3 = Color3.fromRGB(255, 255, 255)
DeleteButton.Parent = LeftFrame

-- حقوق المطور
CreditLabel.Size = UDim2.new(0, 300, 0, 30)
CreditLabel.Position = UDim2.new(0, 10, 0, 360) -- أسفل الواجهة
CreditLabel.Text = "📌 تم التطوير بواسطة SP_HUB ✅"
CreditLabel.TextColor3 = Color3.fromRGB(0, 255, 0) -- لون أخضر
CreditLabel.BackgroundTransparency = 1
CreditLabel.Parent = MainFrame

-- تفعيل القوائم
local function toggleSpeedMenu()
    SpeedFrame.Visible = not SpeedFrame.Visible
    JumpFrame.Visible = false
    CommandsFrame.Visible = false
end

local function toggleJumpMenu()
    JumpFrame.Visible = not JumpFrame.Visible
    SpeedFrame.Visible = false
    CommandsFrame.Visible = false
end

local function toggleCommandsMenu()
    CommandsFrame.Visible = not CommandsFrame.Visible
    SpeedFrame.Visible = false
    JumpFrame.Visible = false
end

local SpeedMenuButton = Instance.new("TextButton")
SpeedMenuButton.Size = UDim2.new(0, 100, 0, 40)
SpeedMenuButton.Position = UDim2.new(0, 10, 0, 230) -- تحت زر الحذف
SpeedMenuButton.Text = "🚀 السرعة"
SpeedMenuButton.BackgroundColor3 = Color3.fromRGB(0, 150, 0) -- لون أخضر داكن
SpeedMenuButton.TextColor3 = Color3.fromRGB(255, 255, 255)
SpeedMenuButton.Parent = LeftFrame
SpeedMenuButton.MouseButton1Click:Connect(toggleSpeedMenu)

local JumpMenuButton = Instance.new("TextButton")
JumpMenuButton.Size = UDim2.new(0, 100, 0, 40)
JumpMenuButton.Position = UDim2.new(0, 10, 0, 280) -- تحت زر السرعة
JumpMenuButton.Text = "🦘 القفز"
JumpMenuButton.BackgroundColor3 = Color3.fromRGB(200, 100, 0) -- لون برتقالي داكن
JumpMenuButton.TextColor3 = Color3.fromRGB(255, 255, 255)
JumpMenuButton.Parent = LeftFrame
JumpMenuButton.MouseButton1Click:Connect(toggleJumpMenu)

local CommandsMenuButton = Instance.new("TextButton")
CommandsMenuButton.Size = UDim2.new(0, 100, 0, 40)
CommandsMenuButton.Position = UDim2.new(0, 10, 0, 330) -- تحت زر القفز
CommandsMenuButton.Text = "⚙️ الأوامر"
CommandsMenuButton.BackgroundColor3 = Color3.fromRGB(0, 100, 200) -- لون أزرق داكن
CommandsMenuButton.TextColor3 = Color3.fromRGB(255, 255, 255)
CommandsMenuButton.Parent = LeftFrame
CommandsMenuButton.MouseButton1Click:Connect(toggleCommandsMenu)

-- تعيين السرعة
local speedValue = 16 -- السرعة الافتراضية
local isSpeedActive = false

local function setSpeed()
    if player.Character and player.Character:FindFirstChild("Humanoid") then
        player.Character.Humanoid.WalkSpeed = speedValue
    end
end

SpeedButton.MouseButton1Click:Connect(function()
    speedValue = tonumber(SpeedInput.Text) or 16
    isSpeedActive = not isSpeedActive
    if isSpeedActive then
        setSpeed()
        SpeedButton.Text = "إيقاف السرعة"
        SpeedButton.BackgroundColor3 = Color3.fromRGB(200, 0, 0) -- لون أحمر
    else
        if player.Character and player.Character:FindFirstChild("Humanoid") then
            player.Character.Humanoid.WalkSpeed = 16 -- العودة للوضع الطبيعي
        end
        SpeedButton.Text = "تعيين السرعة"
        SpeedButton.BackgroundColor3 = Color3.fromRGB(0, 150, 0) -- لون أخضر داكن
    end
end)

-- إعادة تعيين السرعة بعد الموت
player.CharacterAdded:Connect(function()
    if isSpeedActive then
        wait(1) -- انتظار تحميل الشخصية
        setSpeed()
    end
end)

-- تعيين القفز
local function setJump(jump)
    if jump and jump > 0 then
        humanoid.JumpPower = jump
        StarterGui:SetCore("SendNotification", {
            Title = "🦘 القفز!",
            Text = "تم تعيين القفز إلى " .. jump .. "! 🎉",
            Duration = 5
        })
    else
        warn("⚠️ يرجى إدخال رقم صحيح للقفز!")
    end
end

JumpButton.MouseButton1Click:Connect(function()
    local jump = tonumber(JumpInput.Text)
    setJump(jump)
end)

-- جعل القفز ثابتًا حتى بعد الموت
player.CharacterAdded:Connect(function()
    local jump = tonumber(JumpInput.Text)
    if jump and jump > 0 then
        setJump(jump)
    end
end)

-- كشف اللاعبين
local function highlightPlayer(player)
    local function onCharacterAdded(character)
        local head = character:WaitForChild("Head", 5) -- انتظار الرأس حتى يظهر
        if head and not head:FindFirstChild("NameTag") then
            -- إنشاء اللافتة فوق الرأس
            local billboard = Instance.new("BillboardGui")
            billboard.Name = "NameTag"
            billboard.Size = UDim2.new(0, 100, 0, 20) -- حجم صغير
            billboard.StudsOffset = Vector3.new(0, 2, 0) -- ارتفاع فوق الرأس
            billboard.AlwaysOnTop = true
            billboard.Adornee = head
            billboard.Parent = head

            -- إضافة النص
            local textLabel = Instance.new("TextLabel")
            textLabel.Size = UDim2.new(1, 0, 1, 0)
            textLabel.BackgroundTransparency = 1
            textLabel.Text = player.Name
            textLabel.TextColor3 = Color3.fromRGB(0, 150, 0) -- أخضر غامق
            textLabel.TextStrokeColor3 = Color3.fromRGB(0, 0, 139) -- إطار أزرق غامق
            textLabel.TextStrokeTransparency = 0
            textLabel.TextScaled = true
            textLabel.Font = Enum.Font.SourceSansBold
            textLabel.Parent = billboard
        end
    end

    -- تفعيل الكشف عند تغيير الشخصية (بعد الموت أو إعادة الدخول)
    player.CharacterAdded:Connect(onCharacterAdded)

    -- إذا كان لديه شخصية بالفعل، يتم تفعيل الكشف مباشرة
    if player.Character then
        onCharacterAdded(player.Character)
    end
end

local function highlightAllPlayers()
    for _, player in pairs(game.Players:GetPlayers()) do
        highlightPlayer(player)
    end
end

-- تفعيل الكشف عند الضغط على الزر
DetectPlayersButton.MouseButton1Click:Connect(function()
    highlightAllPlayers()
    StarterGui:SetCore("SendNotification", {
        Title = "👥 كشف اللاعبين!",
        Text = "تم تفعيل الكشف عن اللاعبين! 🎉",
        Duration = 5
    })
end)

-- تفعيل الطيران للجوال
FlyButtonMobile.MouseButton1Click:Connect(function()
    loadstring(game:HttpGet("https://raw.githubusercontent.com/ahmidd409/Orion/refs/heads/main/%D8%B3%D9%83%D8%B1%D8%A8%D8%AA%20%D8%B7%D9%8A%D8%B1%D8%A7%D9%86"))()
end)

-- تفعيل الطيران للكمبيوتر
local flying = false
local flySpeed = 50
local bodyGyro = Instance.new("BodyGyro")
local bodyVelocity = Instance.new("BodyVelocity")

local function startFlying()
    bodyGyro.Parent = character.PrimaryPart
    bodyVelocity.Parent = character.PrimaryPart
    bodyGyro.maxTorque = Vector3.new(math.huge, math.huge, math.huge)
    bodyGyro.cframe = character.PrimaryPart.CFrame
    bodyVelocity.velocity = Vector3.new(0, 0, 0)
    bodyVelocity.maxForce = Vector3.new(math.huge, math.huge, math.huge)
end

local function stopFlying()
    bodyGyro:Destroy()
    bodyVelocity:Destroy()
end

FlyButtonPC.MouseButton1Click:Connect(function()
    flying = not flying
    if flying then
        startFlying()
        FlyButtonPC.Text = "🕊️ إيقاف الطيران (G)"
    else
        stopFlying()
        FlyButtonPC.Text = "🕊️ تفعيل الطيران (G)"
    end
end)

UserInputService.InputBegan:Connect(function(input, gameProcessed)
    if flying and not gameProcessed then
        if input.KeyCode == Enum.KeyCode.Space then
            bodyVelocity.velocity = Vector3.new(0, flySpeed, 0)
        elseif input.KeyCode == Enum.KeyCode.LeftShift then
            bodyVelocity.velocity = Vector3.new(0, -flySpeed, 0)
        end
    end
end)

-- زر الإخفاء
HideButton.MouseButton1Click:Connect(function()
    MainFrame.Visible = false
    ShowButton.Visible = true
end)

-- زر الإظهار
ShowButton.MouseButton1Click:Connect(function()
    MainFrame.Visible = true
    ShowButton.Visible = false
end)

-- زر الحذف
DeleteButton.MouseButton1Click:Connect(function()
    ScreenGui:Destroy()
    StarterGui:SetCore("SendNotification", {
        Title = "❌ الحذف!",
        Text = "تم حذف الواجهة بنجاح! 🎉",
        Duration = 5
    })
end)

-- جعل القائمة قابلة للسحب والإفلات
local dragging = false
local dragInput, dragStart, startPos

local function updateInput(input)
    local delta = input.Position - dragStart
    MainFrame.Position = UDim2.new(startPos.X.Scale, startPos.X.Offset + delta.X, startPos.Y.Scale, startPos.Y.Offset + delta.Y)
end

MainFrame.InputBegan:Connect(function(input)
    if input.UserInputType == Enum.UserInputType.MouseButton1 or input.UserInputType == Enum.UserInputType.Touch then
        dragging = true
        dragStart = input.Position
        startPos = MainFrame.Position
        input.Changed:Connect(function()
            if input.UserInputState == Enum.UserInputState.End then
                dragging = false
            end
        end)
    end
end)

MainFrame.InputChanged:Connect(function(input)
    if input.UserInputType == Enum.UserInputType.MouseMovement or input.UserInputType == Enum.UserInputType.Touch then
        dragInput = input
    end
end)

UserInputService.InputChanged:Connect(function(input)
    if dragging and (input == dragInput) then
        updateInput(input)
    end
end)
