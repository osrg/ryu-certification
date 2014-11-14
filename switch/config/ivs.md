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
commit 0348caece3f391600961ba6d00a7f654d6d50c49
Merge: 60af9fb 0841cee
Author:     abat &lt;abat@bigswitch.com&gt;
AuthorDate: Thu Nov 13 18:57:35 2014 -0800
Commit:     abat &lt;abat@bigswitch.com&gt;
CommitDate: Thu Nov 13 18:57:35 2014 -0800

    Merge into master from pull request #220:
    pipeline_lua: remove unnecessary locking (https://github.com/floodlight/ivs/pull/220)

$ modinfo openvswitch
filename:       /lib/modules/3.2.0-29-generic/extra/openvswitch.ko
version:        2.3.90
license:        GPL
description:    Open vSwitch switching datapath
srcversion:     E7E5DFE64E79BDBFF178C1A
depends:        libcrc32c,gre
vermagic:       3.2.0-29-generic SMP mod_unload modversions 
</pre>
