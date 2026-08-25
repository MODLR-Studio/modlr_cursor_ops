# Cursor Ops How-To Guide

A practical guide to the main Cursor Ops workflows.

Cursor Ops is built around a simple interaction loop:

**Place → Adjust → Apply**

---

## Core Workflow

The main workflow is:

1. Use **Cursor Move** to place and orient the 3D Cursor from selected geometry.
2. Refine orientation with **Cursor Rotate** or **Cursor Flip Z** if needed.
3. Use the cursor as a placement, transform, or pivot reference for the next operation.

For faster structure-based placement, use the **Local Z tools**.

For direct visual manipulation, enable the **Move Gizmo**, **Rotate Gizmo**, or **WPlane Grid** as needed.

---

## Cursor Move

**Cursor Move** is the primary and most configurable placement tool in Cursor Ops.

It is selection-driven: placement is calculated from the mesh components you select, not from a viewport raycast.

The modal combines placement, orientation, geometry interpretation, alignment controls, and optional visual systems in one continuous interaction.

### Basic Workflow

1. Run **Cursor Move**.
2. Select a face, edge, or vertex.
3. Add or remove components if needed.
4. Adjust alignment, geometry mode, or orientation if needed.
5. Press **Enter** to confirm or **Esc** to cancel.

### Selection Controls

- Click → select a component
- `Shift + Click` → add to or remove from the selection
- `Alt + A` → clear the current selection

Cursor Move uses deliberate component picking; drag selection and click-off deselection are disabled during the modal.

Cursor Move supports component-based placement on single or multiple selected mesh objects.

### Alignment Modes

Alignment modes control how cursor orientation is resolved.

- **Auto** → automatically chooses the most appropriate alignment from the selected geometry
- **Edge** → uses a clear directional edge when the geometry provides one
- **Local** → keeps orientation aligned consistently to the object’s local axes
- **World** → keeps orientation aligned consistently to the world axes

Use **Auto** for most placements.

If geometry defines a clear normal but no unique X/Y direction, such as a circular face or cylinder cap, **Local** or **World** can provide a more predictable orientation.

### Geometry Modes

Cursor Move can interpret either the original mesh or the evaluated modifier result.

- **Base Geo** → uses the original mesh topology
- **Baked Geo** → uses evaluated geometry with modifiers included

Switching between Base Geo and Baked Geo clears the current component selection because the underlying geometry may change.

### Force World

**Force World** separates placement position from orientation.

- **Off** → cursor orientation follows the selected geometry and alignment mode
- **On** → cursor position remains at the selected placement, but orientation is forced to world axes

Use Force World when you want geometry-based positioning with a consistent world-aligned orientation.

### Show Modifiers

**Show Modifiers** lets you see evaluated modifier geometry while continuing to select the base mesh.

This is useful when you want:

- the final modified shape visible
- selection restricted to the underlying topology

If Show Modifiers is enabled while using Baked Geo, Cursor Move switches to **Base Geo + Show Modifiers** so the evaluated geometry remains visual only.

### Inline Controls

- `R` → rotate 90° around local Z
- `F` → flip cursor Z

These controls allow quick orientation correction without leaving the modal.

### Visual Systems During Cursor Move

The following systems can be toggled while Cursor Move is active:

- Move Gizmo
- Rotate Gizmo
- WPlane Grid

They can be used independently or together.

### N-Panel Synchronization

Cursor Move mode controls are synchronized with the N-panel.

Changes to geometry and placement-mode settings made during the modal are reflected in the panel, and those settings can also be configured before entering Cursor Move.

Use Cursor Move when the cursor needs to inherit a precise position and orientation from selected geometry.

---

## Cursor Rotate

**Cursor Rotate** adjusts cursor orientation without changing its position.

### Basic Workflow

1. Run **Cursor Rotate**.
2. Move the mouse to rotate on the active axis.
3. Press `A` to cycle X, Y, and Z axes.
4. Use increment modifiers if needed.
5. Confirm with **Left Mouse Button** or **Enter**, or press **Esc** to cancel.

### Rotation Increments

- `Ctrl + Shift` → 1°
- `Ctrl` → 5°
- `Alt` → 15°
- `Ctrl + Alt` → 90°

You can also press `F` during rotation to flip the cursor Z axis.

The Move Gizmo, Rotate Gizmo, and WPlane Grid can also be toggled while Cursor Rotate is active.

Use Cursor Rotate when placement is already correct but orientation needs refinement.

---

## Local Z Tools

The Local Z tools provide fast placement along the selected object’s local Z axis without using the full Cursor Move workflow.

Available actions:

- **Top** → place at the upper local Z extent
- **Center** → place at the local Z midpoint
- **Bottom** → place at the lower local Z extent
- **Drop to Surface** → move the cursor to the next surface along its local negative Z axis

Top, Center, and Bottom use the object’s evaluated bounding extents, so modifier results are included.

### Drop to Surface

Drop to Surface behaves like a directional surface walker.

1. Position the cursor above or within the object.
2. Run **Drop to Surface**.
3. Run it again to move to the next intersecting surface.
4. Use **Cursor Flip Z** to reverse the traversal direction.

Drop to Surface evaluates surfaces on the selected active object and can work with modifier-generated geometry.

Use the Local Z tools when you need fast, predictable structure-based placement rather than component-driven placement.

---

## Gizmos and WPlane

Cursor Ops includes three independent visual systems:

- **Move Gizmo**
- **Rotate Gizmo**
- **WPlane Grid**

They can be used individually or together.

### Move Gizmo

- Move along X, Y, or Z
- Move across two-axis planes with the grab pad
- Use incremental snapping
- View live displacement feedback

### Rotate Gizmo

- Rotate around X, Y, or Z
- Use incremental snapping
- View live rotation feedback

### WPlane Grid

The WPlane Grid is a cursor-aligned visual reference for orientation and spatial feedback.

It helps make the cursor’s orientation easier to read during placement and adjustment.

The current WPlane Grid is visual only and does not provide direct snapping to the plane.

The Move Gizmo, Rotate Gizmo, and WPlane Grid can be enabled or disabled independently, including while using Cursor Move or Cursor Rotate.

---

## Sync and Pivot

The Sync tools transfer position and orientation between the 3D Cursor, the active object, and the object’s pivot/origin.

### Cursor to Active

Moves and aligns the cursor to the selected active object.

Use it to capture an existing object transform as cursor state.

### Active to Cursor

Moves and aligns the selected active object to the cursor.

Use it to place an object onto a previously defined cursor transform.

### Pivot to Cursor

Moves the selected active object’s pivot/origin to the cursor without moving the object itself.

### Basic Pivot Workflow

1. Place and orient the cursor where the pivot should be.
2. Run **Pivot to Cursor**.
3. Scale or rotate the object using the new pivot.

---

## Recall and Reset

### Recall Placement

**Recall Placement** restores the last confirmed Cursor Move placement.

It restores:

- Cursor position
- Cursor orientation

It does not restore wider Blender state such as snapping, active tools, viewport settings, or transform orientation settings.

The recall slot is stored automatically when Cursor Move is confirmed.

### Reset to World

**Reset to World** returns the cursor to:

- World origin
- World orientation

Use Recall Placement to recover a known placement state.

Use Reset to World when you want a clean world-space starting point.

---

## Common Workflows

### Place on Angled Geometry

1. Run Cursor Move.
2. Select the required component or components.
3. Adjust alignment or orientation if needed.
4. Confirm.

### Place from Modified Geometry

1. Run Cursor Move.
2. Switch to Baked Geo.
3. Select the evaluated geometry required for placement.
4. Confirm.

### Keep World Orientation on Geometry

1. Run Cursor Move.
2. Place from the required geometry.
3. Enable Force World.
4. Confirm.

### Place an Object from the Cursor

1. Place and orient the cursor.
2. Select the target object.
3. Run Active to Cursor.

### Set a Pivot from Geometry

1. Place the cursor with Cursor Move.
2. Run Pivot to Cursor.
3. Transform the object from the new pivot.

### Walk Through Surfaces

1. Position the cursor along the required local Z path.
2. Run Drop to Surface.
3. Repeat to move through successive surfaces.
4. Flip Z to reverse direction if needed.

### Refine Orientation Without Repositioning

1. Run Cursor Rotate.
2. Cycle axis if needed.
3. Use the appropriate rotation increment.
4. Confirm.

### Recover the Last Placement

1. Run Recall Placement.
2. Continue from the restored cursor position and orientation.

---

This guide is intentionally concise. Additional visual examples and deeper workflow coverage can be added over time.
