# Linoria-Personal-Document

--load a string--
local repo = 'https://raw.githubusercontent.com/wally-rblx/LinoriaLib/main/'

local Library = loadstring(game:HttpGet(repo .. 'Library.lua'))()
local ThemeManager = loadstring(game:HttpGet(repo .. 'addons/ThemeManager.lua'))()
local SaveManager = loadstring(game:HttpGet(repo .. 'addons/SaveManager.lua'))()
------------------

--add window--
local Window = Library:CreateWindow({

    Title = 'Zenith Hub:discord.gg/fSkWXPC74p',
    Center = true,
    AutoShow = true,
})
--------------

--add tab--
local Tabs = {
    Main = Window:AddTab('Main'), 
    ['UI Settings'] = Window:AddTab('UI Settings'),
}
-----------

--define groupbox--

LeftGroupBox:AddToggle('MyToggle', {
    Text = 'This is a toggle',
    Default = false,
    Tooltip = 'This is a tooltip',
})
-------------------

--add toggle--

Toggles.MyToggle:OnChanged(function()
    _G.yoyo = Toggles.MyToggle.Value
    yoyo()
end)

Toggles.MyToggle:SetValue(false)
--------------

--add button--
local MyButton = LeftGroupBox:AddButton('Button', function()
    print('You clicked a button!')
end)
-------------

--add sub button--
local MyButton2 = MyButton:AddButton('Sub button', function()
    print('You clicked a sub button!')
end)
------------------

--label button--
MyButton:AddTooltip('This is a button')
----------------

--add label--
LeftGroupBox:AddLabel('This is a label')
LeftGroupBox:AddLabel('This is a label\n\nwhich wraps its text!', true)
-------------

--divider--
LeftGroupBox:AddDivider()
-----------

--watermark--
Library:SetWatermarkVisibility(true)
Library:SetWatermark('This is a really long watermark to text the resizing')
-------------

--unload--
Library:OnUnload(function()
    print('Unloaded!')
    Library.Unloaded = true
end)
----------

--ui setting tab--
local MenuGroup = Tabs['UI Settings']:AddLeftGroupbox('Menu')
------------------

--last--
