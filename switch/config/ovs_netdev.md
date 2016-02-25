---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
b76d7721-e938-4f2f-9d13-0f28abfc989a
    Bridge "br0"
        Controller "tcp:10.24.150.30:6633"
        fail_mode: secure
        Port "eth23"
            Interface "eth23"
        Port "eth21"
            Interface "eth21"
        Port "br0"
            Interface "br0"
                type: internal
        Port "eth22"
            Interface "eth22"

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 13139a2d-3e11-4d27-bec9-95fb28996f04
controller          : [de2fa630-91eb-44f3-b216-0bc76dd98a46]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [431ec9c5-2501-452d-be13-d7502bf70369, 5705759d-cd35-42a3-8b25-658ad4b45253, 9484d338-2595-4c5d-8b30-94c023f10c62, fc002a6a-b313-482f-9891-accd5538c5ae]
protocols           : ["OpenFlow13"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : de2fa630-91eb-44f3-b216-0bc76dd98a46
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_connect="667", sec_since_disconnect="5", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 9484d338-2595-4c5d-8b30-94c023f10c62
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [ea2162d9-fd7d-46bf-93a9-5b00a5ddb7f7]
name                : "br0"

_uuid               : 431ec9c5-2501-452d-be13-d7502bf70369
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [30cfaf6f-43ee-4d77-98bf-9cf4a4e64636]
name                : "eth23"

_uuid               : 5705759d-cd35-42a3-8b25-658ad4b45253
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [79e22c9c-4a4f-4759-97f3-366d18ec425b]
name                : "eth21"

_uuid               : fc002a6a-b313-482f-9891-accd5538c5ae
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [367f4ea1-1cf3-47d7-b493-e6ef3793cfe9]
name                : "eth22"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 79e22c9c-4a4f-4759-97f3-366d18ec425b
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
statistics          : {collisions=0, rx_bytes=46959602827, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=31381772, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 367f4ea1-1cf3-47d7-b493-e6ef3793cfe9
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=31331263501, tx_dropped=0, tx_errors=0, tx_packets=20922232}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : ea2162d9-fd7d-46bf-93a9-5b00a5ddb7f7
admin_state         : down
duplex              : full
ifindex             : 830
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

_uuid               : 30cfaf6f-43ee-4d77-98bf-9cf4a4e64636
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=9889479000, tx_dropped=0, tx_errors=0, tx_packets=6592986}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit fcde56f53c701d6d49d912a4f6aa8da2e9c0cb94
Author:     Lance Richardson &lt;lrichard@redhat.com&gt;
AuthorDate: Thu Feb 25 10:57:28 2016 -0500
Commit:     Ben Pfaff &lt;blp@ovn.org&gt;
CommitDate: Thu Feb 25 08:24:36 2016 -0800

    tests: Gracefully terminate daemons in OVN tests
    
    Daemons started in OVN tests are currently killed &#40;via &quot;on_exit kill&quot;
    in start_daemon&#40;&#41;&#41;. This is problematic for tools &#40;such as gcov&#41; that
    rely on exit&#40;&#41; being called.
    
    Fix by using &quot;ovs-appctl ... exit&quot; to gracefully terminate the daemons.
    
    Signed-off-by: Lance Richardson &lt;lrichard@redhat.com&gt;
    Tested-by: Aaron Conole &lt;aconole@redhat.com&gt;
    Signed-off-by: Ben Pfaff &lt;blp@ovn.org&gt;
</pre>
