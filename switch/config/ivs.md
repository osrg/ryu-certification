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
commit 1ae882751b3aea51a7b605ebbbdff8637b97576b
Merge: 18076eb 0130547
Author:     abat &lt;abat@bigswitch.com&gt;
AuthorDate: Thu Mar 5 15:46:42 2015 -0800
Commit:     abat &lt;abat@bigswitch.com&gt;
CommitDate: Thu Mar 5 15:46:42 2015 -0800

    Merge into master from pull request #259:
    update submodules (https://github.com/floodlight/ivs/pull/259)

$ modinfo openvswitch
filename:       /lib/modules/3.2.0-29-generic/extra/openvswitch.ko
version:        2.3.90
license:        GPL
description:    Open vSwitch switching datapath
srcversion:     AD40B500DD5C28718A043A4
depends:        libcrc32c,gre
vermagic:       3.2.0-29-generic SMP mod_unload modversions 
</pre>
