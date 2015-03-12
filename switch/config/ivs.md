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
commit 585538096251f033b367f16de81fc55446139b8b
Merge: 92669ba 0a26462
Author:     abat &lt;abat@bigswitch.com&gt;
AuthorDate: Thu Mar 12 15:14:49 2015 -0700
Commit:     abat &lt;abat@bigswitch.com&gt;
CommitDate: Thu Mar 12 15:14:49 2015 -0700

    Merge into master from pull request #270:
    OVSDriver: automatically reconnect uplinks to the datapath (https://github.com/floodlight/ivs/pull/270)

$ modinfo openvswitch
filename:       /lib/modules/3.2.0-29-generic/extra/openvswitch.ko
version:        2.3.90
license:        GPL
description:    Open vSwitch switching datapath
srcversion:     AD40B500DD5C28718A043A4
depends:        libcrc32c,gre
vermagic:       3.2.0-29-generic SMP mod_unload modversions 
</pre>
