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
commit 452a6c71e2d24a88a49e62d1f3e5f1f7c6d4f0b1
Author:     oftutorial &lt;oftutorial@openflowvm.home&gt;
AuthorDate: Fri Aug 29 22:16:30 2014 -0300
Commit:     oftutorial &lt;oftutorial@openflowvm.home&gt;
CommitDate: Fri Aug 29 22:16:30 2014 -0300

    Add the case of a following IPv6 header for copy ttl in and out action.
    
    This commit adds the copy ttl out and in for the case of an IPv6
    header following an MPLS header.
</pre>

# Modified test scenario for switch restrictions
<pre>
$ rm ryu/tests/switch/of13/action/25_SET_FIELD/10_IP_PROTO_IPv6.json
</pre>
