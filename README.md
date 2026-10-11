# Homelab: SSH Brute-Force Attack & Detection

A virtualized attack-and-detect lab built in VMware Workstation Pro. The end goal is to launch an SSH brute-force attack from a Kali Linux attacker against an Ubuntu Server target, then detect and alert on it with the Wazuh SIEM.

> **Status:** In progress. The Ubuntu Server target is built; the attacker and SIEM are next.

## Why this lab

Detection makes more sense once you understand the attack. This lab runs both sides of one common, real-world attack (SSH brute-forcing) so I can see exactly what it looks like in the logs, and then build detection around it. I thought it would be a great learning tool and good hands-on experience in the field. Every tool choice and configuration decision is documented in [`docs/`](docs/).

## Architecture

| Machine | Role | OS | Status |
| --- | --- | --- | --- |
| Target | SSH server under attack | Ubuntu Server [FILL IN: version, e.g. 24.04 LTS] | ✅ Built |
| Attacker | Runs the brute-force attack | Kali Linux | ⬜ Planned |
| SIEM | Collects logs, detects and alerts | Wazuh | ⬜ Planned |

- **Hypervisor:** VMware Workstation Pro
- **Host machine:** [FILL IN: laptop or desktop, CPU, RAM]
- **Network:** [FILL IN: VMware network mode and why]

All attacks run only against VMs I own, on an isolated virtual network.

## Roadmap

- [x] Build Ubuntu Server target VM
- [x] Install and enable OpenSSH server
- [ ] Build Kali Linux attacker VM
- [ ] Deploy Wazuh and enroll the Ubuntu target as an agent
- [ ] Run an SSH brute-force attack from Kali
- [ ] Detect the attack in Wazuh and document the alerts
- [ ] Write a Python script that parses `/var/log/auth.log` and flags IPs with repeated failed logins

## Documentation

| # | Doc | Covers |
| --- | --- | --- |
| 01 | [Ubuntu Server target](docs/01-ubuntu-server.md) | Distro choice, VM setup, OpenSSH install and verification |
| 02 | Kali attacker *(coming soon)* | |
| 03 | Wazuh SIEM *(coming soon)* | |
| 04 | Brute-force exercise *(coming soon)* | |

## Tools

VMware Workstation Pro · Ubuntu Server · OpenSSH · Kali Linux *(planned)* · Wazuh *(planned)*

## Repository structure

```text
homelab/
├── README.md
├── docs/          # One write-up per milestone
├── screenshots/   # Evidence for each step (credentials redacted)
└── scripts/       # Detection scripts (planned)
```

## Author

**Jabran Pasha** · IT student at NYIT, focused on cybersecurity
[LinkedIn](https://linkedin.com/in/jabran-pasha) · [OverTheWire Bandit writeups]([https://github.com/jabranpasha/OverTheWire/tree/main/bandit])
