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
commit 245747a21637de23bcce4dcff166df1547d1cb84
Merge: 44ecc28 6aaad11
Author:     abat &lt;abat@bigswitch.com&gt;
AuthorDate: Fri Feb 20 14:06:15 2015 -0800
Commit:     abat &lt;abat@bigswitch.com&gt;
CommitDate: Fri Feb 20 14:06:15 2015 -0800

    Merge into master from pull request #244:
    add --internal-port command line option (https://github.com/floodlight/ivs/pull/244)

$ modinfo openvswitch
filename:       /lib/modules/3.2.0-29-generic/extra/openvswitch.ko
version:        2.3.90
license:        GPL
description:    Open vSwitch switching datapath
srcversion:     5EE1ABE3E71D861C188558D
depends:        libcrc32c,gre
vermagic:       3.2.0-29-generic SMP mod_unload modversions 
</pre>
