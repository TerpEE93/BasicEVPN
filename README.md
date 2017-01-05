# BasicEVPN
A simple DC model for EVPN using Wistar and Juniper's vQFX and vMX platforms

This topology makes use of the following conventions -- included both for
the purposes of readability and for ease of deployment:

    1.  Node Identifiers
        a. Edge routers are assigned node numbers in the range 1-9.
        b. Spine switches are assigned node numbers in the range 11-19.
        c. Leaf switches are assigned node numbers in the range 101-255.

    2.  Addressing - Underlay
        a. Loopback/router ID
           Edge, Spine: Addressed from 192.168.255.<node-id>/32
           Leaf: Addressed from 192.168.254.<node-id>/32
        b. Underlay infrastructure links (Leaf-Spine and Spine-Edge)
           Addressed from 10.<big-node-id>.<little-node-id>.0/30
           "Big" node gets .1, while "small" node gets .2.
           Edge is bigger than Spine.  Spine is bigger than Leaf.
        c. Underlay host networks (Leaf-to-Host)
           Addressed from 10.<node-id>.<node-id>.0/24
           Leaf switch gets .1

    3.  VPN Identifiers
        a. Reserved for possible admin use: 0-9
        b. L3VPN VPN: 101-255
        c. EVPN: 10,000 + VLAN ID

    4.  Autonomous System Numbers (for Underlay)
        ASN = 65000 + <node-id> for all devices

    5.  Route Distinguishers
        RD = <router-id>:<vpn-id>

    6.  Route/VRF Target
        RT = target:<router-id>:<vpn-id>

    7.  Addressing - Overlay
        a. Loopback in VRF
           Addressed from 192.168.<vpn-id>.<node-id>/32
        b. Physical interfaces in VRF
           Option 1: Taken from customer space
           Option 2: 172.31.<vpn-id>.0/24
