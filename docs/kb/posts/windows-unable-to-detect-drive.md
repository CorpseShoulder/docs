---
title: Windows is Unable to Detect a Virtual Disk Drive
slug: windows-is-unable-to-detect-a-virtual-disk-drive
description: 
published: true
date: 2023-01-23T22:31:40.674Z
tags: vm, windows, virtio, scsi
categories:
  - Troubleshooting
  - VM
editor: markdown
dateCreated: 2022-06-24T13:27:06.698Z
---

## Virtual Disk Drive not detected in Windows

In most cases this is because the disk drive **Interface Type** is set to **virtIO-SCSI** (which is the default value) on any virtual machine that is being created. If that is the case, you will need to load the **virtIO drivers** during the Windows installation process. Windows does not natively recognize virtIO interfaces, so it cannot see the virtual disk.

Open Source virtIO drivers can be downloaded from [here](https://github.com/virtio-win/virtio-win-pkg-scripts/blob/master/README.md) courtesy of Fedora Linux.

If Redhat virtIO drivers are required due to signed driver needs within Windows, a Redhat account will need to be made on their website and the drivers downloaded directly from them.

## Installing virtIO Drivers during Windows Install
During a Windows installation, users can use the console interface tools to change the CD-ROM image to the newly downloaded virtIO drivers iso. Information on using the console interface tools can be found in the inline help within the category titled **VDI** under the section **Using the Console**.

Alternatively, you can choose to change the virtual disk drive **Interface type** to **SATA** and Windows will find the virtual disk and continue with the installation.
> This will come with a performance impact due to SATA drivers being software emulated.
{.is-info}

<br>

> Need more Help? Email <a href="mailto:support@verge.io?subject=Support Inquiry" target="_blank" rel="noopener noreferrer">support@verge.io</a> or call us at <a href="tel:+855-855-8300">(855) 855-8300</a>{.is-info}

<br>
<div style="text-align: center">
  <a href="https://wiki.verge.io/en/public/kb"><button class="button-grey"> <b>↺</b> Back to Knowledgebase</button></a>
<a href="https://www.verge.io/test-drive"><button class="button-orange">🚗 Take a Test Drive Today!</button></a>
</div>