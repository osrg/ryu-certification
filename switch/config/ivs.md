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
commit 0d610a2c99fe1460ce4e3c1dedc5a8653c1eeb86
Merge: fe6cfe9 ba958c6
Author:     abat &lt;abat@bigswitch.com&gt;
AuthorDate: Wed Feb 4 12:10:31 2015 -0800
Commit:     abat &lt;abat@bigswitch.com&gt;
CommitDate: Wed Feb 4 12:10:31 2015 -0800

    Merge into master from pull request #240:
    Lua pipeline improvements (https://github.com/floodlight/ivs/pull/240)

$ modinfo openvswitch
filename:       /lib/modules/3.2.0-29-generic/extra/openvswitch.ko
version:        2.3.90
license:        GPL
description:    Open vSwitch switching datapath
srcversion:     0CEC74FE9E7ADCF67D1F81D
depends:        libcrc32c,gre
vermagic:       3.2.0-29-generic SMP mod_unload modversions 
</pre>
