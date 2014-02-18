---
layout: default
title: Ryu Certification - Netronome NFPP-1U-AC-1001 - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* Netronome NFPP-1U-AC-1001

# OpenFlow related configuration
<pre>
$ cat /etc/netronome.conf
SDN_CONTROLLER=10.24.150.30
SDN_CONTROLLER_PORT=6633
SDN_DPID=0000000000000032
SDN_FIELDS=all
SDN_IPV6=y
SDN_FLOW_SNAPSHOT=/home/ruikubo/flow_snapshot.txt
SDN_MAX_BACKOFF=5000
SDN_INACTIVITY_PROBE=5000
SDN_SWITCH=10.24.32.1
SDN_OFCONFIG_USER=username
SDN_OFCONFIG_PORT=11111
</pre>

# Version information
<pre>
$ uname -a
Linux netronome 3.5.0-44-generic #67~precise1-Ubuntu SMP Wed Nov 13 16:16:57 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux
$ sudo /opt/netronome/bin/ns-sdn version
Netronome SDN version 1.0-r3037:c35f14a588b9.439:e38556dce89b
</pre>

# Modified test scenario for switch restrictions
<pre>
$ find ryu/tests/switch/of13/ -name '*.json' -print0 | xargs -0 sed -i 's/\"port\":2/\"port\":22/g';
$ find ryu/tests/switch/of13/ -name '*.json' -print0 | xargs -0 sed -i 's/output:2/output:22/g';
$ sed -i 's/\"value\":1/\"value\":21/g' ryu/tests/switch/of13/match/00_IN_PORT.json;
$ sed -i 's/in_port=1/in_port=21/g' ryu/tests/switch/of13/match/00_IN_PORT.json;
$ sed -i 's/TARGET_SENDER_PORT = 2/TARGET_SENDER_PORT = 22/g' ryu/tests/switch/tester.py;
$ sed -i 's/TARGET_RECEIVE_PORT = 1/TARGET_RECEIVE_PORT = 21/g' ryu/tests/switch/tester.py;
$ sed -i 's/INTERVAL = 1/INTERVAL = 5/g' ryu/tests/switch/tester.py; 
$ sed -i 's/^        hub.sleep(0)/        hub.sleep(INTERVAL)/g' ryu/tests/switch/tester.py; 
</pre>

