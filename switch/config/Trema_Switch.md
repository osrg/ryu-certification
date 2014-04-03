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
commit 06a6ab474319d5acb956c5d93f9f79376e1e1ee3
Merge: 54d40d7 598c5f9
Author:     Yasuhito Takamiya &lt;yasuhito@gmail.com&gt;
AuthorDate: Thu Apr 3 17:03:14 2014 +0900
Commit:     Yasuhito Takamiya &lt;yasuhito@gmail.com&gt;
CommitDate: Thu Apr 3 17:03:14 2014 +0900

    Merge pull request #117 from rascov/develop
    
    Change variable arp_op to arp_opcode to avoid name collision with netinet/ether.h
</pre>
