---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
98e1bd55-c93a-4fd8-bc69-6342fa82e872
    Bridge "br0"
        Controller "tcp:10.24.150.30:6633"
        fail_mode: secure
        Port "eth21"
            Interface "eth21"
        Port "br0"
            Interface "br0"
                type: internal
        Port "eth23"
            Interface "eth23"
        Port "eth22"
            Interface "eth22"

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : ecd97240-e9b9-45ce-9ebe-d4e20c190e46
controller          : [f9033d32-1c01-4c82-80e4-a58c8ce0e4e7]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [3c253640-bee0-4583-83dd-dab6f8f045aa, 41e12948-f3fb-4079-ad02-4f2da3020247, cb02213b-e4e3-4916-bd29-ae7e3dbc8fee, f549eadc-2ef1-4345-98a3-da1f4e7c2b4b]
protocols           : ["OpenFlow14"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : f9033d32-1c01-4c82-80e4-a58c8ce0e4e7
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_connect="12", sec_since_disconnect="1", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : f549eadc-2ef1-4345-98a3-da1f4e7c2b4b
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [f1f48a6c-0b8a-4ef1-b7b5-c7514067d718]
name                : "eth22"

_uuid               : 41e12948-f3fb-4079-ad02-4f2da3020247
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [f021c5a4-cafd-4b65-b4ee-3a5616cbcded]
name                : "br0"

_uuid               : 3c253640-bee0-4583-83dd-dab6f8f045aa
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [c931999e-2f88-4a38-9fd4-1d093790967f]
name                : "eth21"

_uuid               : cb02213b-e4e3-4916-bd29-ae7e3dbc8fee
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [c0cc30da-c249-4c90-bb1f-4b23846df9b6]
name                : "eth23"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : f1f48a6c-0b8a-4ef1-b7b5-c7514067d718
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=29645663019, tx_dropped=0, tx_errors=0, tx_packets=19788243}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : f021c5a4-cafd-4b65-b4ee-3a5616cbcded
admin_state         : down
duplex              : full
ifindex             : 708
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

_uuid               : c931999e-2f88-4a38-9fd4-1d093790967f
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
statistics          : {collisions=0, rx_bytes=43215079589, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=28864384, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : c0cc30da-c249-4c90-bb1f-4b23846df9b6
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=7083091500, tx_dropped=0, tx_errors=0, tx_packets=4722061}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 39c2baa9e357948fe8f45bc9e96661b456538755
Author:     mweglicx &lt;michalx.weglicki@intel.com&gt;
AuthorDate: Wed Dec 2 23:30:16 2015 -0800
Commit:     Pravin B Shelar &lt;pshelar@nicira.com&gt;
CommitDate: Tue Dec 22 12:35:34 2015 -0800

    netdev_dpdk: pci_dev pointer check.
    
    This change prevents netdev_dpdk from accessing pointer
    which is not valid.
    
    Signed-off-by: Michal Weglicki &lt;michalx.weglicki@intel.com&gt;
    Acked-by: Pravin B Shelar &lt;pshelar@nicira.com&gt;
</pre>
