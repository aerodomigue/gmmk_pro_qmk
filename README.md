# GMMK Pro Custom Keymap v1

A highly customized QMK keymap for the GMMK Pro keyboard featuring advanced RGB lighting controls, macOS integration, and Linux compatibility features.

## Quick Install

**macOS:**
```bash
brew install qmk/qmk/qmk
cd /Users/$USER/qmk_firmware/keyboards/gmmk/pro/rev1/ansi/keymaps
git clone https://github.com/aerodomigue/gmmk_pro_qmk.git v1
```

**Build:**
```bash
qmk compile -kb gmmk/pro/rev1/ansi -km v1 -j 10
```

**Flash:**
```bash
qmk flash -kb gmmk/pro/rev1/ansi -km v1
```

## Features

### 🖱️ **macOS Integration**
- **OS-Adaptive Sleep Shortcut**: `Fn + Escape` - Automatically detects OS and uses appropriate sleep command:
  - **macOS**: `Cmd+Opt+Eject` for instant system sleep
  - **Windows/Linux**: `KC_SLEP` system sleep key
- Optimized for cross-platform workflow and system controls

### 🏠 **Navigation Shortcuts**
- **Home Key**: `Fn + Del` - Quick access to Home key function
- Perfect for text editing and navigation without leaving home row area

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
- 🔵 **Blue**: Sleep key (Escape) - OS-adaptive sleep command
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

- ✅ **macOS**: Full compatibility with adaptive sleep function and media keys
- ✅ **Windows**: Full compatibility with system sleep key and standard functions  
- ✅ **Linux**: Full compatibility with system sleep key and NKRO toggle for enhanced compatibility

## Bootloader Mode

To reset the board into bootloader mode:
* `Fn + Backslash` - Software reset to bootloader
* Hold Reset switch on PCB bottom while connecting USB
* Hold Escape while connecting USB (erases settings)

## Changelog

### v1.0 (2025)
- Major refactor of legacy codebase
- Added OS-adaptive sleep shortcut (Fn + Escape):
  - macOS: Cmd+Opt+Eject for instant sleep
  - Windows/Linux: System sleep key (KC_SLEP)
- Added Home key shortcut (Fn + Del) with cyan visual indicator
- Added NKRO toggle with visual indicator (Fn + Print Screen)
- Enhanced RGB lighting controls and visual feedback
- Improved code organization and documentation
- Updated copyright and licensing information

---

**Author**: aerodomigue  
**License**: GPL v2+  
**Version**: v1.0 (2025)

Most M2x5mm screws should fit fine, although it's best to ensure that the screw head will fit inside the counterbore.
For reference, [this hex socket head screw](https://www.mcmaster.com/91292A005/) from McMaster-Carr should fit nearly flush (head will protrude above the counterbore by ~0.1 mm).
