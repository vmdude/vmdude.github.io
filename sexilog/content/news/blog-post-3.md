---
title: "How many sources hit my SexiLog?"
date: 2015-06-25T15:27:17+06:00
draft: false
# page title background image
bg_image: "images/backgrounds/page-title.jpg"
# post thumbnail
image: "images/ES_head_host_count.png"
# post author
author: "SexiLog"
# taxonomy
categories: ["News"]
tags: ["elasticsearch", "kibana"]
# type
type: "post"
---


[Kibana 3 doesn’t have a great way to visualize the sources count overtime](http://stackoverflow.com/a/26534372) but it is possible to ask gently to your ElasticSearch db 🙂

So until SexiLog comes with Kibana 4, you can use the awesome [head plugin](http://mobz.github.io/elasticsearch-head/) to achieve this goal.

Just copy/paste the following query in the “**Any Request**” tab and check the “value” property:

{{< highlight json >}}
{“aggs”:{“host\_count”:{“cardinality”:{“field”:”hostname.raw”,”precision\_threshold”:40000}}}}
{{< / highlight >}}

If you ever need practice, feel free to test our [online demo](http://demo.sexilog.fr/_plugin/head)!
