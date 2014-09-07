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
commit 0b82d220fdd20f81849bf266aecea94108d95ad5
Author:     oftutorial &lt;oftutorial@openflowvm.home&gt;
AuthorDate: Sun Sep 7 09:23:19 2014 -0300
Commit:     oftutorial &lt;oftutorial@openflowvm.home&gt;
CommitDate: Sun Sep 7 09:23:19 2014 -0300

    Implement SET_NW_TTL and DEC_NW_TTL for IPv6 packets
    
    The implementation of SET_NW_TTL and DEC_NW_TTL was not
    considering IPv6 packets. This commit fix this, setting and decrementing
    the ipv6 hop_limit on respective action.
</pre>

# Modified test scenario for switch restrictions
<pre>
$ rm ryu/tests/switch/of13/action/25_SET_FIELD/10_IP_PROTO_IPv6.json
</pre>
