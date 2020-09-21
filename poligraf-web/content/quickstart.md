---
title: quickstart
---


Here is how you can get and quickly setup this awesome appliance named **PoliGraf**.

## Step 1: Get PoliGraf

[Download OVA appliance – v0.99f “Traptown”](http://files.poligraf.io/poligraf.ova)

{{< hint info >}}
SHA1 sum is: `4007ede0a95e34b583c997b532294200e8538a7e poligraf.ova`
{{< /hint >}}

{{< hint success >}}
You can find all release notes on our [GitHub Milestones page](https://github.com/sexibytes/poligraf/milestones?state=closed)
{{< /hint >}}

{{< hint danger >}}
Default **root** password is: **`Sex!Gr@f`**
{{< /hint >}}

## Step 2: Deploy

PoliGraf appliance aimed to be deployed on a [VMware vSphere™](http://www.vmware.com) environment which can be achieve via several ways:

*   [**vSphere client**](http://pubs.vmware.com/vsphere-50/topic/com.vmware.vsphere.vm_admin.doc_50/GUID-6C847F77-8CB2-4187-BD7F-E7D3D5BD897B.html)
*   [**vSphere Web Client**](http://pubs.vmware.com/vsphere-55/topic/com.vmware.vsphere.vm_admin.doc/GUID-AFEDC48B-C96F-4088-9C1F-4F0A30E965DE.html)
*   [**VMware OVF Tool command-line utility**](https://www.vmware.com/support/developer/ovf/)

## Step 3: Configure

Starting from version 0.99c you can configure network settings during the deployment step and change them later thanks to OVF properties:

![](/img/poligraf_guest_info.png)

By default, PoliGraf is pre-configured in DHCP mode. If you specify network infromations, the appliance will switch into static mode.

_The previous versions of the appliance still relies on the SexiMenu_

## Step 4: Add your vCenter information

In order for PoliGraf to retrieve informations and performance counters from your vCenter servers, you must add your vCenter info and some credential. You can do that very easily as we made some fancy SexiPanel just for you!

First of all, connect to your **PoliGraf** web interface (ie **Grafana**), which is listening on TCP port 80 so you can reach it at [http://your\_appliance\_fqdn\_or\_ipv4/](http://your_appliance_fqdn_or_ipv4/) and select the following dashboard: **PoliGraf Web Admin**. Starting from version 0.99e you can reach your PoliGraf appliance on TCP port 443 as well at [**https**://your\_appliance\_fqdn\_or\_ipv4/](https://your_appliance_fqdn_or_ipv4/) thanks to a self-signed that you will be able to change in a future release.

{{< hint danger >}}
Default login information for web interface is: **`admin`** / **`Sex!Gr@f`**
{{< /hint >}}

![](/img/poligraf_home_4.png)

![](/img/poligraf_menu_admin.png)

Then you’ll just have to click on **Credential Store** and enter your vCenter information (_FQDN or IP_, _username_ and _password_). Once you’ve added a vCenter, click on the **Action** dropdown and select **Enable VI** and **Enable VSAN** (if you got any VSAN cluster):

![](/img/vcenter-credstore.jpg)  

{{< hint success >}}
And here you are, relax and let the graphing begin! The PoliGraf collector will now retrieve information from your vCenter(s) and data will start appearing in graph.
{{< /hint >}}
