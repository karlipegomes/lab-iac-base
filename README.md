## CringerLabs IAC Base

### Description

Esse é um projeto base para os próximos projetos irão vir, o objetivo é padronizar o minimal das máquinas para que todos tenham os mesmos pacotes. Assim como as mesmas configurações iniciais. Este código foi criado para utilizar em ambiente CentOS/RHEL 7.

### Instructions

O primeiro passo foi criar a VM e a partir dela criar um template simples: [*conferir*](https://cringerlabs.com/templace-centos7/)

#### Roles description(main.yml file)

Role inicial, divida em 3 partes, common, packages e services.
```bash
ansible-playbook -f main.yml
```
##### common(ssh key)

Role onde será: alterado o hostname da VM com base no inventory, desabilitado o SELinux no arquivo e em execução, adicionado o usuário ansible assim como dar as devidas permissões(FULL), alterar a porta padrão do SSH, realizar a troca de chave do usuário ansible, desabilitar o login remoto via root e por fim adicionar um banner(motd) para garantir avisos relativos ao ambiente.

##### packages(yum)

Role onde será: instalado o EPEL repository, instalado uma lista de pacotes base para administração (vim, wget, tcpdump, open-vm-tools, bind-utils, net-tools, htop, screen, telnet) e por fim atualizado toda a lista de pacotes do sistema operacional.

##### services(chrony and vmware vmtools)

Role onde será: instalado o chrony (NTP client) e configurado para funcionar com o server da rede e startado o serviço do vmware vmtools.

#### Roles description(main-monitoring.yml file)

Esta segunda parte foi separada pois precisamos dos serviços do zabbix e ELK funcionando para que ambas consigam fazer sentido.
```bash
ansible-playbook -f main-monitoring.yml
```
##### zabbix 5.0(agent passive)

Role onde será: instalado o agent do zabbix e configurado corrigindo o hostname no arquivo de configuração, assim como realizado a liberação na porta ssh.

##### syslog(add file bash.conf)

Role onde será: adicionado no /etc/bashrc e no rsyslog, parâmetros para o monitoramento de comandos realizados na máquina (sonho né, segue um melhor detalhamento no link abaixo). 

[*melhor detalhamento*](https://cringerlabs.com/tooltip-elk-stack-parte4linux-commands-monitoring/)

### Autor

***Karlipe Gomes*** 

*Github* - [@CringerLabsProject](https://github.com/cringerlabs/)
*LinkedIn* - [@karlipegomes](https://www.linkedin.com/in/cfgomes/)
*Website* - [cringerlabs.com](https://www.cringerlabs.com/)

#### Version
1.0
