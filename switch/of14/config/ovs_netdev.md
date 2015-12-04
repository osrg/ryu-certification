---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
fb979ccb-a554-4299-9c57-9fd3ce3ef5a6
    Bridge "br0"
        Controller "tcp:10.24.150.30:6633"
        fail_mode: secure
        Port "eth22"
            Interface "eth22"
        Port "eth21"
            Interface "eth21"
        Port "br0"
            Interface "br0"
                type: internal
        Port "eth23"
            Interface "eth23"

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 1b76ccd2-f40f-4c95-8b2e-dce3633470f8
controller          : [4f0f2c4c-2f2d-47ae-b426-1a129dab43cc]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [19170d0d-df57-415c-82ad-cefd1adf4bbd, 83d820d9-15c0-428b-a183-8895a7bbe0d6, 85bec524-28a8-4635-b9da-f1085a7b5446, cfe6bc82-7ac2-412e-8854-c8bc15a9f596]
protocols           : ["OpenFlow14"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 4f0f2c4c-2f2d-47ae-b426-1a129dab43cc
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_connect="16", sec_since_disconnect="1", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 85bec524-28a8-4635-b9da-f1085a7b5446
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [c3522da7-8c98-4915-808b-729c81c0199f]
name                : "br0"

_uuid               : 83d820d9-15c0-428b-a183-8895a7bbe0d6
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [322696ef-c4ee-4477-9e92-2d6c03b8de76]
name                : "eth21"

_uuid               : 19170d0d-df57-415c-82ad-cefd1adf4bbd
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [8739cd8a-7364-4a1e-a944-31439530c139]
name                : "eth22"

_uuid               : cfe6bc82-7ac2-412e-8854-c8bc15a9f596
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [b30f510d-cce3-4681-a66c-2064c152d402]
name                : "eth23"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : b30f510d-cce3-4681-a66c-2064c152d402
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=5767173000, tx_dropped=0, tx_errors=0, tx_packets=3844782}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 8739cd8a-7364-4a1e-a944-31439530c139
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=28855904532, tx_dropped=0, tx_errors=0, tx_packets=19256929}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 322696ef-c4ee-4477-9e92-2d6c03b8de76
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
statistics          : {collisions=0, rx_bytes=41459790482, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=27684328, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : c3522da7-8c98-4915-808b-729c81c0199f
admin_state         : down
duplex              : full
ifindex             : 650
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
commit 6422372c103d280450eb400ed7fe955b74deeb2a
Author:     Jarno Rajahalme &lt;jarno@ovn.org&gt;
AuthorDate: Fri Dec 4 10:19:07 2015 -0800
Commit:     Jarno Rajahalme &lt;jarno@ovn.org&gt;
CommitDate: Fri Dec 4 10:19:07 2015 -0800

    bond: Use correct type for slave's change_seq.
    
    seq values are 64-bit, and storing them to a 32-bit variable causes
    the stored value never to match actual seq value after the seq value
    gets big enough.
    
    This is a likely cause of OVS main thread using 100% CPU in a system
    using bonds after some runtime.
    
    VMware-BZ: #1564993
    Reported-by: Hiram Bayless &lt;hbayless@vmware.com&gt;
    Signed-off-by: Jarno Rajahalme &lt;jarno@ovn.org&gt;
    Acked-by: Joe Stringer &lt;joe@ovn.org&gt;
    Acked-by: Ben Pfaff &lt;blp@ovn.org&gt;
</pre>
