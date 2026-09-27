# Release notes

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
