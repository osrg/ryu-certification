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
commit 583e20b2388e43acddb96ab23f6a9059fbc49851
Author:     oftutorial &lt;oftutorial@openflowvm.home&gt;
AuthorDate: Sat Sep 6 23:14:54 2014 -0300
Commit:     oftutorial &lt;oftutorial@openflowvm.home&gt;
CommitDate: Sat Sep 6 23:14:54 2014 -0300

    Add checks for bad wildcarded flows.
    
    This commit add functions to check if a masked field is valid.
</pre>

# Modified test scenario for switch restrictions
<pre>
$ rm ryu/tests/switch/of13/action/25_SET_FIELD/10_IP_PROTO_IPv6.json
</pre>
