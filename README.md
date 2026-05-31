# HP-PROBOOK-650-G2-EFI-FOR-MACOS-TAHOE
THis is a efi for lazy people who dont like creating opencore files so hee hee



# HP ProBook 650 G2 - macOS Tahoe Hackintosh (Pre-Patched EFI)

This repository contains a specialized, **pre-patched** OpenCore EFI configuration designed to run macOS Tahoe on the HP ProBook 650 G2 laptop. 

Unlike traditional setups, this EFI structure handles the heavy lifting out of the box, ensuring that you do not need to apply Post-Install Root Patches for basic graphics functionality upon arriving at the desktop.

⚠️ **CRITICAL: You must generate your own SMBIOS serial numbers before booting! Sharing active serials will result in your Apple ID being flagged or banned.**

---

## 💻 Hardware Compatibility & Status

* **Laptop Model:** HP ProBook 650 G2
* **Processor:** Intel Core 6th Generation (Skylake i5/i7)
* **Bootloader:** OpenCore


| Feature | Status | Notes |
| :--- | :--- | :--- |
| **Graphics Acceleration** | ✅ Working | Pre-patched natively inside the EFI framework; zero manual post-install root patching required. |
| **Wi-Fi** | ✅ Working | Fully supported using **HeliPort** via the included Intel Wi-Fi drivers. |
| **Bluetooth** | ✅ Working | Native pairing and connection stability. |
| **Battery Indicator** | ✅ Working | Accurate percentage reading and charging status. |
| **USB Ports** | ✅ Working | Requires a quick adjustment during setup (see instructions below). |

---

## 🛠️ Required Patch Configuration Step

To ensure complete stability and prevent your system ports from dropping out, you must configure your patch utility specifically for this hardware architecture.

1. Download the custom, modded version of the patcher app from the [laobamac/OCLP-Mod GitHub Repository](https://github.com/laobamac/OCLP-Mod).
2. Launch the application on your system.
3. Navigate directly to the **Patch Section / Settings**.
4. Locate the USB configuration options and explicitly **Enable USB Patching**.
5. Save the configuration to finalize the hardware mappings.

---

## 🚀 Pre-Flight Checklist (How to Use This EFI)

### 1. Generate Unique Serial Numbers
1. Download **GenSMBIOS**.
2. Open the included `config.plist` using **ProperTree or OCAT**.
3. Navigate to `PlatformInfo -> Generic`.
4. Generate data using a compatible SMBIOS profile (MacBookPro16,2`) and paste the unique strings into:
   * `SystemSerialNumber`
   * `SystemUUID`
   * `MLB`
5. Save and close the file.

### 2. Configure Your HP BIOS Settings
Ensure your ProBook 650 G2 BIOS has the following options applied before attempting a boot:
* **Disable:** Fast Boot, Secure Boot, VT-d (Virtualization for Directed I/O), Wake on LAN.
* **Enable:** UEFI Boot Mode, VT-x (Intel Virtualization Technology), SATA Mode: AHCI.

---

## 🛑 Maintenance Rules

* **Disable Automatic Updates:** Turn off automatic system updates under *System Settings > General > Software Update*. Minor revision drops can break the pre-patched variables.
* **Keep an EFI Rescue Drive:** Always keep a working copy of this EFI folder on a separate FAT32-formatted USB drive. If an update or manual edit corrupts your boot partition, you can use the external USB to boot back in and fix it.

---

## 🤝 Credits & Acknowledgements
* Apple for macOS.
* The Acidanthera team for OpenCore and vital system kexts.
* [laobamac](https://github.com/laobamac) for the specialized [OCLP-Mod](https://github.com/laobamac/OCLP-Mod) application.
