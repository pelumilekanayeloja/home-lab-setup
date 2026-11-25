# Home Lab — Kali Linux, Ubuntu & Windows

A personal home lab I built to practise cybersecurity and networking: virtual
machines on one shared network, with connectivity verified between hosts.

## Goal

Build a small, isolated lab where I can:

- run Linux and Windows machines side by side,
- put them on the same network,
- confirm the hosts can reach each other,
- use the lab as a base for security practice.

## Environment

| Host | Role | Notes |
| --- | --- | --- |
| Kali Linux | Attacker / testing machine | Metasploit installed |
| Ubuntu | Target / Linux practice | Command line, services |
| Windows | Target / Windows practice | |
| Host machine | Hypervisor | Runs the virtual machines |

**Tools used:** Metasploit, `ping`, standard Linux command line.

## Network layout

```text
+----------------+        +----------------+
|   Kali Linux   |        |     Ubuntu     |
|  <Kali IP>     |        |   <Ubuntu IP>  |
+----------+--------+        +-----------+---------+
          |                         |
          +--------------+---------------+
                      |
            Shared network (same subnet)
                      |
                +--------+---------+
               |   Windows    |
               |  <Windows IP> |
                +------------------+
```

All three virtual machines sit on the same network segment, so they can address
each other directly.

## What I set up

1. Installed the virtual machines for Kali Linux, Ubuntu and Windows.
2. Installed Metasploit on Kali.
3. Configured the virtual network so Kali and Ubuntu are on the same subnet.
4. Checked each machine's address with `ip a` (Linux).
5. Tested connectivity in both directions.

## Verification

From Kali:

```bash
ping -c 4 <Ubuntu IP>
```

From Ubuntu:

```bash
ping -c 4 <Kali IP>
```

Both hosts reply, which confirms the shared-network configuration is working
before I move on to anything more involved.

## What I learned

- how virtual machine networking is configured and why a shared network matters,
- how to check and reason about IP addressing on Linux,
- how to verify connectivity between hosts before testing anything else,
- the discipline of writing down a lab setup so it can be repeated.

## Next steps

- [ ] Document a firewall rule change and its effect on connectivity.
- [ ] Practise a controlled Metasploit exercise between lab hosts only.
- [ ] Add a log-review exercise and write up what the logs showed.

## Practice elsewhere

- TryHackMe
- Hack The Box
- IBM SkillsBuild cyber security labs

---

Pelumi Lekan Ayeloja · [LinkedIn](https://www.linkedin.com/in/pelumi-ayeloja-a08247240)
