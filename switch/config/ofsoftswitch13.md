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
commit f82ec65fb788e1e9b9dcb5fb2de4a98e8d978b10
Author:     oftutorial &lt;ederleaofernandes@gmail.com&gt;
AuthorDate: Thu Oct 9 23:47:02 2014 -0300
Commit:     oftutorial &lt;ederleaofernandes@gmail.com&gt;
CommitDate: Thu Oct 9 23:47:02 2014 -0300

    Fix malloc being called twice on reply_port and reply_queue unpack messages
</pre>

# Modified test scenario for switch restrictions
<pre>
$ rm ryu/tests/switch/of13/action/25_SET_FIELD/10_IP_PROTO_IPv6.json
</pre>
