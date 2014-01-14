---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
0c1f07b1-b3a1-4744-877b-b21c0c6fcb0d
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
_uuid               : 303deda1-f384-4042-8e9d-050c27947db8
controller          : [73ef7db9-351b-4f15-ac0e-eeb117769f82]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [78f88efe-62b8-4b71-b4e9-6fd841ea3b65, b1416323-0daa-407d-b4dd-4e6704df2c52, b282de43-1d49-4d8e-b27e-6b15be398a40]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 73ef7db9-351b-4f15-ac0e-eeb117769f82
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=302, sec_since_disconnect=1, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 78f88efe-62b8-4b71-b4e9-6fd841ea3b65
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [b7bc657a-3cd2-4b5c-b4cf-9b0041987df4]
name                : eth8

_uuid               : b1416323-0daa-407d-b4dd-4e6704df2c52
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [1806f53d-0bf0-4b08-a8f7-42d9f63b48a0]
name                : eth7

_uuid               : b282de43-1d49-4d8e-b27e-6b15be398a40
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [bf8f7921-42cc-457a-9564-25f164555a8b]
name                : br0

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : bf8f7921-42cc-457a-9564-25f164555a8b
admin_state         : up
duplex              : full
ifindex             : 67
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

_uuid               : 1806f53d-0bf0-4b08-a8f7-42d9f63b48a0
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
statistics          : {collisions=0, rx_bytes=1305300, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=13200, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 

_uuid               : b7bc657a-3cd2-4b5c-b4cf-9b0041987df4
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=408440, tx_dropped=0, tx_errors=0, tx_packets=4400}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit ed596d3a10ed0eab9aa0c48d5201b1b8046188cc
Author:     Gurucharan Shetty &lt;gshetty@nicira.com&gt;
AuthorDate: Mon Jan 6 08:47:57 2014 -0800
Commit:     Gurucharan Shetty &lt;gshetty@nicira.com&gt;
CommitDate: Tue Jan 14 08:34:48 2014 -0800

    util: Set program_name for windows correctly.
    
    Windows path uses backward slashes. Also, the executable name
    has a .exe extension in it. While creating log files, we use
    the program name to create log file names. It feels a little odd
    to have log file names like ovsdb-server.exe.log etc. Using
    _splitpath_s() is a way to have same log file names on both
    windows and linux platforms.
    
    Signed-off-by: Gurucharan Shetty &lt;gshetty@nicira.com&gt;
    Acked-by: Ben Pfaff &lt;blp@nicira.com&gt;
</pre>
