# Homelab: SSH Brute-Force Attack & Detection

I'm building a homelab to get some hands-on experience in security to learn by doing, instead of just reading about it. My end goal for this project is to successfully simulate an SSH brute-force attack on an Ubuntu Server from a Kali Linux VM and detect it with a free SIEM tool (in this case Wazuh).

I'm going to be documenting everything as I go, including why I made each decision and documenting any errors or roadblocks I run into along the way.

## Status

**In progress**

- [x] Ubuntu Server VM (target) with OpenSSH
- [ ] Kali Linux VM (attacker)
- [ ] Wazuh (detection)
- [ ] Run the SSH brute-force attack
- [ ] Detect the attack in Wazuh

## Lab Setup

**Host:** HP Victus 16 (Intel Core i7-14650HX, 16 GB RAM, Windows 11 Home) running VMware Workstation Pro

| VM | Role | RAM | CPUs | Disk | Network |
|----|------|-----|------|------|---------|
| Ubuntu Server | Target | 6 GB | 2 | 20 GB | NAT |
| Kali Linux | Attacker | TBD | TBD | TBD | NAT (planned) |
| Wazuh | Detection | TBD | TBD | TBD | NAT (planned) |

> [!NOTE]
> After measuring my RAM usage and researching how much RAM each VM would need, I might push my laptop to its limits with this lab, even if I shrink Ubuntu down to 2 GB (which I will likely do regardless). If that does happen, I have an extra desktop with 16 GB of RAM that I can run Wazuh on. That would also allow me to get constant live data and get a sense of what "normal" data looks like. I'll move it to the desktop if I see my laptop struggling, or if I decide to expand on this setup in the future and require more system resources.

## Tools

- **VMware Workstation Pro**: Hypervisor. I went with Workstation Pro because it's free for personal use, reliable, and easy to create restore points (snapshots) with.
- **Ubuntu Server**: Target machine. I went with the server version so I'd actually have to work from the command line instead of relying on a desktop GUI.
- **Kali Linux**: Attacker machine. I went with Kali Linux because it's the industry standard for offensive cybersecurity and comes pre-installed with a lot of tools that I can use, plus it's also in the Debian family like Ubuntu so a lot of what I have to learn for Ubuntu will carry over to Kali.
- **Wazuh**: Detection. I chose Wazuh as my SIEM tool because it's free and open-source, its agent can monitor Linux hosts like my Ubuntu VM, and it comes with built-in rules for detecting SSH brute-force attacks, which is exactly what this lab needs. It also has XDR capabilities, so later on I can use its Active Response feature to automatically block an attacker's IP.
