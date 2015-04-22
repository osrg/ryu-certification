---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
a3588a24-916d-43f7-82e0-2215f54a3383
    Bridge "br0"
        Controller "tcp:10.24.150.30:6633"
        fail_mode: secure
        Port "eth23"
            Interface "eth23"
        Port "eth21"
            Interface "eth21"
        Port "eth22"
            Interface "eth22"
        Port "br0"
            Interface "br0"
                type: internal

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 1a974a45-dac3-44fc-a137-0f55742beff0
controller          : [a27f3155-f40a-481b-8d6d-ee0af72e5c9d]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [56dde040-66ca-4076-9897-a64f011369e8, 7e101b6e-ed81-4ceb-bb0a-d2f9851f71fb, a6d6e92e-fa37-45e0-95e0-65018d1bebb4, aa51cd04-c8b2-4b34-9df8-d12a015a52a0]
protocols           : ["OpenFlow14"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : a27f3155-f40a-481b-8d6d-ee0af72e5c9d
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_connect="646", sec_since_disconnect="1", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 56dde040-66ca-4076-9897-a64f011369e8
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [176354be-325b-41d2-9d2e-d0a99680b931]
name                : "eth23"

_uuid               : aa51cd04-c8b2-4b34-9df8-d12a015a52a0
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [bba48a58-3624-40c6-bbad-1b79c789adaa]
name                : "br0"

_uuid               : 7e101b6e-ed81-4ceb-bb0a-d2f9851f71fb
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [0201a9ca-0439-49ed-97fd-7a4ad5dd6640]
name                : "eth21"

_uuid               : a6d6e92e-fa37-45e0-95e0-65018d1bebb4
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [c5d03883-1933-43cc-846d-b902e46e31c4]
name                : "eth22"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : bba48a58-3624-40c6-bbad-1b79c789adaa
admin_state         : down
duplex              : full
ifindex             : 933
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_speed          : 10000000
link_state          : down
mac_in_use          : "00:60:e0:56:53:5c"
mtu                 : 1500
name                : "br0"
ofport              : 65534
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=tun, driver_version="1.6", firmware_version="N/A"}
type                : internal

_uuid               : 176354be-325b-41d2-9d2e-d0a99680b931
admin_state         : up
duplex              : full
ifindex             : 25
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_speed          : 1000000000
link_state          : up
mac_in_use          : "00:60:e0:56:53:5e"
mtu                 : 1550
name                : "eth23"
ofport              : 3
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=42598668000, tx_dropped=0, tx_errors=0, tx_packets=28399112}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 0201a9ca-0439-49ed-97fd-7a4ad5dd6640
admin_state         : up
duplex              : full
ifindex             : 23
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_speed          : 1000000000
link_state          : up
mac_in_use          : "00:60:e0:56:53:5c"
mtu                 : 1550
name                : "eth21"
ofport              : 1
statistics          : {collisions=0, rx_bytes=1233829889011, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=822937775, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : c5d03883-1933-43cc-846d-b902e46e31c4
admin_state         : up
duplex              : full
ifindex             : 24
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_speed          : 1000000000
link_state          : up
mac_in_use          : "00:60:e0:56:53:5d"
mtu                 : 1550
name                : "eth22"
ofport              : 2
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=631152723561, tx_dropped=0, tx_errors=0, tx_packets=420938106}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 5e65e080ad4d57eb3fcb7b53980cf6a4d1e8ae19
Author:     Gurucharan Shetty &lt;gshetty@nicira.com&gt;
AuthorDate: Tue Apr 7 17:17:39 2015 -0700
Commit:     Gurucharan Shetty &lt;gshetty@nicira.com&gt;
CommitDate: Wed Apr 22 13:13:28 2015 -0700

    tests: Avoid Windows unit tests from hanging.
    
    It has been observed that sometimes Windows unit tests hang.
    This happens when a daemon is started but does not get terminated
    when the test ends.
    
    In one particular case, OVS_VSWITCHD_STOP is called which inturn
    calls 'ovs-appctl exit'. This causes ovs-vswitchd's atexit handler
    to cleanup the pidfiles. After this, the pthread destructurs get
    called and a deadlock happens in there. This results in the
    daemons not getting force killed resulting in the tests hanging
    because the cleanup file tries to run the command
    &quot;kill `cat ovs-vswitchd.pid`&quot; and ovs-vswitchd.pid no longer exists.
    
    With this commit, we write the pid value of the daemons in the
    cleanup file &#40;instead of asking it to 'cat' the value later from
    the pidfile&#41;. This way, even if the pidfiles get deleted, we can
    still kill the daemons.
    
    This commit also changes the way daemons are force killed in
    Windows. It was observed that 'taskkill //F ' failed to kill
    a deadlocked daemon running its pthread destructor. But
    tskill succeeds.
    
    Signed-off-by: Gurucharan Shetty &lt;gshetty@nicira.com&gt;
    &#40;ON_EXIT_UNQUOTED macro provided by Ben.&#41;
    Co-authored-by: Ben Pfaff &lt;blp@nicira.com&gt;
    Signed-off-by: Ben Pfaff &lt;blp@nicira.com&gt;
</pre>
