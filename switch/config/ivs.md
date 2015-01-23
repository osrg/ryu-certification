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
commit 9b82a803f1045e4da41a9263c44d10cdc06edfbd
Merge: 0b601a5 35b5bbe
Author:     abat &lt;abat@bigswitch.com&gt;
AuthorDate: Thu Jan 22 14:30:32 2015 -0800
Commit:     abat &lt;abat@bigswitch.com&gt;
CommitDate: Thu Jan 22 14:30:32 2015 -0800

    Merge into master from pull request #235:
    setup.sh: install pkg-config (https://github.com/floodlight/ivs/pull/235)

$ modinfo openvswitch
filename:       /lib/modules/3.2.0-29-generic/extra/openvswitch.ko
version:        2.3.90
license:        GPL
description:    Open vSwitch switching datapath
srcversion:     9F2C3F79F744BDAA2DCF4F1
depends:        libcrc32c,gre
vermagic:       3.2.0-29-generic SMP mod_unload modversions 
</pre>
