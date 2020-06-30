## CringerLabs IAC Base

### Instructions

```sh
ansible-playbook -f main.yml
```
##### Roles description(main.yml file)
#### services(chrony and vmware vmtools)

```sh
ansible-playbook -f main-monitoring.yml
```
##### Roles description(main-monitoring.yml file)
#### zabbix 5.0(agent passive);
#### syslog(add file bash.conf).

##### Other roles

#### main(install epel-repo and various packages, vim, wget, tcpdump, open-vm-tools, bind-utils, net-tools, htop, screen, telnet and update all packages on SO);
#### common (disable selinux, add new user called ansible and create private key, allow on sudoers, update SSH port to 2020 and enable on firewalld);

### Version

1.0

### Autor

***Karlipe*** - *Github* - https://github.com/cringerlabs/
