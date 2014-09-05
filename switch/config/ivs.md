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
commit b92ad22d06cfd13f464ff1b0e27451dd1e273c4e
Merge: 6e834f1 a733e4d
Author:     abat &lt;abat@bigswitch.com&gt;
AuthorDate: Fri Sep 5 12:41:38 2014 -0700
Commit:     abat &lt;abat@bigswitch.com&gt;
CommitDate: Fri Sep 5 12:41:38 2014 -0700

    Merge into master from pull request #200:
    implement special pipeline handling for in-band management (https://github.com/floodlight/ivs/pull/200)

$ modinfo openvswitch
filename:       /lib/modules/3.2.0-29-generic/extra/openvswitch.ko
version:        2.3.90
license:        GPL
description:    Open vSwitch switching datapath
srcversion:     2E29248C4E7ACDB1A72CC00
depends:        libcrc32c,gre
vermagic:       3.2.0-29-generic SMP mod_unload modversions 
</pre>
