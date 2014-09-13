---
layout: default
title: Ryu Certification - ivs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ivs

# OpenFlow related configuration
<pre>
$ /usr/sbin/ivs --pipeline=standard-1.3 -c 10.24.150.30:6633 --dpid 0000000000000001 -i eth21 -i eth22 -i eth23
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 0a0aed3e05aab4aacf35e81d0333cb567984e3c4
Merge: 20baacd 1ad3cda
Author:     abat &lt;abat@bigswitch.com&gt;
AuthorDate: Fri Sep 12 17:36:34 2014 -0700
Commit:     abat &lt;abat@bigswitch.com&gt;
CommitDate: Fri Sep 12 17:36:34 2014 -0700

    Merge into master from pull request #203:
    downgrade or remove some INFO logs (https://github.com/floodlight/ivs/pull/203)

$ modinfo openvswitch
filename:       /lib/modules/3.2.0-29-generic/extra/openvswitch.ko
version:        2.3.90
license:        GPL
description:    Open vSwitch switching datapath
srcversion:     0CE5EA9F2D9CD8557A23985
depends:        libcrc32c,gre
vermagic:       3.2.0-29-generic SMP mod_unload modversions 
</pre>
