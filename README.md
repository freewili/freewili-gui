# FreeWili GUI

Desktop application for working with FreeWili boards: device console, GPIO,
I2C, SPI, UART, logic analyzer and player, Wili Blocks editor, simulator and
more.

## Download

Builds are published on the **[Releases](https://github.com/freewili/freewili-gui/releases)** page.
The current downloads for each platform are:

| Platform | Version | Download |
| --- | --- | --- |
| macOS Apple Silicon (arm64), macOS 26.0+, preview | 0.3.2 | [freewili-gui-0.3.2-macos-arm64.zip](https://github.com/freewili/freewili-gui/releases/download/v0.3.2/freewili-gui-0.3.2-macos-arm64.zip) |
| Windows (x64), preview | 0.3.1 | [fwcom-0.3.1.zip](https://github.com/freewili/freewili-gui/releases/download/v0.3.1/fwcom-0.3.1.zip) |
| Linux (x86_64) | 0.3.1 | [fwcom-0.3.1-linux-x86_64.zip](https://github.com/freewili/freewili-gui/releases/download/v0.3.1/fwcom-0.3.1-linux-x86_64.zip) |

Windows 0.3.1 is a **preview** with unresolved GUI regression tests. It includes
CM0 Linux tools, the Firmware Updater, and the OneWili binary streaming API.
Windows and Linux 0.3.1 include updater reliability fixes from Linux testing:
longer processor settling and reconnection waits, SD power/remount handling,
and clearer USB debug-probe errors. macOS 0.3.2 is a preview with native firmware
updating, SD-reader support, and FPGA-first CM0 startup. Complete Mac SD imaging,
clean-machine checks, and Developer ID signing/notarization remain outstanding.
Windows hardware flashing was not repeated for its 0.3.1 package.
The previous [Windows 0.1.3 stable download](https://github.com/freewili/freewili-gui/releases/download/v0.1.3/fwcom-0.1.3.zip) remains available.

### Windows (x64)

1. Download [fwcom-0.3.1.zip](https://github.com/freewili/freewili-gui/releases/download/v0.3.1/fwcom-0.3.1.zip).
2. Extract it to a folder you can write to, such as your Documents or Desktop
   folder. The app stores its `data\` folder and settings next to `fwcom.exe`,
   so `C:\Program Files` will not work.
3. Run `fwcom.exe`.

Notes:

- The build is not code-signed, so Windows SmartScreen warns on first launch.
  Choose **More info**, then **Run anyway**.
- A GPU driver with Vulkan support is required.
- The ZIP includes the C/C++ Wasm compiler, OneWili Python sources/examples,
  map tools, tutorial video libraries, and Linux Imager helper.
- Python Run/Debug requires Python 3.10+ with pip. Initial setup needs internet
  access for debugpy and the included OneWili package's dependencies.
- Display recovery through the built-in debug probe requires separately
  installed Raspberry Pi OpenOCD with RP2350 scripts. The Main recovery-loader
  path does not need it.
- PicoScope hardware requires its PicoSDK runtime and device driver. HackRF
  is not included in this package. Rust Wasm requires a separate Rust toolchain.
- Read the [0.3.1 release notes](https://github.com/freewili/freewili-gui/releases/tag/v0.3.1)
  for firmware requirements, verification results, and known limitations.

### Linux applications on FreeWili 2

Use [WiliCM0BSP](https://github.com/freewili/wilicm0bsp) for examples, agent
instructions, the CM0 driver, and a pinned [OneWili](https://github.com/freewili/onewili)
API. Put applications in the CM0 Linux **`/home/apps/` folder** for easy
launching from Linux Apps. The GUI's CM0 shell, file transfer, and Python tools
require compatible Main firmware and a CM0 image with the matching bridge.

### Linux (x86_64)

1. Download `fwcom-0.3.1-linux-x86_64.zip` and extract it to a folder you can write to (for example your home directory). The app writes its `data/` folder and settings next to the `fwcom` binary; if that folder is read-only it falls back to `~/.local/share/fwcom`.
2. Install the system libraries the build links against. On Debian 13:
   `sudo apt install libavcodec61 libavformat61 libavutil59 libswresample5 libswscale8 libsqlite3-0 libegl1 libssl3t64 libbrotli1 libudev1`
   (older Ubuntu releases ship different FFmpeg package versions; the exact sonames the binary needs are listed in `README-linux.txt` inside the zip.)
3. Run `./fwcom`.

Notes:

- Built on a Debian 13 derivative (glibc 2.41, GCC 14). It will not start on older distributions with an older glibc.
- Requires a GPU driver with Vulkan support.
- Unlike the Windows zip, FFmpeg and OpenSSL are not bundled; they come from the distribution packages above.
- Optional at runtime: `libsecret-1-0` (remembers the AI API key), `xdg-utils` (Open-folder buttons), `pulseview` (Logic Analyzer VCD hand-off), `python3` + `python3-debugpy` (Python editor Run/Debug).
- `desktop/` inside the zip has a `.desktop` entry and icon if you want a launcher.
- The C-to-WASM compiler toolchain (`config/wiliclang`) is Windows-only for now; on Linux the WASM editor looks for a `wiliclang` on `$PATH`.
- Includes OneWili Python sources and examples; Python itself is a system dependency.
- Firmware Updater requires USB permissions and a mounted recovery volume
  (`udisks2` when no desktop automounter is available). Display's debug-probe
  fallback requires Raspberry Pi OpenOCD with `rp2350.cfg`; OpenOCD is not bundled.
- See [0.3.1 release notes](https://github.com/freewili/freewili-gui/releases/tag/v0.3.1)
  for validation and known limitations.

### macOS (Apple Silicon / arm64)

Requires an Apple Silicon Mac running macOS 26.0 or later. This build does not
run on Intel Macs.

1. Download [freewili-gui-0.3.2-macos-arm64.zip](https://github.com/freewili/freewili-gui/releases/download/v0.3.2/freewili-gui-0.3.2-macos-arm64.zip).
2. Extract the ZIP and move **FreeWili GUI.app** to Applications.

Notes:

- This build is ad-hoc signed, not Developer ID signed or notarized. macOS
  Gatekeeper may block a downloaded copy; signing and notarization are still
  required for normal customer distribution.
- Python 3.13, its debugger, the OneWili API, Clang, wasm-ld, and runtime
  libraries are bundled. Homebrew is not required for the included tools.
- Projects and settings are stored in
  `~/Library/Application Support/FreeWili GUI/`.
- Firmware updating passed ten consecutive full-device runs on FX0054 before
  packaging. Display debug-probe recovery requires separate Raspberry Pi
  OpenOCD with RP2350 scripts; it is not bundled.
- Mac SD-reader authorization is fixed, but complete SD imaging and subsequent
  Linux boot remain unverified. This is a preview.
- HackRF and PicoScope plugins are not included. See the
  [0.3.2 release notes](https://github.com/freewili/freewili-gui/releases/tag/v0.3.2) for details and known limitations.

## Release notes

See [CHANGELOG.md](CHANGELOG.md).

## Reporting problems

Open an issue on this repository and include the release version shown on the
app's Welcome screen, your operating system and version, and what you were
doing when the problem occurred.
