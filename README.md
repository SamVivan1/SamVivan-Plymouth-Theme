# SamVivan Plymouth Theme

A high-quality, animated boot splash screen for Linux distributions. This theme features a smooth, optimized animation specifically designed for high-performance laptops and high-resolution displays.

## 📋 Table of Contents
- [Features](#features)
- [Prerequisites](#prerequisites)
- [Installation](#installation)
- [Custom Theme Guide](#custom-theme-guide)
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
sudo apt install plymouth ffmpeg
```

> **Note:** Plymouth is available on most Debian/Ubuntu-based distributions. For other distributions (Fedora, Arch, etc.), use your respective package manager.

---

## 🚀 Installation

### Step 1: Clone or Download the Theme

```bash
git clone <repository-url>
cd SamVivan-Plymouth-Theme
```

### Step 2: Copy Theme to Plymouth Directory

```bash
sudo cp -r samvivan /usr/share/plymouth/themes/
```

### Step 3: Register the Theme with Plymouth

```bash
sudo update-alternatives --install /usr/share/plymouth/themes/default.plymouth default.plymouth /usr/share/plymouth/themes/samvivan/samvivan.plymouth 100
```

### Step 4: Select the Theme

```bash
sudo update-alternatives --config default.plymouth
```

### Step 5: Update Initramfs

```bash
sudo update-initramfs -u
```

### Step 6: Reboot

```bash
sudo reboot
```

---

## 🎨 Custom Theme Guide

Want to create your own custom Plymouth animation? Here’s the workflow used in this project:

### 1. Create Your Logo (SVG)

Use AI tools like Gemini to generate your logo.

- Ask Gemini to export the logo in `.svg` format
- SVG is recommended because:
  - High resolution (no pixelation)
  - Easy to animate in Lottie-based tools

---

### 2. Animate Using LottieLab

Import your SVG into LottieLab and create your animation.

- Keep animation smooth and not too heavy
- Loop-friendly animation works best for boot screens

---

### 3. Export Animation as Video

After finishing the animation:

- Export it as a video (e.g. `.mp4`)

---

### 4. Convert Video to Frames (ffmpeg)

Use ffmpeg to extract frames:

```bash
ffmpeg -i animation.mp4 progress-%d.png
```

Important:
- Rename frames so they start from 0
- Final naming format must be:

progress-0.png  
progress-1.png  
progress-2.png  

---

### 5. Set Resolution

This project uses:

800 x 600

But you are free to use any resolution. Just make sure:
- All frames have the same size
- It matches your Plymouth script configuration

---

### 6. Place Files in Theme Folder

Your structure should look like:

samvivan/  
├── samvivan.plymouth  
├── samvivan.script  
├── progress-0.png  
├── progress-1.png  
├── progress-2.png  

All frame images must be in the same folder as `.plymouth` and `.script`.

---

### 7. Done 🎉

Rebuild initramfs and reboot:

```bash
sudo update-initramfs -u
sudo reboot
```

Your custom animation should now appear during boot.

---

## ⚙️ Configuration

- Main script: `samvivan.script`
- Theme config: `samvivan.plymouth`

You can tweak animation speed, frame count, and positioning inside the script.

---

## 🔧 Troubleshooting

### Theme doesn't appear

```bash
ls /usr/share/plymouth/themes/samvivan/
sudo update-alternatives --config default.plymouth
sudo update-initramfs -u
```

---

### Black screen during boot

```bash
sudo plymouth-set-default-theme spinner
```

---

### Remove the theme

```bash
sudo update-alternatives --remove default.plymouth /usr/share/plymouth/themes/samvivan/samvivan.plymouth
sudo rm -rf /usr/share/plymouth/themes/samvivan/
sudo update-initramfs -u
```

---

## 📁 File Structure

samvivan/  
├── samvivan.plymouth  
├── samvivan.script  
├── progress-*.png  

---

## 📄 License

This theme is released under the terms specified in the LICENSE file. Please see LICENSE for more details.

---

Enjoy your new boot experience! 🎉
