20221004-1616
Status: #idea

Tags:

# Server Security Setup Steps Solution
The steps to secure a digital ocean droplet or some simple server form scratch

I would like to make an **Ansible** script for that

Some responses from people:

> - Create new user with sudo
> - Enable SSH login for user
> - Disable password login for droplet
> - Install and enable ufw (allow out and incoming port 443, 80 and 22).
> - Install and config fail2ban
> For all other roles, usually they start with ufw configuration, install the matching packages (+ the dbg packages when available, they can prove invaluably useful once every two years) and write the project-independant configuration files.
> -- Some user from the forums

> - Install my favorite tools (vim, zsh, htop, glances, sudo, rsync, ufw) + their configuration
> - Install common dependencies required most of the time (git, build-essential)
> - Configure the mail server (postfix)
> - Install most of the debug tools I’ve used in my life, just in case (lsof, gdb, iotop, slurm, strace)
> - Harden SSH login
> - Setup fail2ban
> - Configure logrotate to rotate with dates instead of rolling numbers (easier for archive/backup)
> - Configure time-related stuff (tzdata, ntp, setting the time zone)
> - Setup terminal auto-logout after a few minutes of inactivity
> - Set a random root password (for console login only)
> -- Some user from the forums

>1. Set the timezone to UTC.
>2. Install all updates.
>3. Install NTP.
>4. Set up SSH server: disable password authentication and root login.
>5. Install Fail2ban.
>6. Install vnstat.
>7. Install various other extra packages: dig, git, htop, iftop, iotop, mtr, ncdu, nmap, screen, sysstat, tcpdump, tig, tree, unzip, vim, zsh.
>8. Set up a non-root user: SSH keys, git and other configuration files, sudo access.
>
> A firewall role definitely needs added in there.
> -- Some user from the forums


## Steps
 1. Install utils and tools:
 ```bash
sudo apt-get install neovim tmux htop rsync ufw fail2ban git lsof
 ```
 2. Add a new user with it's newly created ssh keys and stuff
 ```bash
 useradd 
 ```
 3. Change default ssh config by adding a new file `droplet_common_config.conf` to `/etc/ssh/sshd_config.d/` folder
``` droplet_common_config.conf
PermitRootLogin no
MaxAuthTries 3
LoginGraceTime 20
PasswordAuthentication no

ChallengeResponseAuthentication no
KerberosAuthentication no
GSSAPIAuthentication no

X11Forwarding no
AllowAgentForwarding no
AllowTcpForwarding no
PermitTunnel no
DebianBanner no

```
4. Setup fail2ban with ufw for firewall protection and brute force mitigation

---
# References
[Some question on digital ocean](https://www.digitalocean.com/community/questions/best-practices-for-hardening-new-sever-in-2017)