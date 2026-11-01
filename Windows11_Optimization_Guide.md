# Windows 11 Optimization Guide (with Exact Setting Locations)

> Compiled from our earlier chat. Every tweak now shows **where to find the setting**.
> Date: 2026-11-01

---

## Table of Contents

1. [How to Use This Guide](#1-how-to-use-this-guide)
2. [Quick Ways to Open Settings Tools](#2-quick-ways-to-open-settings-tools)
3. [Before You Start: Safety](#3-before-you-start-safety)
4. [Updates and Drivers](#4-updates-and-drivers)
5. [Startup and Background Apps](#5-startup-and-background-apps)
6. [Power and Performance](#6-power-and-performance)
7. [Visual Effects](#7-visual-effects)
8. [Gaming](#8-gaming)
9. [Storage](#9-storage)
10. [Memory (RAM)](#10-memory-ram)
11. [Privacy and Telemetry](#11-privacy-and-telemetry)
12. [Network](#12-network)
13. [Security](#13-security)
14. [Services and Features](#14-services-and-features)
15. [Windows Update Behavior](#15-windows-update-behavior)
16. [Taskbar, Start, and Explorer](#16-taskbar-start-and-explorer)
17. [Browser](#17-browser)
18. [Display and Input](#18-display-and-input)
19. [Audio](#19-audio)
20. [USB, PCIe, and Device Power](#20-usb-pcie-and-device-power)
21. [Advanced Tweaks](#21-advanced-tweaks)
22. [Productivity Tools](#22-productivity-tools)
23. [BIOS / UEFI and Hardware](#23-bios--uefi-and-hardware)
24. [Maintenance and Diagnostics](#24-maintenance-and-diagnostics)
25. [Things to Avoid](#25-things-to-avoid)
26. [Priority Checklists](#26-priority-checklists)
27. [Command Cheat Sheet](#27-command-cheat-sheet)
28. [Previous Chat Context](#28-previous-chat-context)

---

## 1. How to Use This Guide

- **Path notation**: `Settings → System → Display` means open the Settings app (`Win + I`) and click through in that order.
- **Win + R** means press the Windows key and R together, type the command shown, and press Enter.
- **Admin terminal** means right-click Start → *Terminal (Admin)*.
- Work top to bottom. Sections 4-9 give the biggest gains.
- Change one thing at a time so you can undo anything that causes trouble.

---

## 2. Quick Ways to Open Settings Tools

| Tool | How to open |
|---|---|
| Settings app | `Win + I` |
| Task Manager | `Ctrl + Shift + Esc` |
| Run dialog | `Win + R` |
| Device Manager | `Win + R` → `devmgmt.msc` |
| Services | `Win + R` → `services.msc` |
| Group Policy Editor (Pro/Enterprise only) | `Win + R` → `gpedit.msc` |
| Task Scheduler | `Win + R` → `taskschd.msc` |
| System Properties | `Win + R` → `sysdm.cpl` |
| Power Options (classic) | `Win + R` → `powercfg.cpl` |
| Disk Cleanup | `Win + R` → `cleanmgr` |
| Optimize Drives | `Win + R` → `dfrgui` |
| Resource Monitor | `Win + R` → `resmon` |
| Event Viewer | `Win + R` → `eventvwr` |
| Reliability Monitor | `Win + R` → `perfmon /rel` |
| Optional Features | `Win + R` → `optionalfeatures` |
| System Configuration | `Win + R` → `msconfig` |
| Windows Memory Diagnostic | `Win + R` → `mdsched` |
| System Protection (restore points) | `Win + R` → `SystemPropertiesProtection` |
| Sound control panel | `Win + R` → `mmsys.cpl` |
| Indexing Options | Start search → "Indexing Options" |

---

## 3. Before You Start: Safety

| Action | Where | Notes |
|---|---|---|
| Create a restore point | `Win + R` → `SystemPropertiesProtection` → select C: → **Configure** (turn protection on) → **Create** | Do this before touching services, registry, or policies |
| Back up important files | Settings → Accounts → Windows backup (OneDrive), or File History | Keep a second copy on an external drive |

---

## 4. Updates and Drivers

| Setting | Where | What to do |
|---|---|---|
| Windows Update | Settings → Windows Update → **Check for updates** | Install all pending updates |
| Optional updates (drivers) | Settings → Windows Update → Advanced options → **Optional updates** | Install useful driver updates |
| GPU driver | NVIDIA (GeForce Experience / NVIDIA app), AMD Adrenalin, Intel Arc/Graphics Software | Install the latest. For problems, do a clean install |
| Clean GPU driver removal | Use **DDU** (Display Driver Uninstaller) in Safe Mode | Only when troubleshooting |
| Chipset driver | AMD or Intel support site, or your motherboard maker's site | Often skipped, but it affects power and performance |
| BIOS/UEFI update | Motherboard/PC maker support page | Follow the maker's instructions carefully |
| SSD firmware | SSD maker's tool (Samsung Magician, WD Dashboard, Crucial Storage Executive) | Fixes bugs and sometimes speed issues |
| Restart weekly | Start → Power → **Restart** | A real Restart (not Shut down) bypasses Fast Startup |
| Keep 15-20% of the SSD free | File Explorer → This PC → check the drive bar | Full drives slow down |

---

## 5. Startup and Background Apps

| Setting | Where | What to do |
|---|---|---|
| Disable startup apps | Task Manager → **Startup apps** (or Settings → Apps → **Startup**) | Disable Teams, Spotify, Discord, OneDrive, updaters, launchers. Sort by **Startup impact** |
| Background app permissions | Settings → Apps → **Installed apps** → click `⋯` beside an app → **Advanced options** → *Background apps permissions* | Set to **Never** for apps you don't need running (Store apps only) |
| Uninstall bloatware | Settings → Apps → **Installed apps** → `⋯` → **Uninstall** | Remove trial antivirus, OEM apps, unused Xbox/Clipchamp apps |
| Find resource hogs | Task Manager → **Processes** | Sort by CPU, Memory, Disk, Network |
| Deep startup control | **Autoruns** (Microsoft Sysinternals, free download) | Shows every startup entry, including scheduled tasks and drivers |
| Remove stubborn apps | Revo Uninstaller or BCUninstaller | Also cleans leftover files |

---

## 6. Power and Performance

| Setting | Where | What to do |
|---|---|---|
| Power mode | Settings → System → **Power & battery** → *Power mode* | Choose **Best performance** (plugged in) |
| Power plan | Control Panel → Hardware and Sound → **Power Options** (or `powercfg.cpl`) | Pick **High performance** or **Ultimate Performance** |
| Unlock Ultimate Performance | Admin terminal | `powercfg -duplicatescheme e9a42b02-d5df-448d-aa00-03f14749eb61` then refresh Power Options |
| Processor state | Power Options → **Change plan settings** → **Change advanced power settings** → *Processor power management* → *Minimum processor state* | Higher means more performance; lower means quieter and cooler |

---

## 7. Visual Effects

| Setting | Where | What to do |
|---|---|---|
| Performance options | `Win + R` → `sysdm.cpl` → **Advanced** tab → Performance **Settings** → *Adjust for best performance* | Then re-tick **Smooth edges of screen fonts** and **Show thumbnails instead of icons** |
| Transparency effects | Settings → Personalization → **Colors** → *Transparency effects* | Turn off |
| Animation effects | Settings → Accessibility → **Visual effects** → *Animation effects* | Turn off for snappier feel |

---

## 8. Gaming

| Setting | Where | What to do |
|---|---|---|
| Game Mode | Settings → **Gaming** → **Game Mode** | On |
| Hardware-accelerated GPU scheduling | Settings → System → **Display** → **Graphics** → *Change default graphics settings* | Toggle on, restart, then test. Helps on some systems only |
| Per-app graphics preference | Settings → System → Display → **Graphics** → select the game (or **Add desktop app**) → **Options** | Choose **High performance** |
| Optimizations for windowed games | Settings → System → Display → Graphics → *Change default graphics settings* | Leave on for DX10/11 games |
| Xbox Game Bar | Settings → Gaming → **Game Bar** | Turn off if unused |
| Background recording / captures | Settings → Gaming → **Captures** | Turn off background recording |
| XMP / EXPO (RAM speed) | **BIOS/UEFI** → Memory / AI Tweaker / OC section | Enable the XMP (Intel) or EXPO (AMD) profile |
| Resizable BAR / Smart Access Memory | **BIOS/UEFI** → Advanced → PCI Subsystem / Above 4G Decoding | Enable both Above 4G Decoding and Resizable BAR |
| GPU control panel | NVIDIA Control Panel → Manage 3D settings → **Power management mode** → *Prefer maximum performance*; AMD Adrenalin → Gaming → Graphics | Per game or global |
| Confirm game uses the dedicated GPU | Task Manager → **Performance** → GPU | Check GPU 0 vs GPU 1 usage during gameplay |
| Mouse acceleration | See [Display and Input](#18-display-and-input) | Turn off pointer precision |
| Focus mode while gaming | Settings → System → **Focus** | Reduces popups |

---

## 9. Storage

| Setting | Where | What to do |
|---|---|---|
| Storage Sense | Settings → System → **Storage** → *Storage Sense* | Turn on, schedule automatic cleanup |
| Disk Cleanup | `Win + R` → `cleanmgr` → **Clean up system files** | Includes old Windows Update leftovers |
| Windows.old | Disk Cleanup → Clean up system files → *Previous Windows installation(s)* | Delete only if you won't roll back |
| Temp files | `Win + R` → `%temp%` and `C:\Windows\Temp` | Delete contents (skip files in use) |
| TRIM check (SSD) | Admin terminal: `fsutil behavior query DisableDeleteNotify` | Should return `0` |
| Optimize drives | `Win + R` → `dfrgui` | SSD: automatic TRIM, never manual defrag. HDD: defrag monthly |
| Find big files | **WinDirStat** or **WizTree** | Delete or move large unused files |
| Delete old restore points | `sysdm.cpl` → **System Protection** → *Configure* → **Delete** | Then create one fresh point |
| Hibernation file | Admin terminal: `powercfg -h off` | Saves several GB; also disables Fast Startup. Skip if you use hibernate |
| Shrink WinSxS | Admin terminal: `DISM /Online /Cleanup-Image /StartComponentCleanup` | Safe cleanup |
| Move big folders | Settings → System → **Storage** → *Advanced storage settings* → **Where new content is saved** | Move games/downloads off a small C: |
| OS on NVMe | Hardware upgrade | NVMe is much faster than SATA or HDD |

---

## 10. Memory (RAM)

| Setting | Where | What to do |
|---|---|---|
| RAM size | Task Manager → Performance → **Memory** | 16 GB minimum, 32 GB better for gaming/multitasking |
| Page file (keep automatic) | `sysdm.cpl` → Advanced → Performance **Settings** → **Advanced** tab → Virtual memory **Change** | Leave *Automatically manage* ticked. Don't disable |
| Browser memory saver | See [Browser](#17-browser) | Enable Memory Saver / Efficiency mode |
| RAM test | `Win + R` → `mdsched` | Run if you get random crashes |

---

## 11. Privacy and Telemetry

| Setting | Where | What to do |
|---|---|---|
| Advertising ID | Settings → Privacy & security → **General** | Turn off *Let apps show me personalized ads...* |
| Diagnostic data | Settings → Privacy & security → **Diagnostics & feedback** | Turn off *Send optional diagnostic data*; turn off *Tailored experiences* |
| Activity history | Settings → Privacy & security → **Activity history** (if present) | Turn off |
| Widgets | Settings → Personalization → **Taskbar** → *Widgets* | Off |
| Chat / Teams icon | Settings → Personalization → **Taskbar** → *Chat* (if shown) | Off |
| Start recommendations | Settings → Personalization → **Start** | Turn off recommended items/recent files |
| Windows tips and suggestions | Settings → System → **Notifications** → *Additional settings* | Untick *Suggest ways to get the most out of Windows* and similar |

---

## 12. Network

| Setting | Where | What to do |
|---|---|---|
| Prefer Ethernet | Hardware | More stable than Wi-Fi |
| Network driver | Device Manager → **Network adapters** → right-click → *Update driver* (or maker's site) | Keep current |
| Adapter power saving | Device Manager → Network adapters → adapter → **Properties** → **Power Management** | Untick *Allow the computer to turn off this device to save power* |
| Wake on LAN | Same Properties window → **Advanced** tab / **Power Management** | Turn off if unused |
| DNS change | Settings → Network & internet → Wi-Fi or Ethernet → **Hardware properties** → *DNS server assignment* → **Edit** → Manual | Cloudflare `1.1.1.1` / `1.0.0.1` or Google `8.8.8.8` / `8.8.4.4` |
| Delivery Optimization | Settings → Windows Update → Advanced options → **Delivery Optimization** | Turn off *Allow downloads from other PCs* |

---

## 13. Security

| Setting | Where | What to do |
|---|---|---|
| Use Defender only | Start → **Windows Security** | Avoid stacking third-party antivirus |
| Defender exclusions | Windows Security → Virus & threat protection → *Manage settings* → **Exclusions** | Only for trusted game/dev folders |
| Smart App Control / SmartScreen | Windows Security → **App & browser control** | Keep on |
| Memory integrity (VBS/HVCI) | Windows Security → **Device security** → *Core isolation details* → **Memory integrity** | Keep on for security. On older CPUs you may test turning it off, as a trade-off |
| Defender Offline scan (monthly) | Windows Security → Virus & threat protection → **Scan options** → *Microsoft Defender Antivirus (offline scan)* | Run monthly |
| Standard user account | Settings → Accounts → **Other users** | Use a standard account daily and admin only when needed |
| Remove old accounts | Settings → Accounts → **Other users** → select → **Remove** | Clean up unused accounts |
| Device encryption / BitLocker | Settings → Privacy & security → **Device encryption** | Only if you need it; can slightly slow older SSDs |
| Check scheduled tasks | Task Scheduler (`taskschd.msc`) → Task Scheduler Library | Look for suspicious entries |

---

## 14. Services and Features

| Setting | Where | What to do |
|---|---|---|
| Optional features | `Win + R` → `optionalfeatures` | Untick unused items: Internet Explorer mode, Windows Media Player legacy, Work Folders, Hyper-V, Windows Sandbox if unused |
| Services | `Win + R` → `services.msc` → double-click service → **Startup type** | Set rarely used ones to **Manual** (not Disabled): Fax, Retail Demo, Remote Registry, Connected User Experiences, Print Spooler (only if you never print) |
| SysMain (Superfetch) | `services.msc` → **SysMain** | Keep on for HDD. On NVMe you may test turning it off |
| Windows Search indexing | Start search → **Indexing Options** → **Modify** | Limit to Documents and Start Menu. Disable per drive if you use *Everything* |

---

## 15. Windows Update Behavior

| Setting | Where | What to do |
|---|---|---|
| Active hours | Settings → Windows Update → Advanced options → **Active hours** | Set so restarts don't interrupt work |
| Pause updates | Settings → Windows Update → **Pause updates** | Pause 1-5 weeks before big feature updates |
| Get updates as soon as available | Settings → Windows Update → toggle at the top | Off if you prefer stability |
| Clear update cache | `services.msc` → stop **Windows Update** → delete files in `C:\Windows\SoftwareDistribution\Download` → start the service again | Fixes stuck updates and frees space |

---

## 16. Taskbar, Start, and Explorer

| Setting | Where | What to do |
|---|---|---|
| Open Explorer to This PC | File Explorer → `⋯` → **Options** → **General** → *Open File Explorer to* | Choose **This PC** |
| Disable recent/frequent items | File Explorer → `⋯` → Options → General → **Privacy** | Untick *Show recently used files* and *Show frequently used folders* |
| Show file extensions | File Explorer → **View** → Show → **File name extensions** | On |
| Show hidden files | File Explorer → View → Show → **Hidden items** | On |
| Search highlights | Settings → Privacy & security → **Search permissions** → *More settings* | Turn off *Show search highlights* |
| Web results in Start search (Pro) | `gpedit.msc` → Computer Configuration → Administrative Templates → Windows Components → **Search** → *Don't search the web or display web results in Search* | Enable |
| Web results in Start search (Home) | Registry: `HKCU\Software\Policies\Microsoft\Windows\Explorer` → DWORD `DisableSearchBoxSuggestions` = `1` | Restart Explorer or reboot |
| Classic right-click menu | Admin terminal: `reg add "HKCU\Software\Classes\CLSID\{86ca1aa0-34aa-4e8b-a509-50c905bae2a2}\InprocServer32" /f /ve` | Then restart Explorer (Task Manager → Windows Explorer → Restart) |
| Undo classic menu | `reg delete "HKCU\Software\Classes\CLSID\{86ca1aa0-34aa-4e8b-a509-50c905bae2a2}" /f` | Then restart Explorer |
| Shell extensions | **ShellExView** (NirSoft) | Disable third-party extensions that slow right-click |
| Leftover entries | **Autoruns** → *Explorer* tab | Remove entries from uninstalled programs |

---

## 17. Browser

| Setting | Where | What to do |
|---|---|---|
| Edge performance | `edge://settings/system` (or Settings → System and performance) | Turn on **Efficiency mode**, sleeping tabs; hardware acceleration on; turn off *Continue running background extensions and apps when Microsoft Edge is closed* |
| Chrome performance | `chrome://settings/performance` and `chrome://settings/system` | Turn on **Memory Saver**; hardware acceleration on; turn off *Continue running background apps when Google Chrome is closed* |
| Remove extensions | `edge://extensions` or `chrome://extensions` | Remove what you don't use |
| Content blocker | Install **uBlock Origin** | Cuts page weight and RAM use |
| Clear cache | Browser → `Ctrl + Shift + Delete` | Occasionally |

---

## 18. Display and Input

| Setting | Where | What to do |
|---|---|---|
| Refresh rate | Settings → System → **Display** → **Advanced display** → *Choose a refresh rate* | Set the highest your monitor supports |
| G-Sync / FreeSync | NVIDIA Control Panel → *Set up G-SYNC*; AMD Adrenalin → Gaming → Display | Enable |
| Auto HDR | Settings → System → Display → **HDR** | Only if your monitor supports real HDR |
| Native resolution and scaling | Settings → System → Display → *Display resolution* and *Scale* | Use the recommended resolution, and 100-125% scale on most monitors |
| Mouse pointer precision | Settings → Bluetooth & devices → **Mouse** → *Additional mouse settings* → **Pointer Options** | Untick *Enhance pointer precision* |
| Keyboard repeat delay | Control Panel → **Keyboard** (or `Win + R` → `control keyboard`) | Shorter delay, faster repeat rate |

---

## 19. Audio

| Setting | Where | What to do |
|---|---|---|
| Default device | Settings → System → **Sound** → *Output* | Choose the correct device |
| Sample rate | `Win + R` → `mmsys.cpl` → device → **Properties** → **Advanced** | Pick the correct rate (for example 24-bit, 48000 Hz) |
| Audio enhancements | Settings → System → Sound → device → *Audio enhancements* | Turn off if you hear crackling |
| USB headset/DAC dropouts | See [USB selective suspend](#20-usb-pcie-and-device-power) | Disable |

---

## 20. USB, PCIe, and Device Power

| Setting | Where | What to do |
|---|---|---|
| USB selective suspend | Power Options → **Change plan settings** → **Change advanced power settings** → *USB settings* → *USB selective suspend setting* | **Disabled** |
| PCI Express Link State Power Management | Same advanced power settings → *PCI Express* → *Link State Power Management* | **Off** (desktops) |
| USB hubs / devices power saving | Device Manager → **Universal Serial Bus controllers** → *USB Root Hub* → **Properties** → **Power Management** | Untick *Allow the computer to turn off this device* |
| Network adapter power saving | See [Network](#12-network) | Untick the same option |
| Wake on LAN | Device Manager → network adapter → Properties | Off if unused |

---

## 21. Advanced Tweaks

> Create a restore point first (see [Safety](#3-before-you-start-safety)).

| Setting | Where | What to do |
|---|---|---|
| Group Policy: telemetry and consumer features (Pro) | `gpedit.msc` → Computer Configuration → Administrative Templates → Windows Components → **Data Collection and Preview Builds**, and **Cloud Content** | Reduce telemetry; turn off consumer experiences |
| Group Policy: turn off Copilot | `gpedit.msc` → User Configuration → Administrative Templates → Windows Components → **Windows Copilot** (if present) | Enable *Turn off Windows Copilot* |
| Telemetry scheduled tasks | `taskschd.msc` → Task Scheduler Library → Microsoft → Windows → **Application Experience** and **Customer Experience Improvement Program** | **Disable** (don't delete) *Microsoft Compatibility Appraiser* and the CEIP tasks |
| Disable GUI boot | `Win + R` → `msconfig` → **Boot** tab → *No GUI boot* | Tiny boot-time gain |
| Memory integrity test | See [Security](#13-security) | Compare performance with it on and off |
| Timer resolution / MMCSS tweaks | Registry / third-party tools | Marginal and often placebo. Skip unless you know why |
| Look for repeated errors | `eventvwr` → **Windows Logs** → **System** | Repeated errors often point to a failing driver |
| Disable Recall-style features | Settings (Privacy & security) or Group Policy, if present on your edition | Turn off if you don't use them |

---

## 22. Productivity Tools

| Tool | Where / how | Use |
|---|---|---|
| Clipboard history | `Win + V`, or Settings → System → **Clipboard** | Turn on |
| Snap layouts | Settings → System → **Multitasking** → *Snap windows* | Turn on |
| Virtual desktops | `Win + Tab` → **New desktop** | Separate Work / Gaming / Browsing |
| Nearby sharing | Settings → System → **Nearby sharing** | Off if unused |
| Phone Link | Settings → Bluetooth & devices → **Mobile devices** | Off if unused |
| Focus / Do Not Disturb | Settings → System → **Focus** | Use during games and work |
| PowerToys | Microsoft Store or `winget install Microsoft.PowerToys` | FancyZones, PowerToys Run, Keyboard Manager, Always on Top |
| Everything | voidtools.com | Instant file search |
| Winget | Terminal: `winget upgrade --all` | Update all apps at once |
| Windows Terminal + PowerShell 7 | Microsoft Store / `winget install Microsoft.PowerShell` | Better command line |
| Backup | Settings → Accounts → **Windows backup**, or File History | Back up key folders; make a periodic system image |

---

## 23. BIOS / UEFI and Hardware

Enter BIOS: Settings → System → **Recovery** → *Advanced startup* → **Restart now** → Troubleshoot → Advanced options → **UEFI Firmware Settings**. Or tap `Del` / `F2` at boot.

| Setting | Typical BIOS location | What to do |
|---|---|---|
| XMP / EXPO | Memory / AI Tweaker / OC | Enable |
| Resizable BAR + Above 4G Decoding | Advanced → PCI Subsystem | Enable |
| PCIe generation | Advanced → PCI Subsystem | Set to the highest your GPU/SSD supports |
| Virtualization (SVM / VT-x) | Advanced → CPU Configuration | Off if you don't use VMs or WSL; on if you do |
| Fan curve | Monitor / Q-Fan / Smart Fan | Set a sensible curve for cooler, quieter running |
| Upgrade priority | Hardware | HDD → NVMe SSD, then 8 → 16/32 GB RAM, then GPU/CPU |
| Physical cleaning | Case | Dust fans and heatsinks every 6-12 months; replace thermal paste every few years |

---

## 24. Maintenance and Diagnostics

| Task | Where / command | Notes |
|---|---|---|
| Repair system files | Admin terminal: `sfc /scannow` | Run first |
| Repair Windows image | Admin terminal: `DISM /Online /Cleanup-Image /RestoreHealth` | Run if SFC finds problems |
| Disk health | **CrystalDiskInfo** | Check SMART status for SSD/HDD |
| Temperatures | **HWiNFO** or **HWMonitor** | Thermal throttling is a common hidden cause of slowness |
| Find who is using disk/CPU/network | `resmon` | Shows per-process detail |
| Crash history | `perfmon /rel` | At-a-glance stability timeline |
| Boot and app-launch analysis | **Windows Performance Recorder** | Advanced |
| Audio crackle / stutter | **LatencyMon** | Points to the offending driver |
| GPU usage check | Task Manager → Performance → **GPU** | Confirm the dedicated GPU is used |
| RAM test | `mdsched` | For random crashes |

---

## 25. Things to Avoid

- "Registry cleaners" and "PC booster" apps. They rarely help and can break things.
- Disabling Windows Update, Defender, or core services (SysMain, Windows Search) without a clear reason.
- Random debloat scripts. If you use one, make a restore point first and read what it does.
- Large "gaming tweak" packs. Most gains are placebo and they can cause instability.
- Disabling the page file.
- Defragmenting an SSD manually.

---

## 26. Priority Checklists

### Quick wins (about 15 minutes)
1. Disable startup apps (Task Manager → Startup apps)
2. Set Best performance power mode (Settings → System → Power & battery)
3. Turn on Game Mode and GPU scheduling (Settings → Gaming; Settings → System → Display → Graphics)
4. Update GPU/chipset drivers and BIOS
5. Enable XMP/EXPO in BIOS
6. Run Storage Sense and Disk Cleanup
7. Uninstall bloatware
8. Check temps and clean dust

### If you have a bit more time
1. Update chipset/GPU drivers and BIOS; enable XMP/EXPO
2. Trim startup apps and browser extensions
3. Clean storage and move heavy files off C:
4. Fix power and USB settings (selective suspend, PCIe link state)
5. Clean up the browser, then try PowerToys and Everything

---

## 27. Command Cheat Sheet

| Purpose | Command (run in Admin terminal unless noted) |
|---|---|
| Unlock Ultimate Performance plan | `powercfg -duplicatescheme e9a42b02-d5df-448d-aa00-03f14749eb61` |
| Turn off hibernation | `powercfg -h off` |
| Turn hibernation back on | `powercfg -h on` |
| Check SSD TRIM | `fsutil behavior query DisableDeleteNotify` |
| Repair system files | `sfc /scannow` |
| Repair Windows image | `DISM /Online /Cleanup-Image /RestoreHealth` |
| Clean WinSxS | `DISM /Online /Cleanup-Image /StartComponentCleanup` |
| Update all apps | `winget upgrade --all` |
| Classic right-click menu | `reg add "HKCU\Software\Classes\CLSID\{86ca1aa0-34aa-4e8b-a509-50c905bae2a2}\InprocServer32" /f /ve` |
| Undo classic right-click menu | `reg delete "HKCU\Software\Classes\CLSID\{86ca1aa0-34aa-4e8b-a509-50c905bae2a2}" /f` |

---

## 28. Previous Chat Context

### Request 1
> "give me all possible best way to optimize my windows 11 for pc"

**Answer summary**: A 12-part guide covering basics, startup and background apps, power and performance, gaming, storage, RAM, privacy and telemetry, network, security, maintenance tools, BIOS/hardware tweaks, and things to avoid, plus a 15-minute quick-win checklist.

### Request 2
> "give me more things that i can optimize in windows 11"

**Answer summary**: A 14-part follow-up covering services and features, Windows Update behavior, taskbar/Start/Explorer, context menu clean-up, storage deep-clean, browser optimization, display and input, audio, USB/PCIe/device power, Windows features worth checking, advanced tweaks, productivity tools, security hygiene, and diagnostics.

### Request 3
> "you some suggestions but didn't location where is that setting is now create md file with proper structure with all setting locations and privious chat in this context"

**Result**: This file. Every tweak from both earlier answers is merged above, each with its location.

### Open question from earlier
For a tailored shortlist of the 10 or so tweaks that matter most, share:
- Your **CPU, GPU, RAM, and storage type**
- Your **main use** (gaming, video editing, office, coding)

---

*Tip: Make a restore point before changing services, registry, or policies, and change one setting at a time.*
