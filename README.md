# SyxDroid

**Created by [SHAGAABI](https://github.com/shagaabi)**  
**Official Community & Bug Reports:** [**r/SyxDroid on Reddit**](https://www.reddit.com/r/SyxDroid/s/6odWkSNALp)

**SyxDroid** is a native Android launcher and runtime port for the fantasy city-state and empire simulator **Songs of Syx**. It executes the desktop game's Java bytecode and custom **Snake2D** engine directly on Android's native 64-bit runtime (**ART**) with hardware-accelerated **OpenGL ES 3.2** graphics and native Android audio—without CPU emulation.

---

## ⚠️ Important Legal Requirement — PC Game Files Required

> **SyxDroid does NOT include, bundle, or distribute the game *Songs of Syx* or any copyrighted game assets.**  
> To play *Songs of Syx* on Android using SyxDroid, you **must own a legitimate PC copy of *Songs of Syx*** (available on [Steam](https://store.steampowered.com/app/1162750/Songs_of_Syx/), [GOG](https://www.gog.com/en/game/songs_of_syx), or [Itch.io](https://gamatron.itch.io/songs-of-syx)) and import your own PC game `.zip` archive into the launcher.

---

## ⚙️ How SyxDroid Works

Desktop *Songs of Syx* is built on a custom engine (**Snake2D**) designed around desktop LWJGL 3, GLFW windowing, desktop OpenGL 3.3 Core Profile, STBImage, OpenAL, and desktop Java NIO `zipfs` filesystems. SyxDroid bridges these systems natively to Android:

1. **Direct Bytecode Execution on Android ART:** Runs the game's Java logic natively on ARM64 Android devices without Box64, Winlator, or x86_64 CPU emulation overhead.
2. **Real-Time OpenGL ES 3.2 Shader Translator:** Translates desktop `#version 330 core` Vertex, Fragment, and Geometry shaders into `#version 320 es` shaders on the fly, supporting Multiple Render Targets (**MRT**) deferred lighting, normal mapping, dynamic shadows, and `sampler2DRect` texel fetching (`texelFetch`).
3. **Native Android Audio Engine:** Replaces desktop OpenAL and STBVorbis with a low-latency Android `SoundPool` engine for spatial `.wav` sound effects and `MediaPlayer` streaming for `.ogg` music and ambience tracks.
4. **Android Virtual Filesystem & PC Archive Importer:** Automatically extracts PC game archives (`base/data.zip`, `base/locale.zip`, and script packages), strips out unnecessary Windows `jre/` and `.dll` files, and resolves Windows paths case-insensitively inside Android private storage.
5. **Memory & Pathfinding Optimization:** Uses lazy row allocation and automatic floodfill tile eviction to reduce Java heap pressure so settlements and tutorials can load even on Android devices with strict 256 MB per-app heap limits.
6. **Touchscreen & Custom On-Screen Controls:** Translates Android touch gestures, pinch-to-zoom, virtual camera joysticks, and customizable on-screen hotkeys directly into Snake2D's input polling loop.

---

## 📱 Minimum System Requirements

| Component | Minimum Requirement | Recommended |
| :--- | :--- | :--- |
| **OS** | Android 8.0+ (64-bit ARM64) | Android 12.0+ (64-bit ARM64) |
| **GPU** | OpenGL ES 3.2 support (**Qualcomm Adreno** or **ARM Mali**) | Adreno 610+ / Mali-G57+ or higher |
| **RAM** | 4 GB Device RAM | 6 GB – 8 GB+ Device RAM |
| **Storage** | ~1.2 GB free internal space for extracted game assets | 2 GB+ free internal space |
| **Game Files** | Legitimate PC copy of *Songs of Syx* packaged as a `.zip` archive | Windows or Linux PC archive |

---

## 🚀 How to Install & Play

1. **Prepare Your PC Game Archive:**
   * On your PC (or phone), zip your *Songs of Syx* installation folder (containing `SongsOfSyx.jar`, the `base/` folder with `data.zip` and `locale.zip`, etc.) into a `.zip` file (e.g., `Songs of Syx.zip`) and copy it to your phone's `Download` folder.
2. **Install SyxDroid:**
   * Download the latest `.apk` from the [**Releases**](../../releases) section and install it on your Android device.
3. **Import Your Game ZIP:**
   * Open **SyxDroid** and tap the **`⋮`** or **`▶`** button on the instance card (or open the **`☰`** menu and tap **Import PC Game .ZIP**).
   * Select your `Songs of Syx.zip` archive and wait ~15–20 seconds while SyxDroid unpacks `base/data.zip` and `base/locale.zip` and strips out PC runtime bloat.
4. **Configure & Launch:**
   * Tap **`⚙`** on your instance card to choose your preferred internal resolution (`768p`, `864p`, `960p`, or `1080p`), rendering pipeline (**Deferred Lighting** or **Flat Fast Mode**), and **Easy Font** mode.
   * Tap **`▶`** to launch the game!

---

## 🎮 Controls & Features

### On-Screen Control Layout Editor
Open **Edit Controls** from the home screen or the in-game **`⚙`** menu to drag, resize, toggle circle/rectangle shapes, enable grid snapping, toggle button backgrounds, or add new buttons for any *Songs of Syx* hotkey:
- **Camera Movement:** Virtual Joystick (`W` / `A` / `S` / `D` normal scroll, or `Shift + ↑/↓/←/→` slow scroll when `⇧ SHFT` is toggled on).
- **Zoom & Interface:** `N` (Zoom In), `B` (Zoom Out), `M` (Minimap), `Ctrl + X` (Throne / Capital), `Ctrl + F` (Search), `Ctrl + A` (Center / Activate Jobs), plus two-finger pinch-to-zoom.
- **Building & Selection:** `R` (Rotate Object), `E` (Increase Size), `Q` (Decrease Size), `Ctrl + Space` (Select), `Space` (Show / Inspect), `Left Shift` (Place-undo / Slow camera modifier).
- **Game Speed & System:** `P` (Pause), `1` (1x / 1/4x), `2` (3x), `3` (25x), `4` (250x), `Ctrl + S` (Quicksave / Suspend jobs), `Print Screen` (Screenshot), `F11` (Debugger / Stats).
- **Mouse & Navigation:** Dedicated `L-CLK` and `R-CLK` buttons, `Enter` (Confirm), `Backspace` (Back), `Esc` (Menu), and on-screen keyboard toggle (`⌨`).

### Multi-Instance Manager & Save Import / Export
- **Multiple Instances:** Tap **`＋`** to create additional game instances. You can either share base game data from your primary installation (instant setup with isolated saves and settings) or import a separate `.zip` archive.
- **Import & Export Saves:** Easily import `.save` files or `.zip` save packs into any instance, or export individual `.save` files or a full `.zip` backup of all your saved cities to your phone.

---

## 💬 Community, Discussions & Bug Reports

Join the official **SyxDroid** subreddit to share your cities, request features, discuss performance settings, or report bugs (please include your device model, GPU, and the output from the in-app **Logs** button):

👉 [**Official Subreddit: r/SyxDroid**](https://www.reddit.com/r/SyxDroid/s/6odWkSNALp)

---

## 👑 Credits & Acknowledgements

- **Project Creator & Lead Developer:** **SHAGAABI** ([@shagaabi](https://github.com/shagaabi)) — SyxDroid architecture, native Android runtime & GLES 3.2 integration, audio engine, multi-instance manager, and control system.
- **Songs of Syx & Snake2D Engine:** **Jakob de Laval (Gamatron AB)** — Creator and developer of [*Songs of Syx*](https://songsofsyx.com). All original game code, mechanics, and assets belong to Gamatron AB.
- **Graphics & Runtime Compatibility Layer:** Custom LWJGL 3 (`GL11`–`GL32`, `GLFW`, `MemoryUtil`, `STBImage`, `OpenAL`) to Android `GLES32`, `BitmapFactory`, `SoundPool`, and `MediaPlayer` bridge.
- **UI & Control Editor Inspiration:** Inspired by community Android launchers including **RimDroid** and **Zomdroid**.
