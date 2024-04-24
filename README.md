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



## RESULT:
The Metasploit framework for reconnaissance is  examined successfully
