# Linoria-Personal-Document


# load a string
local repo = 'https://raw.githubusercontent.com/wally-rblx/LinoriaLib/main/'

local Library = loadstring(game:HttpGet(repo .. 'Library.lua'))()
local ThemeManager = loadstring(game:HttpGet(repo .. 'addons/ThemeManager.lua'))()
local SaveManager = loadstring(game:HttpGet(repo .. 'addons/SaveManager.lua'))()

# add a window
local Window = Library:CreateWindow({

    Title = 'Zenith Hub:discord.gg/fSkWXPC74p',
    Center = true,
    AutoShow = true,
})

# add a tab
local Tabs = {
    Main = Window:AddTab('Main'), 
    ['UI Settings'] = Window:AddTab('UI Settings'),
}

# define group box

LeftGroupBox:AddToggle('MyToggle', {
    Text = 'This is a toggle',
    Default = false,
    Tooltip = 'This is a tooltip',
})

# add a toggle
Toggles.MyToggle:OnChanged(function()
    _G.yoyo = Toggles.MyToggle.Value
    yoyo()
end)

Toggles.MyToggle:SetValue(false)

# add a button
local MyButton = LeftGroupBox:AddButton('Button', function()
    print('You clicked a button!')
end)

# add a sub button
local MyButton2 = MyButton:AddButton('Sub button', function()
    print('You clicked a sub button!')
end)

# add a label
LeftGroupBox:AddLabel('This is a label')
LeftGroupBox:AddLabel('This is a label\n\nwhich wraps its text!', true)

# add a divider
LeftGroupBox:AddDivider()

# add a watermark
Library:SetWatermarkVisibility(true)
Library:SetWatermark('This is a really long watermark to text the resizing')

# unload button
Library:OnUnload(function()
    print('Unloaded!')
    Library.Unloaded = true
end)

# ui setting tab
local MenuGroup = Tabs['UI Settings']:AddLeftGroupbox('Menu')

# last step
MenuGroup:AddButton('Unload', function() Library:Unload() end)
MenuGroup:AddLabel('Menu bind'):AddKeyPicker('MenuKeybind', { Default = 'RightControl', NoUI = true, Text = 'Menu keybind' }) 

Library.ToggleKeybind = Options.MenuKeybind

ThemeManager:SetLibrary(Library)
SaveManager:SetLibrary(Library)

SaveManager:IgnoreThemeSettings() 

SaveManager:SetIgnoreIndexes({ 'MenuKeybind' }) 

ThemeManager:SetFolder('Zenith Hub')
SaveManager:SetFolder('Zenith Hub/Project Mugetsu')

SaveManager:BuildConfigSection(Tabs['UI Settings']) 

ThemeManager:ApplyToTab(Tabs['UI Settings'])
