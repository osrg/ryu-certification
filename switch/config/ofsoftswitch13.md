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
commit 064980000fe57e5b502e554d36dc75d393a7cc1d
Author:     oftutorial &lt;ederleaofernandes@gmail.com&gt;
AuthorDate: Tue Oct 7 22:29:43 2014 -0300
Commit:     oftutorial &lt;ederleaofernandes@gmail.com&gt;
CommitDate: Tue Oct 7 22:29:43 2014 -0300

    Fix potential bug in handling metadata.
    
    In a OFPIT_WRITE_METADATA the value would be reset, as pointed
    by Jean Tourrilhes.
    This commit fix this behavior and also add tunnel metadata information
    to the packet parsing.
</pre>

# Modified test scenario for switch restrictions
<pre>
$ rm ryu/tests/switch/of13/action/25_SET_FIELD/10_IP_PROTO_IPv6.json
</pre>
