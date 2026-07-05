# Metasploitable Recon — Task: Full Network Reconnaissance

## Legal Notice
This project was conducted exclusively against **Metasploitable**, a deliberately vulnerable virtual machine built for security training in an isolated home lab. All scans were performed against a system I own and control — no external or third-party systems were involved.

The techniques documented here (host discovery, port scanning, service enumeration) should only ever be run against systems you own or have explicit written authorization to test. Scanning systems without permission may be illegal in your jurisdiction.

## Objective
Perform a complete reconnaissance pass against a Metasploitable VM using Nmap, covering host discovery, TCP/UDP port scanning, and advanced scan techniques (FIN, NULL, XMAS, ACK) to understand what each method reveals to a pen tester.

## Repository Structure
```
Metasploitable-Recon/
├── README.md      → Overview, setup, and how to reproduce the scans
└── report.md      → Full technical breakdown, findings, and risk analysis
```

## Tools Used
- Nmap (host discovery, TCP/UDP scanning, advanced scan types)
- Oracle VirtualBox (Metasploitable target VM)

## Setup
1. Run Metasploitable in VirtualBox and note its IP address.
2. Confirm the host is alive:
   ```
   sudo nmap -sn <target-ip>
   ```
3. Run a full TCP SYN scan:
   ```
   sudo nmap -sS -p- <target-ip>
   ```
4. Run a UDP scan on top ports:
   ```
   sudo nmap -sV --top-ports 100 <target-ip>
   ```
5. Run advanced scans (optional, for firewall/IDS behavior testing):
   ```
   sudo nmap -sF -p- <target-ip>   # FIN
   sudo nmap -sN <target-ip>       # NULL
   sudo nmap -sX <target-ip>       # XMAS
   sudo nmap -sA <target-ip>       # ACK
   ```

See `report.md` for full results, findings, and risk analysis.
