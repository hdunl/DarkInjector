# MonoStealthLauncher

MonoStealthLauncher is designed to inject managed assemblies into Mono-based processes. Currently, it is mainly built around **R.E.P.O.**, an indie C# Unity game, to load [DARK](https://github.com/peeberpoober/beta-d.a.r.k.-cheat) but may be extended to other games & platforms. The project is split into a native DLL injector (monoloader.dll) and a modern WPF GUI that manages releases and injection.

---

## Features

- **Dynamic Assembly Injection**  
  Uses hook-based techniques and runtime function resolution to inject managed assemblies into the target Mono process (R.E.P.O.).

- **Auto-Updating Releases**  
  Fetches release information from GitHub (Stable, Beta, Pre-release channels) and downloads the latest selected DLL.

- **Configurable Injection Parameters**  
  Supports user-defined DLL name, namespace, class, and method for injection via a temporary configuration file.

- **Robust Logging & Status Reporting**  
  Provides detailed logging (INFO, DEBUG, SUCCESS, WARNING, ERROR) with real-time feedback in the GUI.

---

## Architecture

- **monoloader.dll (Injector)**
  - Written in C++ using the Windows API.
  - Dynamically loads Mono runtime functions to attach to and inject into the R.E.P.O. process.
  - Reads injection parameters (DLL, namespace, class, method) from a configuration file generated by the GUI.

- **ModernStealthLauncher (GUI)**
  - A WPF application in C# that manages GitHub release fetching, injection settings, and real-time process status.
  - Extracts monoloader.dll from embedded resources and triggers the injection process.
  - Currently tailored for injecting into R.E.P.O. only

---

## Build Instructions

### monoloader.dll
- **Language:** C++
- **Requirements:** Windows SDK; link against standard Windows libraries.
- **Notes:** Configure the project to disable thread library calls and target the correct Mono module names.

### ModernStealthLauncher (GUI)
- **Language:** C#
- **Framework:** WPF (.NET Framework)
- **Dependencies:** Newtonsoft.Json for JSON processing.
- **Notes:** Ensure GitHub API access is enabled by setting an appropriate User-Agent header.

---

## Dependencies

- **Platform:** Windows (tested on Windows 10)
- **Target Process:** R.E.P.O. (Unity/C#)
- **Runtime:** Mono (target process must be Mono-based)
- **Development Tools:** Visual Studio (for both C++ and C# projects)

---

## Disclaimer

This tool is intended for use with the R.E.P.O. game only. Unauthorized modification or injection into software may violate legal and ethical guidelines. Use at your own risk.
