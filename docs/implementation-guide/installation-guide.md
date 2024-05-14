# VergeOS Installation Guide

## Introduction 

Welcome! In this guide, we'll walk through installing VergeOS to get your environment optimally configured for performance and stability. 

Before diving in, check out the Deployment Planning Guide for important guidance on hardware selection, network setup, VLANs, and more to ensure a smooth installation.

---

## Configure Networking

Properly configured networks are critical for a successful VergeOS installation. Here's what you'll need to do:

 - Identify the physical NICs that will connect to your [External](glossary.md/#external-network) and [Core](glossary.md/#fabriccore-network) networks for regular operations and, optionally, a maintenance network for iPMI access and PXE boot. 

 - Collect the MAC addresses for each NIC port and identify which network (External/Core/Maintenace) they will be assigned to.

!!! tip "Obtaining the MAC addresses for each NIC port helps identify the physical cabling."

---

## Install First Controller Node

Now you're ready to install the first controller node:

### Installation Type

1. Boot the server from the VergeOS installer ISO image.

2. Select "Controller" and "Yes" when asked if this is a new install. 

3. Follow the prompts for setting the timezone and current date / local time.

4. Name your cloud and enter your new admin credentials

!!! note "This field cannot be blank and must be at least 8 characters in length"
    Make sure to have this password available for the initial login to the installed VergeOS system. The password can be changed post-install by editing the admin user. 

### Setup Networking

1. Select the number of [Physical](glossary.md/#fabriccore-network) switches you will be connecting to, by default this will be set to the number of NICs detected by the OS.

!!! tip "It is strongly recommended to keep the number that is originally shown so you can configure ALL detected NICs during the installation (even if you not planning to use all of them initially)."

!!! warning "If the External Network ports are to be bonded (LAG), choose one less than what is displayed on this screen."

2. Choose "Yes" to automatically detect network configuration. The installer will find the interfaces if NICs are cabled properly.

3. Select the NIC to be used for the first **[Core Network](glossary.md/#fabriccore-network)**
!!! tip "NICs with an active link will have an asterisk (*) at the beginning of the device description."

4. Configure the first **Physical Core Switch**
    - Name: The name that will be shown in the UI
    - MTU: The MTU setting must be a value supported by the physical switching hardware and large enough to support the required levels of tenancy. The default MTU is 9192. This setting is compatible with nearly all modern switches and will support 5 levels of nested tenancy.
    - Core-Network: Yes indicates that the NIC is designated to be a part of the core network. To remove this designation, edit the field and remove "Yes". You can either type "No" or leave the field blank to remove the designation. In this scenario, "Yes" is the correct answer.
    - VLAN: If the NICs are designated to be in a tagged VLAN, enter the VLAN ID here. In most cases, this setting is left blank since the NICs for the core network should be in a Native VLAN or PVID.
!!! tip "Keyboard Hints:"
    **[Tab]** will not move you between fields but rather moves between the form options(Finish/Edit/Cancel).  

    **[Enter]** toggles edit mode on/off. When a field shows a cursor, edit mode is ON, and you can modify the contents. When a field is highlighted in blue, edit mode is OFF, and you can move between fields with the up/down arrow keys.

5. The network address scheme for the first core NIC defaults to 172.16.1.2/24. In typical use cases, this scheme is acceptable since the NICs should be in a dedicated VLAN, preventing them from broadcasting traffic anywhere outside of the environment.

6. Repeat the above process for your remaining **Core Network NICs**

7. Configure the **Physical External Switchk**
    - Name: The name that will be shown in the UI. We suggest you rename this to **External**
    - MTU: The MTU setting must be a value supported by the physical switching hardware
    - Core-Network: Change this value to **"no"** as this is our external switch
    - VLAN: If the NICs are designated to be in a tagged VLAN, enter the VLAN ID here.

8. Review defaults for the Core and DMZ VXLAN
  - In typical cases, the IP scheme is left as the default setting. It is designed to run in the Carrier Address space to reduce potential conflicts. It is best to consult with VergeIO support for assistance when considering a different IP scheme

9. Select the switch that will provide **external** access

!!! warning "If you do not configure a switch with external UI access, you will only be able to access the VergeOS UI from the local node console until it is configured."

10. Configure network addressing for your external network
!!! note "This will be the IP address used to access vergeOS UI"

11. If you configured a maintenance network, select it here otherwise just select OK

### vSAN Encryption

!!! danger "This option is irreversible and cannot be changed without a full re-install. Do not continue until you are certain whether you are encrypting the vSAN or not."

### vSAN Storage

1. Unselect drives that should be excluded from the vSAN

2. Optionally set custom storage tiers for drives or use the defaults.

!!! warning "All drives in a tier of storage **MUST** have similar geometry!"

3. Configure Swap
    - There are multiple factors to consider in planning swap including: availability of storage, system use, disk type, etc. Review the Implementation Guide or consult with the VergeIO implementation team for further information. The recommendation is to configure enough swap to hold the largest workload expected to run.

The installer will format drives, install VergeOS, and reboot. Once complete, the VergeOS login screen will appear and the first controller node is ready!

---

## Add Second Controller Node  

With the first node installed, let's add the second controller:

1. Boot the second node from the installer ISO.

2. Select "No" when asked if this is a new install to join this node to the first one. 

3. Enter the admin username and password configured during the first node's installation.

4. As before, auto-detect the network config, enable encryption if previosuly enabled, and select drives for the vSAN.

5. Ensure the storage tier assignments match the first node.

After drive formatting and installation, the second node will reboot and automatically join the first one to form an HA cluster. 

---

## Install Additional Nodes

You can now install additional nodes as needed:

- **Scale-out**: Member nodes that expand the vSAN storage 
- **Compute**: Compute-only nodes without vSAN (boot device only)
- **PXE**: Compute nodes that network boot (no local boot device)

!!! note "The PXE option uses a network boot image of VergeOS, not the PXE installer"

Follow the same process as the second controller node, selecting the appropriate node type when prompted.

---

## Verify and Next Steps

Once installation is complete:

1. Open the VergeOS web UI via the system's IP address 
2. Verify the new nodes were added successfully without errors
3. Start deploying VMs and containers!

!!! note "Log entries indicating “root key” errors during the process of adding nodes to a system are normal and can be ignored."

---

## Troubleshooting & Support

If issues arise during installation:

- Press `Esc` to cancel and get a command prompt
- Type `yb-install` to resume or `yb-install --restart` to start over

Need more help? Email support@verge.io or call (855) 855-8300.