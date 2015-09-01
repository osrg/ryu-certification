---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
8933e34c-13ee-48cf-98bb-8c6804d74ed5
    Bridge "br0"
        Controller "tcp:10.24.150.30:6633"
        fail_mode: secure
        Port "br0"
            Interface "br0"
                type: internal
        Port "eth21"
            Interface "eth21"
        Port "eth22"
            Interface "eth22"
        Port "eth23"
            Interface "eth23"

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 112a30db-587c-4fd1-ac22-bd3de050e2cc
controller          : [53cdfb24-c6d6-40d4-8942-9d7595842ea0]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [0c3705dd-9e6a-499d-9728-cfa75a767d6a, 12660c2a-a29c-485f-9e5e-fe91a0440964, 14367b57-3d56-46ea-b612-2f36fef3a79f, d4e8606e-5b91-4d81-a0d5-4014927f436e]
protocols           : ["OpenFlow13"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 53cdfb24-c6d6-40d4-8942-9d7595842ea0
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_disconnect="3", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 0c3705dd-9e6a-499d-9728-cfa75a767d6a
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [3d7a12c1-395a-4392-8415-2c12520e5c6e]
name                : "br0"

_uuid               : 12660c2a-a29c-485f-9e5e-fe91a0440964
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [4f56a87d-322f-44f6-b13b-e6c5c51e7c0b]
name                : "eth21"

_uuid               : d4e8606e-5b91-4d81-a0d5-4014927f436e
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [cb76c526-bc13-403c-bcf1-dbce9d5ad525]
name                : "eth23"

_uuid               : 14367b57-3d56-46ea-b612-2f36fef3a79f
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [fd448288-583a-460c-8741-d32445b1a8ee]
name                : "eth22"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : fd448288-583a-460c-8741-d32445b1a8ee
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

_uuid               : 3d7a12c1-395a-4392-8415-2c12520e5c6e
admin_state         : down
duplex              : full
ifindex             : 413
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

_uuid               : 4f56a87d-322f-44f6-b13b-e6c5c51e7c0b
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

_uuid               : cb76c526-bc13-403c-bcf1-dbce9d5ad525
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
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 7e0d3eed9d6856de79a02de963d06b1a4af99f25
Author:     Russell Bryant &lt;rbryant@redhat.com&gt;
AuthorDate: Wed Aug 26 11:07:52 2015 -0400
Commit:     Ben Pfaff &lt;blp@nicira.com&gt;
CommitDate: Tue Sep 1 11:10:26 2015 -0700

    ovn: Add bridge mappings to ovn-controller.
    
    Add a new OVN configuration entry in the Open_vSwitch database called
    &quot;ovn-bridge-mappings&quot;.  This allows the configuration of mappings
    between a physical network name and an OVS bridge that provides
    connectivity to that network.
    
    For example, if you wanted to configure &quot;physnet1&quot; to map to &quot;br-eth0&quot;
    and &quot;physnet2&quot; to map to &quot;br-eth1&quot;, the configuration would be:
    
      $ ovs-vsctl set open . \
      &gt; external-ids:ovn-bridge-mappings=physnet1:br-eth0,physnet2:br-eth1
    
    Patch ports between these bridges and the integration bridge are
    automatically created and also removed if necessary when the
    configuration changes.
    
    Signed-off-by: Russell Bryant &lt;rbryant@redhat.com&gt;
    Signed-off-by: Ben Pfaff &lt;blp@nicira.com&gt;
</pre>
