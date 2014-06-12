---
layout: default
title: Ryu Certification - ivs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ivs

# OpenFlow related configuration
<pre>
$ /usr/sbin/ivs --pipeline=standard-1.3 -c 10.24.150.30:6633 --dpid 0000000000000001 -i eth7 -i eth8
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 12c4103ec2413571c0f8080e2dc38487ff442fdf
Merge: 494c1a4 3d1104a
Author:     abat &lt;abat@bigswitch.com&gt;
AuthorDate: Thu Jun 12 11:14:41 2014 -0700
Commit:     abat &lt;abat@bigswitch.com&gt;
CommitDate: Thu Jun 12 11:14:41 2014 -0700

    Merge into master from pull request #167:
    update switchlight-common (https://github.com/floodlight/ivs/pull/167)

$ modinfo openvswitch
filename:       /lib/modules/3.2.0-29-generic/extra/openvswitch.ko
version:        2.3.90
license:        GPL
description:    Open vSwitch switching datapath
srcversion:     EDA230F0E0733E30F8D0C4B
depends:        libcrc32c,gre
vermagic:       3.2.0-29-generic SMP mod_unload modversions 
</pre>
