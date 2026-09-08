# WiseMemory
WiseMemory to Open VMware WITHOUT Crashing/Lag

# VMware RAM Optimizer & Memory Saver

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Platform](https://img.shields.io/badge/Platform-Windows%20%7C%20Linux-blue.svg)]()
[![VMware Workstation](https://img.shields.io/badge/VMware-Workstation%20%2F%20ESXi-orange.svg)]()

A lightweight utility and configuration script designed to reduce RAM usage and optimize memory allocation for **VMware Workstation** and **VMware vSphere/ESXi** virtual machines.

---

## ⚡ Overview

When running multiple Virtual Machines (VMs), VMware often reserves significant physical host memory and creates heavy swapping files (`.vmem`). This project provides automated scripts and optimal configuration tweaks to:

* Trim unused working set memory from host processes.
* Prevent aggressive memory caching and background swapping to disk.
* Reduce idle host RAM footprint when running multiple VMs simultaneously.

---

## ✨ Features

* **Disable Host Memory Swapping:** Forces VMware to store guest memory strictly within physical RAM for faster access and reduced disk write cycles.
* **Auto Memory Trimming:** Periodically releases trimmed host memory back to the system.
* **Optimized `config.ini` Rules:** Pre-configured VMware host parameters fine-tuned for performance and low memory overhead.
* **Lightweight & Portable:** No heavy installation needed—just simple batch/shell scripts and config parameters.

---

## 🛠️ Recommended Configuration Tweaks

Add the following lines to your VMware global `config.ini` file (usually located at `C:\ProgramData\VMware\VMware Workstation\config.ini` on Windows):

```ini
# Prevent VMware from trimming guest memory aggressively
MemTrimMode = "Disable"

# Disable host memory swapping to disk (.vmem files)
mainMem.useNamedFile = "FALSE"

# Force memory allocation to physical RAM only
MemAllowFileSync = "TRUE"
prefvmx.minVmMemPct = "100"
prefvmx.useRecommendedLockedMemSize = "TRUE"
