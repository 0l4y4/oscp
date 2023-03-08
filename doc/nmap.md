# Nmap
```bash
sudo nmap -p- --open -sS --min-rate 5000 -vvv -n -Pn 10.10.10.3 -oG allPorts #First enumeration
```
```bash
sudo nmap -sCV -p21,22,139,445,3632 10.10.10.3 -oN targeted #Second enumeration (launch nmap scripts)
```