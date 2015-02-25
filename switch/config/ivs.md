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
commit 16b7b281031bf563459558f6db5518c46f071e67
Merge: 37ed2e9 f703520
Author:     abat &lt;abat@bigswitch.com&gt;
AuthorDate: Wed Feb 25 11:21:37 2015 -0800
Commit:     abat &lt;abat@bigswitch.com&gt;
CommitDate: Wed Feb 25 11:21:37 2015 -0800

    Merge into master from pull request #251:
    use git:// URL for loxigen-artifacts submodule (https://github.com/floodlight/ivs/pull/251)

$ modinfo openvswitch
filename:       /lib/modules/3.2.0-29-generic/extra/openvswitch.ko
version:        2.3.90
license:        GPL
description:    Open vSwitch switching datapath
srcversion:     98151CAB4899109D6F5C5EC
depends:        libcrc32c,gre
vermagic:       3.2.0-29-generic SMP mod_unload modversions 
</pre>
