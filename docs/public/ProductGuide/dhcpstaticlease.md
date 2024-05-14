---
title: Product Guide - Create a DHCP Static Entry
description: Instructions for creating a DHCP static lease
published: true
date: 2023-06-27T15:08:05.179Z
tags: 
editor: markdown
dateCreated: 2023-03-29T21:26:04.464Z
---

# Create a DHCP Static Lease

A network with the **Dynamic DHCP** option enabled will automatically assign IP addresses to clients. For Virtual Machines where it’s advantageous to ensure the same address is always assigned, you can create a static IP Address assigned to the associated MAC address.

**A Static Address can be assigned in one of two ways:**

-   **Change a Dynamic Entry to Static**
After the VM has already received a DHCP address and currently still holds the lease, designate the address to be static from now on.

**-OR-**

-   **Create a New Static Entry**
Create a new IP Address entry, specifying the MAC address from the VM Nic and the desired IP address.
<br>
<br>

## To Change a Dynamic entry to Static:

1.  From the Network Dashboard, click **IP Addresses** on the left menu.
2.  Find the DHCP address, appearing in the IP Addresses listing as type “Dynamic”
3.  **Double-click** the entry and change the ***Type*** to **Static**.
4.  Click **Submit** to save the change.
<br>
<br>

## To Create a New Static Entry:

1.  Obtain the MAC address from the server (within the guest OS or from the VM Dashboard-NICs section.)
2.  From the Network Dashboard, click **New** from the left menu.
3.  In the ***Type*** field, select **Static**.
4.  Enter the desired ***IP Address***.  **Make sure to assign an IP address that is within the network’s address range and not used by another VM on this network.**

5. Enter the ***MAC Address***.
6.  Enter the ***Hostname*** of the server.
7.  **Optionally**, a ***Description*** can be entered to record additional administrative information.
8.  Click **Submit**.

<br>   

> Need more Help? Email <a href="mailto:support@verge.io?subject=Support Inquiry" target="_blank" rel="noopener noreferrer">support@verge.io</a> or call us at <a href="tel:+855-855-8300">(855) 855-8300</a>{.is-info}

<br>

<div style="text-align:center; margin-bottom:5px">
  <a href="../ProductGuide/menu"><button class="button-grey"><b>↺</b> Back to the Product Guide</button></a>
  <a href="https://www.verge.io/test-drive#Demo-Section"><button class="button-cta">🚗 Take a Test Drive Today!</button></a>
</div>