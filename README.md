# TileMapCollisionManager — Lite

> **Stop fighting your engine. Ship faster.**

---

## The Problem

`TileMap.set_layer_enabled()` takes a layer index — a raw integer. Your layers have names. Every time you refactor your TileMap structure, those indices silently shift and your collision code breaks in ways that produce no error messages. You are manually maintaining a number↔name mapping in your head.

---

## The Solution

Drop `script.gd` onto your TileMap node. It builds a name→index cache at startup and exposes a clean string-based API. Call `set_collision_enabled_by_name("Ground", true)` instead of `set_layer_enabled(2, true)`. Your code survives TileMap restructuring.

No plugins. No autoloads. One file.

---

## What's in the Lite Version

- Automatic name→index cache built on `_ready()`
- `set_collision_enabled_by_name(name, bool)` — single layer control
- `refresh_layer_cache()` — rebuild cache after runtime structural changes
- Inspector-configured initial collision state on scene load
- Duplicate layer name detection and warnings
- Debug layer map printing

## What's in the Full Version

The full version adds **batch methods** (`enable_layers_by_name`, `disable_layers_by_name`), **global toggles** (`disable_all_collision`, `enable_all_collision`), and **state serialization** (`get_collision_state_snapshot`, `restore_collision_state_snapshot`) — essential for save/load systems and cutscene state management.

**Full version on itch.io:** https://nullstateassets.itch.io

---

## Quick Start

1. Copy `script.gd` into your Godot project.
2. Attach it to your TileMap node (replaces it — TileMap is the base class).
3. Add your layer names to `initial_enabled_layers` in the Inspector.
4. Hit **Play**.

---

## Compatibility

| Engine    | Language  | Tested On    |
|-----------|-----------|--------------|
| Godot 4.x | GDScript  | 4.2, 4.3     |

---

## License

MIT License. Free for personal and commercial use. Attribution appreciated but not required.
