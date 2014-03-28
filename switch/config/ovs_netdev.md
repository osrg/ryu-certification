---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
759c93e5-af40-4385-835d-7c5557c331e5
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port eth8
            Interface eth8
        Port eth7
            Interface eth7
        Port br0
            Interface br0
                type: internal

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : df008a12-c30a-4b78-b710-e3bfeb88d4bb
controller          : [81ca003d-e485-4902-898d-6e223cee7fa4]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [086c6e4e-d90a-425c-a6a4-3b076d9610dc, 7852d042-80f3-4a1e-8199-d6dc65249723, 7ecb3e98-9ac0-498b-a6ba-2c732a1d273a]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 81ca003d-e485-4902-898d-6e223cee7fa4
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=316, sec_since_disconnect=2, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 7ecb3e98-9ac0-498b-a6ba-2c732a1d273a
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [e7a1318f-9145-4637-a778-8fdac750f79c]
name                : br0

_uuid               : 086c6e4e-d90a-425c-a6a4-3b076d9610dc
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [dc8bc25c-f550-4343-b0dc-594e08e884df]
name                : eth8

_uuid               : 7852d042-80f3-4a1e-8199-d6dc65249723
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [ab2be3cf-a099-4a9b-99ec-dca3043b7f37]
name                : eth7

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : dc8bc25c-f550-4343-b0dc-594e08e884df
admin_state         : up
duplex              : full
ifindex             : 11
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_speed          : 1000000000
link_state          : up
mac_in_use          : 00:60:e0:4a:84:ec
mtu                 : 1550
name                : eth8
ofport              : 2
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=5969071, tx_dropped=0, tx_errors=0, tx_packets=63629}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 

_uuid               : e7a1318f-9145-4637-a778-8fdac750f79c
admin_state         : up
duplex              : full
ifindex             : 779
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 2
link_speed          : 10000000
link_state          : up
mac_in_use          : 00:60:e0:4a:84:eb
mtu                 : 1500
name                : br0
ofport              : 65534
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=tun, driver_version=1.6, firmware_version=N/A}
type                : internal

_uuid               : ab2be3cf-a099-4a9b-99ec-dca3043b7f37
admin_state         : up
duplex              : full
ifindex             : 10
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_speed          : 1000000000
link_state          : up
mac_in_use          : 00:60:e0:4a:84:eb
mtu                 : 1550
name                : eth7
ofport              : 1
statistics          : {collisions=0, rx_bytes=3070897677, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=72712691, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 9b516652a1b0113faf6cfa4df2039b7c8a217838
Author:     YAMAMOTO Takashi &lt;yamamoto@valinux.co.jp&gt;
AuthorDate: Thu Mar 27 14:38:57 2014 +0000
Commit:     Andy Zhou &lt;azhou@nicira.com&gt;
CommitDate: Fri Mar 28 13:14:18 2014 -0700

    recirculation: Some cosmetic fixes
    
    Wrap long lines, fix whitespaces, and fix a typo in a comment.
    No functional changes are intended.
    
    Cc: Andy Zhou &lt;azhou@nicira.com&gt;
    Signed-off-by: YAMAMOTO Takashi &lt;yamamoto@valinux.co.jp&gt;
    Signed-off-by: Andy Zhou &lt;azhou@nicira.com&gt;
</pre>
