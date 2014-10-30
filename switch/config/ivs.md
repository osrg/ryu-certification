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
commit 75481a04e1f6539a2a0316375e8a2167162f7704
Merge: cf80840 19909f0
Author:     abat &lt;abat@bigswitch.com&gt;
AuthorDate: Wed Oct 29 16:16:19 2014 -0700
Commit:     abat &lt;abat@bigswitch.com&gt;
CommitDate: Wed Oct 29 16:16:19 2014 -0700

    Merge into master from pull request #211:
    ivs: change RLIMIT_NOFILE failure to a warning (https://github.com/floodlight/ivs/pull/211)

$ modinfo openvswitch
filename:       /lib/modules/3.2.0-29-generic/extra/openvswitch.ko
version:        2.3.90
license:        GPL
description:    Open vSwitch switching datapath
srcversion:     28E3B7BDA51616251CD3191
depends:        libcrc32c,gre
vermagic:       3.2.0-29-generic SMP mod_unload modversions 
</pre>
