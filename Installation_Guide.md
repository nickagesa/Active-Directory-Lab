# VirtualBox Lab Setup Guide

This document outlines the quick steps to set up a cybersecurity lab using VirtualBox with the following machines:
- Windows Server 2022 (Active Directory Server)
- Kali Linux
- Ubuntu 22.04 (with Splunk installed)
- Windows 10 Client

---

## Install VirtualBox on Windows

1. Download VirtualBox from [https://www.virtualbox.org/](https://www.virtualbox.org/).
2. Run the installer and follow the prompts.
3. Enable network features when prompted.
4. Finish installation and reboot if required.

---

## Install Virtual Machines

### 1. Windows Server 2022 (AD Server)

- Download ISO from Microsoft Evaluation Center [https://www.microsoft.com/en-us/evalcenter/evaluate-windows-server-2022].
- Create a new VM in VirtualBox:
  - **Name:** WinServer2022
  - **Type:** Windows
  - **Version:** Windows 2022 (64-bit)
  - **Memory:** 4GB+
  - **Disk:** 50GB+
- Start VM and select the Windows Server 2022 ISO.
- Install Windows normally.
- After installation:
  - Set a static IP address.
  - Open **Server Manager > Add roles and features > Active Directory Domain Services**.
  - Promote server to Domain Controller and create a new forest.
  - Reboot the server.

### 2. Kali Linux

- Download ISO from [https://www.kali.org/get-kali/](https://www.kali.org/get-kali/).
- Create a new VM in VirtualBox:
  - **Name:** Kali
  - **Type:** Linux
  - **Version:** Debian (64-bit)
  - **Memory:** 4GB+
  - **Disk:** 30GB+
- Start VM and select the Kali ISO.
- Follow guided installation.

### 3. Ubuntu 22.04 (with Splunk)

- Download Ubuntu 22.04 ISO.
- Create a new VM in VirtualBox:
  - **Name:** Ubuntu 22.04
  - **Type:** Linux
  - **Version:** Ubuntu (64-bit)
  - **Memory:** 4GB+
  - **Disk:** 30GB+
- Start VM and install Ubuntu.

#### Install Splunk on Ubuntu:
- Download Splunk `.deb` package from [https://www.splunk.com/](https://www.splunk.com/).
- Open terminal and run:
  ```bash
  sudo dpkg -i splunk_package.deb
  sudo /opt/splunk/bin/splunk start --accept-license
  sudo /opt/splunk/bin/splunk enable boot-start
