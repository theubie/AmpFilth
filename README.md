# AmpFilth

AmpFilth is a HISE-based audio effects plugin project that targets **VST3** and is designed to add subtle (or obvious) analog-style amp artifacts, especially **hum** and **hiss**, to incoming audio.

## Project snapshot

- **Plugin name:** AmpFilth  
- **Current project version:** 0.1.1  
- **Format target:** VST3  
- **Effect category:** Distortion  
- **Company:** Infinite Possibility Media

Core metadata lives in `project_info.xml` and `user_info.xml`.

## What it does

The current patch architecture (see preset backup `v0.1.1`) blends:

- A **dry** path.
- A **wet artifact** path with synthetic amp-noise style components.
- Controllable parameters for:
  - **Hum Level**
  - **Hiss Level**
  - **Hiss Tone**
  - **Output / wet level behavior**

From the DSP network and preset data, the wet signal is built from:

- Low-frequency oscillator components representing mains-style hum (eg. 60/120 Hz style layers).
- Noise-style hiss shaping with filter tone control.
- Gain staging / wet mix controls.

## Repository layout

- `project_info.xml` – HISE project/plugin settings (name, version, plugin categories, export flags).
- `user_info.xml` – developer / company metadata.
- `DspNetworks/` – modular DSP network definitions (eg. `hiss.xml`).
- `Scripts/ScriptProcessors/` – HISE script processor folders per version (`v01`, `v011`, `v02`).
- `Presets/` – `.hip` project presets and autosaves.
- `XmlPresetBackups/` – readable XML snapshots of patch state and UI data.
- `Images/` and `PooledResources/` – bundled artwork/resources.

## Build / export notes (HISE)

This repository is a **HISE project source**, not a standalone CMake project.

Typical workflow:

1. Open the project in HISE.
2. Load the desired preset/version (eg. `v0.1.1` or `v02`) for editing.
3. Verify control mappings and DSP network parameters.
4. Use HISE export tools to build the VST3 target.

Because build/export behavior is HISE-version dependent, ensure your local HISE setup matches the project expectations before release builds.

## Current state

- The repository contains multiple iteration snapshots (`v01`, `v0.1.1`, `v02`).
- Script processor files in the latest folder are currently minimal scaffolding, while significant signal flow lives in preset/network XML.

## Suggested next README additions

As the plugin evolves, consider adding:

- Audio examples (before/after hum & hiss).
- Screenshot of the plugin UI.
- Parameter range table with defaults and automation behavior.
- Release changelog section.
- Exact tested HISE commit/version and OS build matrix.

---

If you are opening this repo for the first time, start by inspecting `project_info.xml` and `XmlPresetBackups/v0.1.1.xml` to understand the active architecture.
