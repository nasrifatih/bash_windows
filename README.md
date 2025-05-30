# Mounting Network Drives in Bash on Windows via WSL

This is a simple guide for setting up **Bash on Windows** using **WSL (Windows Subsystem for Linux)** and mounting network drives (e.g. `F:` drive as `/mnt/k`) that may not automatically appear in your WSL environment.

---

## Prerequisites

- Windows 10 or 11 with WSL support  
- Admin privileges on your machine  
- A network drive mapped in Windows (e.g. `K:`)  

---

## 🛠 Step-by-Step Guide

### 1. Install WSL + Ubuntu

If you haven’t already installed WSL, run this from PowerShell or Command Prompt:

```bash
wsl --install
```

This will install WSL along with Ubuntu by default. A restart might be required.

---

### 2. Launch WSL / Ubuntu

You can now launch your Linux environment by running:

```bash
wsl
```

Or open the **Ubuntu** app from your start menu.

---

### 3. Create a Mount Point in WSL

If your network drives aren’t visible by default inside WSL, create a folder to mount them to.  
For example, to mount a drive as `/mnt/k`:

```bash
sudo mkdir -p /mnt/k
```

---

### 4. Manually Mount the Network Drive (run this command from the subdirectory)

Use the `drvfs` file system type to mount your Windows drive into WSL.  
Here’s how to mount the Windows `K:` drive into `/mnt/k`:

```bash
sudo mount -t drvfs K: /mnt/k
```

Now your network drive is accessible inside WSL at:

```bash
/mnt/k
```

---

## Notes

- You can replace `K:` with any other Windows drive letter.
- If you encounter permission issues, ensure the drive is already mounted and accessible in Windows.
- For drives that disconnect often, you can script this and auto-run it in your WSL profile.

---

## Unmounting (Optional)

To unmount the drive:

```bash
sudo umount /mnt/k
```
