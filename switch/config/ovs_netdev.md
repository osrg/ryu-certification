---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
b8bd920f-ae70-4730-a902-264ec33348c3
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port eth7
            Interface eth7
        Port br0
            Interface br0
                type: internal
        Port eth8
            Interface eth8

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 0499d0e3-b9d0-42a5-bcd5-0df474e1ca13
controller          : [5ac49143-6b37-4baa-9921-a9eede18b4b8]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [62c5f73b-068d-4131-bc10-ceeed3e2a0a2, f8f75daa-6faf-4b9a-b4f4-38a53a4ae7be, f9cdeeec-079a-4034-b4e3-8ccdaa395f72]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 5ac49143-6b37-4baa-9921-a9eede18b4b8
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=371, sec_since_disconnect=2, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : f9cdeeec-079a-4034-b4e3-8ccdaa395f72
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [41771ca7-b6b3-418d-9565-fd0ac846d1c4]
name                : eth8

_uuid               : f8f75daa-6faf-4b9a-b4f4-38a53a4ae7be
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [6dbbfcd1-886c-4aff-b2b5-f5773dba24dc]
name                : br0

_uuid               : 62c5f73b-068d-4131-bc10-ceeed3e2a0a2
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [3e394e19-8b24-4ea0-862b-385328db1cdb]
name                : eth7

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 3e394e19-8b24-4ea0-862b-385328db1cdb
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
statistics          : {collisions=0, rx_bytes=3058694961, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=72588862, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 

_uuid               : 6dbbfcd1-886c-4aff-b2b5-f5773dba24dc
admin_state         : up
duplex              : full
ifindex             : 287
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

_uuid               : 41771ca7-b6b3-418d-9565-fd0ac846d1c4
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=2375634, tx_dropped=0, tx_errors=0, tx_packets=25365}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit f5790bf6eeade6662eaccc95b22b25cecb822c9e
Author:     Romain Lenglet &lt;rlenglet@vmware.com&gt;
AuthorDate: Tue Feb 11 15:21:08 2014 -0800
Commit:     Ben Pfaff &lt;blp@nicira.com&gt;
CommitDate: Wed Feb 19 14:08:35 2014 -0800

    ipfix: fix upcall cookie size checks to support 8 byte cookies
    
    Commit 96ed775f resizes all userspace metadata to be 8 bytes minimum.
    Fix the upcall size checks accordingly.
    
    Signed-off-by: Romain Lenglet &lt;rlenglet@vmware.com&gt;
    Signed-off-by: Ben Pfaff &lt;blp@nicira.com&gt;
</pre>
