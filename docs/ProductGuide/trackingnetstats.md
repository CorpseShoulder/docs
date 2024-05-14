---
title: Product Guide - Tracking Network Statistics
description: Instructions for enabling statistics tracking and viewing those tracked statistics on NAT/PAT and Firewall rules
published: true
date: 2023-06-27T15:07:37.385Z
tags: 
editor: markdown
dateCreated: 2023-03-31T15:07:35.562Z
---

# Tracking Network Statistics

Statistics tracking can be enabled for Accept, Drop, Reject and Translate rules. This allows viewing the total number of packets/bytes processed by a rule.  (Currently, statistics cannot be tracked for Route rules.)

<br>
<br>

## Turn on Statistics Tracking for All Non-routing Rules of a Network

(requires a restart of the network)

1.  From the network dashboard, click **Edit** on the left menu.
2.  Check the ***Track Statistics For All Rules*** checkbox.
3.  Click **Submit**.
4.  Click **Restart** on the left menu to reset and apply the change. A typical restart will cause a momentary disruption.


**See directions below for viewing the tracked statistics.**

<br>
<br>

## Turn on Statistics Tracking for Individual Rules

1.  From the network dashboard, click **Rules** on the left menu.
2.  **Double-click the desired rule**.
3.  Check the ***Track Rule Statistics*** checkbox.
4.  Click **Submit**.
5.  Click **Apply Rules** on the left menu.

**See directions below for viewing the tracked statistics.**

<br>
<br>

## Reset Counter/Clear Statistics for an Individual Rule

1.  From the network dashboard, click **Rules** on the left menu.
2.  **Click the desired rule to select**.
3.  Verify the desired rule is selected (checkbox on the left will be checked.)
4.  Click **Clear Statistics** on the left menu.  Packets/Bytes counters for this rule will **restart again from zero.**

<br>
<br>

## Display Rule Statistics

1.  From the network dashboard, click **Rules** on the left menu.
2.  **Right-click on the columns heading** section at the top.
3.  Check the boxes for ***Packets*** and/or ***Bytes*** to display these columns.

![Show Statistics](/public/userguide-sshots/trackstats-cols.png)

> Enabling the "Statistics" column will show whether or not statistics tracking is enabled for each rule. {.is-success}

<br>   

> Need more Help? Email <a href="mailto:support@verge.io?subject=Support Inquiry" target="_blank" rel="noopener noreferrer">support@verge.io</a> or call us at <a href="tel:+855-855-8300">(855) 855-8300</a>{.is-info}

<br>

<div style="text-align:center; margin-bottom:5px">
  <a href="../ProductGuide/menu"><button class="button-grey"><b>↺</b> Back to the Product Guide</button></a>
  <a href="https://www.verge.io/test-drive#Demo-Section"><button class="button-cta">🚗 Take a Test Drive Today!</button></a>
</div>