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
commit 3d94a50427ebb3394a1e483814c90d7d2f78b736
Merge: 0d610a2 b55fc42
Author:     abat &lt;abat@bigswitch.com&gt;
AuthorDate: Wed Feb 11 13:04:26 2015 -0800
Commit:     abat &lt;abat@bigswitch.com&gt;
CommitDate: Wed Feb 11 13:04:26 2015 -0800

    Merge into master from pull request #241:
    update submodules (https://github.com/floodlight/ivs/pull/241)

$ modinfo openvswitch
filename:       /lib/modules/3.2.0-29-generic/extra/openvswitch.ko
version:        2.3.90
license:        GPL
description:    Open vSwitch switching datapath
srcversion:     EEADF5DA85FA84BEF538FB2
depends:        libcrc32c,gre
vermagic:       3.2.0-29-generic SMP mod_unload modversions 
</pre>
