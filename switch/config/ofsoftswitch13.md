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
commit 242bc555f95c345169cac4a8667a1aaca05fe77c
Author:     Eder Leão Fernandes &lt;ederleaofernandes@gmail.com&gt;
AuthorDate: Mon Dec 8 16:54:11 2014 -0200
Commit:     Eder Leão Fernandes &lt;ederleaofernandes@gmail.com&gt;
CommitDate: Mon Dec 8 16:54:11 2014 -0200

    Various bug fixes.
    
    - Add checksum recalculation after set icmo fields.
    - Fix IPv6 flow label parsing
    - Fix incorrect size of VLAN pcp in the parsing
    - Correct netpdl specification for the IPv6 Neighbor Discovery source
      link layer field.
</pre>

# Modified test scenario for switch restrictions
<pre>
$ rm ryu/tests/switch/of13/action/25_SET_FIELD/10_IP_PROTO_IPv6.json
</pre>
