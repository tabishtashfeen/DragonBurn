# ✅ Checklist – Running **DragonBurn** correctly

| # | Step | Details |
|---|------|---------|
| 1 | **Verify OS** | Windows 10 (20H2 +) **or** Windows 11. |
| 2 | **Install Visual Studio 2022** *(only needed if you compile from source)*. |
| 3 | **Build the project (optional)** | Open `DragonBurn.sln` in Visual Studio 2022 → Set configuration to **Release** → Build solution (`Ctrl+Shift+B`). The compiled binaries `DragonBurn.exe` and `DragonBurn‑kernel.exe` will appear in `x64\Release\` (or `Debug\`). |
| 4 | **Disable Secure Boot** | Required for the kernel driver mapping.  <br>*Open BIOS/UEFI → Secure Boot → Disabled* |
| 5 | **Turn off real‑time protection** | Windows Defender / any AV may block the mapper. <br>*Settings → Windows Security → Virus & threat protection → Manage settings → Real‑time protection → Off* |
| 6 | **(Optional) Apply additional registry fixes**  <br>*(helps on newer Windows builds)* | Run the following commands **as Administrator** in PowerShell:\n`reg add "HKLM\SYSTEM\CurrentControlSet\Control\DeviceGuard\Scenarios\HypervisorEnforcedCodeIntegrity" /v Enabled /t REG_DWORD /d 0 /f`\n`reg add "HKLM\SYSTEM\CurrentControlSet\Control\Lsa" /v RunAsPPL /t REG_DWORD /d 0 /f`\n`reg add "HKEY_LOCAL_MACHINE\System\CurrentControlSet\Control\DeviceGuard" /v EnableVirtualizationBasedSecurity /t REG_DWORD /d 0 /f`\n`bcdedit /set hypervisorlaunchtype off`\n`reg add "HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\CI\Config" /v VulnerableDriverBlocklistEnable /t REG_DWORD /d 0 /f` |
| 7 | **Download the binaries** | You need two files:  
- `DragonBurn.exe` (user‑mode cheat)  
- `DragonBurn‑kernel.exe` (kernel driver)  
Download the latest release from the GitHub page: <https://github.com/ByteCorum/DragonBurn/releases/latest>  
Direct driver link (example): <https://github.com/ByteCorum/DragonBurn/releases/download/v3.7.10.4/DragonBurn-kernel.exe> |
| 8 | **Run the mapper** | Right‑click **`DragonBurn‑kernel.exe`** → **Run as administrator**. <br>Look for a `[+] success` message. |
| 9 | **Launch the cheat** | Double‑click **`DragonBurn.exe`** (no admin required). <br>Press **END** to open/close the in‑game menu. |
|10|**If you see mapping errors** | • *Kernel‑mode driver image empty*: make sure the driver binary is correctly embedded (normally handled by the release build). \n• *`\\Device\\Nal` already in use*: install the [NalFix](https://github.com/VollRagm/NalFix) helper. \n• *Vulnerable driver blocklist*: follow the registry steps in #6 or disable the blocklist via Windows Update KB5020779. |
|11|**Disable anti‑cheat services** (if needed) | Stop interfering services before mapping: \n`sc stop faceit`  (Faceit) \n`sc stop vgc` & `sc stop vgk` (Riot Vanguard) |
|12|**Enjoy** | After the mapper succeeds, the cheat should work in CS 2. Press **END** to toggle the menu and configure features. |

> **Tip** – Keep a copy of the two binaries in a folder without spaces in the path (e.g., `C:\DragonBurn\`). Running the mapper from such a location reduces permission‑related hiccups.

Happy hacking! 🎮
