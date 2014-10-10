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
commit 7e8358b9fed472706bb4c4448ad5c1ce80ebc4b9
Author:     oftutorial &lt;ederleaofernandes@gmail.com&gt;
AuthorDate: Fri Oct 10 19:41:00 2014 -0300
Commit:     oftutorial &lt;ederleaofernandes@gmail.com&gt;
CommitDate: Fri Oct 10 19:41:00 2014 -0300

    Change tunnel_id from network to host byte order.
    
    Without these changes, flows were being added incorrectly.
</pre>

# Modified test scenario for switch restrictions
<pre>
$ rm ryu/tests/switch/of13/action/25_SET_FIELD/10_IP_PROTO_IPv6.json
</pre>
