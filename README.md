# 🎮 Obisidian UI Library Documentation
> An advanced and feature-rich UI library for Roblox exploiting, forked from mstudio45's implementation and enhanced by deivid.

## 📑 Table of Contents
- [Features](#-features)
- [Installation](#-installation)
- [Basic Usage](#-basic-usage)
- [Components](#-components)
- [Advanced Features](#-advanced-features)
- [Themes & Saving](#-themes--saving)
- [Examples](#-examples)

## ✨ Features
- **Fully Customizable UI** with support for:
  - Custom window positioning
  - Resizable windows
  - Custom cursor
  - DPI scaling
  - Right/Left notification positioning
  - Keybind system
- **Rich Component Library** including:
  - Toggles with color pickers
  - Sliders
  - Buttons with double-click support
  - Dropdowns (searchable, multi-select)
  - Input fields
  - Key pickers
  - Labels
  - Dividers
- **Advanced Features**:
  - Theme management system
  - Configuration saving/loading
  - Tabbed interface
  - Groupbox organization
  - Key system integration

## 🚀 Installation

1. Include the main library files:
```lua
local repo = "https://raw.githubusercontent.com/deividcomsono/Obsidian/main/"
local Library = loadstring(game:HttpGet(repo .. "Library.lua"))()
local ThemeManager = loadstring(game:HttpGet(repo .. "addons/ThemeManager.lua"))()
local SaveManager = loadstring(game:HttpGet(repo .. "addons/SaveManager.lua"))()
```

2. Initialize basic window:
```lua
local Window = Library:CreateWindow({
    Title = "My Application",
    Footer = "version: 1.0.0",
    Icon = "IconID",
    NotifySide = "Right",
    ShowCustomCursor = true
})
```

## 🔧 Basic Usage

### Creating Tabs & Groups
```lua
-- Create main tabs
local Tabs = {
    Main = Window:AddTab("Main", "user"),
    Settings = Window:AddTab("Settings", "settings")
}

-- Add groupboxes to tabs
local LeftGroup = Tabs.Main:AddLeftGroupbox("Controls")
local RightGroup = Tabs.Main:AddRightGroupbox("Settings")
```

### Adding Basic Components

1. **Toggles**:
```lua
LeftGroup:AddToggle("MyToggle", {
    Text = "Example Toggle",
    Default = false,
    Tooltip = "This is a tooltip",
    Callback = function(Value)
        print("Toggle is now:", Value)
    end
})
```

2. **Sliders**:
```lua
LeftGroup:AddSlider("MySlider", {
    Text = "Example Slider",
    Default = 0,
    Min = 0,
    Max = 100,
    Rounding = 1,
    Compact = false
})
```

3. **Buttons**:
```lua
LeftGroup:AddButton({
    Text = "Click Me",
    Func = function()
        print("Button clicked!")
    end,
    DoubleClick = false
})
```

## 🎨 Advanced Components

### Dropdowns
```lua
LeftGroup:AddDropdown("MyDropdown", {
    Values = { "Option 1", "Option 2", "Option 3" },
    Default = 1,
    Multi = false,
    Text = "Select Option",
    Tooltip = "Choose an option",
    Searchable = true
})
```

### Color Pickers
```lua
LeftGroup:AddLabel("Color"):AddColorPicker("ColorPicker", {
    Default = Color3.new(0, 1, 0),
    Title = "Choose Color",
    Transparency = 0
})
```

### Key Pickers
```lua
LeftGroup:AddLabel("Keybind"):AddKeyPicker("KeyPicker", {
    Default = "MB2",
    SyncToggleState = false,
    Mode = "Toggle",
    Text = "Select Key"
})
```

## 🔐 Key System Integration

```lua
local KeyTab = Window:AddKeyTab("Key System")

-- Add simple key verification
KeyTab:AddKeyBox("MyKey", function(Success, ReceivedKey)
    if Success then
        print("Correct key entered!")
    end
end)
```

## 💾 Saving & Theme Management

### Configure Save Manager
```lua
SaveManager:SetFolder("MyScriptHub")
SaveManager:SetSubFolder("GameName")
SaveManager:BuildConfigSection(Tabs["Settings"])
```

### Setup Theme Manager
```lua
ThemeManager:SetLibrary(Library)
ThemeManager:SetFolder("MyScriptHub")
ThemeManager:ApplyToTab(Tabs["Settings"])
```

## 🎛️ UI Settings

```lua
-- Add UI control options
local MenuGroup = Tabs.Settings:AddLeftGroupbox("Menu")

MenuGroup:AddToggle("KeybindFrame", {
    Text = "Show Keybinds",
    Default = true
})

MenuGroup:AddDropdown("DPIScale", {
    Values = { "100%", "125%", "150%" },
    Default = "100%",
    Text = "DPI Scale"
})
```

## ⚡ Performance Tips

1. **Callback Optimization**:
   - Use `:OnChanged()` instead of inline callbacks
   - Keep callback functions lightweight
   - Avoid heavy computations in UI updates

2. **Memory Management**:
   - Store references to frequently used components
   - Use `Library:Unload()` when cleaning up
   - Properly handle connections and events

## 🚨 Common Pitfalls

1. **Avoid** direct manipulation of UI elements outside their intended methods
2. **Don't** create excessive numbers of components - use scrollable containers
3. **Remember** to handle errors in callbacks to prevent UI crashes

## 🔧 Troubleshooting

If you encounter issues:

1. **UI Not Showing**:
   - Check if `Window:Show()` was called
   - Verify the loading order of scripts
   - Ensure proper game context

2. **Callbacks Not Firing**:
   - Verify callback function syntax
   - Check for scope issues
   - Ensure components are properly initialized

3. **Save System Issues**:
   - Verify folder permissions
   - Check for proper initialization
   - Ensure proper data serialization

## 📚 Additional Resources

- [Original Repository](https://github.com/mstudio45/LinoriaLib)
- [Modified Version](https://github.com/deividcomsono/Obsidian)

## 📝 License

This project is licensed under MIT - see the LICENSE file for details.

---

*For more examples and detailed API documentation, please check the examples folder in the repository.*
