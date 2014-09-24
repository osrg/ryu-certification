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
commit 8333e31a52b0eb131d19b845dcff0c47bf56a3e1
Merge: 4a0309e 3f3e16d
Author:     abat &lt;abat@bigswitch.com&gt;
AuthorDate: Wed Sep 24 14:18:45 2014 -0700
Commit:     abat &lt;abat@bigswitch.com&gt;
CommitDate: Wed Sep 24 14:18:45 2014 -0700

    Merge into master from pull request #205:
    update submodules (https://github.com/floodlight/ivs/pull/205)

$ modinfo openvswitch
filename:       /lib/modules/3.2.0-29-generic/extra/openvswitch.ko
version:        2.3.90
license:        GPL
description:    Open vSwitch switching datapath
srcversion:     3723E7CFB3400337BB56317
depends:        libcrc32c,gre
vermagic:       3.2.0-29-generic SMP mod_unload modversions 
</pre>
