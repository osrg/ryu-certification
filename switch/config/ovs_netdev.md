---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
304013db-7c33-4de3-8bbe-efad8e6f1f76
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port br0
            Interface br0
                type: internal
        Port eth8
            Interface eth8
        Port eth7
            Interface eth7

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : ed9a1e8d-30ea-4766-b128-d693d3e977de
controller          : [6a6e227d-12f7-45ec-b9a8-4f1870157b9e]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [a8f5fb22-e82f-4d97-bb46-057f35ecc6a1, ac92b208-f459-4881-ae55-de790a125707, d0f68231-402b-4013-a8db-9db55303e94e]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 6a6e227d-12f7-45ec-b9a8-4f1870157b9e
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=302, sec_since_disconnect=0, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : ac92b208-f459-4881-ae55-de790a125707
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [a7a6aab1-61ba-401c-b5b9-bea0d231b1e2]
name                : eth8

_uuid               : d0f68231-402b-4013-a8db-9db55303e94e
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [c1fdfb04-69e3-4fdd-9825-e10a758d0809]
name                : eth7

_uuid               : a8f5fb22-e82f-4d97-bb46-057f35ecc6a1
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [ee603c99-4426-4391-8091-0791581e812b]
name                : br0

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : c1fdfb04-69e3-4fdd-9825-e10a758d0809
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
statistics          : {collisions=0, rx_bytes=3056704048, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=72568798, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 

_uuid               : a7a6aab1-61ba-401c-b5b9-bea0d231b1e2
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=1727758, tx_dropped=0, tx_errors=0, tx_packets=18455}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 

_uuid               : ee603c99-4426-4391-8091-0791581e812b
admin_state         : up
duplex              : full
ifindex             : 228
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
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 5ea1366bc95d68712121c45ef1695d4edf616665
Author:     Gurucharan Shetty &lt;gshetty@nicira.com&gt;
AuthorDate: Thu Feb 6 07:57:12 2014 -0800
Commit:     Gurucharan Shetty &lt;gshetty@nicira.com&gt;
CommitDate: Tue Feb 11 09:55:48 2014 -0800

    stream-ssl: Add support for Windows platform.
    
    This commit creates events and through poll_fd_wait_event()
    associates them with socket file descriptors to get woken up
    from poll_block().
    
    Some other changes:
    
    * Windows does not have sys/fcntl.h but has a fcntl.h
    On Linux, there is fctnl.h too.
    
    * include &lt;openssl/applink.c&gt; to handle different C-Runtime linking
    of OVS and openssl libraries as suggested at
    https://www.openssl.org/support/faq.html#PROG2
    
    The above include will not be needed if we compile Open vSwitch with
    /MD compiler option.
    
    * SHUT_RDWR is equivalent to SD_BOTH on Windows.
    
    Signed-off-by: Gurucharan Shetty &lt;gshetty@nicira.com&gt;
    Acked-by: Ben Pfaff &lt;blp@nicira.com&gt;
</pre>
