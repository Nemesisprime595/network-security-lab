# Findings and reflection

Observed findings: pending execution. No passed tests or blocked traffic results claimed yet.

For unexpected results record source, destination, expected policy, packet path, device output, root cause, correction and retest outcome.

VLANs separate broadcast domains; routing enables communication. The inbound Guest ACL filters packets arriving from Guest. VTY access-class separately restricts administration sources. SSH protects management sessions in transit.

Denied packets are not automatically malicious: user error or misconfiguration can explain them. Describe results as simulated packet behaviour, not SOC telemetry.

Future improvements: dedicated management VLAN; service-specific Staff-to-Server policy with explicit return-traffic design; separate virtual syslog/SIEM investigation lab.
