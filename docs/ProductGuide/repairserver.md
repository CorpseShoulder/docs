---
title: Product Guide - ioGuardian
description: Explanation of the repair server function and instructions for creating a new repair server
published: true
date: 2024-03-12T13:37:19.675Z
tags: 
editor: markdown
dateCreated: 2023-03-31T20:46:27.474Z
---

# Repair Server (ioGuardian)

A Repair Server provides a potential repair mechanism after a system experiences a problem that extends beyond its redundancy tolerance (e.g. simultaneous, multiple drive failures spanning multiple nodes). Typically, a Repair Server is a sync destination that contains a fairly recent replication of the given system. A Repair Server will automatically attempt to pull back any needed blocks from the remote system, potentially avoiding the need to roll back using a Snapshot. It is generally recommended to have a Repair Server in place whenever possible.


> There is a higher chance of repair success when there is a good network connection, with relatively low latency, between the system and its Repair Server.{.is-success}

A Repair Server is created using the existing outgoing sync configuration: VSAN Host (address of the remote destination), VSAN Port, system-generated authorized username/password, and encryption setting (enabled or disabled based on the associated sync configuration).


<br>
<br>


## To Create a Repair Server from an Outgoing Sync (common method)

> Note: Repair servers may be auto-generated when [**Adding Sites to the Dashboard**](/public/ProductGuide/configuringsitesdash-addingsites#Repairserver).{.is-info}

Typically, a repair server is created from an Outgoing Sync because the sync destination would contain a recent copy of the data. This is the recommended method in most cases.

1.  From the Outgoing Sync Dashboard, click **Create Repair Server** on the left menu.
2.  Enter a ***Name*** for the Repair Server. Use a name that will be helpful for future administration, for example a name that includes that of the remote system.
3.  Optionally, a ***Description*** can be entered to store additional information.
4.  Click **Submit** to complete the creation.
A Repair Server is created using the outgoing sync configuration details, including: VSAN Host (address of the remote destination), VSAN Port, system-generated authorized username/password, and encryption setting.

<br>
<br>


## To Create a Repair Server from the Repair Servers List Page
In instances where there is no current Outgoing Sync from which to configure the Repair Server (e.g. a three-way sync configuration or a previous sync destination that is no longer in use), the following instructions can be used:

1.  From the Main Dashboard, select **Backup/DR** from the from the left menu.
2.  Click **Repair Servers** on the left menu.
3.  Click **New** on the left menu.
4.  Enter a ***Name*** for the Repair Server. Use a name that will be helpful for future administration, for example a name that includes that of the remote system.
5.  Optionally, a ***Description*** can be entered to store additional information.

<br>

### Automatic (Copy) Credentialling
Credentials can be copied from an existing outgoing sync:
 - Select **Copy** in the ***Credentialling*** dropdown list.

 - Select **desired Sync** in the ***Copy Credentials from*** dropdown list.

<br>

### Manual Credentialling
To manually enter credential information:
select **Manual** in the ***Credentialling** dropdown list.

### Credential Fields
   -   ***VSAN Host*** url to the root level of the remote system
   -   ***VSAN Port*** default 14201, a different port can be used but must be configured on the remote side as well and ports open on intermediate firewall(s).
   -   ***User***
   -   ***Password*** and ***Confirm Password*** for the specified VergeIO User.
   -   ***Encryption***
6.  Click **Submit** to complete the creation.

<br>

> Need more Help? Email <a href="mailto:support@verge.io?subject=Support Inquiry" target="_blank" rel="noopener noreferrer">support@verge.io</a> or call us at <a href="tel:+855-855-8300">(855) 855-8300</a>{.is-info}

<br>

<div style="text-align:center; margin-bottom:5px">
  <a href="../ProductGuide/menu"><button class="button-grey"><b>↺</b> Back to the Product Guide</button></a>
  <a href="https://www.verge.io/test-drive#Demo-Section"><button class="button-cta">🚗 Take a Test Drive Today!</button></a>
</div>