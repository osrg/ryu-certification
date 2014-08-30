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
commit 36738aeb3501f66fb382e7b59138c88e8843b19c
Author:     Jean Tourrilhes &lt;jean.tourrilhes@hp.com&gt;
AuthorDate: Mon Aug 25 17:00:13 2014 -0700
Commit:     ederlf &lt;ederlf@cpqd.com.br&gt;
CommitDate: Thu Aug 28 23:50:51 2014 -0300

    Fix a few more warnings.
</pre>

# Modified test scenario for switch restrictions
<pre>
$ rm ryu/tests/switch/of13/action/25_SET_FIELD/10_IP_PROTO_IPv6.json
</pre>
