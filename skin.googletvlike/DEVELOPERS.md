# GoogleTV Like Skin - Developer Guide

## Overview

This guide explains how to develop, customize, and extend the GoogleTV Like skin for Kodi.

## Architecture

### Directory Structure

```
skin.googletvlike/
├── addon.xml                    # Addon metadata and requirements
├── changelog.txt               # Version history
├── LICENSE.txt                 # License information
├── README.md                   # User documentation
├── DEVELOPERS.md               # This file
├── resources/
│   ├── skins/
│   │   └── default/
│   │       ├── 1080i/         # 1920x1080 layouts
│   │       │   ├── Home.xml
│   │       │   ├── DialogProgress.xml
│   │       │   ├── DialogSelect.xml
│   │       │   ├── DialogInfo.xml
│   │       │   ├── Settings.xml
│   │       │   └── ...
│   │       ├── 720p/          # 1280x720 layouts
│   │       │   ├── Home.xml
│   │       │   └── ...
│   │       ├── colors/
│   │       │   └── default.xml
│   │       └── fonts/
│   │           └── fonts.xml
│   ├── media/                 # Images, icons, textures
│   │   ├── icon.png          # Addon icon
│   │   ├── fanart.jpg        # Background image
│   │   ├── screenshots/      # Screenshot images
│   │   └── textures/         # UI element textures
│   └── language/
│       └── English/
│           └── strings.po     # Localization strings
└── python/
    └── default.py            # Main skin script (optional)
```

## XML Layout System

### Window Types

Kodi supports several window types:

- `window type="home"` - Main home screen (Window ID 0)
- `window type="dialog"` - Dialog boxes
- `window type="fullscreenvideo"` - Video playback overlay (Window ID 12)
- `window type="fullscreenmusic"` - Music playback overlay (Window ID 13)

### Control Types

Common Kodi control types used in this skin:

#### Label
```xml
<control type="label" id="1">
  <posx>10</posx>
  <posy>10</posy>
  <width>200</width>
  <height>30</height>
  <font>HeadlineSmall</font>
  <textcolor>text_primary</textcolor>
  <label>Text content</label>
</control>
```

#### Button
```xml
<control type="button" id="2">
  <posx>10</posx>
  <posy>50</posy>
  <width>200</width>
  <height>40</height>
  <font>BodyLarge</font>
  <textcolor>text_primary</textcolor>
  <label>Click me</label>
  <onclick>SendClick(5)</onclick>
</control>
```

#### Image
```xml
<control type="image">
  <posx>10</posx>
  <posy>100</posy>
  <width>300</width>
  <height>300</height>
  <texture>path/to/image.png</texture>
  <aspectratio>keep</aspectratio>
</control>
```

#### List/Container
```xml
<control type="list" id="3">
  <posx>10</posx>
  <posy>10</posy>
  <width>400</width>
  <height>600</height>
  <pagecontrol>13</pagecontrol>
  
  <itemlayout height="50">
    <!-- Item layout when not focused -->
  </itemlayout>
  
  <focusedlayout height="50">
    <!-- Item layout when focused -->
  </focusedlayout>
</control>
```

## Color System

### Using Colors

Colors are defined in `colors/default.xml` and referenced in layouts:

```xml
<textcolor>primary_blue</textcolor>
<texture colordiffuse="surface">-</texture>
```

### ARGB Format

Colors use ARGB (Alpha, Red, Green, Blue) format:

```
FF4285F4
├─ FF = Alpha (opacity) - FF is fully opaque
├─ 42 = Red
├─ 85 = Green
└─ F4 = Blue
```

### Custom Colors

To add a new color, edit `colors/default.xml`:

```xml
<color name="my_custom_color">FFRRGGBB</color>
```

Then use it in your layouts:

```xml
<textcolor>my_custom_color</textcolor>
```

## Font System

### Defining Fonts

Edit `fonts/fonts.xml` to add or modify fonts:

```xml
<font>
  <name>MyCustomFont</name>
  <size>24</size>
  <filename>Arial.ttf</filename>
  <style>bold</style>
</font>
```

### Using Fonts

Reference fonts in your layouts:

```xml
<font>HeadlineSmall</font>
```

### Supported Font Styles

- `bold` - Bold text
- `italic` - Italic text
- `light` - Light weight

## Positioning and Sizing

### Coordinate System

- Origin (0,0) is at the top-left
- X increases to the right
- Y increases downward

### Common Screen Sizes

- **1080p**: 1920 x 1080
- **720p**: 1280 x 720

### Responsive Positioning

For responsive layouts, use proportional calculations:

```
1080p width = 1920
1080p content width = 1920 - (40 * 2) = 1840

Percentage at 1080p: 1840 / 1920 = 95.8%
```

## Creating New Layouts

### Step 1: Create the XML File

Create a new file in `resources/skins/default/1080i/`:

```xml
<?xml version="1.0" encoding="UTF-8"?>
<window type="home" id="0">
  <backgroundcolor>background_dark</backgroundcolor>
  
  <!-- Your layout here -->
</window>
```

### Step 2: Add to Both Resolutions

Create a corresponding file in `resources/skins/default/720p/` with scaled dimensions.

### Step 3: Add Localization Strings

Update `language/English/strings.po`:

```
msgctxt "#31100"
msgid "My New Feature"
msgstr ""
```

### Step 4: Test

1. Save the file
2. Restart Kodi
3. Check logs in Settings → System → Debug Log

## Working with Textures

### Texture Requirements

- **Format**: PNG, JPG, JPEG, GIF, or WEBP
- **Location**: `resources/media/`
- **Naming**: Use descriptive names (e.g., `button_bg.png`)

### Using Textures

```xml
<texture>resources/media/button_bg.png</texture>

<!-- With color overlay -->
<texture colordiffuse="primary_blue">resources/media/button_bg.png</texture>

<!-- With border -->
<texture border="10">resources/media/button_bg.png</texture>
```

### Creating Focus Indicators

Use `colordiffuse` to change appearance on focus:

```xml
<control type="button" id="5">
  <texture colordiffuse="surface_variant">button_bg.png</texture>
  <focusedtexture colordiffuse="primary_blue">button_bg.png</focusedtexture>
</control>
```

## Localization (i18n)

### String Format

Strings are stored in `.po` files (GNU gettext format):

```
msgctxt "#31000"
msgid "English Text"
msgstr ""
```

### String IDs

- `#31000 - #31999`: Skin-specific strings
- IDs in this range are reserved for skin developers

### Adding New Languages

1. Create a new folder: `language/[LanguageCode]/`
2. Copy `strings.po` to the new folder
3. Translate all strings (msgstr fields)

Example: `language/Spanish/strings.po`

### Using Strings in Layouts

```xml
<label>$LOCALIZE(31001)</label>
```

## Skin Properties and Settings

### Skin Strings

Define custom settings:

```xml
<skin>
  <setting id="Feature1" type="bool" default="true">
    <label>31050</label>
  </setting>
</skin>
```

### Using Skin Strings

```xml
<label>$INFO[Skin.String(Feature1)]</label>
```

## Information Tags (InfoLabels)

Common Kodi information tags:

```
$INFO[System.Time]           # Current time
$INFO[System.Date]           # Current date
$INFO[ListItem.Title]        # Current list item title
$INFO[ListItem.Plot]         # Current list item plot
$INFO[ListItem.Art(thumb)]   # Current list item thumbnail
```

## Testing and Debugging

### Enable Debug Logging

1. Settings → System → Logging
2. Enable "Log to file"
3. Enable "Components → GUI" for detailed info

### Check Kodi Log

- **Windows**: `%APPDATA%\Kodi\kodi.log`
- **macOS**: `~/Library/Logs/kodi.log`
- **Linux**: `~/.kodi/temp/kodi.log`

### Common Issues

#### XML Parse Errors
- Check for missing closing tags
- Verify attribute syntax
- Use an XML validator

#### Colors Not Displaying
- Ensure color names exist in `colors/default.xml`
- Check ARGB format (should be 8 hex digits)

#### Fonts Not Loading
- Verify font files exist on system
- Check font filename in fonts.xml
- Use fallback fonts for compatibility

## Advanced Features

### Animations

Add animations to controls:

```xml
<control type="button" id="5">
  <animation type="Focus">
    <effect type="scale" start="100" end="110" tween="back" time="200"/>
    <effect type="fade" start="100" end="255" tween="back" time="200"/>
  </animation>
</control>
```

### Conditions

Use conditions to show/hide content:

```xml
<visible>IntegerGreaterThan(ListItem.Index,0)</visible>
<visible>IsEmpty(ListItem.Title)</visible>
<visible>Player.Playing</visible>
```

### Onclick Actions

Navigate and perform actions:

```xml
<onclick>SendClick(5)</onclick>
<onclick>PlayMedia()</onclick>
<onclick>Quit</onclick>
<onclick>ActivateWindow(Settings)</onclick>
```

## Performance Optimization

### Tips

1. **Minimize Textures**: Use smaller image files
2. **Optimize XML**: Remove unnecessary controls
3. **Use Conditions**: Show/hide elements conditionally
4. **Cache Images**: Let Kodi cache textures
5. **Limit Animations**: Keep animations brief and simple

### Profiling

Use Kodi's built-in profiler:
1. Enable debug logging
2. Check log for frame render times
3. Look for slow controls or animations

## Version Compatibility

### Kodi Version Support

This skin targets:
- **Minimum**: Kodi 19.0 (Matrix)
- **Tested**: Kodi 19.x, 20.x
- **GUI Framework**: 5.15.0+

### API Changes

Check [Kodi Wiki - Skin Development](https://kodi.wiki/view/Skin_development) for API changes between versions.

## Contributing

### Code Style

- Use consistent indentation (2 spaces)
- Keep control IDs organized in groups of 100
- Use descriptive names for custom colors/fonts

### Commit Message Format

```
[Feature/Fix/Docs] Brief description

Detailed explanation of changes...
```

### Pull Request Process

1. Fork the repository
2. Create a feature branch
3. Make changes with commits
4. Test thoroughly
5. Submit pull request with description

## Resources

### Official Documentation
- [Kodi Skin Development](https://kodi.wiki/view/Skin_development)
- [Kodi XML Format](https://kodi.wiki/view/XML_formatting)
- [Kodi Controls](https://kodi.wiki/view/Window_controls)

### Related Projects
- [Official Kodi Skins](https://github.com/xbmc/skins)
- [Skin Development Tools](https://github.com/kodi-addons/skin-dev-tools)

### Community
- [Kodi Forums](https://forum.kodi.tv/)
- [Skin Development Section](https://forum.kodi.tv/forumdisplay.php?fid=67)

## License

This skin is released under the GNU General Public License v2.0.
Contributions must also be licensed under GPL-2.0.

---

**Last Updated**: 2026
**Version**: 1.0.0
