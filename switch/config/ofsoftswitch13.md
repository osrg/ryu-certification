---
layout: default
title: Ryu Certification - ofsoftswitch13 - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ofsoftswitch13

# OpenFlow related configuration
<pre>
$ /usr/local/bin/ofdatapath --datapath-id=000000000002 --interface=eth1,eth2 ptcp:3333
$ /usr/local/bin/ofprotocol tcp:127.0.0.1:3333 tcp:10.24.100.30:6633
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit e81430858dcd25ed074f484dedf2763f3e3963a4
Merge: 1d2d11a 519b1c6
Author:     Eder Leão Fernandes &lt;ederlf@cpqd.com.br&gt;
AuthorDate: Mon Feb 17 14:28:24 2014 -0300
Commit:     Eder Leão Fernandes &lt;ederlf@cpqd.com.br&gt;
CommitDate: Mon Feb 17 14:28:24 2014 -0300

    Merge pull request #83 from codeshredder/patch-1
    
    operation for cookie_mask error
</pre>

# Modified test scenario for switch restrictions
<pre>
$ rm ryu/tests/switch/of13/action/25_SET_FIELD/10_IP_PROTO_IPv6.json
</pre>
