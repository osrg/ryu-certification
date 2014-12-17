---
layout: default
title: Ryu Certification - ofsoftswitch13 - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ofsoftswitch13

# OpenFlow related configuration
<pre>
$ /usr/local/bin/ofdatapath --datapath-id=000000000002 --interface=eth21,eth22,eth23 ptcp:3333
$ /usr/local/bin/ofprotocol tcp:127.0.0.1:3333 tcp:10.24.150.30:6633
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 9942fb14a6ca80977a570cff835ba1679286157c
Author:     Eder Leão Fernandes &lt;ederleaofernandes@gmail.com&gt;
AuthorDate: Tue Dec 16 23:31:04 2014 -0200
Commit:     Eder Leão Fernandes &lt;ederleaofernandes@gmail.com&gt;
CommitDate: Tue Dec 16 23:31:04 2014 -0200

    Fix pbb_isid size to conform with the specification.
    
    This huge commit brings lots of changes to conform the the pbb isid
    match field size to conform with the OpenFlow 1.3.4 specification.
    
    Also, changes the code to reconstruct the vlan tag to check if the
    ethertype the default value for VLANs or is the one belonging to PBB.
</pre>

# Modified test scenario for switch restrictions
<pre>
$ rm ryu/tests/switch/of13/action/25_SET_FIELD/10_IP_PROTO_IPv6.json
</pre>
