---
title: "CookBook"
# page title background image
bg_image: "images/dashboard-logicalsession2.png"
# meta description
description : "Follow this recipe if you want your own appliance, aka BYOS 'Build Your Own SexiLog' ! Here are the steps for building this awesome appliance!"
type: "single-post"
---


### Building the system

SexiLog is built on top of [Debian operating system](http://www.debian.org) thanks to the [netinst media](https://www.debian.org/CD/netinst/#netinst-stable).


#### OS Installation

The only customisation done during the OS installation (beside all the network/disk layout brew) was to check `SSH server` and `Standard system utilities` during [tasksel](https://wiki.debian.org/tasksel) step.

#### Prerequisites

In order to prepare your server you will need to install some prerequisites. First, we encourage you to keep your system up-to-date (this is just best practice, not mandatory, but everyone wish for an up-to-date system 🙂 ), then you must install standard packages (if these are not already installed on your system of course):

{{< highlight bash >}}
apt-get update
apt-get upgrade -y
apt-get dist-upgrade -y
apt-get install open-vm-tools openjdk-7-jre-headless vim curl htop resolvconf -y
{{< / highlight >}}

#### Dedicated partition

Due to the way Curator works, it’s best to dedicate a partiton to ElasticSearch indices:

{{< highlight bash >}}
mkdir /sexilog
fdisk /dev/sdb
mkfs.ext4 /dev/sdb1
blkid /dev/sdb1
chown elasticsearch:elasticsearch /sexilog
{{< / highlight >}}

Uptade [**/etc/fstab** with the partition UUID](https://wiki.debian.org/fstab#UUIDs) and [“path.data” in **/etc/elasticsearch/elasticsearch.yml**](http://www.elasticsearch.org/guide/en/elasticsearch/reference/current/setup-dir-layout.html).


### Installing SexiLog components

SexiLog is based on an awesome suite known as the [ELK](http://www.elasticsearch.org/webinars/introduction-elk-stack/) stack, which stands for **E**lasticsearch **L**ogstash **K**ibana, plus some tools ([Curator](https://github.com/elasticsearch/curator) and [Riemann](http://riemann.io/))

As this cookbook is written, below software version were used on the SexiLog appliance:

{{< highlight bash >}}
curl -O https://download.elasticsearch.org/elasticsearch/elasticsearch/elasticsearch-1.3.9.deb
curl -O https://download.elasticsearch.org/logstash/logstash/packages/debian/logstash\_1.4.2-1-2c0f5a1\_all.deb
curl -O https://download.elasticsearch.org/logstash/logstash/packages/debian/logstash-contrib\_1.4.2-1-efd53ef\_all.deb
{{< / highlight >}}

You may want to verify the downloaded files checksum:

{{< highlight bash >}}
curl -O https://download.elasticsearch.org/elasticsearch/elasticsearch/elasticsearch-1.3.9.deb.sha1.txt
curl -O https://download.elasticsearch.org/logstash/logstash/packages/debian/logstash\_1.4.2-1-2c0f5a1\_all.deb.sha1.txt
curl -O https://download.elasticsearch.org/logstash/logstash/packages/debian/logstash-contrib\_1.4.2-1-efd53ef\_all.deb.sha1.txt
{{< / highlight >}}

#### Elasticsearch

You must install [elasticsearch](http://www.elasticsearch.org/overview/elasticsearch) (_a flexible and powerful open source, distributed, real-time search and analytics engine_) with previously downloaded packages and set it up to start with the system:

{{< highlight bash >}}
dpkg -i elasticsearch-1.3.9.deb
update-rc.d elasticsearch defaults 95 10
{{< / highlight >}}

Some elasticsearch plugins must also be installed as they could be usefull for troubleshooting:

{{< highlight bash >}}
/usr/share/elasticsearch/bin/plugin -install mobz/elasticsearch-head
/usr/share/elasticsearch/bin/plugin -install lukas-vlcek/bigdesk
{{< / highlight >}}

#### Logstash

You must install [logstash](http://www.elasticsearch.org/overview/logstash) (_helps you take logs and other time based event data from any system and store it in a single place for additional transformation and processing_) with previously downloaded packages and set it up to start with the system:

{{< highlight bash >}}
dpkg -i logstash\_1.4.2-1-2c0f5a1\_all.deb
update-rc.d logstash defaults
{{< / highlight >}}

Beginning with Logstash 1.5 there will be a new plugin management system, but as SexiLog is currently based on branch 1.4x so we need to install an additionnal package:

{{< highlight bash >}}
dpkg -i logstash-contrib\_1.4.2-1-efd53ef\_all.deb
{{< / highlight >}}

#### Kibana 3 & kibana-proxy

Kibana is Elasticsearch’s data visualization engine, allowing you to natively interact with all your data in Elasticsearch via custom dashboards.

Since kibana 3 is a fully client side JavaScript, we choose to add [kibana-proxy](https://github.com/hmalphettes/kibana-proxy) Node.js express app to avoid Elasticsearch queries from client browser (as it was designed to) and [node-startup](https://github.com/chovy/node-startup) to handle automatic start up of your kibana 3 “server”.

{{< highlight bash >}}
curl -sL https://deb.nodesource.com/setup | bash -
apt-get install -y nodejs git
git clone https://github.com/hmalphettes/kibana-proxy.git /root/kibana-proxy
npm install --global /root/kibana-proxy
git clone https://github.com/chovy/node-startup.git /root/node-startup
sed -i 's/\\/var\\/www\\/example\\.com/\\/usr\\/lib\\/node\_modules\\/kibana-proxy/' /root/node-startup/init.d/node-app
sed -i 's/PORT="3000"/PORT="80"/' /root/node-startup/init.d/node-app
cp /root/node-startup/init.d/node-app /etc/init.d/
update-rc.d node-app defaults
sed -i 's/3003/80/' /usr/lib/node\_modules/kibana-proxy/app.js
sed -i 's/kibana-build/kibana/' /usr/lib/node\_modules/kibana-proxy/app.js
{{< / highlight >}}

#### Curator

Like a museum curator manages the exhibits and collections on display, Elasticsearch Curator helps you curate, or manage your time-series indices. SexiLog use it to limit indices space usage. In order to install it, you can use [pip](https://pypi.python.org/pypi/pip) (a Python packages management tool):

{{< highlight bash >}}
apt-get install python-pip -y
pip install elasticsearch-curator
{{< / highlight >}}

#### Riemann

Riemann aggregates events from SexiLog with a powerful stream processing language and handle mail alerts based on tags. It must be set up to start with the system:

{{< highlight bash >}}
curl -O https://aphyr.com/riemann/riemann\_0.2.6\_all.deb
dpkg -i riemann\_0.2.6\_all.deb
update-rc.d riemann defaults 95 10
{{< / highlight >}}


### Setting up the mixture

#### Elasticsearch

Here are the non-default variables used in `/etc/elasticsearch/elasticsearch.yml`:

* Limit the number of shards used by elasticsearch to 1: `index.number_of_shards: 1`

* Disable the distributed features by setting the number of replicas for shards to 0: `index.number_of_replicas: 0`

* Enable unicast discovery: `discovery.zen.ping.multicast.enabled: false`

These settings were initialy set in order to make this appliance easily “exportable”. Adjust these settings to reflect your environnment

* ElasticSearch performs poorly when JVM starts swapping, we should ensure that it **never** swaps by locking the memory: `bootstrap.mlockall: true`

* ElasticSearch by default assumes that you’re going to use it mostly for searching and querying, so it allocates 90% of its allocated total HEAP memory for searching, but SexiLog case was opposite – the goal is to index vast amounts of logs as quickly as possible, so it was changed to 50/50 (_explaination extracted from a must-read source: [ElasticSearch and Logstash Tuning](http://jablonskis.org/2013/elasticsearch-and-logstash-tuning/index.html)_): `indices.memory.index_buffer_size: 50%`

* Yes, we customized cluster name, and of course it’s **sexilog** ^^: `cluster.name: sexilog`

#### Logstash

Here are the non-default variables used in `/etc/init.d/logstash`:

In order to be able to listen on port <1024 (typically syslog with UDP/514) user running logstash service must be root:

* `LS_USER=root`
* `LS_GROUP=root`

If you plan on using different syslog listening port (ie >1024), these settings aren’t mandatory

* Increase default heap size for logstash: `LS_HEAP_SIZE="1G"`

#### Curator

Curator is set up with a crontab task that is used to set the purge of indice, the `–disk-space 10` parameter tells the purge to use space criteria of 10GB:

{{< highlight bash >}}
cat /etc/crontab
\*/15 \* \* \* \* root curator --loglevel CRITICAL delete --disk-space 40 indices --all-indices
{{< / highlight >}}

#### SNMPd

If you want your SexiLog appliance to be able to receive SNMP trap, you need to install SNMP daemon:

{{< highlight bash >}}
apt-get install snmpd -y
{{< / highlight >}}

Here is the custom configuration done in `/etc/snmp/snmpd.conf`:

* `rocommunity public`
* `includeAllDisks 10%`

Here is the custom configuration done in `/etc/snmp/snmptrapd.conf`:

* `authCommunity log public`

Here is the custom configuration done in `/etc/default/snmpd`:

* `TRAPDRUN=yes`
* `TRAPDOPTS='-Ls 2 -p /var/run/snmptrapd.pid -m ALL -M /usr/share/mibs/vmw/'`

Here is the custom configuration done in `/etc/rsyslog.d/32-snmptrapd.conf`:

* `if $programname == 'snmptrapd' then @localhost:3514`
* `if $programname == 'snmptrapd' then ~`

In order to get VMware SNMP MIB Modules, you will need to visit [VMware KB1013445](http://kb.vmware.com/kb/1013445) to download all `*.mib` files and put them to `/usr/share/mibs/vmw/`

### SexiMenu

In order for SexiMenu to run as expected, you have to download the script and the sample configuration file (used for Riemann configuration) from our [Github repository](https://github.com/sexibytes/sexilog) and make it executable:

{{< highlight bash >}}
mkdir -p /root/seximenu/conf
wget -O /root/seximenu/seximenu.sh https://raw.githubusercontent.com/sexibytes/sexilog/master/seximenu/seximenu.sh
chmod a+x /root/seximenu/seximenu.sh
wget -O /root/seximenu/conf/riemann.config.sample https://github.com/sexibytes/sexilog/blob/master/seximenu/conf/riemann.config.sample
{{< / highlight >}}

Next, you have to add it to the [.bashrc](https://www.gnu.org/software/bash/manual/html_node/Bash-Startup-Files.html) file (for connexion startup):

{{< highlight bash >}}
printf '%s\\n\\t%s\\n%s' 'if ! \[ -z "$PS1" \]; then' '/root/seximenu/seximenu.sh' 'fi' >> /root/.bashrc
{{< / highlight >}}

### Conf files

Up-to-date configuration files can be downloaded straight from [sexilog github repository](https://github.com/sexibytes/sexilog)

### Reboot

Once everything is in place, reboot and enjoy your SexiLog appliance. Have fun!

### Tweaking

Those tweaks were done on SexiLog appliance, and you could do it on your side if you need it.

#### mpt-status

By default on Debian 7 Wheezy when running on VMware, `mpt-status` gets installed by default. Since the virtual machine does not use RAID `mpt-statusd` reports “non-optimal” RAID status in the log every 10 minutes:

{{< highlight bash >}}
mpt-statusd: detected non-optimal RAID status
{{< / highlight >}}

The `mpt-status` package is used to query the status of LSI SCSI HBAs so unless your machine is using such HBA cards the `mpt-status` package should be safe to remove:

{{< highlight bash >}}
apt-get purge mpt-status -y
{{< / highlight >}}

#### ipv6

Default SexiLog appliance uses only ipv4, so we needed to disable ipv6 in order to avoid any issue. It’s done by modifying file `/etc/sysctl.conf`:

* `net.ipv6.conf.all.disable_ipv6 = 1`
* `net.ipv6.conf.default.disable_ipv6 = 1`
* `net.ipv6.conf.lo.disable_ipv6 = 1`
* `net.ipv6.conf.eth0.disable_ipv6 = 1`

#### swappiness

[As instructed by Elasticsearch guys](http://www.elasticsearch.org/guide/en/elasticsearch/guide/current/heap-sizing.html#_swapping_is_the_death_of_performance), let’s tune vm.swappiness in `/etc/sysctl.conf`:

* `vm.swappiness = 1`

#### Certificate generation

In order to ease communication between appliances (in the case for instance you wanted to forward some messages to another appliance), the best way to do it is based on [lumberjack forwarder](https://github.com/elasticsearch/logstash-forwarder) but SSL is mandatory so we need to create certificates:

{{< highlight bash >}}
openssl req -x509 -batch -nodes -newkey rsa:2048 -keyout /etc/logstash/logstash-forwarder.key -out /etc/logstash/logstash-forwarder.crt -days 3650
{{< / highlight >}}
