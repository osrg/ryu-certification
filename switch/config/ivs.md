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
commit 7ccfd8ab1312c74b978dc04c6cd375d4bf147c84
Merge: 87fbdca 6174b8c
Author:     Big Switch Networks &lt;abat@bigswitch.com&gt;
AuthorDate: Fri Nov 6 22:50:17 2015 +0000
Commit:     Big Switch Networks &lt;abat@bigswitch.com&gt;
CommitDate: Fri Nov 6 22:50:17 2015 +0000

    Merge pull request #347 from rlane/local-port

$ modinfo openvswitch
filename:       /lib/modules/3.2.0-29-generic/extra/openvswitch.ko
version:        2.4.90
license:        GPL
description:    Open vSwitch switching datapath
srcversion:     1DC29A07F596CA89D90C07B
depends:        libcrc32c,gre
vermagic:       3.2.0-29-generic SMP mod_unload modversions 
</pre>
