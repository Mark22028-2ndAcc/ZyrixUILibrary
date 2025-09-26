# ZyrixUI Sample Usage Guide

Assume the library is loaded as `local ZyrixUI = loadstring(game:HttpGet("https://raw.githubusercontent.com/Mark22028-2ndAcc/ZyrixUILibrary/refs/heads/main/ZyrixUILibraryTest.lua"))()`

## Creating a Window

```
local window = ZyrixUI:CreateWindow({
    Title = "My Custom UI",
    Size = UDim2.new(0, 600, 0, 400),
    Position = UDim2.new(0.5, -300, 0.5, -200),
    Resizable = true,
    Minimizable = true,
    Closable = true
})
```

## Adding Tabs to the Window

```
local tab1 = window:CreateTab({
    Name = "General Settings",
    ImageId = "1234567890",
    Tooltip = "Basic configurations",
    premiumOnly = false
})

local tab2 = window:CreateTab({
    Name = "Premium Features",
    ImageId = "0987654321",
    Tooltip = "Exclusive tools",
    premiumOnly = true
})
```

## Creating Sections Within Tabs

```
local section1 = tab1:CreateSection({
    Name = "User Controls",
    Collapsible = true,
    DefaultCollapsed = false,
    premiumOnly = false
})

local premiumSection = tab2:CreateSection({
    Name = "Advanced Tools",
    Collapsible = true,
    DefaultCollapsed = true,
    premiumOnly = true
})
```

## Adding Elements to Sections

### Button Example

```
section1:CreateButton({
    Name = "Click Me",
    Callback = function()
        print("Button clicked!")
    end,
    Icon = "rbxassetid://1234567890",
    Tooltip = "Triggers an action",
    premiumOnly = false
})
```

### Toggle Example

```
section1:CreateToggle({
    Name = "Enable Feature",
    Default = true,
    Callback = function(state)
        print("Toggle state:", state)
    end,
    Tooltip = "Turn on/off",
    premiumOnly = false
})
```

### Slider Example

```
section1:CreateSlider({
    Name = "Volume",
    Min = 0,
    Max = 100,
    Default = 50,
    Step = 5,
    Callback = function(value)
        print("Slider value:", value)
    end,
    Tooltip = "Adjust level",
    premiumOnly = false
})
```

### Textbox Example

```
section1:CreateTextbox({
    Name = "Enter Name",
    Placeholder = "Your name...",
    Callback = function(text)
        print("Entered:", text)
    end,
    Clearable = true,
    Tooltip = "Input text",
    premiumOnly = false
})
```

### Dropdown Example

```
section1:CreateDropdown({
    Name = "Select Option",
    Items = {"Option1", "Option2", "Option3"},
    Default = "Option1",
    MultiSelect = false,
    Search = true,
    Callback = function(selected)
        print("Selected:", selected)
    end,
    Tooltip = "Choose from list",
    premiumOnly = false
})
```

### Colorpicker Example

```
section1:CreateColorpicker({
    Name = "Pick Color",
    Default = Color3.fromRGB(255, 0, 0),
    DefaultAlpha = 1,
    IncludeAlpha = true,
    Callback = function(color, alpha)
        print("Color:", color, "Alpha:", alpha)
    end,
    Tooltip = "Select a color",
    premiumOnly = false
})
```

### Label and Paragraph Examples

```
section1:CreateLabel({
    Text = "Info Label",
    Emphasis = true,
    Icon = "rbxassetid://1234567890",
    Tooltip = "Additional info",
    premiumOnly = false
})

section1:CreateParagraph({
    Text = "Paragraph",
    Font = Enum.Font.Gotham,
    Size = 14,
    premiumOnly = false
})
```

## Notifications and Loading Screens

### Notification Example

```
window:CreateNotification({
    Title = "Hey!",
    Description = "Notif",
    Duration = 5,
    ImageId = "1234567890",
    Callback = function()
        print("Notification closed")
    end
})
```

### Loading Screen Example

```
local loading = ZyrixUI:CreateLoadingScreen("Loading UI", "Please wait...", function()
    return math.random()  -- Progress from 0 to 1
end)

wait(3)
loading:DestroyWithFade()
```

## Theme Customization

Change the UI theme globally:

```
ZyrixUI:SetTheme({
    Accent = Color3.fromRGB(255, 100, 0),  -- Orange accent
    Background = Color3.fromRGB(20, 20, 20)
})
```

## Premium Locking Notes

- For buyers, set `premiumOnly = false` in the options when creating tabs/sections/elements.
- Locked elements show disabled visuals and trigger a notification on interaction.
- This allows easy toggling without code changes.

Library Source Code:
https://raw.githubusercontent.com/Mark22028-2ndAcc/ZyrixUILibrary/refs/heads/main/ZyrixUILibraryTest.lua
