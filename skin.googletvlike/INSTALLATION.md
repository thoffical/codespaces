# Installation & Quick Start Guide

## System Requirements

- **Kodi**: 19.0 (Matrix) or later
- **GUI Framework**: 5.15.0 or higher
- **Resolution**: 1920x1080 or 1280x720
- **Operating System**: Windows, macOS, Linux, or any Kodi-supported platform

## Installation Methods

### Method 1: Manual Installation (Recommended for Development)

1. **Locate Kodi Addons Directory:**
   - **Windows**: `C:\Users\[YourUsername]\AppData\Roaming\Kodi\addons\`
   - **macOS**: `~/Library/Application Support/Kodi/addons/`
   - **Linux**: `~/.kodi/addons/`

2. **Copy the Skin Folder:**
   - Copy the entire `skin.googletvlike` folder to your addons directory

3. **Restart Kodi**
   - Exit Kodi completely and relaunch it

4. **Activate the Skin:**
   - Go to: **Settings → Appearance → Skin**
   - Select **GoogleTV Like**
   - Kodi will restart

### Method 2: From ZIP File

1. Download `skin.googletvlike.zip`
2. Go to: **Settings → Add-ons → Install from ZIP file**
3. Navigate to and select the ZIP file
4. Wait for installation to complete
5. Go to: **Settings → Appearance → Skin**
6. Select **GoogleTV Like**

### Method 3: From Repository (When Available)

1. Go to: **Settings → Add-ons → Install from Repository**
2. Select appropriate repository
3. Navigate to: **Skins**
4. Select **GoogleTV Like**
5. Click **Install**

## Verify Installation

1. **Check Folder Exists:**
   - Navigate to your addons directory
   - Confirm `skin.googletvlike` folder exists

2. **Check Kodi Settings:**
   - Settings → Appearance → Skin
   - GoogleTV Like should be listed

3. **Check Debug Log:**
   - Settings → System → Logging
   - Enable "Log to file"
   - Restart Kodi
   - Check log for any errors

## First Time Setup

### Theme Selection
The skin comes with a default dark theme inspired by Google TV. No additional setup is required.

### Optional Customization
See [CUSTOMIZATION.md](CUSTOMIZATION.md) for:
- Changing primary accent color
- Adjusting font sizes
- Creating custom themes
- Modifying layouts

## Configuration Files

### Essential Files to Know

- **`addon.xml`** - Skin metadata (don't modify unless you know what you're doing)
- **`resources/skins/default/colors/default.xml`** - Color definitions
- **`resources/skins/default/fonts/fonts.xml`** - Font definitions
- **`resources/skins/default/1080i/Home.xml`** - Main layout (1080p)
- **`resources/skins/default/720p/Home.xml`** - Main layout (720p)

## Troubleshooting Installation

### Skin Not Appearing in List

**Solution 1: Check File Location**
```
✓ Correct: C:\Users\Name\AppData\Roaming\Kodi\addons\skin.googletvlike\
✗ Wrong:  C:\Users\Name\AppData\Roaming\Kodi\addons\skin.googletvlike\skin.googletvlike\
```

**Solution 2: Restart Kodi**
- Exit Kodi completely (not just minimize)
- Wait 5 seconds
- Relaunch Kodi

**Solution 3: Check Kodi Version**
- Settings → System → About
- Must be 19.0 or later

### Skin Crashes or Black Screen

1. **Clear Cache:**
   - Settings → System → Library → Clean Library
   
2. **Check Debug Log:**
   - Settings → System → Logging
   - Enable "Components → GUI"
   - Find errors in kodi.log
   
3. **Revert to Default Skin:**
   - Press `ESC` repeatedly to get back to settings
   - Switch to default "Confluence" skin
   - Delete skin.googletvlike folder
   - Reinstall

### Text Not Displaying Properly

**Install System Fonts:**
- Windows: Install `Roboto` font family from Google Fonts
- macOS: Usually pre-installed
- Linux: `sudo apt install fonts-roboto`

Or edit `fonts/fonts.xml` to use system fonts like Arial or Ubuntu.

### Layouts Look Stretched

1. Check your display resolution (Settings → Display)
2. Make sure it's either 1920x1080 or 1280x720
3. If using ultra-wide displays, 1080p layouts will be used with black bars (normal)

## Upgrading

### From Previous Version

1. **Backup Current Installation:**
   ```
   Rename: skin.googletvlike → skin.googletvlike.backup
   ```

2. **Install New Version:**
   - Copy new `skin.googletvlike` folder to addons
   - Restart Kodi

3. **Reactivate Skin:**
   - Settings → Appearance → Skin → GoogleTV Like

4. **Clean Up:**
   - If all works, delete `skin.googletvlike.backup`

## Performance Optimization

### For Slower Devices

1. **Reduce Image Quality:**
   - Edit Home.xml, find featured image section
   - Use smaller resolution images

2. **Disable Animations:**
   - Edit skin layout files
   - Remove `<animation>` sections

3. **Clear Cache Regularly:**
   - Settings → System → Library → Clean Library

## Development Setup

### For Skin Developers

1. **Clone Repository** (if available):
   ```
   git clone https://github.com/thoffical/codespaces
   cd skin.googletvlike
   ```

2. **Set Up Development Folder:**
   ```
   Copy to: ~/.kodi/addons/skin.googletvlike
   ```

3. **Enable Development Mode:**
   - Settings → System → Logging
   - Enable "Log to file"
   - Enable "Components → GUI"

4. **Edit and Test:**
   - Modify XML files in your editor
   - Use Kodi's skin debugging window (toggle with CTRL+SHIFT+D)
   - Monitor kodi.log for errors

See [DEVELOPERS.md](DEVELOPERS.md) for detailed development guide.

## Uninstallation

### Method 1: From Settings
1. Settings → Add-ons → Installed add-ons → Skins
2. Select GoogleTV Like
3. Click "Uninstall"

### Method 2: Manual
1. Switch to default skin first
2. Navigate to addons folder
3. Delete `skin.googletvlike` folder
4. Restart Kodi

### Method 3: Clean Complete Removal
```
On Windows:
1. Uninstall using Method 1
2. Delete: C:\Users\[User]\AppData\Roaming\Kodi\addons\skin.googletvlike\
3. Delete: C:\Users\[User]\AppData\Roaming\Kodi\userdata\addon_data\skin.googletvlike\
```

## Getting Help

### Resources
- Main Documentation: [README.md](README.md)
- Developer Guide: [DEVELOPERS.md](DEVELOPERS.md)
- Customization Guide: [CUSTOMIZATION.md](CUSTOMIZATION.md)
- Kodi Wiki: https://kodi.wiki/view/Skin_development

### Reporting Issues
1. Check existing documentation first
2. Check Kodi debug log for errors
3. Visit Kodi forums: https://forum.kodi.tv/forumdisplay.php?fid=67

### Common Questions

**Q: Can I use this skin on Kodi 18 or earlier?**
A: No, it requires Kodi 19.0 or later. Older versions use a different GUI framework.

**Q: How do I change the color scheme?**
A: See [CUSTOMIZATION.md](CUSTOMIZATION.md) - Color Customization section.

**Q: Will this work on Android/iOS?**
A: Yes, if Kodi is installed on those platforms. File paths will differ.

**Q: Can I share my customized version?**
A: Yes, see CUSTOMIZATION.md - Sharing Your Customizations.

---

**Version**: 1.0.0  
**Last Updated**: 2026  
**Compatible Kodi Versions**: 19.0+
