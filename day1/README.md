# vodafone_dynatrace_6thOct2025

### A basic microservice app design

<img src="app1.png">


### Dynatrace Deployment modes (SAAS / On-prem / private cloud)

<img src="app2.png">


## Dynatrace OneAgent 

<img src="app3.png">

### checking monitoring mode of Oneagent in linux host 

```
ec2-user@ip-172-31-34-163 agent]$ cd
[ec2-user@ip-172-31-34-163 ~]$ 
[ec2-user@ip-172-31-34-163 ~]$ 
[ec2-user@ip-172-31-34-163 ~]$ cd /opt/dynatrace/oneagent/agent/
[ec2-user@ip-172-31-34-163 agent]$ ls
SELinuxPolicy                authorizedkeys  conf         dt_fips_disabled.flag  installer.version  lib64      rdp  tools
THIRDPARTYLICENSEREADME.txt  bin             datasources  initscripts            lib                libmusl64  res  uninstall.sh
[ec2-user@ip-172-31-34-163 agent]$ ls tools/
data  dynatrace_ingest  lib64  oneagentctl
[ec2-user@ip-172-31-34-163 agent]$ 
[ec2-user@ip-172-31-34-163 agent]$ sudo ./tools/oneagentctl  -v
1.321.51.20250905-075429
[ec2-user@ip-172-31-34-163 agent]$ sudo ./tools/oneagentctl --get-monitoring-mode  
fullstack
[ec2-user@ip-172-31-34-163 agent]$ 

```