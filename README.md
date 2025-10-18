# excalocal 🎨

<div align="center">

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Node.js](https://img.shields.io/badge/Node.js-16+-green.svg)](https://nodejs.org/)
[![Excalidraw](https://img.shields.io/badge/Excalidraw-0.17.6-purple.svg)](https://github.com/excalidraw/excalidraw)
[![Views](https://hits.seeyoufarm.com/api/count/incr/badge.svg?url=https%3A%2F%2Fgithub.com%2FMahdiMirzadeh%2Fexcalocal&count_bg=%2379C83D&title_bg=%23555555&icon=&icon_color=%23E7E7E7&title=views&edge_flat=false)](https://hits.seeyoufarm.com)

</div>

> **Local Excalidraw server with custom handwritten font and advanced instance management**

A self-hosted Excalidraw server that runs locally with a beautiful handwritten font (Excalifont) and powerful instance management features. Perfect for offline sketching, diagramming, and visual brainstorming.

## 📚 Table of Contents

- [✨ Features](#-features)
- [📦 Installation](#-installation)
  - [Step 1: Install Prerequisites](#step-1-install-prerequisites)
  - [Step 2: Create Directory Structure](#step-2-create-directory-structure)
  - [Step 3: Install JavaScript Dependencies](#step-3-install-javascript-dependencies)
  - [Step 4: Download Custom Font](#step-4-download-custom-font)
  - [Step 5: Download and Install excalocal](#step-5-download-and-install-excalocal)
  - [Step 6: Add to PATH](#step-6-add-to-path)
- [🚀 Usage](#-usage)
- [📁 Directory Structure](#-directory-structure)
- [🛠️ Configuration](#%EF%B8%8F-configuration)
- [🐛 Troubleshooting](#-troubleshooting)
- [🙏 Acknowledgments](#-acknowledgments)
- [📝 License](#-license)
- [🚀 Uninstall](#-uninstall)

## ✨ Features

- 🖋️ **Custom Excalifont** - Beautiful handwritten font that enhances the sketchy feel
- 🔄 **Instance Management** - Run multiple named instances with state tracking
- 🌙 **Dark Theme** - Default dark mode for comfortable use
- 💾 **Auto-Save** - Automatic save/restore of drawings using localStorage
- 🚀 **Background Mode** - Daemon support for persistent instances
- 📱 **Responsive** - Works on desktop and mobile browsers
- 🔒 **Privacy-First** - Everything runs locally, no data sent to external servers

## 📦 Installation

### Step 1: Install Prerequisites

First, install Node.js and a package manager on your system:

#### Node.js Installation by Distribution

**Debian/Ubuntu-based systems:**
```bash
sudo apt update
sudo apt install nodejs npm
```

**RHEL/CentOS/Fedora:**
```bash
# Fedora
sudo dnf install nodejs npm
# RHEL/CentOS (with EPEL)
sudo yum install epel-release
sudo yum install nodejs npm
```

**Arch Linux-based systems:**
```bash
sudo pacman -S nodejs npm
```

**OpenSUSE:**
```bash
sudo zypper install nodejs npm
```

**Alpine Linux:**
```bash
sudo apk add nodejs npm
```

**Gentoo:**
```bash
sudo emerge nodejs
```

#### Alternative Package Managers

After installing Node.js, you can optionally install alternative package managers:

**Yarn:**
```bash
npm install -g yarn
```

**pnpm:**
```bash
npm install -g pnpm
```

**Bun:**
```bash
curl -fsSL https://bun.sh/install | bash
source ~/.bashrc
```

#### Verify Installation
```bash
node -v
npm -v
# If using alternatives:
# yarn -v
# pnpm -v  
# bun -v
```

### Step 2: Create Directory Structure

Create the necessary directories for excalocal:

```bash
mkdir -p ~/.local/share/excalocal/fonts ~/.local/bin
```

### Step 3: Install JavaScript Dependencies

Choose your preferred package manager:
```bash
cd ~/.local/share/excalocal
npm install react react-dom @excalidraw/excalidraw@0.17.6
# yarn install react react-dom @excalidraw/excalidraw@0.17.6
# pnpm install react react-dom @excalidraw/excalidraw@0.17.6
# bun  install react react-dom @excalidraw/excalidraw@0.17.6
```

### Step 4: Download Custom Font

```bash
curl -L -o ~/.local/share/excalocal/fonts/Excalifont.woff2 \
  https://raw.githubusercontent.com/MahdiMirzadeh/excalocal/refs/heads/master/Excalifont-Regular.woff2
```

### Step 5: Download and Install excalocal

```bash
curl -L -o ~/.local/bin/excalocal \
  https://raw.githubusercontent.com/MahdiMirzadeh/excalocal/refs/heads/master/excalocal

chmod +x ~/.local/bin/excalocal
```

### Step 6: Add to PATH

Ensure `~/.local/bin` is in your PATH:

```bash
echo $PATH | grep -qo "$HOME/.local/bin" || \
  ( echo 'export PATH="$HOME/.local/bin:$PATH"' >> ~/.bashrc; source ~/.bashrc )
```

### ✅ Verify Installation

```bash
excalocal --version
```

## 🚀 Usage

### Quick Start

```bash
# Start excalocal (opens at http://localhost:3030)
excalocal
```

### Basic Commands

| Command | Description |
|---------|-------------|
| `excalocal` | Start server on default port (3030) |
| `excalocal -p 8080` | Start on specific port |
| `excalocal -b -n work` | Start named instance in background |
| `excalocal -l` | List all running instances |
| `excalocal -o work` | Open existing instance in browser |
| `excalocal -k work` | Kill specific instance |
| `excalocal -c` | Cleanup inactive instances |
| `excalocal -h` | Show help |
| `excalocal -V` | Show version |

### 📚 Usage Examples

**Start a simple server:**
```bash
excalocal
# Opens http://localhost:3030 in your browser
```

**Create named instances for different projects:**
```bash
# Start work-related sketches
excalocal -b -n work -p 3031

# Start personal projects
excalocal -b -n personal -p 3032

# Start presentation prep
excalocal -b -n presentation -p 3033
```

**Manage multiple instances:**
```bash
# List all running instances
excalocal -l

# Open specific project
excalocal -o work

# Kill specific instance
excalocal -k presentation

# Clean up dead instances
excalocal -c
```

### 🌐 Accessing Your Drawings

- **Local**: `http://localhost:3030`
- **Network**: `http://YOUR_IP:3030` (accessible from other devices on your network)
- **Custom Port**: `http://localhost:YOUR_PORT`

## 📁 Directory Structure

After installation, your files will be organized as:

```
~/.local/
├── bin/
│   └── excalocal                    # Main executable
└── share/excalocal/
    ├── fonts/
    │   └── Excalifont.woff2        # Custom handwritten font
    ├── package.json                # Dependencies manifest
    └── node_modules/               # JavaScript libraries
        ├── react/
        ├── react-dom/
        └── @excalidraw/excalidraw/
```

*This keeps your `~/.local/bin` directory clean while storing all dependencies in the standard `~/.local/share` location.*

## 🛠️ Configuration

### Environment Variables

- `PORT` - Default port (default: 3030)
- `XDG_STATE_HOME` - Instance state directory (default: `~/.local/state`)

### Instance State

Instance information is stored in:
```
~/.local/state/excalidraw/instances.json
```

## 🐛 Troubleshooting

### Common Issues

**Port already in use:**
```bash
# excalocal automatically finds the next available port
excalocal  # Will use 3031 if 3030 is busy
```

**Font not loading:**
```bash
# Check if font file exists
ls ~/.local/share/excalocal/fonts/Excalifont.woff2

# Re-download if missing
curl -L -o ~/.local/share/excalocal/fonts/Excalifont.woff2 \
  https://raw.githubusercontent.com/MahdiMirzadeh/excalocal/refs/heads/master/Excalifont-Regular.woff2
```

**Command not found:**
```bash
# Check if ~/.local/bin is in PATH
echo $PATH | grep ".local/bin"

# If not, add it:
echo 'export PATH="$HOME/.local/bin:$PATH"' >> ~/.bashrc
source ~/.bashrc
```

## 🙏 Acknowledgments

Special thanks to:

- **[Dawid Wraga](https://github.com/DawidWraga)** for the brilliant solution on implementing custom fonts in Excalidraw. His article ["How to use a custom font on Excalidraw.com"](https://dev.to/dawidcodes/how-to-use-a-custom-font-on-excalidrawcom-4jl4) was the foundation that made the Excalifont integration possible.

- **[The Excalidraw Team](https://github.com/excalidraw/excalidraw)** for creating this amazing virtual whiteboard tool that makes sketching and diagramming so intuitive and enjoyable.

## 📝 License

MIT License - see LICENSE file for details.

## 🚀 Uninstall

```bash
rm -rf ~/.local/share/excalocal ~/.local/bin/excalocal
```
