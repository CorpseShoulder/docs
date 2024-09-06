---
title: Creating Bootable Installation Media
slug: creating-bootable-installation-media
description: How to create a bootable USB to install VergeOS.
draft: false
date: 2023-03-27T18:31:37.067Z
tags: iso, rufus, bootable, usb
categories:
  - Installation
editor: markdown
dateCreated: 2022-08-04T18:16:50.678Z
---

# Creating Bootable Installation Media

This guide explains how to create a bootable USB to install VergeOS on different operating systems.

## Windows

1. **Download the VergeOS installation ISO** from [https://updates.verge.io/download](https://updates.verge.io/download).

2. **Insert a USB drive** into your computer.

    !!! warning
        This USB drive will be overwritten.

3. **Download and launch Rufus** from [https://rufus.ie/en/](https://rufus.ie/en/).

4. In Rufus:
    - Select your **USB device** under **Device**.
    - Click the **Select** button and choose the VergeOS installation ISO.
    - Click **Start**.

5. **Choose ISO mode** when prompted by Rufus, then select **DD** mode to proceed.

    !!! danger "It is critical to choose **DD mode** during this step. Selecting the wrong mode can result in an unbootable USB drive"

6. Rufus will begin creating the bootable USB. Once complete, your USB is ready to be used for VergeOS installation.

---

## macOS

1. **Download the VergeOS installation ISO** from [https://updates.verge.io/download](https://updates.verge.io/download).


2. **Insert a USB drive** into your computer.

    !!! warning
        This USB drive will be overwritten.

3. **Download and install BalenaEtcher** from [https://www.balena.io/etcher/](https://www.balena.io/etcher/).

4. **Launch BalenaEtcher** and:
    - Click **Flash from file**, and select the VergeOS ISO.
    - Select the target **USB disk** (be careful not to select hidden drives).
    - Click **Flash!** to start the process.

5. Once the flashing process is complete, your USB drive will be ready to boot and install VergeOS.

---

## Linux Mint

1. **Download the VergeOS installation ISO** from [https://updates.verge.io/download](https://updates.verge.io/download).


2. **Insert a USB drive** into your computer.

    !!! warning
        This USB drive will be overwritten.

3. Using Mint’s file browser, navigate to the downloaded ISO file:
    - **Right-click** the ISO and choose **Make bootable USB stick**.
    - In the USB Image Writer, select the **USB media** to write the installation file to.
    - Authenticate with your admin password when prompted.
    - Click **Authenticate** to start writing the ISO to the USB drive.

4. Once the process is finished, your bootable USB stick will be ready for VergeOS installation.

---

By following these steps for your specific operating system, you'll have a bootable USB ready to install VergeOS on your server.
