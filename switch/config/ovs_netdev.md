---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
c17453da-ceed-41d3-8bb8-123472970c04
    Bridge "br0"
        Controller "tcp:10.24.150.30:6633"
        fail_mode: secure
        Port "eth22"
            Interface "eth22"
        Port "br0"
            Interface "br0"
                type: internal
        Port "eth21"
            Interface "eth21"
        Port "eth23"
            Interface "eth23"

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 0854606c-7593-41c7-8b8a-81d53c3214f0
controller          : [2fabdbe4-3f79-4df2-851a-ad2798571b99]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [65473e53-0501-4542-862e-493c642eaf6b, 9977a002-a163-407f-a856-cb8e4f6f6480, bb3d22e5-ef59-40f8-9a20-e3ddbb10c91a, f1307fd5-e9c6-4de9-8165-9afb75284d23]
protocols           : ["OpenFlow13"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 2fabdbe4-3f79-4df2-851a-ad2798571b99
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_connect="662", sec_since_disconnect="0", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : f1307fd5-e9c6-4de9-8165-9afb75284d23
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [6e87fd91-61a1-404b-93ec-cd0bdf97d8b3]
name                : "eth23"

_uuid               : bb3d22e5-ef59-40f8-9a20-e3ddbb10c91a
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [3a577af4-aa63-45ae-ab85-45eb8e6ff6ce]
name                : "eth21"

_uuid               : 9977a002-a163-407f-a856-cb8e4f6f6480
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [a0132492-0330-4650-a728-5007d13b8a2a]
name                : "br0"

_uuid               : 65473e53-0501-4542-862e-493c642eaf6b
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [49c0839e-baff-4e5d-8c18-fe96f8253c3a]
name                : "eth22"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 3a577af4-aa63-45ae-ab85-45eb8e6ff6ce
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
statistics          : {collisions=0, rx_bytes=41810846897, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=27920336, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 6e87fd91-61a1-404b-93ec-cd0bdf97d8b3
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=6030318000, tx_dropped=0, tx_errors=0, tx_packets=4020212}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 49c0839e-baff-4e5d-8c18-fe96f8253c3a
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=29013895923, tx_dropped=0, tx_errors=0, tx_packets=19363216}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : a0132492-0330-4650-a728-5007d13b8a2a
admin_state         : down
duplex              : full
ifindex             : 660
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
commit 839c723379c5bc6beb678aa97fe4a33d05358f4b
Author:     Pravin B Shelar &lt;pshelar@nicira.com&gt;
AuthorDate: Mon Dec 7 18:23:21 2015 -0800
Commit:     Pravin B Shelar &lt;pshelar@nicira.com&gt;
CommitDate: Tue Dec 8 09:48:31 2015 -0800

    datapath: Backport: vxlan: interpret IP headers for ECN correctly
    
    Upstream commit:
        When looking for outer IP header, use the actual socket address family, not
        the address family of the default destination which is not set for metadata
        based interfaces &#40;and doesn't have to match the address family of the
        received packet even if it was set&#41;.
    
        Fix also the misleading comment.
    
        Signed-off-by: Jiri Benc &lt;jbenc@redhat.com&gt;
        Signed-off-by: David S. Miller &lt;davem@davemloft.net&gt;
    
    Upstream: ce212d0f6f5 &#40;&quot;vxlan: interpret IP headers for ECN correctly&quot;&#41;
    Signed-off-by: Pravin B Shelar &lt;pshelar@nicira.com&gt;
    Acked-by: Jesse Gross &lt;jesse@kernel.org&gt;
</pre>
