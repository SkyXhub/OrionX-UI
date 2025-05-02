[GITHUB_README.md](https://github.com/user-attachments/files/20010651/GITHUB_README.md)[Uploadin![OrionX-UI](OrionX-Thumbnail.png)

# OrionX-UI Library
This documentation is for the enhanced modular version of Orion Library.

## Booting the Library
```lua
local OrionLib = loadstring(game:HttpGet(('https://raw.githubusercontent.com/SkyXhub/OrionX-UI/refs/heads/main/OrionX-UI')))() 
```

## Creating a Window
```lua
local Window = OrionLib:MakeWindow({Name = "Title of the library", HidePremium = false, SaveConfig = true, ConfigFolder = "OrionXConfig"})

--[[
Name = <string> - The name of the UI.
HidePremium = <bool> - Whether or not the user details shows Premium status or not.
SaveConfig = <bool> - Toggles the config saving in the UI.
ConfigFolder = <string> - The name of the folder where the configs are saved.
IntroEnabled = <bool> - Whether or not to show the intro animation.
IntroText = <string> - Text to show in the intro animation.
IntroIcon = <string> - URL to the image you want to use in the intro animation.
Icon = <string> - URL to the image you want displayed on the window.
CloseCallback = <function> - Function to execute when the window is closed.
]]
```

## Creating a Tab
```lua
local Tab = Window:MakeTab({
	Name = "Tab 1",
	Icon = "home",
	PremiumOnly = false
})

--[[
Name = <string> - The name of the tab.
Icon = <string> - The icon of the tab. Icons now use names instead of rbxassetid.
PremiumOnly = <bool> - Makes the tab accessible to premium users only.
]]
```

## Creating a Section
```lua
local Section = Tab:AddSection({
	Name = "Section"
})

--[[
Name = <string> - The name of the section.
]]
```
You can add elements to sections the same way you would add them to a tab normally.

## Notifying the user
```lua
OrionLib:MakeNotification({
	Name = "Title!",
	Content = "Notification content... what will it say??",
	Image = "info",
	Time = 5
})

--[[
Title = <string> - The title of the notification.
Content = <string> - The content of the notification.
Image = <string> - The icon of the notification (uses the icon name, not rbxassetid).
Time = <number> - The duration of the notification.
]]
```

## Creating a Button
```lua
Tab:AddButton({
	Name = "Button!",
	Callback = function()
      		print("button pressed")
  	end    
})

--[[
Name = <string> - The name of the button.
Callback = <function> - The function of the button.
]]
```

## Creating a Checkbox toggle
```lua
Tab:AddToggle({
	Name = "This is a toggle!",
	Default = false,
	Callback = function(Value)
		print(Value)
	end    
})

--[[
Name = <string> - The name of the toggle.
Default = <bool> - The default value of the toggle.
Callback = <function> - The function of the toggle.
]]
```

### Changing the value of an existing Toggle
```lua
CoolToggle:Set(true)
```

## Creating a Color Picker
```lua
Tab:AddColorpicker({
	Name = "Colorpicker",
	Default = Color3.fromRGB(255, 0, 0),
	Callback = function(Value)
		print(Value)
	end	  
})

--[[
Name = <string> - The name of the colorpicker.
Default = <color3> - The default value of the colorpicker.
Callback = <function> - The function of the colorpicker.
]]
```

### Setting the color picker's value
```lua
ColorPicker:Set(Color3.fromRGB(255,255,255))
```

## Creating a Slider
```lua
Tab:AddSlider({
	Name = "Slider",
	Min = 0,
	Max = 20,
	Default = 5,
	Color = Color3.fromRGB(255,255,255),
	Increment = 1,
	ValueName = "bananas",
	Callback = function(Value)
		print(Value)
	end    
})

--[[
Name = <string> - The name of the slider.
Min = <number> - The minimal value of the slider.
Max = <number> - The maxium value of the slider.
Increment = <number> - How much the slider will change value when dragging.
Default = <number> - The default value of the slider.
ValueName = <string> - The text after the value number.
Callback = <function> - The function of the slider.
]]
```

### Change Slider Value
```lua
Slider:Set(2)
```
Make sure you make your slider a variable (local CoolSlider = Tab:AddSlider...) for this to work.

## Creating a Label
```lua
Tab:AddLabel("Label")
```

### Changing the value of an existing label
```lua
CoolLabel:Set("Label New!")
```

## Creating a Paragraph
```lua
Tab:AddParagraph("Paragraph","Paragraph Content")
```

### Changing an existing paragraph
```lua
CoolParagraph:Set("Paragraph New!", "New Paragraph Content!")
```

## Creating an Adaptive Input
```lua
Tab:AddTextbox({
	Name = "Textbox",
	Default = "default box input",
	TextDisappear = true,
	Callback = function(Value)
		print(Value)
	end	  
})

--[[
Name = <string> - The name of the textbox.
Default = <string> - The default value of the textbox.
TextDisappear = <bool> - Makes the text disappear in the textbox after losing focus.
Callback = <function> - The function of the textbox.
]]
```

## Creating a Keybind
```lua
Tab:AddBind({
	Name = "Bind",
	Default = Enum.KeyCode.E,
	Hold = false,
	Callback = function()
		print("press")
	end    
})

--[[
Name = <string> - The name of the bind.
Default = <keycode> - The default value of the bind.
Hold = <bool> - Makes the bind work like: Holding the key > The bind returns true, Not holding the key > Bind returns false.
Callback = <function> - The function of the bind.
]]
```

### Changing the value of a bind
```lua
Bind:Set(Enum.KeyCode.E)
```

## Creating a Dropdown menu
```lua
Tab:AddDropdown({
	Name = "Dropdown",
	Default = "1",
	Options = {"1", "2"},
	Callback = function(Value)
		print(Value)
	end    
})

--[[
Name = <string> - The name of the dropdown.
Default = <string> - The default value of the dropdown.
Options = <table> - The options in the dropdown.
Callback = <function> - The function of the dropdown.
]]
```

### Adding a set of new Dropdown buttons to an existing menu
```lua
Dropdown:Refresh(List<table>,true)
```

The above boolean value "true" is whether or not the current buttons will be deleted.

### Selecting a dropdown option
```lua
Dropdown:Set("dropdown option")
```

## Mobile Support (New in OrionX)

OrionX-UI automatically detects mobile devices and enhances the experience with a mobile toggle button.

### Toggling Mobile Button Visibility
```lua
OrionLib.Mobile:SetToggleVisibility(true) -- Show the mobile toggle button
OrionLib.Mobile:SetToggleVisibility(false) -- Hide the mobile toggle button
```

### Setting Mobile Toggle Position
```lua
OrionLib.Mobile:SetTogglePosition("TopRight") -- Can be "TopRight", "TopLeft", "BottomRight", or "BottomLeft"
```

## Theme Customization (New in OrionX)

OrionX-UI includes several built-in themes and the ability to create custom themes.

### Setting a Theme
```lua
OrionLib.Themes:SetTheme("Default") -- Available themes: "Default", "Dark", "Light", "Ocean", "Blood"
```

### Creating a Custom Theme
```lua
OrionLib.Themes:AddTheme("Custom", {
    Main = Color3.fromRGB(40, 40, 70),
    Second = Color3.fromRGB(50, 50, 80),
    Stroke = Color3.fromRGB(80, 80, 110),
    Divider = Color3.fromRGB(80, 80, 110),
    Text = Color3.fromRGB(240, 240, 250),
    TextDark = Color3.fromRGB(170, 170, 190)
})
```

# Finishing your script (REQUIRED)
The below function needs to be added at the end of your code.
```lua
OrionLib:Init()
```

### How flags work.
The flags feature in the UI may be confusing for some people. It serves the purpose of being the ID of an element in the config file, and makes accessing the value of an element anywhere in the code possible.
Below in an example of using flags.
```lua
Tab1:AddToggle({
    Name = "Toggle",
    Default = true,
    Save = true,
    Flag = "toggle"
})

print(OrionLib.Flags["toggle"].Value) -- prints the value of the toggle.
```
Flags only work with the toggle, slider, dropdown, bind, and colorpicker.

### Making your interface work with configs.
In order to make your interface use the configs function you first need to add the `SaveConfig` and `ConfigFolder` arguments to your window function. The explanation of these arguments in above.
Then you need to add the `Flag` and `Save` values to every toggle, slider, dropdown, bind, and colorpicker you want to include in the config file.
The `Flag = <string>` argument is the ID of an element in the config file.
The `Save = <bool>` argument includes the element in the config file.
Config files are made for every game the library is launched in.

## Destroying the Interface
```lua
OrionLib:Destroy()
```

## Offline Mode

OrionX-UI includes a robust fallback mechanism to ensure your scripts work even when GitHub resources aren't available.

```lua
-- Attempt to load from GitHub with local fallback
local OrionLib

local success, result = pcall(function()
    return loadstring(game:HttpGet("https://raw.githubusercontent.com/SkyXhub/OrionX-UI/refs/heads/main/OrionX-UI"))()
end)

if success and result then
    OrionLib = result
else
    warn("Failed to load OrionX from GitHub. Using local fallback.")
    OrionLib = loadstring(readfile("OrionX.lua"))()
end

OrionLib:Init()
```g GITHUB_README.md…]()
