# Cursor Ops — GitHub Changelog

This document tracks public, user-visible changes by version.

---

## v1.0.0 — Stable Release

Type: Stable Release  
Release Date: 2026-02-23

### Added
- Quick Menu for direct access to:
  - Cursor Move
  - Cursor Rotate
  - Cursor Flip Z
  - Local Z alignment (Top / Center / Bottom)
  - Cursor ↔ Active sync utilities
- Emergency modal cleanup system preventing stuck timers or draw handlers
- Explicit Object Mode validation across all operators

### Improved
- Confirm and cancel reliability across modal operators
- Viewport draw stability and timer handling
- WPlane grid shader compatibility
- Rotate gizmo drawing consistency
- Add-on metadata and issue reporting integration

### Compatibility
Tested on:
- Blender 3.3.19 LTS
- Blender 3.6.21 LTS
- Blender 4.2.18 LTS
- Blender 4.5.7 LTS
- Blender 5.0.1

---

## v0.6.0 — Gizmos and Working Plane

### Added
- Cursor gizmo system for visual manipulation.
- Working Plane (WPlane) grid tools.
- Add‑on preferences for shortcut visibility and reset.
- Header toggles for gizmos and grid.

### Improved
- Rotate snapping behavior with refined modifier combinations.
- Keymap registration framework.

---

## v0.5.0 — Workflow Simplification

### Changed
- Removed legacy origin tools to focus on cursor workflows.
- Streamlined panel layout and reduced UI complexity.

### Improved
- Cursor Move responsiveness.

---

## v0.4.1 — Modular Architecture

### Changed
- Converted add‑on from single file to modular package structure.
- Updated branding and metadata.

---

## v0.4.0 — Input and HUD Refinements

### Improved
- Modal input filtering and confirmation behavior.
- HUD rendering clarity.

---

## v0.3.0 — Sync System Introduction

### Added
- Local Z Sync for persistent cursor alignment.
- Sync to Active workflow.

---

## v0.2.0 — Cursor Engine Expansion

### Added
- Cursor Move and Rotate modals.
- Placement system with snapping and flip tools.
- Cursor ↔ Active utilities.

---

## v0.1.0 — Initial Release

### Added
- Local Z origin and cursor placement tools.
- Basic N‑panel workflow.
