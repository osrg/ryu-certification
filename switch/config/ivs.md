---
layout: default
title: Ryu Certification - ivs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ivs

# OpenFlow related configuration
<pre>
$ /usr/sbin/ivs --pipeline=standard-1.3 -c 10.24.150.30:6633 --dpid 0000000000000001 -i eth7 -i eth8
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 25d4a12c23b241acaed86693f45d2d2b91a1b9f5
Merge: eff697d 9c4763d
Author:     abat &lt;abat@bigswitch.com&gt;
AuthorDate: Tue Jun 17 15:33:25 2014 -0700
Commit:     abat &lt;abat@bigswitch.com&gt;
CommitDate: Tue Jun 17 15:33:25 2014 -0700

    Merge into master from pull request #173:
    print tcp flags attribute (https://github.com/floodlight/ivs/pull/173)

$ modinfo openvswitch
filename:       /lib/modules/3.2.0-29-generic/extra/openvswitch.ko
version:        2.3.90
license:        GPL
description:    Open vSwitch switching datapath
srcversion:     5E11CF567A61626DAAFFCFD
depends:        libcrc32c,gre
vermagic:       3.2.0-29-generic SMP mod_unload modversions 
</pre>
