# GoogleTV Like - Kodi Skin

A modern, minimalist Kodi skin inspired by Google TV's clean design language.

## Features

- **Modern Google TV-Inspired Design**: Clean, dark theme with Google's design principles
- **Card-Based Content Layout**: Grid-based presentation of your media library
- **Google Material Design**: Uses Material Design 3 typography and color system
- **Dark Theme**: Easy on the eyes with dark backgrounds and Google Blue accents
- **Responsive Layout**: Supports both 1080p and 720p resolutions
- **Minimal Navigation**: Intuitive and uncluttered interface
- **Google Brand Colors**: Primary blue (#4285F4) with complementary accent colors

## Design Principles

This skin follows Google TV's design language:

1. **Content First**: Large featured content area with grid-based browsing
2. **Clean & Minimal**: Remove visual clutter, focus on content
3. **Dark Theme**: Dark backgrounds (nearly black) with white text
4. **Google Blue Accents**: Primary actions use Google's signature blue color
5. **Typography**: Uses Roboto font family for a modern look
6. **Spacing**: Generous whitespace for breathing room
7. **Consistency**: Uniform sizing and alignment throughout

## Color Palette

### Primary Colors
- **Background Dark**: `#0D0D0D`
- **Surface**: `#1A1A1A`
- **Surface Variant**: `#2A2A2A`

### Brand Colors
- **Google Blue**: `#4285F4` (Primary accent)
- **Google Red**: `#EA4335` (Error/Alert)
- **Google Yellow**: `#FBBC04` (Warning)
- **Google Green**: `#34A853` (Success)

### Text Colors
- **Primary Text**: `#FFFFFF`
- **Secondary Text**: `#B3B3B3`
- **Tertiary Text**: `#808080`

## Installation

### For Development

1. Clone or place the `skin.googletvlike` folder into your Kodi's addons directory:
   - **Windows**: `C:\Users\[YourUsername]\AppData\Roaming\Kodi\addons\`
   - **macOS**: `~/Library/Application Support/Kodi/addons/`
   - **Linux**: `~/.kodi/addons/`

2. Restart Kodi

3. Go to **Settings > Appearance > Skin** and select **GoogleTV Like**

### For End Users

Once packaged as a Kodi addon, install via:
1. Kodi Settings → Add-ons
2. Install from zip file or repository
3. Select GoogleTV Like
4. Settings → Appearance → Skin → GoogleTV Like

## File Structure

```
skin.googletvlike/
├── addon.xml                          # Addon metadata
├── changelog.txt                      # Version history
├── LICENSE.txt                        # GPL-2.0 license
├── README.md                          # This file
├── resources/
│   ├── skins/
│   │   └── default/
│   │       ├── 1080i/                # HD layouts (1920x1080)
│   │       │   ├── Home.xml          # Main home screen
│   │       │   ├── DialogSelect.xml  # Selection dialogs
│   │       │   ├── DialogProgress.xml # Progress dialogs
│   │       │   └── ...
│   │       ├── 720p/                 # SD layouts (1280x720)
│   │       │   ├── Home.xml
│   │       │   └── ...
│   │       ├── colors/
│   │       │   └── default.xml       # Color scheme definitions
│   │       └── fonts/
│   │           └── fonts.xml         # Typography definitions
│   ├── media/                        # Images and media assets
│   │   ├── icon.png                  # Addon icon
│   │   ├── fanart.jpg                # Background fanart
│   │   └── ...
│   └── language/
│       └── English/
│           └── strings.po            # Localization strings
└── ...
```

## Layout Files

### 1080i (1920x1080)

- **Home.xml**: Main home screen with featured content and grid layout

### 720p (1280x720)

- **Home.xml**: Scaled-down version for 720p displays

## Future Enhancements

- Additional dialog layouts (Settings, Select, Context Menu)
- Search and filtering interface
- Library browsing with multiple view modes
- Video/Music player overlay
- Settings dialog with theme customization
- Side navigation menu
- Custom keyboard layout

## Color Customization

To customize colors, edit `resources/skins/default/colors/default.xml`:

```xml
<color name="primary_blue">FF4285F4</color>
<!-- Change FF4285F4 to your preferred color code (ARGB format) -->
```

## Font Customization

To modify fonts, edit `resources/skins/default/fonts/fonts.xml`:

```xml
<font>
  <name>DisplayLarge</name>
  <size>60</size>
  <filename>Roboto-Regular.ttf</filename>
</font>
```

## Requirements

- **Kodi**: Version 19.0 (Matrix) or later
- **GUI Framework**: 5.15.0 or higher
- **Resolution Support**: 1920x1080 and 1280x720

## Known Limitations

- Requires system fonts to be installed (Roboto family recommended)
- Some advanced features require Kodi skin scripting
- Dialog layouts are still being developed

## License

GNU General Public License v2.0 - See LICENSE.txt for details

This is a fan project inspired by Google TV. It is not affiliated with Google or Google TV.

## Contributing

To contribute improvements:

1. Fork the project
2. Create a feature branch
3. Make your changes
4. Submit a pull request with a description

## Credits

- Inspired by **Google TV** design language
- Built with **Kodi Skin XML** framework
- Uses **Google Material Design 3** principles
- Google fonts and brand colors used under fair use

## Troubleshooting

### Skin Not Showing

1. Verify the folder is in the correct addons directory
2. Restart Kodi completely
3. Check Kodi logs for XML parsing errors

### Text Not Displaying

1. Ensure system fonts (Roboto) are installed
2. Font fallback may use system defaults
3. Check font file paths in fonts.xml

### Performance Issues

1. Reduce animation complexity
2. Clear Kodi cache: Settings → System → Library → Clean Library
3. Update to the latest Kodi version

## Support

For issues, questions, or suggestions:
- Check existing documentation
- Review Kodi skin development wiki: https://kodi.wiki/view/Skin_development

---

**Version**: 1.0.0  
**Last Updated**: 2026  
**Status**: Beta/Development
