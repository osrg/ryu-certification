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
commit 0b601a5f27c1e147200f3fe3bc5d58f0e09b8193
Merge: 15bef2f 8d843e9
Author:     abat &lt;abat@bigswitch.com&gt;
AuthorDate: Tue Jan 13 16:28:48 2015 -0800
Commit:     abat &lt;abat@bigswitch.com&gt;
CommitDate: Tue Jan 13 16:28:48 2015 -0800

    Merge into master from pull request #233:
    update submodules (https://github.com/floodlight/ivs/pull/233)

$ modinfo openvswitch
filename:       /lib/modules/3.2.0-29-generic/extra/openvswitch.ko
version:        2.3.90
license:        GPL
description:    Open vSwitch switching datapath
srcversion:     EABBF9402BC3C42298A5444
depends:        libcrc32c,gre
vermagic:       3.2.0-29-generic SMP mod_unload modversions 
</pre>
