---
title: Product Guide - IPMI
description: Explanation of IPMI and how it is supported for use within the VergeIO interface. 
published: true
date: 2024-03-29T18:36:07.895Z
tags: 
editor: markdown
dateCreated: 2023-03-27T21:14:30.263Z
---

# IPMI

IPMI is a universal standard (supported by almost all hardware) for managing and accessing servers. It is accessible even when a server is powered off and allows for remotely controlling servers and monitoring hardware status, including things such as temperature, power consumption, voltage, hardware errors, etc. VergeIO integrates with IPMI to provide for remote server power control (power on, power cycle, etc.) and convenient access via the VergeIO user interface.

> Because IPMI deals with physical hardware, it only applies to host level nodes (not tenant nodes). {.is-info}


<br>
<br>

## To Test IPMI Connectivity

1.  From the Main Dashboard, click on the **Nodes** count box.
2.  **Double-click the desired node** to access the node dashboard.
3.  Under the **IPMI** submenu, click **Test** on the left menu.

<br>
<br>

### IPMI Connection Status
The node dashboard will indicate IPMI ***status*** and ***date/time of last time connected***:

  - **IPMI Status** - "OK" indicates that the last attempt to connect was successful. If the last attempt was unsuccessful, an error message is displayed.
  <br>

  - **IPMI Last Connected** - displays the last date/time the VergeIO system successfully connected to IPMI. (If there was never a successful IPMI connection, the field will report "NA".)
  <br>

![nodedash-ipmistatus.png.png](/public/userguide-sshots/nodedash-ipmistatus.png)

<br>
<br>

## To Change Stored IPMI login credentials
> The following instructions provide for changing the IPMI credentials a node will use to interface with IPMI. Changing these fields does not perform IPMI user administration; connect to your IPMI web interface to add or change IPMI users. {.is-success}

1.  From the Node Dashboard, click **Edit** on the from the left menu.
2.  Enter a valid ***IPMI User***. (IPMI user should have administrator-level privileges.)
3.  Enter ***IPMI Password***.
4.  Click **Submit** to save the changes to the node.


<br>
<br>

## To Access the IPMI Web Interface

> Successfully connecting to the IPMI web interface through the VergeIO user interface requires valid username/password is stored and appropriate networking configuration is in place for the system to interact with the node's IPMI. {.is-info}

1.  From the main dashboard, click **Nodes**.
2.  **Double-click the desired node** to access the node dashboard.
3.  Under the **IPMI** submenu on the left menu, click **Connect**.
4.  A new browser tab is opened to the IPMI web interface login page.

<br>   

> Need more Help? Email <a href="mailto:support@verge.io?subject=Support Inquiry" target="_blank" rel="noopener noreferrer">support@verge.io</a> or call us at <a href="tel:+855-855-8300">(855) 855-8300</a>{.is-info}

<br>

<div style="text-align:center; margin-bottom:5px">
  <a href="../ProductGuide/menu"><button class="button-grey"><b>↺</b> Back to the Product Guide</button></a>
  <a href="https://www.verge.io/test-drive#Demo-Section"><button class="button-cta">🚗 Take a Test Drive Today!</button></a>
</div>