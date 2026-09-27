# Unbound

> **Experimental Notice:** This tool is currently experimental. Because it requires Windows Test Signing and Secure Boot to be disabled, **it should be avoided if you play games protected by kernel-level anti-cheat (e.g., Easy Anti-Cheat, BattlEye, Vanguard)**, as those titles may refuse to launch or flag your system.
>
> **Hardware Caution:** Raising power limits beyond factory specifications significantly increases thermal output and VRM electrical stress. Adequate cooling is essential. Unbound only raises allowable power ceilings—it does not guarantee specific wattage or override internal hardware failsafes.

Unbound modifies NVIDIA mobile GPU power and current limits directly in memory on Windows. It unlocks up to a **250 W Base TGP** (alongside 250 A NVVDD / 100 A MSVDD limits) so external tuning tools and control centers can push higher sustained wattage.

It does **not** flash vBIOS, alter driver files on disk, or trip permanent hardware locks. Changes reset upon reboot unless reapplied by the included startup task.

---

## Supported Hardware

Compatible with mobile NVIDIA GPUs regardless of laptop brand (Clevo, Tongfang, Razer, Lenovo, etc.):

- **NVIDIA GeForce RTX 5070 Ti Laptop GPU**
- **NVIDIA GeForce RTX 5080 Laptop GPU**
- **NVIDIA GeForce RTX 5090 Laptop GPU**

*Note: Desktop GPUs are not supported. Exactly one supported discrete mobile GPU must be present.*

---

## Prerequisites

Before starting, configure your system to allow development-signed kernel drivers:

1. **Back up your BitLocker Recovery Key** (or temporarily suspend BitLocker) before modifying UEFI boot options.
2. **Disable Secure Boot** in your laptop's BIOS/UEFI settings.
3. **Download & Extract** the complete `Unbound-Target.zip` to a local folder (do not run files from inside the archive).

---

## Quick Start

### 1. Enable Test Mode
1. Right-click `TESTMODE-ON.bat` and select **Run as administrator**.
2. Restart your computer. (A "Test Mode" watermark will appear in the bottom-right corner of your desktop).

### 2. Install Unbound
1. Right-click `INSTALL-XMGPOWERPATCH.bat` and select **Run as administrator**.
2. If the console shout out a previous runtime detected you had to restart and use the installer again.
3. Once the console reports `STARTUP_INSTALLED`, restart your computer.
4. Log in to Windows. The patch applies automatically via an elevated scheduled task at login.

### 3. Apply Your Power Profile
Open the bundled Uniwill-Control-Utility (UCU):
1. Go into Settings > Advanced Features and enable "Power boost mode"
2. Navigate to the Presets page
3. Under "Nvidia GPU Tuning", set the TGP to a desired value (up to 250W)
4. Apply the preset

---

## Uninstallation

To cleanly remove all background tasks, drivers, and restore default Windows signing:

1. Right-click `UNINSTALL-XMGPOWERPATCH.bat` and select **Run as administrator**.
2. Right-click `TESTMODE-OFF.bat` and select **Run as administrator**.
3. Restart your computer.
4. *(Optional)* Re-enable Secure Boot in your UEFI firmware.
