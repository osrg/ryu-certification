---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
1bd4a317-880b-4a78-9ad1-78bc7c7c3683
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port eth23
            Interface eth23
        Port eth22
            Interface eth22
        Port br0
            Interface br0
                type: internal
        Port eth21
            Interface eth21

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : bcf4ebff-824a-4275-9324-0eb00c2082eb
controller          : [d69b8800-4ee0-4007-9dbc-487f455f4ea4]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
mcast_snooping_enable: false
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [03eb43ae-1a94-4663-8ac0-c10d3d267921, 17d62413-2832-4c07-abeb-b8b31a4b8763, 39fc264f-b2ec-430a-bfe0-90cc7e404a7e, 7fa4950c-6d97-47e1-8ed4-2fd5e8540ea5]
protocols           : [OpenFlow14]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : d69b8800-4ee0-4007-9dbc-487f455f4ea4
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=677, sec_since_disconnect=0, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 7fa4950c-6d97-47e1-8ed4-2fd5e8540ea5
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [d646cf17-b438-481e-9038-3e3b4336e1cf]
name                : eth21

_uuid               : 03eb43ae-1a94-4663-8ac0-c10d3d267921
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [9dcc87dc-cb86-4321-bbb4-4169ddb89c60]
name                : eth23

_uuid               : 39fc264f-b2ec-430a-bfe0-90cc7e404a7e
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [78f67120-572b-4759-9d4f-770171ab2c11]
name                : br0

_uuid               : 17d62413-2832-4c07-abeb-b8b31a4b8763
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [995a7584-ef4e-4dd2-9483-a3623ec23329]
name                : eth22

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 995a7584-ef4e-4dd2-9483-a3623ec23329
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=1321204080, tx_dropped=0, tx_errors=0, tx_packets=23798458}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 78f67120-572b-4759-9d4f-770171ab2c11
admin_state         : down
duplex              : full
ifindex             : 94
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

_uuid               : 9dcc87dc-cb86-4321-bbb4-4169ddb89c60
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=3431910000, tx_dropped=0, tx_errors=0, tx_packets=2287940}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : d646cf17-b438-481e-9038-3e3b4336e1cf
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
statistics          : {collisions=0, rx_bytes=2976657070, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=33505559, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 63520eeb2b1942a764f0668164d4c2df8c2f9741
Author:     Nithin Raju &lt;nithin@vmware.com&gt;
AuthorDate: Fri Aug 29 15:48:10 2014 -0700
Commit:     Ben Pfaff &lt;blp@nicira.com&gt;
CommitDate: Thu Sep 4 12:40:48 2014 -0700

    datapath-windows: add support for GET_DP command to dump datpaths
    
    In this patch, we add support for the GET_DP netlink command to dump
    the datpaaths. The userspace workflow to get this to work is the same
    as on Linux. dpif-linux.c initiates a dump start by writing a netlink
    message, and after that continues to read data from the kernel while
    the kernel has data. The state is maintained in the kernel, and not in
    userspace. This approach was taken since there was not great benefit
    of maintaining state in userspace, and also to avoid userspace changes
    specific to Windows.
    
    This hopefully serves as a template to base the other dump commands on.
    
    validation:
    - With a hacked up dpif-linux.c to work on Windows,
      dpif_linux_enumerate&#40;&#41; successfully enumerated the datapaths in the
      kernel.
    
    Signed-off-by: Nithin Raju &lt;nithin@vmware.com&gt;
    Signed-off-by: Ankur Sharma &lt;ankursharma@vmware.com&gt;
    Acked-by: Ankur Sharma &lt;ankursharma@vmware.com&gt;
    Acked-by: Saurabh Shah &lt;ssaurabh@vmware.com&gt;
    Signed-off-by: Ben Pfaff &lt;blp@nicira.com&gt;
</pre>
