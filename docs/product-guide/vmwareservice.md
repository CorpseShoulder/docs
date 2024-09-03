# VMware Service

The VergeOS VMware Service provides a direct interface with vSphere to run a backup agent for VMware virtual machines, allowing for both one-time imports and ongoing backup, DR, and migration solutions.

## Create a VMware Service

1. From the Main Dashboard, click **Backup/DR** on the left menu.
2. Click **VMware** on the left menu.
3. Click **New** on the left menu.
4. Enter a **Name** for the VMware service (required).
5. Set **Cores** and **RAM** (default 2 cores and 2GB RAM is typically sufficient).
6. Select a **Network** on which to run the VMware service.

!!! info "The selected network must have DHCP enabled."

7. Enter the **vSphere DNS or IP** (required).
8. Enter the **vSphere Port** (default is 443).
9. Enter the **vSphere User** and **Password**.
10. Click **Submit** to save the new service.
11. Select the new service and click **Power On** on the left menu.

### Advanced vSphere Settings

After powering on the service, you can modify advanced settings:

1. From the VMware Service Dashboard, click **Edit** on the left menu.
2. Adjust the following settings as needed:
   - **Max Concurrent VM backups**: Number of simultaneous VMware backups (default is 4).
   - **Name for auto-created snapshot**: Name given to temporary VMware-created snapshots during backup.
   - **Default VM backup schedule**: Automatically assign a backup schedule to newly detected VMs.
   - **Automatically enable change tracking per VM**: Enable VMware CBT feature for each VM (recommended).
   - **Backup storage tier**: VergeOS storage tier for backup data (default is tier 4).
3. Click **Submit** to save changes.

## Create a VMware Backup Schedule

1. From the VMware Service Dashboard, click **Schedules** on the left menu.
2. Click **New** on the left menu.
3. Enter a **Name** for the new Schedule.
4. Click **Submit**.
5. Double-click the new Schedule in the list.
6. Click **New Task** on the left menu.
7. Configure the task settings:
   - **Name**: Enter a descriptive name for the task.
   - **Scheduling**: Set the frequency and time for the backup.
   - **Backup Job Retention**: Specify how long to keep the backup.
   - **Backup Mode**: Choose Differential, Full Backup (Thick provisioned), or Full Backup (Thin provisioned).
8. Click **Submit** to save the task.

!!! info "Repeat steps 6-8 to add additional tasks to the schedule as needed."

## Assign Schedules to VMs

1. From the VMware Service Dashboard, click **Virtual Machines** on the left menu.
2. Select the desired VM(s) from the list.
3. Click **Edit Backup Schedules** on the left menu.
4. Select the **Schedule** from the dropdown list.
5. Click **Submit**.

## Perform a Manual Backup

1. From the VMware Service Dashboard, click **Virtual Machines** on the left menu.
2. Select one or more VM(s) in the list.
3. Click **Backup** on the left menu.
4. Click **Yes** to confirm the backup action.

## Import VMware VMs into VergeOS

### Prepare for Import

1. Ensure the VMware Service is set up and connected to your vSphere environment.
2. From the VMware Service Dashboard, click **Virtual Machines** on the left menu.
3. Verify that the VMs you want to import are listed and have a recent backup.

!!! warning "For production VMs, it's recommended to perform a final backup while the VMs are powered off to ensure data consistency."

### Perform the Import

1. From the VMware Service Dashboard, click **Backup Jobs** on the left menu.
2. Locate the backup job containing the VMs you want to import.
3. Double-click the backup job to open its dashboard.
4. In the Virtual Machines section, select the VM(s) you want to import.
5. Click **Import VMs** on the left menu.
6. In the import settings:
   - Choose whether to **Preserve MAC Addresses**.
   - Select the desired **Preferred Tier** for VM storage.
7. Click **Submit** to start the import process.

!!! info "The import process duration depends on the size and number of VMs being imported. Large VMs or multiple VMs may take considerable time."

### Post-Import Steps

1. Once the import is complete, navigate to **Machines** > **Virtual Machines** on the main dashboard.
2. Locate the imported VM(s) in the list.
3. Select a VM and click **Edit** on the left menu to adjust any settings if needed.
4. To start the VM, click **Power On** on the left menu.

!!! warning "Before powering on imported VMs, ensure that the network settings in VergeOS match your desired configuration to prevent potential conflicts."

### Verify the Imported VM

1. After powering on the VM, click **Remote Console** on the left menu to access the VM's console.
2. Verify that the VM boots correctly and all expected data and applications are present.
3. Test network connectivity and functionality within the VergeOS environment.

!!! info "If you encounter any issues with the imported VM, check the VM's logs and consider reimporting using a different backup job or adjusting the import settings."

## Restore VMware Backups

### File-level Restore

1. From the Backup Job Dashboard, double-click the individual VM.
2. Click **Import VM** on the left menu.
3. Power on the imported VM in the VergeOS environment.
4. Extract the desired files to the VergeOS NAS.
5. Access the files via CIFS or NFS.

### Restore to VMware Environment

Individual VMs or entire VMware system backups can be pushed back to the VMware environment. Contact VergeOS support for detailed instructions on this process.

### DR/Business Continuity

1. Power up VMware VMs in VergeOS from the backup.
2. Use built-in Site-Sync to synchronize VMware backups offsite.

!!! info "Site-Sync provides a mechanism for quick recovery in the event of a disaster or primary facility outage."

## Troubleshoot VMware Service Connection Errors

If you encounter connection errors:

1. Verify the correct vSphere address and port.
2. Ensure network connectivity between the VMware service network and the vSphere system.
3. Confirm vSphere login credentials are correct.
4. For self-signed certificates, enable the "Allow Insecure Certificates" option:
   - From the VMware Service Dashboard, click **Edit** on the left menu.
   - Check the box for **Disable SSL host certificate verification**.
   - Click **Submit**.

!!! info "Check the Logs at the bottom of the Dashboard page for additional troubleshooting information."