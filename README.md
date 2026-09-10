# FreeWili GUI

Desktop application for working with FreeWili boards: device console, GPIO,
I2C, SPI, UART, logic analyzer and player, Wili Blocks editor, simulator and
more.

## Download

Builds are published on the **[Releases](https://github.com/freewili/freewili-gui/releases)**
page. Get the latest release from
**[releases/latest](https://github.com/freewili/freewili-gui/releases/latest)**.

### Windows (x64)

1. Download `fwcom-<version>.zip` from the release.
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

### Linux and macOS

No current build is published for these platforms yet. Check the Releases page
for updates.

## Reporting problems

Open an issue on this repository and include the release version shown on the
app's Welcome screen, your Windows version, and what you were doing when the
problem occurred.
