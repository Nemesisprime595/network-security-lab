# Segmented Network Security Lab

Author: Raaed Saeed, final year BSc (Hons) Cyber Security, Solent University.

**Status: build kit prepared; simulator build and tests pending.** Fresh rebuild after previous local files were lost. No working .pkt or captured test evidence is included yet.

## Objective
Demonstrate segmentation, controlled administration and repeatable network security testing in an isolated simulated network.

## Topology
Cisco 2911 R1 G0/0 connects to Cisco 2960 SW1 G0/1 as an 802.1Q trunk. Use copper straight-through cables.

| SW1 port | Device | VLAN | Address | Gateway |
|---|---|---|---|---|
| F0/1 | Admin PC | 10 Staff | 192.168.10.10/24 | 192.168.10.1 |
| F0/2 | Staff PC | 10 Staff | 192.168.10.20/24 | 192.168.10.1 |
| F0/3 | Guest PC | 20 Guest | 192.168.20.10/24 | 192.168.20.1 |
| F0/4 | Web Server | 30 Server | 192.168.30.10/24 | 192.168.30.1 |

Router gateways use .1 in each subnet. SW1 management is 192.168.10.2/24. No Internet, DNS, DHCP or NAT.

## Policy
- Staff and Server communicate in both directions in this baseline.
- Guest may ping its own gateway; all other routed Guest traffic is denied.
- Only Admin PC may attempt SSH to R1 and SW1; valid credentials remain required.
- Telnet is disabled. Unused switch ports are shut down.

See [build guide](docs/BUILD.md), [test record](docs/TESTS.md), [analysis](docs/ANALYSIS.md), and [templates](configs).

## Limits
Packet Tracer is a simulator. ACLs are stateless: Guest return packets are filtered too. Router ACLs cannot filter same-VLAN traffic. Management shares Staff VLAN 10, and an IP restriction does not prevent address impersonation. This project does not demonstrate SIEM triage, intrusion detection or production SOC telemetry.
