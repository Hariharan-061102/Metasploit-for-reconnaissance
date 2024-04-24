# Metasploit-for-reconnaissance
# Metasploit
Metasploit for reconnaissance in pentesting

# AIM:

To get introduced to Metasploit Framework and to  perform reconnaissance  in pentesting .

## DESIGN STEPS:

### Step 1:

Install kali linux either in partition or virtual box or in live mode

### Step 2:

Investigate on the various categories of tools as follows:

### Step 3:

Open terminal and try execute some kali linux commands

## EXECUTION STEPS AND ITS OUTPUT:

Finding the ip address of the attackers system.
```
ifconfig
```
## OUTPUT:
![image](https://github.com/Hariharan-061102/Metasploit-for-reconnaissance/assets/93427270/cf5deb82-f4a6-42a3-8aca-64744a93adb1)

Invoking msfconsole
```
msfconsole 
```
## OUTPUT:
![image](https://github.com/Hariharan-061102/Metasploit-for-reconnaissance/assets/93427270/0568a896-1de3-48b5-a893-0e4b69083cb4)

Type help or a question mark "?" to see the list of all available commands you can use inside msfconsole.

## OUTPUT:
![image](https://github.com/Hariharan-061102/Metasploit-for-reconnaissance/assets/93427270/800b0f80-78c0-4ba8-9225-a931f24448af)

Port Scanning:
Following command is executed for scanning the systems on our local area network with a TCP scan (-sT) looking for open ports between 1 and 1000 (-p1-1000).
```
msf >  nmap -sT 192.168.237.0/24 -p1-1000
```
## OUTPUT:
![image](https://github.com/Hariharan-061102/Metasploit-for-reconnaissance/assets/93427270/3b5d0b57-028f-42a2-aaaa-173df17229bb)

Metasploit has a multitude of scanning modules built in. If we open another terminal, we can navigate to Metasploit's auxiliary modules and list all the scanner modules.
```
cd /usr/share /metasploit-framework/modules/auxiliary
kali > ls -l
```

## OUTPUT:
![image](https://github.com/Hariharan-061102/Metasploit-for-reconnaissance/assets/93427270/374108e3-0804-4885-9554-8be1c5277ea2)

Search is a powerful command in Metasploit that you can use to find what you want to locate. 
```
msf >search name:Microsoft type:exploit
```
## OUTPUT:
![image](https://github.com/Hariharan-061102/Metasploit-for-reconnaissance/assets/93427270/d4fa23d6-d4cc-4853-85d6-66307e8c103f)

The info command provides information regarding a module or platform.

## OUTPUT:
![image](https://github.com/Hariharan-061102/Metasploit-for-reconnaissance/assets/93427270/41548c2f-7414-45be-ab33-241bc85c28e8)

Before beginning, set up the Metasploit database by starting the PostgreSQL server and initialize msfconsole database as follows:
```
systemctl start postgresql
msfdb init
```
## MYSQL ENUMERATION
Find the IP address of the Metasploitable machine first. Then, use the db_nmap command in msfconsole with Nmap flags to scan the MySQL database at 3306 port.
```
db_nmap -sV -sC -p 3306 <metasploitable_ip_address>
```
## OUTPUT:
![image](https://github.com/Hariharan-061102/Metasploit-for-reconnaissance/assets/93427270/7138d821-0612-453b-8eac-11f2923ba638)


Use the db-nmap command to scan and save the results into Metasploit's postgresql attached database. In that way, you can use those results in the exploitation stage later.
scan the targets with the command db_nmap as follows.
```
msf > db_nmap 192.168.181.0/24
```
if the database is not connected start the service by the following commands.
```
udo service postgresql start
```
![image](https://github.com/Hariharan-061102/Metasploit-for-reconnaissance/assets/93427270/0003c106-bc07-4cf0-ace2-1c7b2bb70505)

Use the search option to look for an auxiliary module to scan and enumerate the MySQL database.
```
search type:auxiliary mysql
```
## OUTPUT:
![image](https://github.com/Hariharan-061102/Metasploit-for-reconnaissance/assets/93427270/b334ac2c-ad84-4b97-b945-489ff3d08440)



use the auxiliary/scanner/mysql/mysql_version module by typing the module name or associated number to scan MySQL version details.
```
use 11
```
or 
```
use auxiliary/scanner/mysql/mysql_version
```
## OUTPUT:
![image](https://github.com/Hariharan-061102/Metasploit-for-reconnaissance/assets/93427270/74491c26-92b0-4fc3-a535-0a7aa51ef167)

Use the set rhosts command to set the parameter and run the module, as follows:
```
set rhosts 192.168.120.142
```
## OUTPUT:
![image](https://github.com/Hariharan-061102/Metasploit-for-reconnaissance/assets/93427270/1b27bf3a-cc98-4638-b6cc-ee7e494e5b75)

After scanning, you can also brute force MySQL root account via Metasploit's auxiliary(scanner/mysql/mysql_login) module.

## OUTPUT:
![image](https://github.com/Hariharan-061102/Metasploit-for-reconnaissance/assets/93427270/d1f21e01-bd40-4bbb-82ff-0b3d760d6c9c)

set the PASS_FILE parameter to the wordlist path available inside /usr/share/wordlists
```
set PASS_FILE /usr/share/wordlists/rockyou.txt
```
Then, specify the IP address of the target machine with the RHOSTS command.
```
set RHOSTS <metasploitable-ip-address>
```
Set BLANK_PASSWORDS to true in case there is no password set for the root account.
```
set BLANK_PASSWORDS true
```
## OUTPUT:
![image](https://github.com/Hariharan-061102/Metasploit-for-reconnaissance/assets/93427270/56677963-3a00-42e3-8d5d-4a446ab2ccde)


## RESULT:
The Metasploit framework for reconnaissance is  examined successfully
