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
commit dfd8d139d48eafefe3007f6fdd577c64d5a2517a
Merge: 75481a0 f2085d8
Author:     abat &lt;abat@bigswitch.com&gt;
AuthorDate: Mon Nov 3 14:16:29 2014 -0800
Commit:     abat &lt;abat@bigswitch.com&gt;
CommitDate: Mon Nov 3 14:16:29 2014 -0800

    Merge into master from pull request #212:
    convert LOCI list iteration to of_object_t (https://github.com/floodlight/ivs/pull/212)

$ modinfo openvswitch
filename:       /lib/modules/3.2.0-29-generic/extra/openvswitch.ko
version:        2.3.90
license:        GPL
description:    Open vSwitch switching datapath
srcversion:     28E3B7BDA51616251CD3191
depends:        libcrc32c,gre
vermagic:       3.2.0-29-generic SMP mod_unload modversions 
</pre>
