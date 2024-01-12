---
subcollection: vmware-service
copyright:
  years: 2023
lastupdated: "2023-12-21"

content-type: tutorial
services: vmware-service
account-plan: paid
completion-time: 30m

---
{{site.data.keyword.attribute-definition-list}}

# Migrating {{site.data.keyword.vmware-service_short}} workloads with cloud-to-cloud connections
{: #vcda-migrating-cloudtocloud-vmaas}
{: toc-content-type="tutorial"}
{: toc-services="vmware-service"}
{: toc-completion-time="30m"}

You can use VMware Cloud Director Availability (VCDA) to create cloud-to-cloud connections to migrate your workloads between {{site.data.keyword.vmware-service_full}} instances.

## Objectives
{: #vcda-migrating-cloudtocloud-vmaas-objectives}

In this tutorial, you learn how to create cloud-to-cloud connections between your instance and other {{site.data.keyword.vmware-service_short}} instances.

## Before you begin
{: #vcda-migrating-cloudtocloud-vmaas-prereqs}

The VCDA service is optionally included in your {{site.data.keyword.vmware-service_short}} single-tenant Cloud Director site order at no charge and is included as a default option in {{site.data.keyword.vmware-service_short}} multitenant virtual data centers (VDCs).

This tutorial requires:

* An {{site.data.keyword.cloud_notm}} [billable account](/docs/account?topic=account-accounts).
* Required user permissions. Ensure that your user account has sufficient permissions [to create and manage {{site.data.keyword.vmware-service_short}} resources](/docs/vmware-service?topic=vmware-service-getting-started).
* [A preprovisioned {{site.data.keyword.vmware-service_short}} Cloud Director site](/docs/vmwaresolutions?topic=vmwaresolutions-tenant-ordering).
* [The VCDA service is installed on your Cloud Director site instance](/docs/vmware-service?topic=vmware-service-vcda-adding-deleting).
* An existing {{site.data.keyword.vmware-service_short}} instance to migrate.

## Create a pairing between {{site.data.keyword.vmware-service_short}} instances
{: #vcda-migrating-cloudtocloud-vmaas-pairing}

<!-- The {: #step-1} tag and the ordered list that has only 1s are intentional. Do not delete. This coding is necessary for proper indentation when the procedure is translated. -->

1. From the VMware Solutions console, install VCDA on a {{site.data.keyword.vmware-service_short}} single-tenant source instance. For more information, see [Adding and deleting VMware Cloud Director Availability](/docs/vmware-service?topic=vmware-service-vcda-adding-deleting#vcda-adding-deleting-add-proc). {: #step-1}
1. Install VCDA on a {{site.data.keyword.vmware-service_short}} single-tenant destination instance.
1. Navigate to the source instance details where you installed VCDA and click the **Add-on services** tab.
1. Click the **{{site.data.keyword.vmware-service_short}} pairings** tab and click **Create pairing**.
1. On the **Create connection** panel, complete the following configuration.
   1. For **Zones**, the default zone of the resource pool is displayed. If the instance has multiple PVDCs belonging to different zones, all the zones are displayed. Select the zone pairing.
   1. For **Peer geography**, the geography where the peer site is installed is displayed.
   1. For **Peer site name**, return to the VMware Cloud Director Availability details page and click the **Instance endpoints** tab. Click the **Copy to clipboard** icon for the **Site name** for the instance to pair. Paste the site name in the create connection configuration.
   1. For **Peer region**, select the region where the peer site is installed.
   1. For **Administrator notes**, you can enter notes to provide more information for the pairing. The maximum length is 200 characters and the % & < > " ' / characters are not supported.
1.	Click **Create pairing**. The **Creating** status displays. When the **Waiting for peer pairing status** displays, repeat the previous steps to complete the pairing connection with the Cloud Director site to pair.
1. In the VMware Solutions console, click **Resources > {{site.data.keyword.vmware-service_short}}** from the left navigation pane.
1. In the **{{site.data.keyword.vmware-service_short}}** table, click the **Cloud Director site** tab, then click a single-tenant instance name to pair with the first pairing.
1. Click the **Add-on services** tab, then expand the **VMware Cloud Director Availability** service.
1. On the **{{site.data.keyword.vmware-service_short}} pairings** tab, click **Create pairing**.
1. On the **Create connection** panel, complete the following configuration.
   1. For **Zones**, the default zone of the resource pool is displayed. If the instance has multiple PVDCs belonging to different zones, all the zones are displayed. Select the zone pairing.
   1. For **Peer geography**, the geography where the peer site is installed is displayed.
   1. For **Peer site name**, return to the VMware Cloud Director Availability details page and click the **{{site.data.keyword.vmware-service_short}} pairings** tab. Click the **Copy to clipboard** icon for the **Peer site name** that you created for the first pairing. Paste the site name in the create connection configuration.
   1. For **Peer region**, select the region of the first pairing.
   1. For **Administrator notes**, you can enter notes to provide more information for the pairing. The maximum length is 200 characters and the % & < > " ' / characters are not supported.
1. Click **Create pairing**. The **Available** status displays when the pairing is complete.

The following pairing status options are available.
| Status | Description |
|:---- |:----------- |
| Creating | The pairing task starts. |
| Waiting for peer pairing | The pairing is complete on one site. |
| Available | The pairing is complete on both sites. |
{: caption="Table 1. Pairing status" caption-side="bottom"}

## Migrate your virtual machine through the {{site.data.keyword.vmware-service_short}} pairing
{: #vcda-migrating-cloudtocloud-migrate-pairing}

<!-- The {: #step-2} tag and the ordered list that has only 2s are intentional. Do not delete. This coding is necessary for proper indentation when the procedure is translated. -->

2. From the VMware Solutions console, navigate to the instance where you created the pairing and click **VMware console**. {: #step-2}
2. Click **More > Availability (<datacenter_name>)**. For example, *Availability (sdirw360t04vcda)*.
2. From the left panel, click **Incoming Replications**.
2. From the **Incoming Replications** page, click **ALL ACTIONS > New migration**.
2. Provide the login credentials for the peer site and click **LOGIN**.
2. Select the following options in the **New Incoming Migration** window.
   * For **Source VMs and vApps**:
   2. From the **SELECT SITE** drop-down menu, select the name of the paired instance. The source virtual machine (VM) displays for migration.
   2. If the source VM is a multitenant instance, select the source organization ID from the **Source organization** drop-down menu.
   2. Select the VM to migrate and click **NEXT**.
   * For **Destination VDC and Storage policy**:
   2. Select the target VDC to migrate the VM to.
   2. If the destination VDC is a multitenant instance, select the target organization ID from the **Target organization** drop-down menu.
   2. Click **NEXT**.
   * For **Settings**, keep the default options and click **NEXT**.
   * For **Ready to complete**, review the settings and click **FINISH**.

   The VM is first configured and then synchronized. The replication is complete when the **Last changed** column moves from *Synchronizing* to the date and time of the replication.

2. When the replication is complete, ensure that the newly replicated VM is selected and click **ALL ACTIONS > Migrate** to begin the migration.
2. Select the following options from the **Migrate** window.
   * For **Migrate Settings**, keep the default options and click **NEXT**.
   * For **Ready to complete**, review the settings and click **FINISH**.

   The VCDA service copies the runtime data from the source VM to the destination VM. When the replication is complete, the migrated VM powers on in the Cloud Director site and powers off in the source instance. The migration is complete when the **Recovery state** column moves from *Not started* to *Failed-Over*.

2. Click the destination virtual data center name to verify the migration. Click **Compute > Virtual Machines** to view the VM.
2. After the migration is complete, delete the failed-over migration. Click **ALL ACTIONS > Delete replication**.

The migration metadata is deleted. Deleting the replication does not delete the source or the destination VMs.
{: note}