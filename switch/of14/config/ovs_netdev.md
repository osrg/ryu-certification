---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
ac782439-ebf7-455c-a563-16d7895274a4
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port br0
            Interface br0
                type: internal
        Port eth23
            Interface eth23
        Port eth21
            Interface eth21
        Port eth22
            Interface eth22

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : db962546-aed3-481f-80a6-5ad81b74ad25
controller          : [afee18a4-27db-411f-9052-d3b10e114bab]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
mcast_snooping_enable: false
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [266aa446-04d0-4cc0-b3d4-bf852fc0b9f5, 501db436-ba24-4051-8faa-9a81d1e3b35e, 7deb989c-c052-448c-a66d-8d066a71cbd1, aa46dff8-6602-4a0a-a96e-b04748e46662]
protocols           : [OpenFlow14]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : afee18a4-27db-411f-9052-d3b10e114bab
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=661, sec_since_disconnect=7, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 7deb989c-c052-448c-a66d-8d066a71cbd1
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [db374edf-ff16-4556-bac8-ba9cf42e32b8]
name                : eth21

_uuid               : aa46dff8-6602-4a0a-a96e-b04748e46662
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [65c792e8-9c97-493d-ac03-5a800599838b]
name                : eth22

_uuid               : 501db436-ba24-4051-8faa-9a81d1e3b35e
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [31e84064-f3b1-49b0-9c65-46c62e567638]
name                : eth23

_uuid               : 266aa446-04d0-4cc0-b3d4-bf852fc0b9f5
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [a06de3b2-e543-4ab9-a225-c2a22fdf5e6c]
name                : br0

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 65c792e8-9c97-493d-ac03-5a800599838b
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=2981022366, tx_dropped=0, tx_errors=0, tx_packets=44952073}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 31e84064-f3b1-49b0-9c65-46c62e567638
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=213275204, tx_dropped=0, tx_errors=0, tx_packets=3005495}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : a06de3b2-e543-4ab9-a225-c2a22fdf5e6c
admin_state         : down
duplex              : full
ifindex             : 115
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

_uuid               : db374edf-ff16-4556-bac8-ba9cf42e32b8
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
statistics          : {collisions=0, rx_bytes=1881094400, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=64280348, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 5f7487da0a1659a5492baae87926e4b1293cf108
Author:     Nithin Raju &lt;nithin@vmware.com&gt;
AuthorDate: Tue Sep 9 13:50:57 2014 -0700
Commit:     Gurucharan Shetty &lt;gshetty@nicira.com&gt;
CommitDate: Tue Sep 9 14:02:48 2014 -0700

    netlink-socket: remove local variable in do_lookup_genl_family.
    
    'sock' is not initialized and hence should not be un-initialized
    as well in the failure path.
    
    Reported-by: Gurucharan Shetty &lt;shettyg@nicira.com&gt;
    Signed-off-by: Nithin Raju &lt;nithin@vmware.com&gt;
    Signed-off-by: Gurucharan Shetty &lt;gshetty@nicira.com&gt;
</pre>
