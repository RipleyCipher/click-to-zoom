# click-to-zoom

> **Forked from [BlankSourceCode/obs-zoom-to-mouse](https://github.com/BlankSourceCode/obs-zoom-to-mouse)**
> 
> This project is a variant of the original OBS Zoom-to-Mouse script by BlankSourceCode. Full credit for the core implementation and concept goes to the original author. This fork is called **click-to-zoom** to reflect its focus on click/keyboard hotkey-based zooming and modernized documentation.

---

## What is click-to-zoom?

**click-to-zoom** is an OBS Lua script that lets you smoothly zoom in on a display capture source, centering the zoom on your mouse position. It is ideal for tutorials, code walkthroughs, or any scenario where you want to highlight a part of your screen in real time. Zooming is triggered by a hotkey ("click to zoom"), and the script can optionally follow your mouse as you move.

- **Platform support:** Windows, Linux, and Mac
- **Smooth animation:** Zoom in/out with customizable speed
- **Hotkey-driven:** Assign hotkeys to toggle zoom and mouse following
- **Auto-follow:** Optionally track the mouse while zoomed in
- **Multi-monitor aware:** Can auto-select the correct display source under your mouse
- **Advanced options:** Manual source position, scaling, and more
- **Debug logging:** For troubleshooting and advanced users

---

## Installation

1. Download or copy `click-to-zoom.lua` from this repository.
2. Launch OBS Studio.
3. Add a **Display Capture** source to your scene (if you don't have one already).
4. Go to **Tools → Scripts** in OBS.
5. Click the `+` button and add `click-to-zoom.lua`.
6. (Optional) For best results, set your Display Capture source's transform:
   - **Positional Alignment:** Top Left
   - **Bounding Box type:** Scale to inner bounds
   - **Alignment in Bounding Box:** Top Left
   - **Crop:** All zeros
7. (Optional) If you want to crop, add a **Crop/Pad** filter (set to Relative: False).

> **Note:** If your Display Capture source uses a different transform/crop, the script may attempt to auto-correct it for zoom compatibility, which could affect your layout.

---

## Usage

### Hotkeys
- Go to **File → Settings → Hotkeys** in OBS.
- Assign hotkeys for:
  - `Toggle zoom to mouse` (main zoom in/out action)
  - `Toggle follow mouse during zoom` (optional: toggle auto-follow)

### Script Settings
Open the **Scripts** window and select `click-to-zoom.lua` to configure:

- **Zoom Source:** Which display capture to zoom
- **Zoom Factor:** How much to zoom in
- **Zoom Speed:** Animation speed for zoom in/out
- **Auto follow mouse:** Track the mouse automatically while zoomed in
- **Follow outside bounds:** Continue tracking even if the mouse leaves the source
- **Follow Speed:** How quickly the zoomed area follows the mouse
- **Follow Border:** How close to the edge the mouse must get before following
- **Lock Sensitivity:** How still the mouse must be before "locking" the view
- **Auto Lock on reverse direction:** Stop following if you move the mouse back toward the center
- **Show all sources:** Allow any OBS source (not just display capture) as the zoom target (requires manual position setup)
- **Set manual source position:** Manually specify the source's position, size, and scale if auto-detection is wrong or using a non-display source
- **Debug logging:** Enable extra output for troubleshooting
- **Auto-select source by mouse position:** Automatically pick the display source under your mouse before zooming/following

### How it works
- Press your assigned hotkey to zoom in on the current mouse position.
- If auto-follow is enabled, the view will track your mouse as you move.
- When you move the mouse to the edge of the zoomed area, the view will follow; when you stop, it "locks" until you move to the edge again.
- Press the hotkey again to zoom out.

---

## Advanced Features
- **Multi-monitor support:** Can auto-select the correct display capture based on mouse position.
- **Manual overrides:** For non-standard sources or complex setups, you can manually specify source geometry and scaling.
- **Debug logging:** Enable to get detailed logs in the OBS script log for troubleshooting.

---

## Known Limitations
- Automatic zoom/follow only works with Display Capture sources by default. For other sources, you must manually set position/size.
- On Linux, you may need to install extra packages for display capture compatibility.
- On Mac, manual monitor height may be needed for correct Y coordinate handling.
- Dual machine/remote mouse tracking is described in the original project but not implemented in this fork.

## Additional notes
- In order for this script to work on Fedora Linux 43, it's necessary to execute OBS with the following setting: QT_QPA_PLATFORM=xcb, in order to avoid the execution with Wayland, which avoid sharing mouse position between different applications.

<img width="829" height="433" alt="image" src="https://github.com/user-attachments/assets/72512d3f-4e4a-4e7b-819a-508b953262c0" />


---

## Credits
- **Original Author:** [BlankSourceCode/obs-zoom-to-mouse](https://github.com/BlankSourceCode/obs-zoom-to-mouse)
- **Forked by eadmin2:** https://github.com/eadmin2/click-to-zoom
- **Forked as:** click-to-zoom (this project)
- **Inspired by:** [tryptech/obs-zoom-and-follow](https://github.com/tryptech/obs-zoom-and-follow)
- **Inspired by:** [giswqs/obs-zoom-to-mouse](https://github.com/giswqs/obs-zoom-to-mouse)

---

## Development
- Edit `click-to-zoom.lua` as needed
- Click `Reload Scripts` in the OBS Scripts window to apply changes

