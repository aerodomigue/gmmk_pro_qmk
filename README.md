# GMMK Pro Custom Keymap

**The Ultimate Cross-Platform QMK Experience for GMMK Pro**

A comprehensive, feature-rich QMK keymap specifically designed for the **Glorious GMMK Pro 75% keyboard**. This keymap transforms your GMMK Pro into a truly intelligent keyboard, built from the ground up with modern QMK features that automatically adapt to your operating system and provide seamless integration across macOS, Windows, and Linux environments.

✨ **Key Highlights:**
- 🌍 **Smart OS Detection** - Automatically adapts sleep commands and behaviors
- 🎨 **Advanced RGB System** - Sophisticated per-key lighting with visual feedback
- ⌨️ **Adaptive Input** - NKRO toggle for maximum compatibility  
- 🚀 **Enhanced Productivity** - Virtual numpad, media controls, and shortcuts
- 🔧 **Developer-Friendly** - Clean, well-documented code with extensive customization options

## Features

### 🖱️ **Cross-Platform Sleep Integration**
- **Sleep Shortcut**: `Fn + Escape` - Adaptive sleep command based on operating system
- **Automatic OS Detection**: Uses QMK's built-in OS detection to send appropriate sleep commands

#### **Platform-Specific Behavior:**
- **macOS**: Sends `Cmd + Option + Eject` combination
  - **Why not KC_SLEP?**: macOS doesn't respond reliably to the standard `KC_SLEP` keycode
  - **Workaround**: Uses the macOS-specific key combination that forces immediate sleep without confirmation dialogs
  - **Result**: Instant sleep activation without user prompts or delays

- **Windows**: Sends standard `KC_SLEP` system sleep keycode
  - **Behavior**: Triggers Windows sleep mode through standard system sleep key
  - **Compatibility**: Works with all Windows power management settings

- **Linux**: Sends standard `KC_SLEP` system sleep keycode
  - **Behavior**: Triggers system suspend through standard sleep key
  - **Compatibility**: Works with most Linux desktop environments and power managers

### ⌨️ **NKRO Toggle**
- **NKRO Control**: `Fn + Print Screen` - Toggle between N-Key Rollover and 6-Key Rollover
- **Visual Indicator**: Print Screen key shows current state when Fn is held:
  - 🟢 **Green**: NKRO enabled (unlimited key rollover)
  - 🟠 **Orange**: 6KRO enabled (6-key rollover for Linux compatibility)
- Setting persists across power cycles

### 🎮 **Virtual Numpad**
When `Fn` is held, the right side of the keyboard becomes a numpad:
```
T Y U    →    7 8 9
G H J    →    4 5 6
V B N    →    1 2 3
```

### 🎵 **Media Controls**
- `Fn + A`: Previous track (🟢 Spring Green)
- `Fn + S`: Play/Pause (🟡 Gold)
- `Fn + D`: Next track (🟢 Spring Green)
- `Fn + W`: Stop (🟡 Gold)

### 🌈 **Advanced RGB Lighting**

#### **RGB Controls via Rotary Encoder**
| Modifier | Action | Effect |
|----------|--------|---------|
| `Shift + Knob` | Turn | Change RGB effect mode |
| `Right Shift + Knob` | Turn | Adjust effect speed |
| `Ctrl + Knob` | Turn | Adjust hue |
| `Alt + Knob` | Turn | Adjust saturation |
| `Ctrl + Alt + Knob` | Turn | Adjust brightness |

#### **RGB Mode Switching via Knob Click**
| Modifier | Click | Effect |
|----------|-------|---------|
| `Ctrl + Click` | Toggle | Switch between USER_SOLID_SIDE ↔ QMK_FANCY_ALL |
| `Alt + Click` | Toggle | Switch between QMK_FANCY_SIDE ↔ QMK_FANCY_ALL |
| `Shift + Click` | Toggle | RGB on/off |
| `Right Ctrl + Click` | Save | Save current RGB settings to EEPROM |

### 🔧 **Function Layer Visual Indicators**

When `Fn` is held, keys light up to show their function:
- 🔵 **Blue**: Cross-platform sleep key (Escape) - Auto-detects OS for appropriate sleep command
- 🟣 **Magenta**: Bootloader key (Backslash)
- 🔴 **Red**: RGB hue control (Left Shift)
- 🟢 **Green**: RGB saturation control (Left Ctrl)
- 🔵 **Blue**: RGB brightness control (Left Win)
- 🩷 **Pink**: RGB speed control (Right Shift)
- 🔵 **Azure**: Save RGB settings (Right Ctrl)
- ⚪ **White**: Virtual numpad keys
- 🟢/🟠 **Green/Orange**: NKRO status (Print Screen)
- 🔵 **Cyan**: Home key (Del)

### 🔒 **Caps Lock Indicator**
- Entire Caps Lock row turns red when Caps Lock is active

## Configuration

### Enabled Features (rules.mk)
```makefile
VIA_ENABLE          = yes    # VIA compatibility for easy remapping
EXTRAKEY_ENABLE     = yes    # Media keys and system controls
NKRO_ENABLE         = yes    # N-Key Rollover support
OS_DETECTION_ENABLE = yes    # Automatic OS detection for adaptive features
```

## Compatibility

- ✅ **macOS**: Full compatibility with automatic OS detection
  - Sleep function uses `Cmd+Option+Eject` for immediate sleep without prompts
  - Media keys and system controls work natively
- ✅ **Windows**: Full compatibility with automatic OS detection  
  - Sleep function uses standard `KC_SLEP` system sleep key
  - All media keys and system controls work natively
- ✅ **Linux**: Full compatibility with automatic OS detection
  - Sleep function uses standard `KC_SLEP` system sleep key
  - NKRO toggle available for systems with limited N-Key Rollover support
  - Compatible with most desktop environments (GNOME, KDE, XFCE, etc.)

## Bootloader Mode

To reset the board into bootloader mode:
* `Fn + Backslash` - Software reset to bootloader
* Hold Reset switch on PCB bottom while connecting USB
* Hold Escape while connecting USB (erases settings)

## Installation

### Prerequisites

**All Platforms:**
- QMK firmware environment set up
- GMMK Pro keyboard in bootloader mode

### Platform-Specific Setup

#### **macOS**
```bash
# Install QMK via Homebrew
brew install qmk/qmk/qmk

# Set up QMK (first time only)
qmk setup

# Navigate to keymaps directory
cd ~/qmk_firmware/keyboards/gmmk/pro/rev1/ansi/keymaps

# Clone this keymap
git clone https://github.com/aerodomigue/gmmk_pro_qmk.git gmmk_pro_qmk
```

#### **Windows**
```cmd
# Install QMK via pip (requires Python)
pip install qmk

# Set up QMK (first time only)
qmk setup

# Navigate to keymaps directory
cd %USERPROFILE%\qmk_firmware\keyboards\gmmk\pro\rev1\ansi\keymaps

# Clone this keymap
git clone https://github.com/aerodomigue/gmmk_pro_qmk.git gmmk_pro_qmk
```

#### **Linux (Ubuntu/Debian)**
```bash
# Install dependencies
sudo apt update
sudo apt install git python3-pip

# Install QMK
python3 -m pip install --user qmk

# Add local bin to PATH (add to ~/.bashrc for permanent)
export PATH=$PATH:~/.local/bin

# Set up QMK (first time only)
qmk setup

# Navigate to keymaps directory
cd ~/qmk_firmware/keyboards/gmmk/pro/rev1/ansi/keymaps

# Clone this keymap
git clone https://github.com/aerodomigue/gmmk_pro_qmk.git gmmk_pro_qmk
```

#### **Linux (Arch/Manjaro)**
```bash
# Install from AUR
yay -S qmk

# Or via pip
sudo pacman -S python-pip git
pip install qmk

# Set up QMK (first time only)
qmk setup

# Navigate to keymaps directory
cd ~/qmk_firmware/keyboards/gmmk/pro/rev1/ansi/keymaps

# Clone this keymap
git clone https://github.com/aerodomigue/gmmk_pro_qmk.git gmmk_pro_qmk
```

### Build and Flash

**Compile the keymap:**
```bash
qmk compile -kb gmmk/pro/rev1/ansi -km gmmk_pro_qmk -j 8
```

**Flash to keyboard:**

**Option 1: Command Line (Recommended)**
```bash
# Put keyboard in bootloader mode first (Fn + Backslash or physical reset)
qmk flash -kb gmmk/pro/rev1/ansi -km gmmk_pro_qmk
```

**Option 2: QMK Toolbox (GUI)**
1. **Download QMK Toolbox**: Get it from [qmk.fm/toolbox](https://github.com/qmk/qmk_toolbox/releases)
2. **Compile firmware**: 
   ```bash
   qmk compile -kb gmmk/pro/rev1/ansi -km gmmk_pro_qmk
   ```
3. **Locate the .bin file**: Find `gmmk_pro_rev1_ansi_gmmk_pro_qmk.bin` in `qmk_firmware/.build/`
4. **Open QMK Toolbox**: 
   - Click "Open" and select your `.bin` file
   - Microcontroller should show: **STM32F303** (or similar)
5. **Enter bootloader mode**: Press `Fn + Backslash` on your keyboard
6. **Flash**: Click "Flash" button when the keyboard is detected

**Alternative: Manual flash (if auto-flash fails)**
```bash
# Compile to .bin file
qmk compile -kb gmmk/pro/rev1/ansi -km gmmk_pro_qmk

# Flash manually using QMK Toolbox or dfu-util
# The .bin file will be in qmk_firmware/.build/
```

### Troubleshooting

**Common Issues:**
- **Permission denied (Linux)**: Add your user to the `dialout` group: `sudo usermod -a -G dialout $USER`
- **Keyboard not detected**: Ensure keyboard is in bootloader mode (Fn + Backslash)
- **Build errors**: Check that all required features are enabled in rules.mk
- **Python issues (Windows)**: Install Python from python.org and ensure it's in PATH

**Verify Installation:**
```bash
# Check QMK version
qmk --version

# Test compile without flashing
qmk compile -kb gmmk/pro/rev1/ansi -km gmmk_pro_qmk --clean
```

## Changelog

### v1.0 (2025)
- Major refactor of legacy codebase from 2022
- **Cross-platform sleep functionality**: Automatic OS detection for appropriate sleep commands
  - macOS: Uses `Cmd+Option+Eject` workaround for immediate sleep without confirmation dialogs
  - Windows/Linux: Uses standard `KC_SLEP` system sleep key
- Added NKRO toggle with visual indicator (Fn + Print Screen)
- Added Home key shortcut (Fn + Del)
- Enhanced RGB lighting controls and visual feedback system
- Improved code organization and comprehensive documentation
- Updated copyright and licensing information

---

**Author**: aerodomigue  
**License**: GPL v2+  
**QMK Version**: Compatible with current QMK firmware
