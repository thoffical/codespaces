# GoogleTV Like Skin - Customization Guide

This guide helps you customize the GoogleTV Like skin to match your preferences.

## Quick Customizations

### Changing the Primary Color

The default color is Google Blue. To change it:

1. Open: `resources/skins/default/colors/default.xml`
2. Find the line: `<color name="primary_blue">FF4285F4</color>`
3. Replace with your color in ARGB format (e.g., `FFFF5722` for Deep Orange)

**Common Color Codes (ARGB format):**
- Google Blue: `FF4285F4`
- Deep Orange: `FFFF5722`
- Deep Purple: `FF673AB7`
- Teal: `FF009688`
- Red: `FFEA4335`
- Green: `FF34A853`

Also update `primary_blue_focus`:
```xml
<color name="primary_blue_focus">FF357AE8</color>
```

### Changing Background Color

1. Open: `resources/skins/default/colors/default.xml`
2. Find: `<color name="background_dark">FF0D0D0D</color>`
3. Change to your preferred dark color

**Tips:**
- Keep it dark for Google TV aesthetic
- Use values like `FF000000` to `FF1A1A1A`
- Very dark: `FF050505`
- Light dark: `FF303030`

### Changing Text Colors

1. Open: `resources/skins/default/colors/default.xml`
2. Modify `text_primary`, `text_secondary`, `text_tertiary`

**Example - High Contrast:**
```xml
<color name="text_primary">FFFFFFFF</color>      <!-- Pure white -->
<color name="text_secondary">FF808080</color>    <!-- Mid-gray -->
<color name="text_tertiary">FF404040</color>     <!-- Dark gray -->
```

### Changing Font Size

1. Open: `resources/skins/default/fonts/fonts.xml`
2. Modify the `<size>` values in font definitions

**Current sizes (1080p):**
- DisplayLarge: 60
- HeadlineLarge: 32
- TitleLarge: 22
- BodyLarge: 16

To increase all sizes by 20%, multiply by 1.2:
- 60 × 1.2 = 72
- 32 × 1.2 = 38
- 22 × 1.2 = 26
- 16 × 1.2 = 19

## Theme Customization

### Bright Theme

Create a bright version of the skin:

**colors/default.xml:**
```xml
<color name="background_dark">FFF5F5F5</color>
<color name="surface">FFFFFFFF</color>
<color name="text_primary">FF212121</color>
<color name="text_secondary">FF616161</color>
```

### Warm Colors Theme

Use warm accent colors:

```xml
<color name="primary_blue">FFFF6D00</color>        <!-- Orange -->
<color name="primary_blue_focus">FFFFA500</color>
<color name="surface">FF1A1513</color>              <!-- Warm dark -->
```

### Cool Colors Theme

Use cool accent colors:

```xml
<color name="primary_blue">FF00BCD4</color>        <!-- Cyan -->
<color name="primary_blue_focus">FF0097A7</color>
```

## Advanced Customizations

### Creating a Custom Color Scheme

1. Plan your colors:
   - Pick a primary accent color
   - Choose compatible background colors
   - Select readable text colors

2. Edit `colors/default.xml`:
   ```xml
   <!-- Add new colors -->
   <color name="my_accent">FFRRGGBB</color>
   <color name="my_background">FFRRGGBB</color>
   ```

3. Use in layouts by replacing old color names

### Adjusting Layout Spacing

To make the interface feel more spacious:

1. Open: `resources/skins/default/1080i/Home.xml`
2. Increase `<posy>` and `<posx>` values for padding
3. Increase `<height>` values for vertical spacing

**Example: Increase top navigation height**
```xml
<height>80</height>  <!-- Change to 100 -->
```

### Customizing Featured Content Section

1. Open: `resources/skins/default/1080i/Home.xml`
2. Find: `<!-- Featured Content Section -->`
3. Modify dimensions:
   - `<height>500</height>` - Total section height
   - `<width>800</width>` - Image width
   - `<height>400</height>` - Image height

### Changing Grid Layout

The home screen shows content cards in a grid:

**Default (1080p):** 5 cards per row, 300px wide each

To change to 4 cards:
1. Change card width from 300 to 375
2. Adjust positions:
   - Card 1: 60
   - Card 2: 465
   - Card 3: 870
   - Card 4: 1275

```xml
<!-- Content Item 1 -->
<control type="button" id="301">
  <posx>60</posx>
  <width>375</width>
  ...
</control>
```

## Configuration Files Reference

### colors/default.xml

Define all colors used by the skin. Format:
```xml
<color name="color_name">FFRRGGBB</color>
```

### fonts/fonts.xml

Define typography. Available for:
- Display fonts (headings)
- Title fonts
- Body fonts (text)
- Label fonts (small text)

Edit:
- `<size>` - Font size in pixels
- `<filename>` - Font file name
- `<style>` - bold, italic, light

### Home.xml (1080i & 720p)

Main interface layout. Divided into sections:
- Group 100: Top navigation
- Group 200: Featured content
- Group 300: Content grid
- Group 900: Status bar

## Using Custom Fonts

To use different system fonts:

1. Install font on your system
2. Edit: `resources/skins/default/fonts/fonts.xml`
3. Change `<filename>` to font name:

```xml
<filename>YourFontName.ttf</filename>
```

Common system fonts:
- **Windows**: Arial, Segoe UI, Verdana
- **macOS**: SF Pro, Helvetica
- **Linux**: Ubuntu, Dejavu Sans

## Texture Customization

### Adding Custom Backgrounds

1. Create a 1920x1080 PNG image
2. Place in: `resources/media/`
3. Reference in Home.xml:
   ```xml
   <texture>resources/media/your_background.png</texture>
   ```

### Creating Custom Buttons

1. Design a button graphic (PNG with transparency)
2. Save to: `resources/media/`
3. Use in layout:
   ```xml
   <texture>resources/media/my_button.png</texture>
   ```

## Testing Your Changes

1. **Backup**: Save original files first
2. **Edit**: Modify the XML/color files
3. **Restart Kodi**: Changes take effect on restart
4. **Check Logs**: If something breaks, see the debug log

## Reverting Changes

Keep a backup of original files. If something breaks:

1. Restore from backup
2. Or reinstall the skin
3. Check `/path/to/skin/` for original files

## Performance Tips

- Keep image files small (<500KB each)
- Avoid overly complex color schemes
- Test on your target device
- Keep animation times short (200-300ms)

## Common Customization Tasks

### Make Text Larger

Edit `fonts/fonts.xml` - increase all `<size>` values by 20%

### Change Navigation Bar Color

Edit `colors/default.xml`:
```xml
<color name="surface">FFRRGGBB</color>
```

This affects all surface elements (top bar, bottom bar, cards)

### Hide Sections

Add to a control in Home.xml:
```xml
<visible>false</visible>
```

To show again:
```xml
<visible>true</visible>
```

### Adjust Opacity

Use alpha channel (first two hex digits):
- `FF` = Fully opaque (no transparency)
- `CC` = 80% opaque
- `99` = 60% opaque
- `66` = 40% opaque
- `33` = 20% opaque
- `00` = Fully transparent

Example:
```xml
<color name="overlay_dark">CC000000</color>  <!-- 80% opaque black -->
```

## Sharing Your Customizations

To share your custom version:

1. Create a new folder with your skin name
2. Copy the entire `skin.googletvlike` folder
3. Change addon.xml `id` to something unique:
   ```xml
   <addon id="skin.googletvlike.mytheme" ...>
   ```
4. Share the folder with others

## Troubleshooting

### Colors Look Wrong
- Check ARGB format (should be 8 hex digits)
- Verify color names in colors/default.xml
- Restart Kodi

### Text Too Small/Large
- Edit fonts/fonts.xml
- Adjust `<size>` values
- Remember 720p needs smaller sizes than 1080p

### Layout Looks Broken
- Check XML syntax for errors
- Use proper indentation
- Verify all tags are closed
- Check Kodi debug log for errors

### Changes Not Taking Effect
- Completely restart Kodi
- Clear Kodi cache: Settings → System → Library → Clean Library
- Check if file was saved

## Need Help?

- Check the main README.md
- See DEVELOPERS.md for technical details
- Review official Kodi skin wiki: https://kodi.wiki/view/Skin_development

---

**Version**: 1.0.0
**Last Updated**: 2026
