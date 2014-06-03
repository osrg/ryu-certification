---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
d519be9a-1e0b-4581-8751-6484601c7d30
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port eth23
            Interface eth23
        Port eth22
            Interface eth22
        Port eth21
            Interface eth21
        Port br0
            Interface br0
                type: internal

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : c8b57db4-b229-4998-8836-4a26e75b9227
controller          : [871d79a8-0769-49b2-bfca-b7501bc15b44]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [0afcb8db-084f-4061-a23b-2e7964aeb4ca, 3a2bd5f6-a516-41a8-9c48-b1f727601da1, 753d5268-b338-4277-b38e-8bd18a9b0ec1, f641d858-7fdd-4650-a82b-94ae04dd68e6]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 871d79a8-0769-49b2-bfca-b7501bc15b44
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=967, sec_since_disconnect=0, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : f641d858-7fdd-4650-a82b-94ae04dd68e6
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [5fb1daab-5f65-457e-a4f8-7a452886efa7]
name                : br0

_uuid               : 753d5268-b338-4277-b38e-8bd18a9b0ec1
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [d567cf50-51dd-46c2-aa71-a6b1bc2e2065]
name                : eth21

_uuid               : 3a2bd5f6-a516-41a8-9c48-b1f727601da1
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [07b9c163-772c-4010-ba58-f3625b05ac20]
name                : eth22

_uuid               : 0afcb8db-084f-4061-a23b-2e7964aeb4ca
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [07197ea9-f710-4fb5-b2c6-d31953491ae1]
name                : eth23

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : d567cf50-51dd-46c2-aa71-a6b1bc2e2065
admin_state         : up
duplex              : full
ifindex             : 23
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_speed          : 1000000000
link_state          : up
mac_in_use          : 00:60:e0:56:53:5c
mtu                 : 1550
name                : eth21
ofport              : 1
statistics          : {collisions=0, rx_bytes=3165325520, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=10746956, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 07197ea9-f710-4fb5-b2c6-d31953491ae1
admin_state         : up
duplex              : full
ifindex             : 25
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_speed          : 1000000000
link_state          : up
mac_in_use          : 00:60:e0:56:53:5e
mtu                 : 1550
name                : eth23
ofport              : 3
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=3598886204, tx_dropped=0, tx_errors=0, tx_packets=5262569}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 07b9c163-772c-4010-ba58-f3625b05ac20
admin_state         : up
duplex              : full
ifindex             : 24
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_speed          : 1000000000
link_state          : up
mac_in_use          : 00:60:e0:56:53:5d
mtu                 : 1550
name                : eth22
ofport              : 2
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=2639308514, tx_dropped=0, tx_errors=0, tx_packets=4639506}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 5fb1daab-5f65-457e-a4f8-7a452886efa7
admin_state         : down
duplex              : full
ifindex             : 344
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_speed          : 10000000
link_state          : down
mac_in_use          : 00:60:e0:56:53:5c
mtu                 : 1500
name                : br0
ofport              : 65534
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=tun, driver_version=1.6, firmware_version=N/A}
type                : internal
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 65ffea171c03a6307797f602eee6a509e57f4aec
Author:     Joe Stringer &lt;joestringer@nicira.com&gt;
AuthorDate: Tue Jun 3 21:09:59 2014 +1200
Commit:     Joe Stringer &lt;joestringer@nicira.com&gt;
CommitDate: Wed Jun 4 10:46:24 2014 +1200

    ofproto: Remove ofproto_refresh_rule&#40;&#41;.
    
    The only user of this function was removed in the previous patch, so
    remove it.
    
    Signed-off-by: Joe Stringer &lt;joestringer@nicira.com&gt;
    Acked-by: Alex Wang &lt;alexw@nicira.com&gt;
</pre>
