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
commit 3a2b1e56207d77667368ad0cff84f832d9084bfa
Merge: 7bd61bf 3061705
Author:     abat &lt;abat@bigswitch.com&gt;
AuthorDate: Mon Jul 7 18:01:27 2014 -0700
Commit:     abat &lt;abat@bigswitch.com&gt;
CommitDate: Mon Jul 7 18:01:27 2014 -0700

    Merge into master from pull request #185:
    add support for unicast/multicast/broadcast port counters (https://github.com/floodlight/ivs/pull/185)

$ modinfo openvswitch
filename:       /lib/modules/3.2.0-29-generic/extra/openvswitch.ko
version:        2.3.90
license:        GPL
description:    Open vSwitch switching datapath
srcversion:     F59B363F4F274FB51AE1897
depends:        libcrc32c,gre
vermagic:       3.2.0-29-generic SMP mod_unload modversions 
</pre>
