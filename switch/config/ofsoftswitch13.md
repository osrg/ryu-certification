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
commit a30149a0a4d4c3de9318aa9fad27665351ff625f
Author:     Eder Leão Fernandes &lt;ederleaofernandes@gmail.com&gt;
AuthorDate: Thu May 21 13:43:01 2015 -0300
Commit:     Eder Leão Fernandes &lt;ederleaofernandes@gmail.com&gt;
CommitDate: Thu May 21 13:43:01 2015 -0300

    Minor refactor to meter token bucket.
    
    This commit modified the token bucket capacity unity.
    Previously the code considered tokens in Kbps. For this
    reason the packet size, which is presented in bytes,
    value was also converted. This packet size convertion was wrong,
    because small packets sizes were truncated to 0 in Kbps preventing
    token remotion.
    
    The code now changes the bucket capacity and packet conversion to bits.
    It avoids divisions and eliminates errors of truncation.
</pre>

# Modified test scenario for switch restrictions
<pre>
$ rm ryu/tests/switch/of13/action/25_SET_FIELD/10_IP_PROTO_IPv6.json
</pre>
