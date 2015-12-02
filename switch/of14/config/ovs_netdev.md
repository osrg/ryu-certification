---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
f1af0022-6160-4c62-ad0b-17eaf3ed5c02
    Bridge "br0"
        Controller "tcp:10.24.150.30:6633"
        fail_mode: secure
        Port "br0"
            Interface "br0"
                type: internal
        Port "eth22"
            Interface "eth22"
        Port "eth21"
            Interface "eth21"
        Port "eth23"
            Interface "eth23"

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 03547e3d-10f9-4139-b1bb-630f99f8fad5
controller          : [e61c1534-096a-4850-adb1-90d91a55e6d6]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [5d4e6ac2-cbe5-4a15-bf4b-4ad1102dadbe, 8cbd1128-f34f-4a9f-8e5d-9f7163cf5eeb, 8e0cfbfc-30bb-45dd-945f-4b0c7489ff78, c89f73e7-ea4e-4790-8ea5-5c5a94b2ce52]
protocols           : ["OpenFlow14"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : e61c1534-096a-4850-adb1-90d91a55e6d6
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_connect="17", sec_since_disconnect="0", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 8cbd1128-f34f-4a9f-8e5d-9f7163cf5eeb
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [d3bc73ec-4e55-48f9-92ab-4cffae7b186d]
name                : "eth22"

_uuid               : 8e0cfbfc-30bb-45dd-945f-4b0c7489ff78
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [01af0ec1-cf56-4969-99e0-d5795f217918]
name                : "eth21"

_uuid               : 5d4e6ac2-cbe5-4a15-bf4b-4ad1102dadbe
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [64b285e2-8368-41f9-bb01-66c3d2309b9f]
name                : "br0"

_uuid               : c89f73e7-ea4e-4790-8ea5-5c5a94b2ce52
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [f575fe48-22f3-417f-a2d8-09a239122721]
name                : "eth23"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : f575fe48-22f3-417f-a2d8-09a239122721
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=5591701500, tx_dropped=0, tx_errors=0, tx_packets=3727801}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : d3bc73ec-4e55-48f9-92ab-4cffae7b186d
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=28750579766, tx_dropped=0, tx_errors=0, tx_packets=19186071}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 01af0ec1-cf56-4969-99e0-d5795f217918
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
statistics          : {collisions=0, rx_bytes=41225716200, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=27526963, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 64b285e2-8368-41f9-bb01-66c3d2309b9f
admin_state         : down
duplex              : full
ifindex             : 642
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
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 873d85653d84289eb3a7fd253d95ebcbdad920f0
Author:     Gurucharan Shetty &lt;guru@ovn.org&gt;
AuthorDate: Mon Nov 30 15:52:09 2015 -0800
Commit:     Gurucharan Shetty &lt;guru@ovn.org&gt;
CommitDate: Wed Dec 2 10:00:46 2015 -0800

    debian: Skip systemctl redirect.
    
    After some experimentation on Ubuntu15.04, I see the
    following behavior.
    
    1. If you install openvswitch-switch with 'apt-get install',
    then you automatically get a upstart and systemd config files
    for openvswitch. The integration with 'interfaces' fails
    because both the upstart and systemd jobs do not have logic
    to handle it.
    
    The above behavior will likely get fixed soon in upstream
    Ubuntu.
    
    2. If you install openvswitch-switch via the packages
    created from the openvswitch repo, there is no systemd or
    upstart conf files installed. But systemd notices this
    and creates a runtime openvswitch conf file which does
    nothing but call back the sysv startup script.
    
    In the above case when you call
    &quot;/etc/init.d/openvswitch-switch start&quot;, it inturn calls
    &quot;/bin/systemctl start openvswitch-switch.service&quot; and
    that inturn again calls &quot;/etc/init.d/openvswitch-switch start&quot;.
    But the above for some reason simply hangs. It looks like a call
    to ifup when invoked in this manner does not return.
    I am not sure why this is happening.
    
    We can avoid the above behavior completely by skipping the
    systemctl redirect as done in this commit. This should fix
    both 1. and 2. above.
    
    Signed-off-by: Gurucharan Shetty &lt;guru@ovn.org&gt;
    Acked-by: Ben Pfaff &lt;blp@ovn.org&gt;
</pre>
