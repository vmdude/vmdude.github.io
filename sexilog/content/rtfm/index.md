---
title: "#RTFM"
### page title background image
bg_image: "images/dashboard-sql.png"
### meta description
description : "Here are some frequently questions asked"
type: "single-post"
---


### Hard drive extension

By default, **SexiLog** is published with 2 hard disks. The first one is dedicated to the system and host `/` mount point. The second one (_50GB_) is dedicated to `/sexilog` and is used to host all elasticsearch, logstash and kibana data.

If you want to extend the second disk, you should follow these steps:

* Extend the hard disk of the appliance (through vSphere Client, PowerCLI or any other mean 🙂 )
* Update your OS informations (with `fdisk` command line)
* Update your mount point (with `resize2fs` tool)

### Curator

[Curator](https://github.com/elasticsearch/curator) is used to purge elasticsearch shards in order to limit data growth. If you have extended hard drive that hosts elasticsearch data, you should update Curator settings as well in order to reflect these changes.

This is done via updating crontab configuration file located at `/etc/crontab`

{{< highlight bash >}}
# cat /etc/crontab
5 * * * * root curator delete --disk-space 10
{{< / highlight >}}

You just have to update the parameter `--disk-space 10` to specify the limit (in _GB_) elasticsearch shards should be limited to.

### SNMPd

As described in [the Features tab](/features/), `snmptrapd` forwards traps to `logstash` through `rsyslog`. You can [configure Veeam B&R server to send SNMP traps to SexiLog](/sexiboards/veeam-backup/) but also [ESXi](https://pubs.vmware.com/vsphere-51/topic/com.vmware.vsphere.monitoring.doc/GUID-EA64297A-35FD-4226-A1B2-367C57D38CBD.html) and vCenter:

![doc_snmp_vpxd](/images/doc_snmp_vpxd.png)
![doc_snmp_esxi](/images/doc_snmp_esxi.png)

### vCenter logs & Windows EventLog

SexiLog is ready to receive Windows vpxd logs (aka `vpxd.log`) as well as Windows EventLog(s). You simply need to install the small [NXLog](http://nxlog.co/products/nxlog-community-edition/download) agent and use [the pre-configured configuration file available on the GitHub repository](https://github.com/sexibytes/sexilog/blob/master/nxlog/nxlog.conf). You’ll need to replace “127.0.0.1” entries in `nxlog.conf` by the right SexiLog IP or FQDN. Since NXLog will also forward the `vpxd-profiler.log` file (aka [profiled metrics](http://kb.vmware.com/kb/1021804)) you’ll get a lot of vCenter metrics like active sessions:

&nbsp;

![](/images/2015-03-03_01-01-12.png)

If you’re using vCenter Server Appliance (aka VCSA) you can follow the [VMware Log Insight KB article](http://pubs.vmware.com/log-insight-20/topic/com.vmware.log-insight.administration.doc/GUID-ABB7293F-5978-478D-AD57-BBC5E1E60B0E.html) 🙂

### SexiMenu

SexiMenu have been built to make appliance’s common configuration steps easier. It’s automatically launched when connecting to the appliance (through SSH or console) and feature some pre-defined actions like restarting services, or updating network settings.

The main purpose of SexiMenu is to automate all basic operations to avoid manual step (if you want you can still do it manually of course, but we thought about lazy admins 🙂 )

&nbsp;

![](/images/2015-03-02_13-55-20.png)

![](/images/2015-03-02_13-54-43.png)

![](/images/2015-03-02_13-55-43.png)

![](/images/2015-03-02_13-54-24.png)

  

### Importing dashboard from GiST code in Kibana 3

Kibana 3 comes with a built-in dashboard importer, that lets you load additional files for custom views, either from local files, or Gist storage on GitHub. We make all SexiBoards available on our GiST account in order to let you import their definition in just 5 easy steps:

1. In Kibana’s toolbar, click the icon, then hover over the Advanced option.
2. In Gist number or URL input field, enter the URL of your dashboard Gist (provided on each SexiBoard page).
3. To open the custom dashboard, click `Get gist:<gist-id>` button.
4. To load the dashboard, click the dashboard name below the Gist ID button.
5. Save the loaded dashboard by clicking on the icon

![](/images/kibana_3_import11.png)

![](/images/kibana_3_import21.png)

![](/images/kibana_3_import3.png)

  

### Kibana 3 explanation

We thought we should explain why SexiLog is provided with Kibana 3 instead of Kibana 4 (which was [released on February 19th](http://www.elasticsearch.org/blog/kibana-4-literally/)).

There are several reasons that explain it, one of the main is that IMHO Kibana 3 is easier to apprehend for most of users. Also Kibana 4 was released as we were working on SexiLog launch, so we didn’t want to postpone it while we redesigned all the dashboards for the new branch (which is a complete redesign from scratch, much better, but very different in conception 🙂 ). We prefered to stay on Kibana 3 branch and release SexiLog for you !

But as Kibana 4 is the new production branch, rest assured that we work now on making new SexiLog update with Kibana 4 dashboards !

### Elasticsearch plugins

Sexilog is loaded with 2 awesome and very useful Elasticsearch plugins [Head](https://github.com/mobz/elasticsearch-head) and [Bigdesk](http://bigdesk.org/).

Go to `http://your_appliance_fqdn_or_ipv4/_plugin/head` and `http://your_appliance_fqdn_or_ipv4/_plugin/bigdesk` or try the [demo](http://demo.sexilog.fr/_plugin/head).

![es_plugin_head](/images/es_plugin_head.png)
