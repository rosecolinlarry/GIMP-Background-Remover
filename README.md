# GIMP-Background-Remover
A small gimp plugin to easily remove the background of an image with [LDF](https://arxiv.org/pdf/2008.11048.pdf).  [Github of LDF](https://github.com/weijun88/LDF). 

## Made for GIMP 3.0 on Windows and Linux

Fork from the Linux only version [GIMP-Background-Remover ](https://github.com/manu12121999/GIMP-Background-Remover).

## Platform-specific Python Setup
The plugin creates a local virtual environment (`gimpenv`) and runs model inference through it. On Windows, GIMP's bundled Python is not suitable for installing standard PyPI wheels, so the installer requires a separate 64-bit Python 3.12 installation. On Linux, the installer uses the Python interpreter running GIMP.

---

## Prerequisites
1. **GIMP 3.0** (or newer) on Windows or Linux.
2. On **Windows**, install **Python 3.12 (64-bit)**:
   * Download from [python.org](https://python.org).
    * The installer discovers Python from the Windows registry, common installation paths, or `PATH`; the `py` launcher is not required.
3. On **Linux**, make sure the GIMP Python installation can create virtual environments and that `curl` is installed.
---

## Installation Steps

### Step 1: Copy Plugin Files to GIMP
1. Locate your GIMP 3.0 plug-ins directory in **Edit** > **Preferences** > **Folders** > **Plug-ins**.
    * On Windows, `%APPDATA%\GIMP\3.0\plug-ins` is the usual location.
2. Copy the `background-remover` folder into the plug-ins directory. Keep the folder named `background-remover`.

### Step 2: Install for Your GIMP Distribution

<details>
<summary><b>For GIMP Flatpak on Linux</b></summary>

1. Open **GIMP 3.0**.
2. Select **Filters** > **Remove_BG** > **[INSTALL] Offline Background Remover**.
3. Confirm the dialog and wait for the environment and model download to finish.
4. Restart GIMP if the new filter does not appear.

</details>

<details>
<summary><b>For other GIMP installations (Linux)</b></summary>

1. Install Python 3, its `venv` support, and `curl` using your distribution's package manager.
2. Open a terminal in the `background-remover` plug-in folder and run:

    ```bash
    bash ./setup.sh
    ```

3. Restart GIMP after installation.

</details>

<details>
<summary><b>For Windows</b></summary>

1. Install **Python 3.12 (64-bit)** from [python.org](https://python.org). The `py` launcher is not required.
2. Open **GIMP 3.0** and select **Filters** > **Remove_BG** > **[INSTALL] Offline Background Remover**.
3. Confirm the dialog and wait for the environment and model download to finish.
4. Restart GIMP if the new filter does not appear.

</details>

---

## Usage
1. Open an image in **GIMP 3.0** and select the layer you want to cut out.
2. Go to **Filters** > **Remove_BG** > **Offline Background Remover**.
3. The plugin will process the image offline and apply the cutout as a **Layer Mask** on your active layer.

![Image](https://github.com/user-attachments/assets/843f3074-f595-4fc0-b209-c5f0b486745c)

## Notes:
- The results might be slightly worse than with my [removebg](https://github.com/manu12121999/RemoveBG-GIMP) plugin, but it works offline and the libraries are open source.
