---
layout: default
title: Ryu Certification - Trema Switch - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* Trema Switch

# OpenFlow related configuration
<pre>
$ sudo -E ./objects/switch/switch/switch -d --datapath_id=1 --server_ip=10.24.150.30 --server_port=6633 --switch_ports=eth21,eth22,eth23
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 3a14bce8a78baa43f3321f3533972ff037594275
Merge: 06a6ab4 63c72dc
Author:     Yasuhito Takamiya &lt;yasuhito@gmail.com&gt;
AuthorDate: Fri Apr 4 17:08:51 2014 +0900
Commit:     Yasuhito Takamiya &lt;yasuhito@gmail.com&gt;
CommitDate: Fri Apr 4 17:08:51 2014 +0900

    Merge pull request #118 from rascov/develop
    
    Keep using the interface append_oxm_match_arp_op() and add an exception in oxm-helper.c
</pre>

# Modified test scenario for switch restrictions
<pre>
$ sed -i 's/group_id=ofp.OFPG_ALL/group_id=0/g' ryu/tests/switch/tester.py;
</pre>
