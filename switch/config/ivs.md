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
commit 542d2b48053317727c2e571e66701fd3c8290a52
Merge: 70d3417 f55fe20
Author:     abat &lt;abat@bigswitch.com&gt;
AuthorDate: Thu Jun 26 21:47:17 2014 -0700
Commit:     abat &lt;abat@bigswitch.com&gt;
CommitDate: Thu Jun 26 21:47:17 2014 -0700

    Merge into master from pull request #178:
    update submodules (https://github.com/floodlight/ivs/pull/178)

$ modinfo openvswitch
filename:       /lib/modules/3.2.0-29-generic/extra/openvswitch.ko
version:        2.3.90
license:        GPL
description:    Open vSwitch switching datapath
srcversion:     44AF8B54258F3FA2BECF946
depends:        libcrc32c,gre
vermagic:       3.2.0-29-generic SMP mod_unload modversions 
</pre>
