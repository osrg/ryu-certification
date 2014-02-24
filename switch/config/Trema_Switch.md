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
commit c0b6f02a3f1b730c5a159ea2aaee673487d8d716
Merge: cc9ac33 edba47e
Author:     sugyo &lt;sugyo.org@gmail.com&gt;
AuthorDate: Mon Feb 24 17:28:46 2014 +0900
Commit:     sugyo &lt;sugyo.org@gmail.com&gt;
CommitDate: Mon Feb 24 17:28:46 2014 +0900

    Merge pull request #109 from iHiroakiKawai/fixes2
    
    fix typo
</pre>
