---
layout: default
title: Ryu Certification - Trema Switch - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* Trema Switch

# OpenFlow related configuration
<pre>
$ sudo -E ./objects/switch/switch/switch -d --datapath_id=1 --server_ip=10.24.100.30 --server_port=6633 --switch_ports=eth1,eth2
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 54acd51efa7c1f6844b0b5ca8e8c309325971fb3
Merge: 0638c3c e759b88
Author:     sugyo &lt;sugyo.org@gmail.com&gt;
AuthorDate: Mon Feb 17 14:23:30 2014 +0900
Commit:     sugyo &lt;sugyo.org@gmail.com&gt;
CommitDate: Mon Feb 17 14:23:30 2014 +0900

    Merge pull request #106 from iHiroakiKawai/fixes
    
    various tiny fixes
</pre>
