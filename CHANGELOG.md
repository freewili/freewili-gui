# Release notes

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
