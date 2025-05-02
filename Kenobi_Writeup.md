
# Kenobi - TryHackMe CTF Write-up

## Summary

The *Kenobi* room was a challenging yet valuable learning experience. I had to lean on online resources to get through some of the steps, and although I didn’t fully grasp everything right away, it gave me several areas to explore further.

## Methodology

1. **Port Scanning**
   - Ran an Nmap scan to identify open ports on the target machine.

2. **Samba Enumeration**
   - Used Nmap scripting to enumerate Samba shares.
   - Discovered and downloaded a useful log file from one of the shares.

3. **FTP Analysis**
   - Connected to the open FTP port using netcat.
   - Identified the running version of ProFTPD.
   - Used `searchsploit` to look up known vulnerabilities.

4. **Exploiting ProFTPD**
   - Found a vulnerability in the ProFTPD version allowing me to copy files from any part of the system.
   - Retrieved the private SSH key of a user.

5. **Gaining User Access**
   - Logged in with the user’s private key.
   - Retrieved the user flag from the home directory.

6. **Privilege Escalation**
   - Enumerated SUID binaries to find potential privilege escalation paths.
   - Found a binary that could be run with root privileges.
   - Used it to spawn a root shell and retrieved the root flag.

## Tools Used

- Nmap
- Netcat
- Searchsploit
- SSH
- Linux CLI (SUID enumeration, file permissions)

## Reflection

This room was tricky and really pushed me to think critically and learn on the fly. I didn’t get everything right away, but that’s what made it rewarding. The room highlighted the importance of persistence, and how valuable it is to document and research unfamiliar techniques.

---

#TryHackMe #CTF #CyberSecurity #PrivilegeEscalation #LinuxSecurity
