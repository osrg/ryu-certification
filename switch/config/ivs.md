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
commit 5cb535df06f66387f91d7e58f02bcdd1396201e0
Merge: 0348cae 5a1e9ab
Author:     abat &lt;abat@bigswitch.com&gt;
AuthorDate: Mon Nov 17 11:10:50 2014 -0800
Commit:     abat &lt;abat@bigswitch.com&gt;
CommitDate: Mon Nov 17 11:10:50 2014 -0800

    Merge into master from pull request #221:
    pipeline_lua: embed base Lua code during the build process and create sandbox (https://github.com/floodlight/ivs/pull/221)

$ modinfo openvswitch
filename:       /lib/modules/3.2.0-29-generic/extra/openvswitch.ko
version:        2.3.90
license:        GPL
description:    Open vSwitch switching datapath
srcversion:     E7E5DFE64E79BDBFF178C1A
depends:        libcrc32c,gre
vermagic:       3.2.0-29-generic SMP mod_unload modversions 
</pre>
