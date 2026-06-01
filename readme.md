rhcsa learning notes in structrued

objective 1  - Essential Tools                
objective 2  - Shell Scripting               
objective 3  - Operate Running Systems       
objective 4  - Configure Local Storage/LVM   
objective 5  - Create and Configure Filesystems 
objective 6  - Deploy and Maintain Systems    
objective 7  - Manage Basic Networking        
objective 8  - Manage Users and Groups        
objective 9  - Manage Security/SELinux        
objective 10 - Flatpak                       
objective 11 - Systemd Timers

# RHCSA EX200 v10 rtudy roadmap deatails

## objective 1 - essential tools
1. navigate the filesystem
2. create, copy, move, delete files and directories
3. find/locate files
4. read and edit files
5. input output redirection and pipes
6. archiving, compression and extration
7. access documentation using man pages

## objective 2 - fundamental shell scriptings
1. create and run basic shell scripts
2. variables and user input
3. conditionals (if, else, elif)
4. loops (for, while)
5. functions
6. script arguments and exit codes
7. scheduling scripts with cron and at

## objective 3 -operate running systems
1. boot targets and systemd
2. start, stop, restart, and enable services
3. process management (ps, top, kill, nice)
4. boot into rescue and emergency mode
5. interrupt boot to gain root access
6. manage system logs with journalctl
7. transfer files securely between systems (scp, rsync)
8. set system tuning profiles with tuned adm

## objective 4 : configure local storage LVM
1. lists and inspect disks and partitions
2. create MBR and GPT partitions with fdisk and gdisk
3. create physical volumes (PV)
4. create volume groups (VG)
5. create and extend logical volumes (LV)
6. reduce and remove logical volumes safely
7. persistent storage with /etc/fstab

## objective 5 :create and configure filesystems
1. create ext4 and xfs filesystems
2. mount and unmount filesystems manually
3. persistent mounts using /etc/fstab
4. create and use swap space
5. find and use network filesystems (NFS)
6. fonfigure autofs for automatic mountings

## objective 6 - deploy & maintain systems
1. install and update softwares with dnf
2. enable and manage dnf repositories
3. work with rpm packages directly
4. configure automatic updates
5. manage system time and timezones
6. basic Kickstart concepts for exam awareness

## objective 7 :managing basic networking
1. view and configure network interfaces with nmcli
2. set static ip addresses
3. configure hostname and DNS
4. test connectivity (ping, dig, traceroute)
5. configure SSH server and client
6. manage firewalld rules and zones

## objective 8 :manage users/groups & permissions
1. create and delete users
2. modify user properties (shell, home, expiry)
3. manage passwords and password policies
4. create and manage groups
5. configure sudo access
6. understand and use su and sudo
7. user and group file permissions more details

## objective 9 :manage security, SELinux in Redhat world
1. understand selinux modes (enforcing, permissive, disabled)
2. check and change selinux contexts
3. restore default selinux contexts with restorecon
4. manage selinux booleans
5. read and interpret selinux audit logs
6. configure firewalld for service access
7. set file permissions with ACLs (getfacl, setfacl)

## objective 10 :flatpak
1. what flatpak is and why it exist
2. install and configures with flatpak
3. add and manage flatpak repositories (remotes)
4. install, updates, and removes flatpak applications
5. list and inspects installed flatpaks

## objective 11 :systemd timers
1. understand systemd timers vs cron
2. anatomy of a timer unit file
3. create a basic systemd timer
4. enable, start, and verify timer
5. one shot vs recurring timer
6. list and monitor active timers

---

## exam basics 
- exam is RHCSA EX200 v10 base on RHEL 10
- three hours in total, performance based, not multiple choices
- no internet allowed, man pages are only available references
- system gets rebooted after submission, everything must survive rebooting
- systemctl enable is just as important as systemctl start
- exact filenames and exact paths matter, no partial credits
- one free retake if first exam taking fail :)
- results within 3 business days (united states)
- flatpak and systemd timers are new added in v10

---

## key exam tips & tricks
- objectives 4 and 5 (LVM and filesystems) are common fail points
- objective 9 (SELinux) is secondary fail points, it will blocks things silently
- always verify the work after every tasks
- always use systemctl enable not just at start
- use man pages with / to search, do not read the whole pages
- tab completion prevents typos, make it habbit to use it regularly
- skip stuck tasks and come back, do not try to waste many minutes on one task
- always rebooting to verify before considering a task completion. exam itself test it all with rebooting after taking the exam 