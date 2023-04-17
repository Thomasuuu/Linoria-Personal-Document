
# My Personal Linoria UI document

I DO NOT OWN ANY OF THE UI, ALL THE CREDIT GOES TO THE CREATOR OF LINORIA UI


## Load a string
```local repo = 'https://raw.githubusercontent.com/wally-rblx/LinoriaLib/main/'
local Library = loadstring(game:HttpGet(repo .. 'Library.lua'))()
local ThemeManager = loadstring(game:HttpGet(repo .. 'addons/ThemeManager.lua'))()
local SaveManager = loadstring(game:HttpGet(repo .. 'addons/SaveManager.lua'))()
```
## Add a Window
```
local Window = Library:CreateWindow({

    Title = 'Zenith Hub:discord.gg/fSkWXPC74p',
    Center = true,
    AutoShow = true,
})
```
## Add A Tab
```
local Tabs = {
    Main = Window:AddTab('Main'), 
    ['UI Settings'] = Window:AddTab('UI Settings'),
}
```
## Define a group box side
```
local LeftGroupBox = Tabs.Main:AddLeftGroupbox('Groupbox')
```
## Add a toggle
```
# add a toggle
Toggles.MyToggle:OnChanged(function()
    _G.yoyo = Toggles.MyToggle.Value
    yoyo()
end)

Toggles.MyToggle:SetValue(false)
```
## Add a button
```
local MyButton = LeftGroupBox:AddButton('Button', function()
    print('You clicked a button!')
end)
```
## Add a Slider
```
LeftGroupBox:AddSlider('MySlider', {
    Text = 'This is my slider!',

    Default = 16,
    Min = 0,
    Max = 1000,
    Rounding = 1,

    Compact = false,
})

local Number = Options.MySlider.Value
Options.MySlider:OnChanged(function()
    print('MySlider was changed! New value:', Options.MySlider.Value)
end)
```
## Add a Textbox
```
LeftGroupBox:AddInput('MyTextbox', {
    Default = 'My textbox!',
    Numeric = false,
    Finished = false,

    Text = 'This is a textbox',
    Tooltip = 'This is a tooltip',

    Placeholder = 'Placeholder text',
})

Options.MyTextbox:OnChanged(function()
    print('Text updated. New text:', Options.MyTextbox.Value)
end)
```
## Add a dropdown
```
LeftGroupBox:AddInput('MyTextbox', {
    Default = 'My textbox!',
    Numeric = false,
    Finished = false,

    Text = 'This is a textbox',
    Tooltip = 'This is a tooltip',

    Placeholder = 'Placeholder text',
})

Options.MyTextbox:OnChanged(function()
    print('Text updated. New text:', Options.MyTextbox.Value)
end)
```
## Add a label
```
LeftGroupBox:AddLabel('This is a label')
```
## Add a divider
```
LeftGroupBox:AddDivider()
```
## Add a watermark
```
Library:SetWatermarkVisibility(true)
Library:SetWatermark('This is a really long watermark to text the resizing')
```
## Unload Button
```
Library:OnUnload(function()
    print('Unloaded!')
    Library.Unloaded = true
end)
```
## UI Setting
```
local MenuGroup = Tabs['UI Settings']:AddLeftGroupbox('Menu')
```
## Last Step
```
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
```
