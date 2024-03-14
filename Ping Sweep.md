# SKIP IF YOU CREATED INTERNAL, PING_SWEEP AND TARGETS FOLDERS

### (VICTIM) 
```
for i in {1..254}; do (ping -c 1 192.168.1.$i | grep "bytes from" &); done
```
Copy and save
### (ATTACKER) 

```
mkdir internal
```

```
cd internal
```

```
ls
```

```
nano ping_sweep
```

```
cat ping_sweep
```

```
cat ping_sweep | awk -F ":" '{print $1}'
```

```
cat ping_sweep | awk -F ":" '{print $1}'at ping_sweep | awk -F " " '{print $4}'
```

```
cat ping_sweep | awk -F ":" '{print $1}'at ping_sweep | awk -F " " '{print $4}' | sort -V
```

```
cat ping_sweep | awk -F ":" '{print $1}'at ping_sweep | awk -F " " '{print $4}' | sort -V >> targets
```

```
cat targets
```


You can delete the IP ending in 1.1 "it doesint play nice"


```
cat targets | xargs mkdir 
```

(Making directories so we can share 
information and organize the data better)

```
for i in 192.*;do echo $i > ./$i/scope; done 
```

(Make scope files in each directory so we can use 
these files directly over the proxy)
