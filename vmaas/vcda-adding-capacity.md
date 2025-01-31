---

copyright:

  years: 2023

lastupdated: "2023-11-16"

keywords: add capacity, capacity adding

subcollection: vmware-service


---

{{site.data.keyword.attribute-definition-list}}

# Adding migration capacity
{: #vcda-capacity-adding}

After your {{site.data.keyword.vmware-service_full}} Cloud Director site instance order is complete, configure your instance capacity based on how many virtual machines (VMs) you plan to migrate.

Select from the following estimated capacity resource options that are required for your provider virtual data center (PVDC) to migrate your VMs. Each resource is per instance.

VMware Cloud Director Availability (VCDA) resources can include the VCDA Manager VM, Tunnel VM, and Replicator VMs. Resources are deployed into the workload PVDC and consume RAM and CPU from the PVDCs in each zone for the site.

When you select and apply a resource configuration, you can upgrade to only a greater configuration.
{: important}

| Range of VMs | Number of replicators | RAM | CPU |
|:--------- |:------- |:--------- |:------- |
| 0 - 750 | 1 | 16 GB | 14 vCPU |
| 750 - 1500 | 2 | 24 GB | 22 vCPU |
| 1500 - 5000 | 6 | 56 GB | 54 vCPU |
| 5000 - 10000 | 12 | 104 GB| 102 vCPU |
{: caption="Table 1. Options for estimated migration capacity" caption-side="bottom"}

## Procedure to configure your VMware Cloud Director instance capacity
{: #vcda-capacity-adding-proc}

1. In the VMware Solutions console, click **Resources > {{site.data.keyword.vmware-service_short}}** from the left navigation pane.
2. In the **{{site.data.keyword.vmware-service_short}}** table, click the **Cloud Director site** tab, then click a single-tenant instance name.
3. Click the **Add-on services** tab, then expand the **VMware Cloud Director Availability** service.
4. In the **Migration estimated capacity** section, click **Edit capacity**.
5. Select a resource configuration.
6. Click **Apply**.

## Related links
{: #vcda-capacity-adding-links}

* [VMware Cloud Director Availability for {{site.data.keyword.vmware-service_short}} overview](/docs/vmware-service?topic=vmware-service-tenant-vcda)
* [Viewing and deleting {{site.data.keyword.vmware-service_short}} Cloud Director sites](/docs/vmware-service?topic=vmware-service-tenant-viewing-sites)
* [Adding and deleting VMware Cloud Director Availability](/docs/vmware-service?topic=vmware-service-vcda-adding-deleting)
