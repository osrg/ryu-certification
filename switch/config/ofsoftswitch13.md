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
commit cc167ab6d8f6ccf49f921dbb96d76d1dd2590847
Merge: 491a896 54d0013
Author:     Eder Leão Fernandes &lt;ederlf@cpqd.com.br&gt;
AuthorDate: Fri Nov 22 04:29:40 2013 -0800
Commit:     Eder Leão Fernandes &lt;ederlf@cpqd.com.br&gt;
CommitDate: Fri Nov 22 04:29:40 2013 -0800

    Merge pull request #72 from mcanini/upstream
    
    A couple of fixes.
</pre>

# Modified test scenario for switch restrictions
<pre>
$ rm ryu/tests/switch/of13/action/25_SET_FIELD/10_IP_PROTO_IPv6.json
</pre>
