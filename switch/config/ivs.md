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
commit 6b091b776610f2135e401ef68912bb4c98d0a3ac
Merge: bcd1a2c ad1c926
Author:     abat &lt;abat@bigswitch.com&gt;
AuthorDate: Wed Jul 16 14:06:38 2014 -0700
Commit:     abat &lt;abat@bigswitch.com&gt;
CommitDate: Wed Jul 16 14:06:38 2014 -0700

    Merge into master from pull request #187:
    Create stats abstraction (https://github.com/floodlight/ivs/pull/187)

$ modinfo openvswitch
filename:       /lib/modules/3.2.0-29-generic/extra/openvswitch.ko
version:        2.3.90
license:        GPL
description:    Open vSwitch switching datapath
srcversion:     F59B363F4F274FB51AE1897
depends:        libcrc32c,gre
vermagic:       3.2.0-29-generic SMP mod_unload modversions 
</pre>
