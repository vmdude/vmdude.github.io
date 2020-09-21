---
title: The roooooooot situation
date: 2015-09-28
---


![roooooot](/img/roooooot.png)

If you got this behavior, it’s because you’re in a RDP or ICA session trying to enter your root credentials. The only way to work around is the famous VMware KB [Repeated characters when typing in remote console](http://kb.vmware.com/kb/196):

```
keyboard.typematicMinDelay = "2000000"
```
