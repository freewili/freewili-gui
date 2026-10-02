# Release notes

## 0.4.0 Windows - 2026-10-02

[Windows x64 release](https://github.com/freewili/freewili-gui/releases/tag/v0.4.0).
Linux remains at 0.3.3 (preview) and macOS at 0.3.2 (preview).

- New **Firmware** tab in the FreeWili OG updater: one **Update and verify** button
  installs the official Stable or Preview OG firmware, installs the OG display
  bootloader first when a board needs it, and confirms MAIN and DISPLAY report
  the release. The Bootloader tab's Install and Erase actions now work.
- First Windows build of the **Protocol > Wi-Fi & BT** explorer (not yet
  device-tested on Windows).
- Graphical Panels instrument dashboards, infotainment templates and modern widgets;
  CAN FD event names from SD-card DBC files; Logic Analyzer `.dom` captures with
  shared cursor bubbles; rThon examples browser; embedded default map; more robust
  OneWili serial streaming; AI Workbench on AIlocal 0.2.1.
- Native CTest 45/45; full GUI suite 739/764 with no new failures versus 0.3.2.
  Clean Windows VM/N/KN checks and code signing remain outstanding.

## 0.3.2 Windows and macOS previews - 2026-09-28

[Windows x64 and Apple Silicon macOS 26+ previews](https://github.com/freewili/freewili-gui/releases/tag/v0.3.2).
Linux remains at 0.3.1; matching Linux 0.3.2 validation is pending.

- Windows package refreshed to 0.3.2 with FPGA-first CM0 startup, the consecutive
  firmware-update serial discovery fix, current OneWili sources, the bundled
  Wasm compiler, map tools, Linux Imager helper, and public instrument plugins.
- Windows remains unsigned and a preview: existing GUI regression failures,
  clean-machine/N/KN checks, and repeated Windows hardware flashing remain open.
- Native Mac firmware updater discovery and private Main recovery-volume mounting.
- Fix stale serial discovery between consecutive firmware updates.
- Enable Mac SD-reader imaging and correct the disk authorization handoff.
- Power FPGA before CM0 and RUN in Linux Console and Linux Imager.
- Updater implementation passed ten consecutive Main + Display + wifiCPU runs
  on FX0054 before this versioned package; the archive was not endurance-tested.
- Complete physical SD imaging/boot, clean-machine verification, and Developer ID
  signing/notarization remain outstanding. Display SWD needs external RP2350 OpenOCD.

## 0.3.1 Windows and Linux - 2026-09-27

[Windows x64 preview and Linux x86_64 release](https://github.com/freewili/freewili-gui/releases/tag/v0.3.1).
Windows GUI regression failures remain unresolved. macOS remains at 0.2.0,
with updater implementation and verification gaps.

- Longer Main/Display settling, SD-mount, and USB reconnect windows during updates.
- Accept successful power acknowledgements that contain startup diagnostics.
- Detect disconnected POSIX serial ports and report Display probe USB failures.
- Include OneWili Python sources, examples, and license in the Linux package.
- Windows includes the updater fixes found during Linux testing, plus the
  existing Wasm compiler, OneWili Python API/examples, map tools, Linux Imager
  helper, and public plugins. Windows hardware flashing was not repeated.
- Operator reported a successful hardware retry after the timing changes;
  intermittent SD/probe issues and broader release qualification remain open.

## 0.3.0 preview - 2026-09-26

[Windows x64 preview](https://github.com/freewili/freewili-gui/releases/tag/v0.3.0).
GUI regression failures remain unresolved, so this release is marked prerelease.
Matching macOS and Linux builds and hardware verification are pending; existing
downloads remain at macOS 0.2.0 and Linux 0.1.3.

- CM0 Linux console, shell, Python run/debug, file browsing/transfers, and Linux Imager.
- Firmware Updater with Stable/Preview releases, verified manifests and images,
  local firmware files, and coordinated Main, Display, and wifiCPU installation.
- Latest OneWili Python API with raw binary frames, CAN FD, complete logic-analyzer
  samples, stream diagnostics, and a PWM capture example.
- Logic Analyzer/Player cursor and DOM controls, editor examples/help, offline
  map and AI Workbench improvements.
- Packaging includes OneWili Python and installation notes, excludes developer
  scratch files and debug symbols, and stamps the executable with the release version.

For CM0 app development, use [WiliCM0BSP](https://github.com/freewili/wilicm0bsp)
and install apps under **`/home/apps/`** for the Linux Apps launcher.
See the release notes for Python/OpenOCD requirements and platform gaps.

## 0.2.0 - 2026-09-12

[macOS Apple Silicon release](https://github.com/freewili/freewili-gui/releases/tag/v0.2.0), requiring macOS 26.0 or later.
Windows and Linux remain available in [0.1.3](https://github.com/freewili/freewili-gui/releases/tag/v0.1.3).

- Native macOS app with Metal rendering and the FreeWili Dock icon.
- Bundled Python 3.13, debugger, OneWili API, and ten Python examples.
- Rthon editor with ten OneWili examples and embedded language reference.
- C/C++ Wasm editor with bundled Clang and wasm-ld.
- Logic Analyzer cursor bubbles and Save DOM / Load DOM controls on Setup.
- Embedded help, tutorials, AI Workbench, and runtime libraries; no Homebrew required.
- Projects and settings stored in `~/Library/Application Support/FreeWili GUI/`.

The package is ad-hoc signed, not Developer ID signed or notarized; Gatekeeper
may block a downloaded copy. The HackRF plugin is not included. See the release
notes for installation instructions and known limitations.

## 0.1.3 — 2026-09-10

Windows (x64) zip and Linux (x86_64) zip: https://github.com/freewili/freewili-gui/releases/tag/v0.1.3

### What's new since 0.1.1
- Offline map display control with bundled map fonts and runtime.
- Logic Player: on-waveform cursor editing, time and difference bubbles, per-channel generators with validation, and hex payload defaults.
- Logic Analyzer: SPI MOSI and MISO decode annotations are shown separately.
- HackRF plugin with streaming, channel DSP and audio transport.
- AI Workbench view and picoscope plugin.
- Numerous view, editor and simulator fixes.
