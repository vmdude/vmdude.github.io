---
title: Cannot read property ‘graphiteVersion’ of null
date: 2019-05-28
---


After upgrading to 0.99f version, you get this error on any dashboard:

![](/img/graphite_version_null.png)

Starting from Grafana 4.5, the version of the graphite datasource is mandatory and that’s why we update a record in the sqlite database during the upgrade process. **For a small population of users**, this record is not updated for an unknown reason.

To correct that issue, you simply need to force the “0.9” version in the graphite datasource:

![](/img/poligraf-datasource.png)

![](/img/poligraf-datasource-2.png)
