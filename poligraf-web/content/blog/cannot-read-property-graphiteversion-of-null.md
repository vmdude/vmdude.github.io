---
title: Cannot read property ‘graphiteVersion’ of null
date: 2019-05-28
---


After upgrading to 0.99f version, you get this error on any dashboard:

![](http://www.sexigraf.fr/wp-content/uploads/2019/05/graphite_version_null.png)

Starting from Grafana 4.5, the version of the graphite datasource is mandatory and that’s why we update a record in the sqlite database during the upgrade process. **For a small population of users**, this record is not updated for an unknown reason.

To correct that issue, you simply need to force the “0.9” version in the graphite datasource:

![](http://www.sexigraf.fr/wp-content/uploads/2019/05/Screenshot-2019-05-28-at-17.26.36.png)

![](http://www.sexigraf.fr/wp-content/uploads/2019/05/Screenshot-2019-05-28-at-17.25.50-756x1024.png)
