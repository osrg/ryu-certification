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
commit 7f73422b803902c645ad2536a3bfa7e24426da62
Merge: 4b46b77 61e1cf4
Author:     abat &lt;abat@bigswitch.com&gt;
AuthorDate: Fri Oct 17 15:16:40 2014 -0700
Commit:     abat &lt;abat@bigswitch.com&gt;
CommitDate: Fri Oct 17 15:16:40 2014 -0700

    Merge into master from pull request #209:
    update submodules (https://github.com/floodlight/ivs/pull/209)

$ modinfo openvswitch
filename:       /lib/modules/3.2.0-29-generic/extra/openvswitch.ko
version:        2.3.90
license:        GPL
description:    Open vSwitch switching datapath
srcversion:     2B697D868E5CB8C6927CA1E
depends:        libcrc32c,gre
vermagic:       3.2.0-29-generic SMP mod_unload modversions 
</pre>
