# TWRP 3.1.1 — Blackview BV5500 (MT6580)

<p align="center">
  <img src="https://img.shields.io/badge/TWRP-3.1.1-blue?style=for-the-badge&logo=android" alt="TWRP 3.1.1">
  <img src="https://img.shields.io/badge/Android-8.1%20Oreo%20Go-brightgreen?style=for-the-badge&logo=android" alt="Android 8.1">
  <img src="https://img.shields.io/badge/Chipset-MT6580A-orange?style=for-the-badge&logo=mediatek" alt="MediaTek MT6580">
  <img src="https://img.shields.io/badge/Arch-ARM%20(32--bit)-red?style=for-the-badge" alt="ARM 32-bit">
  <img src="https://img.shields.io/badge/Status-Stable%20%2F%20Working-success?style=for-the-badge" alt="Status">
</p>

Custom recovery environment based on **TeamWin Recovery Project (TWRP) 3.1.1** tailored for the **Blackview BV5500 (Standard / Base model)**.

---

> [!WARNING]
> **Compatibility Notice:**  
> This recovery is compiled strictly for the **Blackview BV5500 Base model (MediaTek MT6580)**.  
> Do **NOT** attempt to flash this on the **BV5500 Pro** (MT6739 / 64-bit) or **BV5500 Plus**. Doing so will cause an immediate bootloop or brick.

> [!IMPORTANT]
> **Backup NVRAM & NVDATA First:**  
> MediaTek devices store cellular network calibrations and IMEI numbers in the `nvram` and `nvdata` partitions. Upon your first successful boot into TWRP, perform a full backup of both partitions and save it to an external MicroSD card or PC.

---

## 📱 Device Specifications

| Parameter | Specification |
| :--- | :--- |
| **Device Model** | Blackview BV5500 (Base) |
| **SoC** | MediaTek MT6580A Quad-Core @ 1.30 GHz |
| **GPU** | ARM Mali-400 MP2 |
| **CPU Architecture** | 32-bit (`arm` / ARMv7-A) |
| **RAM** | 2 GB LPDDR3 |
| **Internal Storage** | 16 GB eMMC |
| **Display** | 5.5" IPS HD+ (1440 × 720, 18:9) |
| **Stock OS** | Android 8.1 Oreo (Go Edition) |
| **Kernel Version** | Linux 3.18.xx |
| **Partition Scheme** | A-only (`system-as-system`) |

---

## 📋 Status & Working Features

- [x] **Boot & Display:** Powers on normally with full native resolution support.
- [x] **Touchscreen:** Responsive input navigation.
- [x] **Storage Mounting:** Internal Storage, MicroSD card, and USB OTG drives.
- [x] **Nandroid Backup & Restore:** `Boot`, `System`, `Vendor`, `Data`, `NVRAM`, and `NVDATA`.
- [x] **MTP Interface:** File transfer between phone and computer while inside TWRP.
- [x] **ADB Access:** Full ADB root shell support (`adb shell`).
- [x] **ZIP Flashing:** Magisk root, system patches, and zip packages.
- [x] **GSI Image Flashing:** Project Treble system images (`ARM A-only`).

---

## 🚀 Installation Guide

### Prerequisites
* Unlocked Bootloader (**OEM Unlocking** enabled in *Developer Options*).
* ADB & Fastboot drivers or MediaTek VCOM drivers installed on your PC.
* Downloaded recovery image: [`TWRP_Blackview_BV5500.img`](../../releases).

---

### Method 1: Via Fastboot (Recommended)

1. Put your phone into Bootloader / Fastboot mode:
   ```bash
   adb reboot bootloader
   ```
2. Confirm the device is recognized:
   ```bash
   fastboot devices
   ```
3. Unlock the bootloader *(if not already done — will wipe user data)*:
   ```bash
   fastboot oem unlock
   ```
   *(Press **Volume Up** on the phone to confirm)*.
4. Flash the TWRP image to the recovery partition:
   ```bash
   fastboot flash recovery TWRP_Blackview_BV5500.img
   ```
5. **Important:** Do not reboot normally into system, as the stock ROM may restore the stock recovery. Boot directly into TWRP:
   * Disconnect the USB cable.
   * Hold **Volume Up + Power**.
   * In the boot selection menu, highlight `[Recovery]` using *Volume Up* and confirm with *Volume Down*.

---

### Method 2: Via SP Flash Tool (MediaTek)

1. Open **SP Flash Tool** (v5.18xx or v5.19xx).
2. Under **Scatter-loading File**, select `MT6580_Android_scatter.txt`.
3. Uncheck all partition checkmarks.
4. Check **only** the `recovery` partition line.
5. Double-click the location column for `recovery` and choose `TWRP_Blackview_BV5500.img`.
6. Click **Download**.
7. Turn off the phone completely and connect it to the PC via USB.
8. Once the green **Download OK** ring appears, disconnect and power on holding **Volume Up + Power**.

---

## 📦 Flashing Custom ROMs / GSIs

Because the BV5500 features Project Treble on Android 8.1, you can install Generic System Images (GSIs):

* **Architecture Requirement:** Must be **`ARM` (32-bit)** and **`A-only`** (e.g., `system-arm-aonly-*.img`).
* **Format Data:** Always perform **Wipe > Format Data** (type `yes`) to decrypt userdata before booting a new ROM.

---

## 📜 Disclaimer & License

```
Your warranty is now void.
I am not responsible for bricked devices, damaged hardware, or corrupted partitions.
Proceed at your own risk.
```

* **TWRP:** Licensed under [GNU General Public License v3.0](https://www.gnu.org/licenses/gpl-3.0.html).
* **Base Kernel:** Proprietary MediaTek / Blackview kernel source.

---

## 🤝 Credits & Acknowledgments

* **[TeamWin](https://twrp.me/)** — For developing and maintaining the TWRP project.
* **Blackview** — For the original BV5500 device and kernel foundation.
* **Jemmini (4PDA)** — For the initial MT6580 recovery porting trees.
