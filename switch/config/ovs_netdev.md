---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
bb98eee3-8ea3-496a-be82-e92abedfcf78
    Bridge "br0"
        Controller "tcp:10.24.150.30:6633"
        fail_mode: secure
        Port "eth22"
            Interface "eth22"
        Port "eth23"
            Interface "eth23"
        Port "br0"
            Interface "br0"
                type: internal
        Port "eth21"
            Interface "eth21"

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 578f5545-78e1-4387-a512-58be18d33b08
controller          : [75d58e05-b740-4678-9ae0-3d50818656d5]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [07c3cd79-c067-4ed1-8064-e3f0dc750a1c, 2a69df8e-796b-4a3e-928c-325449964fb8, 805e8e86-40d6-465a-87d1-4777689fadf9, b3a6b27e-2bbf-4b60-abba-911c67b85793]
protocols           : ["OpenFlow13"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 75d58e05-b740-4678-9ae0-3d50818656d5
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_connect="662", sec_since_disconnect="1", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 07c3cd79-c067-4ed1-8064-e3f0dc750a1c
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [9c30b436-43e0-4144-a45b-c36ad75a7747]
name                : "eth22"

_uuid               : 2a69df8e-796b-4a3e-928c-325449964fb8
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [0e046331-f34d-410d-9f65-76bb590cc686]
name                : "eth23"

_uuid               : 805e8e86-40d6-465a-87d1-4777689fadf9
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [925b051b-02fa-4558-9e4a-bdeda9101bbb]
name                : "br0"

_uuid               : b3a6b27e-2bbf-4b60-abba-911c67b85793
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [e70e71a1-5df2-45d5-8029-0a4a24af9247]
name                : "eth21"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 0e046331-f34d-410d-9f65-76bb590cc686
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=5591701500, tx_dropped=0, tx_errors=0, tx_packets=3727801}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : e70e71a1-5df2-45d5-8029-0a4a24af9247
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
statistics          : {collisions=0, rx_bytes=41225715942, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=27526960, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 9c30b436-43e0-4144-a45b-c36ad75a7747
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=28750579508, tx_dropped=0, tx_errors=0, tx_packets=19186068}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 925b051b-02fa-4558-9e4a-bdeda9101bbb
admin_state         : down
duplex              : full
ifindex             : 640
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
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 873d85653d84289eb3a7fd253d95ebcbdad920f0
Author:     Gurucharan Shetty &lt;guru@ovn.org&gt;
AuthorDate: Mon Nov 30 15:52:09 2015 -0800
Commit:     Gurucharan Shetty &lt;guru@ovn.org&gt;
CommitDate: Wed Dec 2 10:00:46 2015 -0800

    debian: Skip systemctl redirect.
    
    After some experimentation on Ubuntu15.04, I see the
    following behavior.
    
    1. If you install openvswitch-switch with 'apt-get install',
    then you automatically get a upstart and systemd config files
    for openvswitch. The integration with 'interfaces' fails
    because both the upstart and systemd jobs do not have logic
    to handle it.
    
    The above behavior will likely get fixed soon in upstream
    Ubuntu.
    
    2. If you install openvswitch-switch via the packages
    created from the openvswitch repo, there is no systemd or
    upstart conf files installed. But systemd notices this
    and creates a runtime openvswitch conf file which does
    nothing but call back the sysv startup script.
    
    In the above case when you call
    &quot;/etc/init.d/openvswitch-switch start&quot;, it inturn calls
    &quot;/bin/systemctl start openvswitch-switch.service&quot; and
    that inturn again calls &quot;/etc/init.d/openvswitch-switch start&quot;.
    But the above for some reason simply hangs. It looks like a call
    to ifup when invoked in this manner does not return.
    I am not sure why this is happening.
    
    We can avoid the above behavior completely by skipping the
    systemctl redirect as done in this commit. This should fix
    both 1. and 2. above.
    
    Signed-off-by: Gurucharan Shetty &lt;guru@ovn.org&gt;
    Acked-by: Ben Pfaff &lt;blp@ovn.org&gt;
</pre>
