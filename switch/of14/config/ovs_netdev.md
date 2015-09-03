---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
4eb0799b-a281-4057-b4fa-74ae5c3de3ca
    Bridge "br0"
        Controller "tcp:10.24.150.30:6633"
        fail_mode: secure
        Port "eth23"
            Interface "eth23"
        Port "eth22"
            Interface "eth22"
        Port "br0"
            Interface "br0"
                type: internal
        Port "eth21"
            Interface "eth21"

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : f053b626-5063-4a4f-8d2b-f972589a8d89
controller          : [d33a9bc1-dd5d-42be-856e-1f27cdf9e8a9]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [30a02031-b1d2-4367-b9bc-286b13284ac1, 3459595c-7a4f-4977-9a3e-51d5bd798e10, 5ac9e6c3-902c-473e-80b9-c71ee073915d, be804e7a-6a30-4146-8b71-1fc9b583de12]
protocols           : ["OpenFlow14"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : d33a9bc1-dd5d-42be-856e-1f27cdf9e8a9
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_disconnect="3", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 3459595c-7a4f-4977-9a3e-51d5bd798e10
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [bcf00a6f-4903-4947-abdc-9d2b9ff834d6]
name                : "eth22"

_uuid               : 30a02031-b1d2-4367-b9bc-286b13284ac1
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [e892a115-eac6-4482-a94c-ba68a821277d]
name                : "eth23"

_uuid               : be804e7a-6a30-4146-8b71-1fc9b583de12
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [aa099a91-c7d0-450b-be84-3a795f635913]
name                : "eth21"

_uuid               : 5ac9e6c3-902c-473e-80b9-c71ee073915d
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [26a63219-5764-4a17-a4cc-86758d26ba68]
name                : "br0"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : e892a115-eac6-4482-a94c-ba68a821277d
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=1176922500, tx_dropped=0, tx_errors=0, tx_packets=784615}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : aa099a91-c7d0-450b-be84-3a795f635913
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
statistics          : {collisions=0, rx_bytes=24024581534, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=16026376, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 26a63219-5764-4a17-a4cc-86758d26ba68
admin_state         : down
duplex              : full
ifindex             : 423
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

_uuid               : bcf00a6f-4903-4947-abdc-9d2b9ff834d6
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=18089315792, tx_dropped=0, tx_errors=0, tx_packets=12064077}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit ad2dade5654257359764c1af9130ebc5cbddab79
Author:     Anoob Soman &lt;anoob.soman@citrix.com&gt;
AuthorDate: Thu Sep 3 14:53:19 2015 +0100
Commit:     Jesse Gross &lt;jesse@nicira.com&gt;
CommitDate: Thu Sep 3 12:51:26 2015 -0700

    netdev-linux: Don't set ethtool flags if flag is already set on netdev
    
    Check if ethtool flags is already set on a netdev, before trying to set it.
    
    This patch works around issues with some older verison of ethernet drivers,
    which tend to reset the NIC when call to disable LRO is made, even if LRO is
    already disable on that NIC. NIC reset is not desirable in OVS upgrade scenario
    as it causes extended downtime.
    
    Signed-off-by: Anoob Soman &lt;anoob.soman@citrix.com&gt;
    Signed-off-by: Jesse Gross &lt;jesse@nicira.com&gt;
</pre>
