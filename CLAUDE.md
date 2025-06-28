# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Repository Overview

This is a configuration repository for AeroSpace, an i3-like tiling window manager for macOS. The main configuration file is `aerospace.toml`.

## Key Configuration Elements

### Window Management
- Gap size: 8px between windows and screen edges
- Mouse follows focus when switching windows/monitors
- Primary modifier key: `alt`

### Keybinding Patterns
- Navigation: `alt+{h,j,k,l}` (vim-style directional movement)
- Window movement: `alt+shift+{h,j,k,l}`
- Workspace switching: `alt+{1-9}` and `alt+{a-z}`
- Layout modes: `alt+/` (tiles), `alt+,` (accordion)
- Service commands: `alt+shift+;` (reload config, flatten tree, etc.)

### App-Specific Rules
- Ghostty terminal: Set to floating layout by default (see `[[on-window-detected]]` section)

## Common Tasks

### Apply Configuration Changes
1. Edit `aerospace.toml`
2. Reload config: Press `alt+shift+;` then `r`

### Add New Keybinding
Add to the `[mode.main.binding]` section following the existing pattern:
```toml
alt-<key> = '<command>'
```

### Configure App Behavior
Add to `[[on-window-detected]]` section:
```toml
[[on-window-detected]]
if.app-id = 'com.example.app'
run = 'layout floating'
```

## Architecture Notes

- Single TOML configuration file controls all behavior
- No build system or tests - pure configuration
- Configuration is loaded by AeroSpace daemon on startup/reload
- Changes require manual reload via keybinding
- Repository also contains `.wezterm.lua` (unrelated terminal config)