---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
7ce52836-8410-4488-b603-6dde4936efac
    Bridge "br0"
        Controller "tcp:10.24.150.30:6633"
        fail_mode: secure
        Port "br0"
            Interface "br0"
                type: internal
        Port "eth23"
            Interface "eth23"
        Port "eth21"
            Interface "eth21"
        Port "eth22"
            Interface "eth22"

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 0c99a3dc-d9fa-4ace-a88d-536de6a9df4a
controller          : [c32629a1-2300-4e55-8e09-90a47e184653]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [46566d29-95a2-4a08-9e51-27e290c3fada, 5b074b86-798b-459c-a6a4-f9b16419f663, 8ef80519-5603-4db2-b4e7-29f7920e3c00, 9a48fbb5-bdca-460c-8789-7b8d82bc8e52]
protocols           : ["OpenFlow14"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : c32629a1-2300-4e55-8e09-90a47e184653
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_disconnect="2", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 8ef80519-5603-4db2-b4e7-29f7920e3c00
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [d25eda24-d5f8-429c-abca-3d979cfc862b]
name                : "eth21"

_uuid               : 46566d29-95a2-4a08-9e51-27e290c3fada
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [cdd21b61-9e96-4cfc-bfd6-f52f907eb963]
name                : "br0"

_uuid               : 9a48fbb5-bdca-460c-8789-7b8d82bc8e52
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [5c1926a0-97cc-47d5-ae1e-5cf24ec4a6d1]
name                : "eth22"

_uuid               : 5b074b86-798b-459c-a6a4-f9b16419f663
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [8ea3dd4b-8547-40f5-9f32-33961fd81773]
name                : "eth23"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : d25eda24-d5f8-429c-abca-3d979cfc862b
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

_uuid               : 5c1926a0-97cc-47d5-ae1e-5cf24ec4a6d1
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

_uuid               : cdd21b61-9e96-4cfc-bfd6-f52f907eb963
admin_state         : down
duplex              : full
ifindex             : 439
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

_uuid               : 8ea3dd4b-8547-40f5-9f32-33961fd81773
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
commit c02819293d52f7ea7b714242d871b2b01f57f905
Author:     Russell Bryant &lt;rbryant@redhat.com&gt;
AuthorDate: Thu Sep 3 12:45:01 2015 -0400
Commit:     Ben Pfaff &lt;blp@nicira.com&gt;
CommitDate: Tue Sep 8 11:51:31 2015 -0700

    ovn: Add &quot;localnet&quot; logical port type.
    
    Introduce a new logical port type called &quot;localnet&quot;.  A logical port
    with this type also has an option called &quot;network_name&quot;.  A &quot;localnet&quot;
    logical port represents a connection to a network that is locally
    accessible from each chassis running ovn-controller.  ovn-controller
    will use the ovn-bridge-mappings configuration to figure out which
    patch port on br-int should be used for this port.
    
    OpenStack Neutron has an API extension called &quot;provider networks&quot; which
    allows an administrator to specify that it would like ports directly
    attached to some pre-existing network in their environment.  There was a
    previous thread where we got into the details of this here:
    
      http://openvswitch.org/pipermail/dev/2015-June/056765.html
    
    The case where this would be used is an environment that isn't actually
    interested in virtual networks and just wants all of their compute
    resources connected up to externally managed networks.  Even in this
    environment, OVN still has a lot of value to add.  OVN implements port
    security and ACLs for all ports connected to these networks.  OVN also
    provides the configuration interface and control plane to manage this
    across many hypervisors.
    
    As a specific example, consider an environment with two hypvervisors
    &#40;A and B&#41; with two VMs on each hypervisor &#40;A1, A2, B1, B2&#41;.  Now imagine
    that the desired setup from an OpenStack perspective is to have all of
    these VMs attached to the same provider network, which is a physical
    network we'll refer to as &quot;physnet1&quot;.
    
    The first step here is to configure each hypervisor with bridge mappings
    that tell ovn-controller that a local bridge called &quot;br-eth1&quot; is used to
    reach the network called &quot;physnet1&quot;.  We can simulate the inital setup
    of this environment in ovs-sandbox with the following commands:
    
      # Setup the local hypervisor &#40;A&#41;
      ovs-vsctl add-br br-eth1
      ovs-vsctl set open . external-ids:ovn-bridge-mappings=physnet1:br-eth1
    
      # Create a fake remote hypervisor &#40;B&#41;
      ovn-sbctl chassis-add fakechassis geneve 127.0.0.1
    
    To get the behavior we want, we model every Neutron port connected to a
    Neutron provider network as an OVN logical switch with 2 ports.  The
    first port is a normal logical port to be used by the VM.  The second
    logical port is a special port with its type set to &quot;localnet&quot;.
    
    To simulate the creation of the OVN logical switches and OVN logical
    ports for A1, A2, B1, and B2, you can run the following commands:
    
      # Create 4 OVN logical switches.  Each logical switch has 2 ports,
      # port1 for a VM and physnet1 for the existing network we are
      # connecting to.
      for n in 1 2 3 4; do
          ovn-nbctl lswitch-add provnet1-$n
    
          ovn-nbctl lport-add provnet1-$n provnet1-$n-port1
          ovn-nbctl lport-set-macs provnet1-$n-port1 00:00:00:00:00:0$n
          ovn-nbctl lport-set-port-security provnet1-$n-port1 00:00:00:00:00:0$n
    
          ovn-nbctl lport-add provnet1-$n provnet1-$n-physnet1
          ovn-nbctl lport-set-macs provnet1-$n-physnet1 unknown
          ovn-nbctl lport-set-type provnet1-$n-physnet1 localnet
          ovn-nbctl lport-set-options provnet1-$n-physnet1 network_name=physnet1
      done
    
      # Bind lport1 &#40;A1&#41; and lport2 &#40;A2&#41; to the local hypervisor.
      ovs-vsctl add-port br-int lport1 -- set Interface lport1 external_ids:iface-id=provnet1-1-port1
      ovs-vsctl add-port br-int lport2 -- set Interface lport2 external_ids:iface-id=provnet1-2-port1
    
      # Bind the other 2 ports to the fake remote hypervisor.
      ovn-sbctl lport-bind provnet1-3-port1 fakechassis
      ovn-sbctl lport-bind provnet1-4-port1 fakechassis
    
    After running these commands, we have the following logical
    configuration:
    
      $ ovn-nbctl show
        lswitch 035645fc-b2ff-4e26-b953-69addba80a9a &#40;provnet1-4&#41;
            lport provnet1-4-physnet1
                macs: unknown
            lport provnet1-4-port1
                macs: 00:00:00:00:00:04
        lswitch 66212a85-b3b6-4688-bcf6-8062941a2d96 &#40;provnet1-2&#41;
            lport provnet1-2-physnet1
                macs: unknown
            lport provnet1-2-port1
                macs: 00:00:00:00:00:02
        lswitch fc5b1141-0216-4fa7-86f3-461811c1fc9b &#40;provnet1-3&#41;
            lport provnet1-3-physnet1
                macs: unknown
            lport provnet1-3-port1
                macs: 00:00:00:00:00:03
        lswitch 9b1d2636-e654-4d43-84e8-a921af611b33 &#40;provnet1-1&#41;
            lport provnet1-1-physnet1
                macs: unknown
            lport provnet1-1-port1
                macs: 00:00:00:00:00:01
    
    We can also look at OVN_Southbound to see that 2 logical ports are bound
    to each hypervisor:
    
      $ ovn-sbctl show
      Chassis &quot;56b18105-5706-46ef-80c4-ff20979ab068&quot;
          Encap geneve
              ip: &quot;127.0.0.1&quot;
          Port_Binding &quot;provnet1-1-port1&quot;
          Port_Binding &quot;provnet1-2-port1&quot;
      Chassis fakechassis
          Encap geneve
              ip: &quot;127.0.0.1&quot;
          Port_Binding &quot;provnet1-3-port1&quot;
          Port_Binding &quot;provnet1-4-port1&quot;
    
    Now we can generate several packets to test how a packet would be
    processed on hypervisor A.  The OpenFlow port numbers in this demo are:
    
      1 - patch port to br-eth1 &#40;physnet1&#41;
      2 - tunnel to fakechassis
      3 - lport1 &#40;A1&#41;
      4 - lport2 &#40;A2&#41;
    
    Packet test #1: A1 to A2 - This will be output to ofport 1.  Despite
    both VMs being local to this hypervisor, all packets betwen the VMs go
    through physnet1.  In practice, this will get optimized at br-eth1.
    
      ovs-appctl ofproto/trace br-int \
        in_port=3,dl_src=00:00:00:00:00:01,dl_dst=00:00:00:00:00:02 -generate
    
    Packet test #2: physnet1 to A2 - Consider this a continuation of test
    is attached to will be considered.  The end result should be that the
    only output is to ofport 4 &#40;A2&#41;.
    
      ovs-appctl ofproto/trace br-int \
        in_port=1,dl_src=00:00:00:00:00:01,dl_dst=00:00:00:00:00:02 -generate
    
    Packet test #3: A1 to B1 - This will be output to ofport 1, as physnet1
    is to be used to reach any other port.  When it arrives at hypervisor B,
    processing would look just like test #2.
    
      ovs-appctl ofproto/trace br-int \
        in_port=3,dl_src=00:00:00:00:00:01,dl_dst=00:00:00:00:00:03 -generate
    
    Packet test #4: A1 broadcast. - Again, the packet will only be sent to
    physnet1.
    
      ovs-appctl ofproto/trace br-int \
        in_port=3,dl_src=00:00:00:00:00:01,dl_dst=ff:ff:ff:ff:ff:ff -generate
    
    Packet test #5: B1 broadcast arriving at hypervisor A.  This is somewhat
    a continuation of test #4.  When a broadcast packet arrives from
    physnet1 on hypervisor A, we should see it output to both A1 and A2
    &#40;ofports 3 and 4&#41;.
    
      ovs-appctl ofproto/trace br-int \
        in_port=1,dl_src=00:00:00:00:00:03,dl_dst=ff:ff:ff:ff:ff:ff -generate
    
    Signed-off-by: Russell Bryant &lt;rbryant@redhat.com&gt;
    Signed-off-by: Ben Pfaff &lt;blp@nicira.com&gt;
</pre>
