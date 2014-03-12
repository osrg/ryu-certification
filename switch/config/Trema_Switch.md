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
commit b7dceacdedef6865cbbd076c2526c68e486fed50
Merge: c0b6f02 3785f23
Author:     Yasuhito Takamiya &lt;yasuhito@gmail.com&gt;
AuthorDate: Wed Mar 12 13:11:04 2014 +0900
Commit:     Yasuhito Takamiya &lt;yasuhito@gmail.com&gt;
CommitDate: Wed Mar 12 13:11:04 2014 +0900

    Merge pull request #110 from ejima/develop
    
    Add support for ruby 2.1
</pre>
