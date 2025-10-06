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

### few more details 

```
ec2-user@ip-172-31-34-163 agent]$ systemctl status oneagent
● oneagent.service - Dynatrace OneAgent
     Loaded: loaded (/etc/systemd/system/oneagent.service; enabled; preset: disabled)
     Active: active (running) since Mon 2025-10-06 01:50:56 UTC; 5h 9min ago
   Main PID: 2173 (oneagentwatchdo)
      Tasks: 49 (limit: 4652)
     Memory: 269.2M
        CPU: 2min 4.807s
     CGroup: /system.slice/oneagent.service
             ├─2173 /opt/dynatrace/oneagent/agent/lib64/oneagentwatchdog -bg -config=/opt/dynatrace/oneagent/agent/conf/watchdog.conf
             ├─2181 oneagentos -Dcom.compuware.apm.WatchDogTimeout=900 -watchdog.restart_file_location=/var/lib/dynatrace/oneagent/agent/watch>
             ├─2288 oneagentnetwork -Dcom.compuware.apm.WatchDogTimeout=900 -Dcom.compuware.apm.WatchDogPipe=/var/lib/dynatrace/oneagent/agent>
             ├─2290 oneagentloganalytics -Dcom.compuware.apm.WatchDogTimeout=900 -Dcom.compuware.apm.WatchDogPipe=/var/lib/dynatrace/oneagent/>
             ├─2292 oneagentextensions -Dcom.compuware.apm.WatchDogTimeout=900 -Dcom.compuware.apm.WatchDogPipe=/var/lib/dynatrace/oneagent/ag>
             └─2522 /opt/dynatrace/oneagent/agent/lib64/oneagentebpfdiscovery --log-dir /var/log/dynatrace/oneagent/os/ --log-no-stdout --log->

Oct 06 01:50:55 ip-172-31-34-163.ap-south-1.compute.internal systemd[1]: Starting oneagent.service - Dynatrace OneAgent...
Oct 06 01:50:56 ip-172-31-34-163.ap-south-1.compute.internal oneagent[2174]: 01:50:56 Dynatrace OneAgent service started.
Oct 06 01:50:56 ip-172-31-34-163.ap-south-1.compute.internal systemd[1]: Started oneagent.service - Dynatrace OneAgent.
[ec2-user@ip-172-31-34-163 agent]$ ls /var/log/dynatrace/
oneagent
[ec2-user@ip-172-31-34-163 agent]$ ls /var/log/dynatrace/oneagent/
apache  dumpproc  extensions  installer  loganalytics  network  os  plugin  process  sdk  watchdog
[ec2-user@ip-172-31-34-163 agent]$ 
[ec2-user@ip-172-31-34-163 agent]$ 

```

### having your own UI app to monitor details 

```
sudo cp -rf /var/www/html/webapp1/ /var/www/html/ashuuiapp1

```