---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
4f6401b5-2a59-43e9-964a-16265e6ba4e7
    Bridge "br0"
        Controller "tcp:10.24.150.30:6633"
        fail_mode: secure
        Port "eth22"
            Interface "eth22"
        Port "br0"
            Interface "br0"
                type: internal
        Port "eth23"
            Interface "eth23"
        Port "eth21"
            Interface "eth21"

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 6ae87a8d-42fe-4e6f-a3c8-ee81e4d4ce00
controller          : [7b942a8c-935b-4f8a-9926-8fbfaec8b5b3]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [193b7599-ed62-4b2b-9f46-09090c7bb656, 647ad537-24a2-472a-83a6-ec029c1c727e, 75949526-32cd-41f0-b9d9-e8832a6355b5, ba0c4a93-b77c-4fa5-b11c-e205c83551b6]
protocols           : ["OpenFlow13"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 7b942a8c-935b-4f8a-9926-8fbfaec8b5b3
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_connect="657", sec_since_disconnect="1", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 193b7599-ed62-4b2b-9f46-09090c7bb656
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [4a1e96c4-b731-49e9-964e-8329250e52c0]
name                : "eth22"

_uuid               : 75949526-32cd-41f0-b9d9-e8832a6355b5
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [1743fe0b-fb32-46c7-a5f8-4954cbae0e2a]
name                : "eth23"

_uuid               : 647ad537-24a2-472a-83a6-ec029c1c727e
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [b6dbcc31-ed5d-4fa2-a562-df5a01f46bd9]
name                : "br0"

_uuid               : ba0c4a93-b77c-4fa5-b11c-e205c83551b6
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [5e765171-6fba-4541-811e-c132e816142d]
name                : "eth21"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 4a1e96c4-b731-49e9-964e-8329250e52c0
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=610371365916, tx_dropped=0, tx_errors=0, tx_packets=407065887}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : b6dbcc31-ed5d-4fa2-a562-df5a01f46bd9
admin_state         : down
duplex              : full
ifindex             : 823
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

_uuid               : 5e765171-6fba-4541-811e-c132e816142d
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
statistics          : {collisions=0, rx_bytes=1204332484758, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=803234909, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 1743fe0b-fb32-46c7-a5f8-4954cbae0e2a
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=37806393000, tx_dropped=0, tx_errors=0, tx_packets=25204262}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 0d42597cd1b9fa32fdfc6c033c97d28c09087b57
Author:     Alin Serdean &lt;aserdean@cloudbasesolutions.com&gt;
AuthorDate: Mon Mar 30 15:34:28 2015 +0000
Commit:     Gurucharan Shetty &lt;gshetty@nicira.com&gt;
CommitDate: Mon Mar 30 10:08:34 2015 -0700

    build-aux/cccl: Enhance --with-debug option
    
    This patch changes the behaviour in case the configure argument: --with-debug
    was specified.
    
    Currently the optimization flag in the case of debugging is the following:
    https://msdn.microsoft.com/en-us/library/f9534wye.aspx
    which does not fully disable optimization, that is why it was changed with
    the following flag:
    https://msdn.microsoft.com/en-us/library/aafb762y.aspx
    which disables all code optimization.
    
    Also this patch includes the definition of the following preprocessor
    definitions:
    _DEBUG - in case --with-debug is specified
    
    The above definitions usually are defined when compiling with the following
    flags:
    https://msdn.microsoft.com/en-us/library/2kzt1wy3.aspx
    Since we are not compiling with the above flag, mimic the behaviour the
    debug becahviour.
    
    Signed-off-by: Alin Gabriel Serdean &lt;aserdean@cloudbasesolutions.com&gt;
    Signed-off-by: Gurucharan Shetty &lt;gshetty@nicira.com&gt;
    Acked-by: Ben Pfaff &lt;blp@nicira.com&gt;
</pre>
