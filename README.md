<div align="center">

# Skera

**A viewer that edits, without ever leaving the picture.**

A fast, image-first desktop viewer and light editor. Open a folder of full-resolution photographs — camera RAW included on macOS and Linux — and move through them instantly, with the full EXIF record, side-by-side compare, and non-destructive White Balance / Tone / HSL editing.

[**Download the latest release**](https://github.com/AdnanTemurBarcha/skera-releases/releases/latest) ·
[Website](https://skera.nexylius.com) ·
[Guide](https://skera.nexylius.com/raw-image-viewer/) ·
[Privacy](https://skera.nexylius.com/privacy/)

macOS (Apple Silicon and Intel) · Windows · Linux

</div>

---

## What this repository is

This is the **public releases repository for Skera**. It holds the installers and nothing else: every release here is built automatically from the Skera source repository and published to this page so anyone can download it without an account.

The Skera application source is private. There is no code to browse here. To get the app, use the [Releases](https://github.com/AdnanTemurBarcha/skera-releases/releases) page; to learn what it does, read below or visit [skera.nexylius.com](https://skera.nexylius.com).

## What is Skera?

Skera is a navigation engine for images, not a photo manager. There is no catalog and no import step: point it at a folder and the pictures are there.

- **Reads RAW directly** — NEF, CR2, ARW, DNG, RAF and more, on macOS and Linux.
- **Instant next and previous** — a byte-budgeted image cache, a priority thread pool that cancels work you have moved past, and neighbour preloading.
- **Full EXIF** — body, lens, exposure, ISO and GPS in an Info panel (`I`).
- **Side-by-side compare** — lock image A, sweep through B; zoom and pan stay linked (`C`).
- **Light, non-destructive editing** — White Balance, Basic Tone, Presence and an eight-channel HSL panel, previewed live (`E`). Nothing is written until you choose **Save** or **Save a Copy**.
- **Image-first** — `Tab` hides the toolbar and filmstrip so it is just the picture, and everything is on the keyboard.

## Downloads

Each release contains four files and a checksum list. Pick the one for your system:

| System | File | Notes |
| --- | --- | --- |
| **macOS — Apple Silicon** (M1, M2, M3 and later) | `Skera-<version>-mac-arm64.dmg` | Drag to Applications |
| **macOS — Intel** | `Skera-<version>-mac-intel.dmg` | Drag to Applications |
| **Windows** (64-bit) | `Skera-<version>-windows-setup.exe` | Installer with Start Menu shortcut and an uninstaller |
| **Linux** (x86_64) | `Skera-<version>-linux-x86_64.AppImage` | Single file, no install step |

**RAW support:** the macOS and Linux builds open camera RAW files. The Windows build opens every common format (JPEG, PNG, WebP, TIFF, GIF, BMP) but not RAW yet.

**Not sure which Mac you have?** Open the Apple menu → **About This Mac**. If the chip says *Apple M…*, use the Apple Silicon build. If it says *Intel*, use the Intel build.

[**→ Go to the latest release**](https://github.com/AdnanTemurBarcha/skera-releases/releases/latest)

## Installing

> **Builds are not code-signed yet.** Your operating system will warn about an "unidentified developer" the first time you open Skera. That is expected, and the steps below get past it once.

### macOS

1. Open the `.dmg` and drag **Skera** onto the **Applications** shortcut.
2. Open **Applications**, then **right-click Skera → Open**, and confirm.
3. On **macOS 15 (Sequoia) or later** the right-click shortcut may not offer *Open*. In that case, try to open the app once, then go to **System Settings → Privacy & Security**, scroll to the message about Skera and click **Open Anyway**.

You only need to do this the first time.

### Windows

1. Run `Skera-<version>-windows-setup.exe` and follow the wizard.
2. If SmartScreen says *"Windows protected your PC"*, click **More info**, then **Run anyway**.

Skera installs to Program Files, adds a Start Menu shortcut (and a desktop one if you tick the box), and can be removed from **Settings → Apps** like any other program.

### Linux

1. Make the file executable, then run it:

   ```bash
   chmod +x Skera-*-linux-x86_64.AppImage
   ./Skera-*-linux-x86_64.AppImage
   ```

2. If it does not start, your system may be missing FUSE 2, which AppImages use. On Ubuntu and Debian:

   ```bash
   sudo apt install libfuse2
   ```

   or run it without FUSE:

   ```bash
   ./Skera-*-linux-x86_64.AppImage --appimage-extract-and-run
   ```

The AppImage needs glibc 2.31 or newer (Ubuntu 20.04+, Debian 11+, Fedora 34+). It bundles Qt; a few system libraries (xcb, fontconfig) are assumed to be present, as they are on virtually every desktop distribution.

### Verifying a download (optional)

Every release includes `SHA256SUMS.txt`. Download it next to your file, then:

```bash
# macOS / Linux
shasum -a 256 -c SHA256SUMS.txt --ignore-missing

# Windows (PowerShell) — compare the output with the line in SHA256SUMS.txt
Get-FileHash .\Skera-*-windows-setup.exe -Algorithm SHA256
```

## Using Skera

1. **Open a folder** with `⇧⌘O` / `Ctrl+Shift+O`, or a single image with `⌘O` / `Ctrl+O`.
2. Move with `←` / `→` / `Space`, jump with `Home` / `End`. The wheel zooms; drag to pan.
3. `I` shows EXIF, `C` enters compare mode, `E` opens the Edit panel, `Tab` hides the chrome, `Esc` leaves the current mode.
4. **Save** (`⌘S` / `Ctrl+S`) overwrites the original after asking. **Save a Copy** (`⇧⌘S` / `Ctrl+Shift+S`) writes a new file and never touches the original.

The full shortcut list is on the [website](https://skera.nexylius.com).

## Your data and privacy

- **Local only.** Skera has no account, no sign-in, no analytics and no telemetry, and it makes **no network requests**.
- **Your images never leave your machine.** Skera reads the files you open and writes only when you choose Save or Save a Copy.

Full policy: [skera.nexylius.com/privacy](https://skera.nexylius.com/privacy/).

## Uninstalling

- **macOS** — drag Skera from Applications to the Trash.
- **Windows** — uninstall it from **Settings → Apps**.
- **Linux** — delete the AppImage.

## Updating

Skera does not update itself. To update, download the newest release from the [Releases](https://github.com/AdnanTemurBarcha/skera-releases/releases) page and install it over the old one.

## Reporting a problem or asking for a feature

Please [open an issue](https://github.com/AdnanTemurBarcha/skera-releases/issues) in this repository, or email **adnantemur.se@gmail.com**. It helps to include:

- your operating system and version, and whether it is Apple Silicon or Intel on a Mac,
- the Skera version (the release tag you downloaded),
- the kind of file involved (for RAW problems, the camera model),
- what you did, what you expected, and what happened instead.

## About

Skera is built by [Adnan Temur Barcha](https://adnantemurbarcha.nexylius.com) and published under the [Nexylius](https://nexylius.com) brand, alongside other local-first tools.

The application source is private; only the installers are published here.
