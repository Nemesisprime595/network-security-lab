# Build guide

1. Record Packet Tracer version: pending. Place and cable devices as described in README. Adapt interface names if your model differs and document changes.
2. Set endpoint addresses in Desktop > IP Configuration with mask 255.255.255.0 and listed gateway. Leave DNS blank.
3. On Server > Services > HTTP enable HTTP. Use a simple lab page without private data.
4. Decline initial device setup dialogue if shown. In a LOCAL copy of each template replace BOTH credential placeholders with unique disposable lab credentials. Paste SW1 template then R1 template. Stop and resolve rejected commands.
5. On BOTH devices enter configure terminal, run crypto key generate rsa, and choose 2048 bits if supported at the prompt. Record any simulator limitation requiring a smaller key. Then run ip ssh version 2, end, and copy running-config startup-config. Accept the destination prompt.
6. Wait for green links. R1: show ip interface brief; show ip route. SW1: show vlan brief; show interfaces trunk; show ip interface brief.
7. Inspect show running-config locally on both devices. Every available VTY line must use login local, transport input ssh and access-class 10 in. Configure any extra VTY ranges exposed by your model.
8. Run TESTS.md. Initial pings may time out during ARP; retry before drawing conclusions. Use Simulation mode and ACL counters where supported to establish why traffic drops.
9. Save lab/segmented-network-v1.pkt. Reopen and retest. Add redacted screenshots under evidence/ and actual results in TESTS.md.
10. Commit sanitized templates and evidence, never private populated exports. A .pkt can contain credentials: use lab-only secrets and keep a second backup outside this PC.

Troubleshoot in order: cables/link state, addresses/masks/gateways, VLAN membership, trunk allowed VLANs, dot1Q subinterfaces, ACL order and direction. A timeout alone does not prove an ACL caused a drop.

## References
- [Cisco SSH configuration](https://www.cisco.com/c/en/us/support/docs/security-vpn/secure-shell-ssh/4145-ssh.html)
- [Cisco IP access lists](https://www.cisco.com/c/en/us/support/docs/security/ios-firewall/23602-confaccesslists.html)
- [Cisco Networking Academy Packet Tracer SSH exercise](https://contenthub.netacad.com/legacy/ITE/7.01/en/course/files/11.5.5.3%20Packet%20Tracer%20-%20Use%20Telnet%20and%20SSH.pdf)

Templates are an original lab design; not yet validated in your simulator.
