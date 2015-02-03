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
commit fe6cfe9c77a4fd2fe57162f0aae6c77e7ae68038
Merge: 500804c d20b87f
Author:     abat &lt;abat@bigswitch.com&gt;
AuthorDate: Mon Feb 2 15:31:21 2015 -0800
Commit:     abat &lt;abat@bigswitch.com&gt;
CommitDate: Mon Feb 2 15:31:21 2015 -0800

    Merge into master from pull request #239:
    set inband control queue priority (https://github.com/floodlight/ivs/pull/239)

$ modinfo openvswitch
filename:       /lib/modules/3.2.0-29-generic/extra/openvswitch.ko
version:        2.3.90
license:        GPL
description:    Open vSwitch switching datapath
srcversion:     9F2C3F79F744BDAA2DCF4F1
depends:        libcrc32c,gre
vermagic:       3.2.0-29-generic SMP mod_unload modversions 
</pre>
