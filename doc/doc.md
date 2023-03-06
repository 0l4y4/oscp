# System
## install bat + alias
```bash
sudo apt install bat
echo 'alias cat="batcat"' >> ~/.zshrc
```
## add function extractPorts
```bash
vi ~/zshrc

function extractPorts(){
        ports="$(cat $1 | grep -oP '\d{1,5}/open' | awk '{print $1}' FS='/' | xargs | tr ' ' ',')"
        ip_address="$(cat $1 | grep -oP '\d{1,3}\.\d{1,3}\.\d{1,3}\.\d{1,3}' | sort -u | head -n 1)"
        echo -e "\n[*] Extracting information...\n" > extractPorts.tmp
        echo -e "\t[*] IP Address: $ip_address"  >> extractPorts.tmp
        echo -e "\t[*] Open ports: $ports\n"  >> extractPorts.tmp
        echo $ports | tr -d '\n' | xclip -sel clip
        echo -e "[*] Ports copied to clipboard\n"  >> extractPorts.tmp
        cat extractPorts.tmp; rm extractPorts.tmp
}

# usar batcat (apt install bat)
alias cat="batcat"
```

# Nmap
```bash
sudo nmap -p- --open -sS --min-rate 5000 -vvv -n -Pn 10.10.10.3 -oG allPorts #First enumeration
```
```bash
sudo nmap -sCV -p21,22,139,445,3632 10.10.10.3 -oN targeted #Second enumeration (launch nmap scripts)
```