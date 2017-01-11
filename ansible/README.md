# Ansible-izing the BasicEVPN model
An Ansible playbook and supporting files for automating the deployment of the
BasicEVPN topology.

Creates config files for a fully-functional Spine-Leaf architecture with an EVPN-over-VXLAN overlay, and L3 gateway on the Spines.  And it leverages EBGP
with labeled-unicast in the Underlay.  So if you want to layer on some other
VPN technology (like L3VPN-over-MPLS), you can drop it right in with no
additional signaling or interface commands required.

Simple group and host variables are included for illustration purposes.  And
don't kill yourself trying to reverse the root or admin passwords.  Both are
set for "Juniper1".
