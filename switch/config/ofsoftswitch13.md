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
commit 8f9cad4f072f0cd1897bb88bfdb0ff6d197194d8
Author:     oftutorial &lt;ederleaofernandes@gmail.com&gt;
AuthorDate: Tue Oct 7 23:59:36 2014 -0300
Commit:     oftutorial &lt;ederleaofernandes@gmail.com&gt;
CommitDate: Tue Oct 7 23:59:36 2014 -0300

    Fix IPv4 checksum on IPv4 ECN or DSCP set field
    
    This commit updates the IPv4 packet checksum after changing the DSCP
    or ECN fields. Furthermore, it add the case of setting IPv6 DSCP and ECN.
</pre>

# Modified test scenario for switch restrictions
<pre>
$ rm ryu/tests/switch/of13/action/25_SET_FIELD/10_IP_PROTO_IPv6.json
</pre>
