# FreeWili GUI

Desktop application for working with FreeWili boards: device console, GPIO,
I2C, SPI, UART, logic analyzer and player, Wili Blocks editor, simulator and
more.

## Download

Builds are published on the **[Releases](https://github.com/freewili/freewili-gui/releases)** page.
The current downloads for each platform are:

| Platform | Version | Download |
| --- | --- | --- |
| macOS Apple Silicon (arm64), macOS 26.0+ | 0.4.2 | [freewili-gui-0.4.2-macos-arm64.zip](https://github.com/freewili/freewili-gui/releases/download/v0.4.2/freewili-gui-0.4.2-macos-arm64.zip) |
| Windows (x64) | 0.4.0 | [fwcom-0.4.0.zip](https://github.com/freewili/freewili-gui/releases/download/v0.4.0/fwcom-0.4.0.zip) |
| Linux (x86_64) | 0.4.1 | [fwcom-0.4.1-linux-x86_64.zip](https://github.com/freewili/freewili-gui/releases/download/v0.4.1/fwcom-0.4.1-linux-x86_64.zip) or [fwcom_0.4.1_amd64.deb](https://github.com/freewili/freewili-gui/releases/download/v0.4.1/fwcom_0.4.1_amd64.deb) |

Windows 0.4.0 adds one-click official firmware updates for FreeWili OG
(**Setup > FreeWili OG updater > Firmware**), including installing the OG display
bootloader when a board needs it, plus the Wi-Fi & BT explorer and the latest
Graphical Panels, logic, CAN FD and rThon features.
Linux 0.4.1 adds the same features plus a Wi-Fi connection to FreeWili 2
(Main over the standard Wi-Fi firmware) and a Debian package. macOS 0.4.2 brings
the OG firmware updates and the Wi-Fi connection to Apple Silicon Macs. It also
connects over USB to an OG running the official ogfw firmware. Complete Mac SD
imaging, clean-machine checks, and Developer ID signing/notarization remain outstanding.
The previous [Windows 0.1.3 stable download](https://github.com/freewili/freewili-gui/releases/download/v0.1.3/fwcom-0.1.3.zip) remains available.

### Windows (x64)

1. Download [fwcom-0.4.0.zip](https://github.com/freewili/freewili-gui/releases/download/v0.4.0/fwcom-0.4.0.zip)
   and verify it against [SHA256SUMS-windows.txt](https://github.com/freewili/freewili-gui/releases/download/v0.4.0/SHA256SUMS-windows.txt).
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
- Read the [0.4.0 release notes](https://github.com/freewili/freewili-gui/releases/tag/v0.4.0)
  for firmware requirements, verification results, and known limitations.

### Linux applications on FreeWili 2

Use [WiliCM0BSP](https://github.com/freewili/wilicm0bsp) for examples, agent
instructions, the CM0 driver, and a pinned [OneWili](https://github.com/freewili/onewili)
API. Put applications in the CM0 Linux **`/home/apps/` folder** for easy
launching from Linux Apps. The GUI's CM0 shell, file transfer, and Python tools
require compatible Main firmware and a CM0 image with the matching bridge.

### Linux (x86_64)

Install the [Debian package](https://github.com/freewili/freewili-gui/releases/download/v0.4.1/fwcom_0.4.1_amd64.deb)
with `sudo apt install ./fwcom_0.4.1_amd64.deb`, which pulls in the system libraries and adds
a launcher, or use the portable ZIP. Verify either against
[SHA256SUMS-linux.txt](https://github.com/freewili/freewili-gui/releases/download/v0.4.1/SHA256SUMS-linux.txt).

1. Download `fwcom-0.4.1-linux-x86_64.zip` and extract it to a folder you can write to (for example your home directory). The app writes its `data/` folder and settings next to the `fwcom` binary; if that folder is read-only it falls back to `~/.local/share/fwcom`.
2. Install the system libraries the build links against. On Debian 13:
   `sudo apt install libavcodec61 libavformat61 libavutil59 libswresample5 libswscale8 libsqlite3-0 libegl1 libssl3t64 libbrotli1 libudev1 libglib2.0-0t64`
   (older Ubuntu releases ship different FFmpeg package versions; the exact sonames the binary needs are listed in `README-linux.txt` inside the zip.)
3. Run `./fwcom`.

Notes:

- Built against Debian 13-era libraries (FFmpeg 7, glibc 2.38 or newer, libstdc++ 14). Older distributions are not verified.
- Requires a GPU driver with Vulkan support.
- Unlike the Windows zip, FFmpeg and OpenSSL are not bundled; they come from the distribution packages above.
- Optional at runtime: `libsecret-1-0` (remembers the AI API key), `xdg-utils` (Open-folder buttons), `pulseview` (Logic Analyzer VCD hand-off), `python3` + `python3-debugpy` (Python editor Run/Debug).
- `desktop/` inside the zip has a `.desktop` entry and icon if you want a launcher.
- The C-to-WASM compiler toolchain (`config/wiliclang`) is Windows-only for now; on Linux the WASM editor looks for a `wiliclang` on `$PATH`.
- Includes OneWili Python sources and examples; Python itself is a system dependency.
- Firmware Updater requires USB permissions and a mounted recovery volume
  (`udisks2` when no desktop automounter is available). Display's debug-probe
  fallback requires Raspberry Pi OpenOCD with `rp2350.cfg`; OpenOCD is not bundled.
- The Wi-Fi & BT explorer needs the separate [ESP32-C5 companion firmware](https://github.com/freewili/freewili-gui/releases/download/v0.3.3/fwcom-0.3.3-esp32c5-companion.zip)
  for live capture; it replaces the stock Wi-Fi firmware services used by the Wi-Fi connection. Read its INSTALL.md first.
- See [0.4.1 release notes](https://github.com/freewili/freewili-gui/releases/tag/v0.4.1)
  for validation and known limitations.

### macOS (Apple Silicon / arm64)

Requires an Apple Silicon Mac running macOS 26.0 or later. This build does not
run on Intel Macs.

1. Download [freewili-gui-0.4.2-macos-arm64.zip](https://github.com/freewili/freewili-gui/releases/download/v0.4.2/freewili-gui-0.4.2-macos-arm64.zip)
   and verify it against [SHA256SUMS-macos.txt](https://github.com/freewili/freewili-gui/releases/download/v0.4.2/SHA256SUMS-macos.txt).
2. Extract the ZIP and move **FreeWili GUI.app** to Applications.

Notes:

- This build is ad-hoc signed, not Developer ID signed or notarized. If macOS
  blocks the first launch, open **System Settings > Privacy & Security** and
  choose **Open Anyway**. Signing and notarization are still outstanding.
- Python 3.13, its debugger, the OneWili API, Clang, wasm-ld, and runtime
  libraries are bundled. Homebrew is not required for the included tools.
- Projects and settings are stored in
  `~/Library/Application Support/FreeWili GUI/`.
- Display debug-probe recovery requires separate Raspberry Pi OpenOCD with
  RP2350 scripts; it is not bundled.
- An OG running ogfw connected over USB on a Mac. The OG **Firmware** tab, the
  Wi-Fi connection and network search have not yet been run against hardware
  on a Mac.
- Mac SD-reader authorization is fixed, but complete SD imaging and subsequent
  Linux boot remain unverified.
- HackRF and PicoScope plugins are not included. See the
  [0.4.2 release notes](https://github.com/freewili/freewili-gui/releases/tag/v0.4.2) for details and known limitations.

## Release notes

See [CHANGELOG.md](CHANGELOG.md).

## Reporting problems

Open an issue on this repository and include the release version shown on the
app's Welcome screen, your operating system and version, and what you were
doing when the problem occurred.
