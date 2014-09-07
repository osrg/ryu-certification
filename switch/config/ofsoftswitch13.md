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
commit f2ab22481a97d2178f54db9af0d4255d134f5763
Author:     oftutorial &lt;oftutorial@openflowvm.home&gt;
AuthorDate: Sat Sep 6 23:19:04 2014 -0300
Commit:     oftutorial &lt;oftutorial@openflowvm.home&gt;
CommitDate: Sat Sep 6 23:19:04 2014 -0300

    Fix some match errors
    
    - Fix error while matching masked IPv6, IPv4 and ethernet addresses.
    - Fix default metadata value. The older value was leading to wrong flow misses.
</pre>

# Modified test scenario for switch restrictions
<pre>
$ rm ryu/tests/switch/of13/action/25_SET_FIELD/10_IP_PROTO_IPv6.json
</pre>
