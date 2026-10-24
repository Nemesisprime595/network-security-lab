# Test record

All actual results pending. Record date, version, actual outcome and evidence filename per test. PC SSH: ssh -l labadmin ADDRESS.

| ID | Source and action | Expected | Actual |
|---|---|---|---|
| T01 | Admin ping 192.168.10.20 | Replies, same VLAN | Pending |
| T02 | Staff ping 192.168.10.1 | Replies | Pending |
| T03 | Guest ping 192.168.20.1 | Replies | Pending |
| T04 | Staff ping 192.168.30.10 | Replies, routed | Pending |
| T05 | Staff browser http://192.168.30.10 | Page loads | Pending |
| T06 | Guest ping 192.168.10.10 | Blocked | Pending |
| T07 | Guest ping 192.168.30.10 | Blocked | Pending |
| T08 | Guest browser http://192.168.30.10 | Blocked | Pending |
| T09 | Admin SSH to 192.168.10.1 and .2 | Valid login succeeds | Pending |
| T10 | Staff .20 SSH to 192.168.10.1 and .2 | Blocked by VTY restriction | Pending |
| T11 | Guest SSH to 192.168.10.1 and .2 | Blocked by Guest ACL | Pending |
| T12 | Admin Telnet to 192.168.10.1 and .2 | No session | Pending |
| T13 | Server ping 192.168.10.20 | Replies | Pending |
| T14 | Reopen saved project; repeat T04 T07 T09 | Same results | Pending |

Capture R1 show ip interface brief, show ip route, show access-lists, show ip ssh; SW1 show vlan brief, show interfaces trunk, show ip ssh. Redact secrets.

For T07/T08 compare deny counters before/after if supported or capture Simulation mode drops. T10 on SW1 independently tests VTY filtering because Staff and switch management share a subnet.

Staff-initiated ping to Guest fails too: Guest echo replies are denied. This is not a stateful firewall.
