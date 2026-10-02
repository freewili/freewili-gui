# Release notes

## 0.4.2 macOS - 2026-10-02

[macOS Apple Silicon release](https://github.com/freewili/freewili-gui/releases/tag/v0.4.2) (macOS 26.0+).
Windows is at 0.4.0 and Linux at 0.4.1.

- Brings the 0.4.0 and 0.4.1 features to macOS: the FreeWili OG updater's one-click
  **Firmware** tab, the Wi-Fi connection to FreeWili 2 with **Search network**, the
  **Protocol > Wi-Fi & BT** explorer, Graphical Panels dashboards, CAN FD DBC names,
  Logic Analyzer `.dom` captures and more. AI Workbench is now included on macOS.
- An OG running the official ogfw firmware now connects over USB (Main, Display and FPGA).
- Package audits, a fresh-extraction launch and 39 GUI tests passed on the build Mac.
  Native tests passed 17/18: the Wi-Fi discovery test cannot run beside macOS's mDNS
  service. OG firmware updates, real Wi-Fi use, a clean Mac/Gatekeeper launch and
  notarization are not verified.

## 0.4.1 Linux - 2026-10-02

[Linux x86_64 release](https://github.com/freewili/freewili-gui/releases/tag/v0.4.1) as a ZIP and a Debian package.
Windows is at 0.4.0 and macOS at 0.3.2 (preview).

- Connect to a FreeWili 2 over Wi-Fi: the toolbar Wi-Fi icon and **Search network**
  find devices on the local network, or enter `ws://<device-ip>:8765/` as the Main
  connection. File transfer, firmware updating and SD imaging still use USB.
- Includes the 0.4.0 features: the FreeWili OG updater's one-click **Firmware** tab,
  Graphical Panels dashboards, CAN FD DBC names, Logic Analyzer `.dom` captures and more.
- New Debian package (`sudo apt install ./fwcom_0.4.1_amd64.deb`).
- Linux Release build, package gates, 26 CTest checks and 6 OG updater GUI tests passed;
  older distributions and Windows/macOS Wi-Fi use are not verified.

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

## 0.3.3 Linux preview — 2026-09-28

New **Protocol → Wi-Fi & BT** explorer for the ESP32-C5 inside FreeWili 2.

- BLE advertising and scan-response inspection, discovered names with gray MAC addresses, service/manufacturer decoding, raw bytes, and RSSI history.
- Passive Wi-Fi management-frame capture on selected 2.4 GHz and 5 GHz channels, with country/channel controls.
- Sortable single-line device rows, resizable device/detail panes, five-second arrival/departure highlights, and adjustable absence timeout.
- Clear results while capture continues; capture import/export, demo data, and built-in Help.
- ESP32 connection appears in Hardware Connection Settings and uses the internal USB hub.

### Downloads and firmware

This release provides Linux x86_64 only. Windows and macOS remain at 0.3.2; the new explorer has not been built or device-tested on those platforms.

Download `fwcom-0.3.3-linux-x86_64.zip`. Linux requires the system libraries listed in its README-linux.txt, glibc 2.41 or newer, and a Vulkan-capable GPU.

Live capture requires the separate `fwcom-0.3.3-esp32c5-companion.zip`. Read its INSTALL.md before installing. It replaces ESP32 wireless firmware, including stock Bottlenose services; it does not replace Main or Display. The GUI does not install it automatically. Demo/import can be used without installing firmware.

BLE supports legacy advertisements/scan responses, not BT Classic, connected traffic, or extended advertisements. Wi-Fi captures management frames on one channel at a time, up to 512 bytes per frame; no 6 GHz or data-payload capture. Wi-Fi and BLE capture run separately.

### Verification and remaining gaps

Linux Release build and 34 sniffer checks passed. Feature testing on FreeWili FX0106 covered live BLE names, 2.4 GHz channels 1/6, 5 GHz channel 36, sorting, splitters, highlights, Help, and clearing during capture. Channel 149 tuning was acknowledged but reception was not verified. Not every selectable channel has been RF-tested.

Windows/macOS feature validation, clean-machine Linux checks, physical USB unplug testing, and long-duration capture remain outstanding. Existing full-application GUI regression failures from prior previews have not been requalified. Firmware replacement and other device operations were not repeated across all three desktop platforms. This remains a preview.

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
