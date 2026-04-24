# SamVivan Plymouth Theme

A high-quality, animated boot splash screen for Linux distributions. This theme features a smooth, optimized animation specifically designed for high-performance laptops and high-resolution displays.

## 📋 Table of Contents
- [Features](#features)
- [Prerequisites](#prerequisites)
- [Installation](#installation)
- [Configuration](#configuration)
- [Troubleshooting](#troubleshooting)
- [License](#license)

## ✨ Features

- Smooth, multi-frame animation for an elegant boot experience
- Optimized for high-resolution displays (4K and above)
- Lightweight and performant on modern systems
- Easy installation and configuration
- Compatible with most Linux distributions

## 📦 Prerequisites

Before installing the SamVivan Plymouth theme, ensure you have the Plymouth boot splash system installed on your system:

```bash
sudo apt install plymouth
```

> **Note:** Plymouth is available on most Debian/Ubuntu-based distributions. For other distributions (Fedora, Arch, etc.), use your respective package manager.

## 🚀 Installation

### Step 1: Clone or Download the Theme

If you haven't already, clone this repository or download the theme files:

```bash
git clone <repository-url>
cd SamVivan-Plymouth-Theme
```

### Step 2: Copy Theme to Plymouth Directory

Copy the theme to the Plymouth themes directory:

```bash
sudo cp -r samvivan /usr/share/plymouth/themes/
```

### Step 3: Register the Theme with Plymouth

Install and register the new theme as an alternative:

```bash
sudo update-alternatives --install /usr/share/plymouth/themes/default.plymouth default.plymouth /usr/share/plymouth/themes/samvivan/samvivan.plymouth 100
```

### Step 4: Select the Theme

Choose the SamVivan theme as your default boot splash screen:

```bash
sudo update-alternatives --config default.plymouth
```

A menu will appear with all available Plymouth themes. **Select the number corresponding to the SamVivan theme** and press Enter.

Example output:
```
There are 3 choices for the alternative default.plymouth (providing /usr/share/plymouth/themes/default.plymouth).

  Selection    Path                                              Priority   Status
----
  0            /usr/share/plymouth/themes/ubuntu/ubuntu.plymouth 100       auto mode
* 1            /usr/share/plymouth/themes/samvivan/samvivan.plymouth 100   manual mode
  2            /usr/share/plymouth/themes/spinner/spinner.plymouth 50      manual mode

Press <enter> to keep the current choice[*], or type selection number: 1
```

### Step 5: Update Initramfs

After selecting the theme, rebuild the initial ramdisk to apply the changes:

```bash
sudo update-initramfs -u
```

This command may take a minute or two depending on your system. Wait for it to complete before rebooting.

### Step 6: Verify Installation

Reboot your system to see the new Plymouth theme in action:

```bash
sudo reboot
```

The SamVivan theme should now display during the boot process.

## ⚙️ Configuration

The theme's configuration can be modified by editing the Plymouth script:

- **Main script:** `samvivan.script` - Contains animation and visual settings
- **Theme configuration:** `samvivan.plymouth` - Plymouth metadata file

> **Note:** Most users will not need to modify these files. Only edit them if you have specific customization requirements.

## 🔧 Troubleshooting

### Theme doesn't appear during boot

1. Verify the theme was installed correctly:
   ```bash
   ls /usr/share/plymouth/themes/samvivan/
   ```

2. Check that the theme is selected:
   ```bash
   sudo update-alternatives --config default.plymouth
   ```

3. Make sure initramfs was updated:
   ```bash
   sudo update-initramfs -u
   ```

### Black screen during boot

- This is often a display scaling issue. Try disabling Plymouth animations:
  ```bash
  sudo plymouth-set-default-theme spinner
  ```
- Then re-enable with: `sudo update-alternatives --config default.plymouth`

### Remove the theme

If you want to uninstall the SamVivan theme:

```bash
sudo update-alternatives --remove default.plymouth /usr/share/plymouth/themes/samvivan/samvivan.plymouth
sudo rm -rf /usr/share/plymouth/themes/samvivan/
sudo update-initramfs -u
```

## 📁 File Structure

```
samvivan/
├── samvivan.plymouth          # Plymouth theme metadata
└── samvivan.script            # Animation and theme logic
```

## 📄 License

This theme is released under the terms specified in the LICENSE file. Please see [LICENSE](LICENSE) for more details.

---

**Enjoy your new boot experience!** 🎉
