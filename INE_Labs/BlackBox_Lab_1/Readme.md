# 172.16.64.101 (Owned)

Nmap results in file nmap/101.nmap

- By running dirb/gobuster found Manager app (Login required)
- Googled defualt credentials for tomcat and found a list on github
- Started brute forecing and found used default creds - tomcat/s3cret
- Found a module called tomcat_mgr_upload on metasploit
- Used msfconsole to get a shell (meterpreter session)
- Found 2 flags on user desktops

---

# 172.16.64.140 (Owned)

Nmap results in file nmap/140.nmap

- By running dirb/gobuster found "/project" directory (Login required)
- Tried various crednetials and credentials admin:admin worked (BRUH....)
- Ran dirbuster on "/project" directory using flag `-u admin:admin`
- Found file which stated the whole path of flag
- Found flag by going to address specified in file, http://172.16.64.140/project/354253425234234/flag.txt

---

# 172.16.64.182

Nmap results in file nmap/182.nmap

---

# 172.16.64.199

Nmap results in file nmap/199.nmap