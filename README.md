

# 🔥 SSL-BYPASS

### Android APK Security Research Toolkit

**Decompile · Inspect · Modify · Rebuild · Sign**

[![Platform](https://img.shields.io/badge/Platform-Android%20%7C%20Termux-3DDC84?style=for-the-badge&logo=android&logoColor=white)](https://termux.dev/)
[![Language](https://img.shields.io/badge/Language-Python-3776AB?style=for-the-badge&logo=python&logoColor=white)](https://www.python.org/)
[![Tool](https://img.shields.io/badge/Tool-Apktool-red?style=for-the-badge)](https://apktool.org/)
[![Author](https://img.shields.io/badge/MADE%20BY-AMI--VILLAIN-black?style=for-the-badge&logo=github)](https://github.com/Ami-Villain)

**Developer:** [@Ami-Villain](https://github.com/Ami-Villain)
:::

------------------------------------------------------------------------

## 📌 About

**SSL-BYPASS** is a Python-based Android APK research utility designed
to help authorized testers inspect how Android applications handle
network security configuration and selected VPN-related checks.

The program uses **Apktool** to decompile an APK, applies its configured
modifications to the decoded project, rebuilds the package, and signs
the resulting APK with a local debug keystore.

> ⚠️ This tool changes application security behaviour. Use it only with
> applications you own or have explicit permission to assess.

## ✨ What it does

-   **APK decompilation:** decodes an APK project with Apktool.
-   **Network security configuration:** adds a configuration that
    permits cleartext traffic and trusts system and user-installed
    certificates.
-   **Static Smali modification:** attempts to alter selected boolean
    methods whose code contains VPN/network-related indicators.
-   **APK rebuild:** rebuilds the decoded project with Apktool.
-   **Debug signing:** signs the rebuilt APK using a local debug
    keystore.

*Results depend on the target app. This is an experimental utility, not
a universal compatibility guarantee.*

## ⚙️ Requirements

-   Android device with [Termux](https://termux.dev/) (the script
    includes Termux setup checks), or a compatible Linux environment.
-   Python 3
-   `colorama` Python package
-   Java JDK / OpenJDK (including `keytool` and `jarsigner`)
-   `aapt`
-   [Apktool](https://apktool.org/) (the script attempts to download it
    automatically in Termux)

### Install on Termux

``` bash
pkg update && pkg upgrade
pkg install -y python openjdk-17 aapt
pip install colorama
```

The script attempts to download Apktool into the Termux `bin` directory
if it is not already available.

## 🚀 Usage

Clone the repository:

``` bash
git clone https://github.com/Ami-Villain/-SSL-BYPASS.git
cd -SSL-BYPASS
```

Run the script with an APK you are authorized to test:

``` bash
python sslbps.py path/to/your-app.apk
```

Optional: choose an output directory:

``` bash
python sslbps.py path/to/your-app.apk path/to/output
```

The output directory contains the decoded project, an unsigned rebuilt
APK, and the signed APK (named with the `_patched.apk` suffix).

## 🔄 High-level workflow

``` text
Input APK
   │
   ▼
Decode with Apktool
   │
   ▼
Apply configured network-security changes
   │
   ▼
Attempt selected Smali checks modification
   │
   ▼
Rebuild APK
   │
   ▼
Sign with local debug keystore
   │
   ▼
Test artifact (for authorized assessment)
```

## 📁 Project structure

``` text
-SSL-BYPASS/
├── assets/
│   └── banner.png
├── sslbps.py
├── requirements.txt
└── README.md
```

## ⚠️ Important notes

-   Keep an untouched backup of the original APK.
-   The generated APK is signed with a **debug key**, not the original
    developer's signing key. It will not be an authentic update for the
    original app.
-   Rebuilding or modifying an APK can break its behaviour or cause
    installation failures.
-   The script's pattern-based Smali changes may miss checks or modify
    code unexpectedly.
-   The script may download and execute third-party build tooling.
    Review those downloads and their sources before running it.
-   Do not use this tool against apps, accounts, networks, or data
    without authorization.

## 🛡️ Disclaimer

This project is provided for **educational purposes, defensive security
research, and authorized Android application testing only**.

-   Only test applications that you own or have explicit written
    permission to assess.
-   Do not use this project to access, intercept, modify, or interfere
    with another person's data or services.
-   Do not redistribute modified third-party applications unless you
    have the necessary rights.
-   You are responsible for complying with all applicable laws,
    regulations, and platform terms.
-   The developer is not responsible for misuse, damage, data loss, or
    legal consequences arising from use of this project.

## 👨‍💻 Author

::: {align="center"}
### **Ami-Villain**

[![GitHub](https://img.shields.io/badge/GitHub-Ami--Villain-181717?style=for-the-badge&logo=github)](https://github.com/Ami-Villain)

**Made with curiosity for Android security research.**
:::

------------------------------------------------------------------------

::: {align="center"}
**⭐ If this repository helps your authorized research, consider giving
it a star.**

*Stay Ethical · Stay Secure*
:::
