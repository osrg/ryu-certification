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
commit f17b384ee9d0ea84b6cf832937c2af1f583a0262
Merge: 4aff748 90efa44
Author:     abat &lt;abat@bigswitch.com&gt;
AuthorDate: Fri Mar 6 16:45:21 2015 -0800
Commit:     abat &lt;abat@bigswitch.com&gt;
CommitDate: Fri Mar 6 16:45:21 2015 -0800

    Merge into master from pull request #262:
    OVSDriver: move datapath name hash to upper bytes of dpid (https://github.com/floodlight/ivs/pull/262)

$ modinfo openvswitch
filename:       /lib/modules/3.2.0-29-generic/extra/openvswitch.ko
version:        2.3.90
license:        GPL
description:    Open vSwitch switching datapath
srcversion:     AD40B500DD5C28718A043A4
depends:        libcrc32c,gre
vermagic:       3.2.0-29-generic SMP mod_unload modversions 
</pre>
