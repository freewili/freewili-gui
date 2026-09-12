# FreeWili GUI

Desktop application for working with FreeWili boards: device console, GPIO,
I2C, SPI, UART, logic analyzer and player, Wili Blocks editor, simulator and
more.

## Download

Builds are published on the **[Releases](https://github.com/freewili/freewili-gui/releases)** page.
The current downloads for each platform are:

| Platform | Version | Download |
| --- | --- | --- |
| macOS Apple Silicon (arm64), macOS 26.0+ | 0.2.0 | [freewili-gui-0.2.0-macos-arm64.zip](https://github.com/freewili/freewili-gui/releases/download/v0.2.0/freewili-gui-0.2.0-macos-arm64.zip) |
| Windows (x64) | 0.1.3 | [fwcom-0.1.3.zip](https://github.com/freewili/freewili-gui/releases/download/v0.1.3/fwcom-0.1.3.zip) |
| Linux (x86_64) | 0.1.3 | [fwcom-0.1.3-linux-x86_64.zip](https://github.com/freewili/freewili-gui/releases/download/v0.1.3/fwcom-0.1.3-linux-x86_64.zip) |

The macOS release is 0.2.0; Windows and Linux downloads remain at 0.1.3.

### Windows (x64)

1. Download [fwcom-0.1.3.zip](https://github.com/freewili/freewili-gui/releases/download/v0.1.3/fwcom-0.1.3.zip).
2. Extract it to a folder you can write to, such as your Documents or Desktop
   folder. The app stores its `data\` folder and settings next to `fwcom.exe`,
   so `C:\Program Files` will not work.
3. Run `fwcom.exe`.

Notes:

- The build is not code-signed, so Windows SmartScreen warns on first launch.
  Choose **More info**, then **Run anyway**.
- A GPU driver with Vulkan support is required.
- Everything the app needs is inside the zip. No installer or separate runtime
  is needed.

### Linux (x86_64)

1. Download `fwcom-0.1.3-linux-x86_64.zip` and extract it to a folder you can write to (for example your home directory). The app writes its `data/` folder and settings next to the `fwcom` binary; if that folder is read-only it falls back to `~/.local/share/fwcom`.
2. Install the system libraries the build links against. On Debian 13 / Ubuntu 24.04 and newer:
   `sudo apt install libavcodec61 libavformat61 libavutil59 libswresample5 libswscale8 libsqlite3-0 libegl1 libssl3t64 libbrotli1 libudev1`
   (older Ubuntu releases ship different FFmpeg package versions; the exact sonames the binary needs are listed in `README-linux.txt` inside the zip.)
3. Run `./fwcom`.

Notes:

- Built on Debian 13 (glibc 2.41, GCC 14). It will not start on older distributions with an older glibc.
- Requires a GPU driver with Vulkan support.
- Unlike the Windows zip, FFmpeg and OpenSSL are not bundled; they come from the distribution packages above.
- Optional at runtime: `libsecret-1-0` (remembers the AI API key), `xdg-utils` (Open-folder buttons), `pulseview` (Logic Analyzer VCD hand-off), `python3` + `python3-debugpy` (Python editor Run/Debug).
- `desktop/` inside the zip has a `.desktop` entry and icon if you want a launcher.
- The C-to-WASM compiler toolchain (`config/wiliclang`) is Windows-only for now; on Linux the WASM editor looks for a `wiliclang` on `$PATH`.

### macOS (Apple Silicon / arm64)

Requires an Apple Silicon Mac running macOS 26.0 or later. This build does not
run on Intel Macs.

1. Download [freewili-gui-0.2.0-macos-arm64.zip](https://github.com/freewili/freewili-gui/releases/download/v0.2.0/freewili-gui-0.2.0-macos-arm64.zip).
2. Extract the ZIP and move **FreeWili GUI.app** to Applications.

Notes:

- This build is ad-hoc signed, not Developer ID signed or notarized. macOS
  Gatekeeper may block a downloaded copy; signing and notarization are still
  required for normal customer distribution.
- Python 3.13, its debugger, the OneWili API, Clang, wasm-ld, and runtime
  libraries are bundled. Homebrew is not required for the included tools.
- Projects and settings are stored in
  `~/Library/Application Support/FreeWili GUI/`.
- The HackRF plugin is not included in this package. See the
  [0.2.0 release notes](https://github.com/freewili/freewili-gui/releases/tag/v0.2.0) for details and known limitations.

## Release notes

See [CHANGELOG.md](CHANGELOG.md).

## Reporting problems

Open an issue on this repository and include the release version shown on the
app's Welcome screen, your operating system and version, and what you were
doing when the problem occurred.
