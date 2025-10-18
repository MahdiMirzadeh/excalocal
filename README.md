# excalocal 🎨

<div align="center">

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Node.js](https://img.shields.io/badge/Node.js-16+-green.svg)](https://nodejs.org/)
[![Excalidraw](https://img.shields.io/badge/Excalidraw-0.17.6-purple.svg)](https://github.com/excalidraw/excalidraw)

</div>

> **Local Excalidraw server with custom handwritten font and advanced instance management**

A self-hosted Excalidraw server that runs locally with a beautiful handwritten font (Excalifont) and powerful instance management features. Perfect for offline sketching, diagramming, and visual brainstorming.

## 📚 Table of Contents

- [✨ Features](#-features)
- [📦 Installation](#-installation)
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

Install excalocal globally using npm:

```bash
npm install -g excalocal
```

That's it! The package will automatically:
- Install all required dependencies
- Download the custom Excalifont
- Set up the necessary directory structure
- Make the `excalocal` command available globally

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

## 🛠️ Configuration

### Environment Variables

- `PORT` - Default port (default: 3030)
- `XDG_STATE_HOME` - Instance state directory (default: `~/.local/state`)

### Instance State

Instance information is stored in:
- **Linux**: `~/.local/state/excalocal/instances.json`
- **macOS**: `~/Library/Application Support/excalocal/instances.json`
- **Windows**: `%APPDATA%\excalocal\instances.json`

## 🐛 Troubleshooting

### Common Issues

**Port already in use:**
```bash
# excalocal automatically finds the next available port
excalocal  # Will use 3031 if 3030 is busy
```

**Command not found:**
```bash
# Make sure excalocal is installed globally
npm list -g excalocal

# If not installed, install it:
npm install -g excalocal
```

**Permission issues on Linux/macOS:**
```bash
# If you get permission errors, you may need to use sudo
sudo npm install -g excalocal
```

## 🙏 Acknowledgments

Special thanks to:

- **[Dawid Wraga](https://github.com/DawidWraga)** for the brilliant solution on implementing custom fonts in Excalidraw. His article ["How to use a custom font on Excalidraw.com"](https://dev.to/dawidcodes/how-to-use-a-custom-font-on-excalidrawcom-4jl4) was the foundation that made the Excalifont integration possible.

- **[The Excalidraw Team](https://github.com/excalidraw/excalidraw)** for creating this amazing virtual whiteboard tool that makes sketching and diagramming so intuitive and enjoyable.

## 📝 License

MIT License - see LICENSE file for details.

## 🚀 Uninstall

```bash
npm uninstall -g excalocal
```
