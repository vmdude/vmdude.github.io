---
title: "vim.*"
date: 2015-04-02T15:27:17+06:00
draft: false
# page title background image
bg_image: "images/dashboard-vim.png"
# Research image
image: "images/sexiboards/dashboard-vim-360x200.png"
# type
type: "sexiboards"
---


VIM stands for Virtual Infrastructure Methodology, the [RESTful API][1] of vSphere. The **vim** dashboard is a simple Kibana `topN` query on the `vim` field. This field is created any time logstash see something like `vim.method.call```

 

![dashboard-vim][2]

 

This dashboard is embedded in SexiLog. If you want up-to-date version for your own platform, the Gist code for this dashboard is:  `https://gist.github.com/sexibytes/e903439deb87e163d683`

_More information about dashboard import in Kibana is available **[here][3]**_

[1]: http://en.wikipedia.org/wiki/Representational_state_transfer
[2]: /images/dashboard-vim.png
[3]: /rtfm/#dashboardimport "Documentation"

