# Joplin Desktop Flatpak

A Flatpak build configuration for Joplin Desktop, the open-source note-taking and to-do application.

## About

This repository contains the Flatpak manifest to build and package Joplin Desktop as a Flatpak application. Joplin is a free, open-source note-taking and to-do application that supports markdown formatting, end-to-end encryption, and synchronization across multiple devices.

## Features

- Network access for synchronization
- Hardware acceleration support (DRI)
- Desktop integration with proper icons and .desktop file

## Build Requirements

- Flatpak
- Flatpak Builder

## Building

1. Clone the repo:
```bash
git clone https://github.com/overwatcheddude/Joplin_Flatpak
```

2. Change directory:
```bash
cd Joplin_Flatpak
```

3. Install the app:
```bash
flatpak run org.flatpak.Builder --user --install --force-clean build-dir io.github.overwatcheddude.joplin_desktop.yml
```

## Running

After installation, you can run Joplin Desktop using:

```bash
flatpak run io.github.overwatcheddude.joplin_desktop
```

Or launch it from your desktop environment's application menu.

## Permissions

This Flatpak has the following permissions:

- **Wayland socket**: For GUI display
- **DRI device access**: Hardware acceleration support
- **Network access**: For synchronization with cloud services

## Technical Details

### Build Process

The build process:

1. Downloads the official Joplin `.deb` package
2. Extracts the package contents
3. Copies application files to the appropriate Flatpak directories
4. Creates a wrapper script that launches Joplin with `--no-sandbox` flag
5. Installs desktop integration files (icons and .desktop file)
6. Updates the .desktop file to work correctly within the Flatpak environment

### File Structure

- Main application files are installed to `/app/joplin_desktop/`
- Executable wrapper script is placed in `/app/bin/joplin_desktop`
- Desktop integration files are installed to standard XDG locations
- Icons are properly integrated into the hicolor icon theme

## Troubleshooting

### Synchronization issues
- Verify network connectivity
- Check Joplin's synchronization settings
- Ensure your sync service credentials are correct

### File access problems
- If you need access to other locations, you may need to override permissions

## Related Links

- [Joplin GitHub Repository](https://github.com/laurent22/joplin)
- [Flathub-provided Joplin GitHub Repository](https://github.com/flathub/net.cozic.joplin_desktop)